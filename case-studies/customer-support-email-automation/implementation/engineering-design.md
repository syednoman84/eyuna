# Engineering Design — Customer Support Email Automation

| Property            | Value                                                                                                     |
| -------------------- | ------------------------------------------------------------------------------------------------------------ |
| Case Study            | [Customer Support Email Automation](../README.md)                                                         |
| Work Order            | [WO-104 — Customer Support Implementation](../../../work-orders/delivery/WO-104-Customer-Support-Implementation.md) |
| Source Implementation Plan | [Implementation Plan](implementation-plan.md)                                                          |
| Source Architecture   | [Solution Architecture](../architecture/solution-architecture.md)                                          |
| Prepared By           | AI Software Engineer                                                                                        |
| ACM Phase             | Modernize                                                                                                    |
| Status                | Draft — Pending Client Review                                                                                |
| Version               | 1.0                                                                                                           |
| Date                  | 2026-08-03                                                                                                    |

---

## Table of Contents

- [1. Purpose and How to Use This Document](#1-purpose-and-how-to-use-this-document)
- [2. Service Catalog](#2-service-catalog)
- [3. Shared Libraries](#3-shared-libraries)
- [4. Package Structure](#4-package-structure)
- [5. API Design Standards](#5-api-design-standards)
- [6. Event Design](#6-event-design)
- [7. Database Ownership](#7-database-ownership)
- [8. Configuration Strategy](#8-configuration-strategy)
- [9. Error Handling](#9-error-handling)
- [10. Logging](#10-logging)
- [11. Security Design](#11-security-design)
- [12. Testing Design](#12-testing-design)
- [13. CI/CD Design](#13-cicd-design)
- [14. Coding Standards](#14-coding-standards)
- [15. Development Workflow](#15-development-workflow)
- [16. Implementation Sequence](#16-implementation-sequence)
- [17. Engineering Handoff](#17-engineering-handoff)

---

## 1. Purpose and How to Use This Document

This document is the concrete engineering blueprint beneath the [Solution Architecture](../architecture/solution-architecture.md) and the [Implementation Plan](implementation-plan.md). It assumes both have already been read and does not restate the business requirements, the architecture's component rationale, or the sprint/release sequencing already defined in the Implementation Plan.

What follows is **how any developer builds any service consistently** — naming conventions, contracts, package layout, and per-service build order — so that two engineers working on different services independently produce code that fits together without a design conversation. Nothing in this document generates source code or infrastructure-as-code; it defines the shape that code and infrastructure must take when it is written.

---

## 2. Service Catalog

Each entry is the technical reference for one deployable unit. "Owns" refers to the database schema detailed in [Section 7](#7-database-ownership).

| Service                    | Module Path                       | API Base Path                | Owns Schema            | Depends On (sync)                          | Publishes Events                          | Consumes Events                    |
| ------------------------------- | -------------------------------------- | -------------------------------- | -------------------------- | ---------------------------------------------- | ---------------------------------------------- | --------------------------------------- |
| `ingestion-gateway`               | `services/ingestion-gateway`             | `/v1/intake`                       | `intake`                     | —                                                 | `EmailReceived`                                  | —                                          |
| `classification-service`          | `services/classification-service`        | `/v1/classifications`              | `classification`             | `ai-capability-interface`, `business-rules-client` | `EmailClassified`                                | `EmailReceived`                            |
| `priority-service`                | `services/priority-service`              | `/v1/priorities`                   | `priority`                    | `ai-capability-interface`, `business-rules-client` | `PriorityAssigned`                               | `EmailClassified`                          |
| `routing-service`                 | `services/routing-service`               | `/v1/routing`                      | `routing`                     | `business-rules-client`                            | `RoutingDecided`                                 | `PriorityAssigned`                         |
| `escalation-service`              | `services/escalation-service`            | `/v1/escalations`                  | `escalation`                  | `business-rules-client`, `approval-gate-service` (sync) | `EscalationRecommended`                          | `RoutingDecided`                           |
| `drafting-service`                | `services/drafting-service`              | `/v1/drafts`                       | `drafting`                    | `ai-capability-interface`                          | `DraftGenerated`                                 | `RoutingDecided`                           |
| `duplicate-detection-service`     | `services/duplicate-detection-service`   | `/v1/duplicates`                   | `duplicate_detection`         | `ai-capability-interface`                          | `DuplicateFlagged`                               | `RoutingDecided`                           |
| `approval-gate-service`           | `services/approval-gate-service`         | `/v1/approvals`                    | `approval`                    | —                                                 | `ApprovalDecided`                                | `EscalationRecommended`, `DraftGenerated`  |
| `business-rules-store`            | `services/business-rules-store`          | `/v1/rules`                        | `rules`                       | —                                                 | `RuleUpdated`                                    | —                                          |
| `audit-logging-service`           | `services/audit-logging-service`         | `/v1/audit`                        | `audit`                       | —                                                 | —                                                 | *(all pipeline event types)*                |
| `reporting-service`               | `services/reporting-service`             | `/v1/reports`                      | `reporting`                   | —                                                 | —                                                 | *(all pipeline event types, read-only)*     |
| `agent-review-workspace`          | `web/agent-review-workspace`             | *(frontend, no API of its own)*     | —                              | `approval-gate-service`, `routing-service`, `duplicate-detection-service` (via their APIs) | —                                 | —                                          |

**Reading the "Depends On (sync)" column:** every other relationship between services is event-driven (see [Section 6](#6-event-design)). The only synchronous, blocking calls in the system are to a shared library, to `business-rules-client` (reading current rules), and `escalation-service`'s call into `approval-gate-service` to check for an existing decision — everything else on the happy path is asynchronous by design.

---

## 3. Shared Libraries

Every service consumes these as versioned dependencies, not copy-pasted code. A service may not implement its own version of any capability listed here.

### `ai-capability-interface`

```java
interface AiCapability {
    ClassificationResult classify(EmailContent content);
    PriorityResult assignPriority(EmailContent content, ClassificationResult classification);
    DraftResult generateDraft(EmailContent content, RoutingResult routing);
    SimilarityResult findSimilar(EmailContent content, List<TicketReference> recentTickets);
}
```

- Every result type carries a `confidence` field (`0.0`–`1.0`) and a `modelIdentifier` field (which model/version produced it) — no result type may omit either.
- No service may import a vendor LLM SDK directly. Only the implementation module behind this interface may do so. This is the one rule in this document with zero exceptions: it is what keeps the AI provider swappable.
- Callers must treat every method as potentially slow and potentially failing — see [Section 9](#9-error-handling) for the required timeout/circuit-breaker wrapping.

### `pii-minimization`

```java
interface PiiMinimizer {
    String redact(String rawText);
    <T> T maskForLog(T dto);
    boolean containsPii(String rawText);
}
```

- DTOs that carry potentially sensitive fields are annotated `@PiiField` on those fields; `maskForLog` uses reflection over that annotation so a developer cannot forget to mask a new field — they only have to remember to annotate it.
- `redact` is used before any content crosses a service boundary into a component that does not need the raw content (e.g., `reporting-service` never receives unredacted email bodies).

### `business-rules-client`

```java
interface RulesClient {
    PriorityCriteria getPriorityCriteria();
    RoutingCriteria getRoutingCriteria();
    EscalationCriteria getEscalationCriteria();
    SensitiveCommunicationDefinition getSensitiveDefinition();
}
```

- Implements a short-TTL local cache (default 60 seconds) invalidated early on a `RuleUpdated` event, so services see rule changes quickly without querying `business-rules-store` on every request.
- Every returned criteria object carries the `ruleVersion` it was resolved from, which callers must attach to whatever decision they make — this is how a classification or routing decision stays traceable to the exact rule version in effect (feeds the audit record, not re-derived here).

### `event-contracts`

- Contains the shared event envelope type and one payload type per event listed in [Section 6](#6-event-design).
- Is the **only** place event schemas are defined. A service must not define its own copy of an event payload type.

---

## 4. Package Structure

Every backend service follows the same internal package layout, so switching between services requires no re-orientation:

```text
com.eyuna.customersupport.<service>
├── api            # controllers, request/response DTOs — never expose domain or persistence types here
├── domain          # domain model, pure business logic, no framework annotations
├── service          # orchestration: calls domain logic, shared libraries, repositories, event publishers
├── repository        # persistence layer, one repository interface per owned table
├── event
│   ├── publisher      # translates a domain outcome into an event-contracts payload and publishes it
│   └── consumer       # translates an inbound event into a call into the service layer
└── config             # startup configuration binding (see Section 8)
```

Shared libraries live under `com.eyuna.customersupport.shared.<library-name>` and expose only interfaces plus DTOs from their root package — implementation classes are package-private so a consuming service cannot accidentally depend on internals.

The frontend (`agent-review-workspace`) follows a feature-folder convention: `src/features/<feature>/{components,hooks,api}`, with a single `src/api/client.ts` responsible for attaching the auth token ([Section 11](#11-security-design)) and correlation ID ([Section 10](#10-logging)) to every request, so no individual feature re-implements request plumbing.

---

## 5. API Design Standards

- **Resource naming:** plural nouns, kebab-case paths (`/v1/classifications`, not `/v1/classification` or `/v1/getClassification`).
- **HTTP verbs:** `POST` to create a decision record, `GET` to read it, `PATCH` for an agent override (e.g., correcting a classification) — never `POST` for a read or `GET` with side effects.
- **Status codes:** `201` on creation, `200` on read/override, `202` when a request is accepted for async processing rather than resolved synchronously (e.g., a drafting request that is queued), `409` when an operation conflicts with existing state (e.g., approving an already-approved item), `422` for a well-formed request that fails business validation, `502`/`503` for downstream failures per [Section 9](#9-error-handling).
- **Standard error envelope**, used by every service:

```json
{
  "error": {
    "code": "STRING_ENUM",
    "message": "human-readable, safe to display to an engineer, never contains PII",
    "correlationId": "uuid",
    "details": {}
  }
}
```

- **Standard confidence-bearing response shape**, used by every AI-backed endpoint (classification, priority, routing, duplicate detection):

```json
{
  "result": {},
  "confidence": 0.0,
  "modelIdentifier": "string",
  "ruleVersion": "string-or-null"
}
```

- **Idempotency:** every `POST` endpoint that can be triggered by event replay (i.e., anything consuming from the pipeline) requires an `Idempotency-Key` header; the service persists a short-lived record of keys it has already processed and returns the original result on replay rather than reprocessing.
- **Correlation:** every request and every published event carries a `correlationId` that is generated once at `ingestion-gateway` and propagated unchanged through the entire pipeline — this is the join key across services, logs, and audit records.
- **Versioning:** breaking changes to a response shape require a new path version (`/v2/...`); additive fields do not require a version bump.

---

## 6. Event Design

### Envelope

Every event, regardless of type, is wrapped identically:

```json
{
  "eventId": "uuid",
  "eventType": "EmailClassified",
  "eventVersion": 1,
  "occurredAt": "ISO-8601 timestamp",
  "correlationId": "uuid",
  "ticketId": "string",
  "payload": {}
}
```

### Event Catalog

| Event                  | Published By                 | Payload Contains (shape lives in `event-contracts`)             |
| --------------------------- | --------------------------------- | ---------------------------------------------------------------------- |
| `EmailReceived`               | `ingestion-gateway`                  | Redacted content reference, channel metadata                             |
| `EmailClassified`              | `classification-service`             | Category, confidence, model identifier, rule version                     |
| `PriorityAssigned`             | `priority-service`                   | Priority level, confidence, rule version                                  |
| `RoutingDecided`                | `routing-service`                    | Target team/queue, confidence, rule version                               |
| `EscalationRecommended`         | `escalation-service`                 | Escalation reason, target approver role                                   |
| `DraftGenerated`                 | `drafting-service`                   | Draft reference (not raw content), confidence, model identifier            |
| `DuplicateFlagged`               | `duplicate-detection-service`        | Candidate ticket ID(s), similarity score                                   |
| `ApprovalDecided`                | `approval-gate-service`              | Decision (approved/edited/rejected), deciding agent ID, timestamp          |
| `RuleUpdated`                     | `business-rules-store`               | Rule category, new version identifier                                      |
| `ActionWrittenBack`               | `ingestion-gateway`                  | Action taken, target system reference                                      |

### Rules

- **Naming:** past-tense, domain-meaningful verbs. Never `<Entity>Updated` for something that has a more specific meaning (`RoutingDecided`, not `RoutingUpdated`).
- **Topic/queue naming:** `triage.<event-type-in-kebab-case>.v<eventVersion>` (e.g., `triage.email-classified.v1`). A schema-breaking change gets a new topic (`.v2`), so old and new consumers can run side by side during migration.
- **Consumer groups:** one consumer group per consuming service (`audit-logging-service` and `reporting-service` each get their own group on every topic, since both need every event independently).
- **Delivery guarantee:** at-least-once. Every consumer must be idempotent against redelivery of the same `eventId` — this is a required property of the consumer, not an edge case to handle later.
- **Failure handling:** a consumer that fails to process an event retries with exponential backoff (starting 1s, capped at 5 attempts); after exhausting retries the event moves to `<topic>.dlq` and the failure is logged at `ERROR` with the full envelope (minus PII, per [Section 10](#10-logging)) for manual triage.
- **Schema evolution:** within a version, only additive, optional fields may be introduced. Removing or repurposing a field requires a new `eventVersion`.

---

## 7. Database Ownership

| Schema                | Owning Service              | Representative Tables                                  |
| -------------------------- | -------------------------------- | ------------------------------------------------------------ |
| `intake`                     | `ingestion-gateway`                 | `inbound_events`, `writeback_actions`                            |
| `classification`             | `classification-service`            | `classifications`, `classification_overrides`                     |
| `priority`                    | `priority-service`                   | `priority_assignments`                                            |
| `routing`                      | `routing-service`                    | `routing_decisions`                                                |
| `escalation`                    | `escalation-service`                 | `escalation_recommendations`                                       |
| `drafting`                       | `drafting-service`                   | `drafts`, `draft_revisions`                                        |
| `duplicate_detection`             | `duplicate-detection-service`        | `duplicate_matches`                                                 |
| `approval`                         | `approval-gate-service`              | `approval_requests`, `approval_decisions`                           |
| `rules`                              | `business-rules-store`               | `rule_versions`, `rule_definitions`                                  |
| `audit`                                | `audit-logging-service`              | `decision_events`, `override_events`                                 |
| `reporting`                              | `reporting-service`                  | `metric_rollups` (derived/materialized, not source of truth)          |

**Ownership rules:**

- A service is the only writer to its own schema. Any other service that needs that data gets it from the owning service's API or from the events it publishes — never a direct cross-schema query.
- Cross-service references are stored as opaque IDs (`ticketId`, `classificationId`, etc.), never as a database foreign key into another service's schema — there is no cross-schema referential integrity, by design, because that would recreate the coupling the service boundaries exist to avoid.
- `reporting-service`'s tables are explicitly derived/materialized from events, not a source of truth — if they were lost, they are rebuildable by replaying the event history, they must never be the only copy of a fact.
- Every table storing PII-bearing content carries the retention-support column described in the Implementation Plan's Database Strategy; this document does not repeat that decision, only confirms every owning service listed above is responsible for implementing it in its own schema.

---

## 8. Configuration Strategy

Three distinct kinds of configuration exist, and they are never handled the same way:

| Kind                        | Example                                       | Mechanism                                                                 |
| -------------------------------- | -------------------------------------------------- | -------------------------------------------------------------------------------- |
| **Deployment configuration**       | DB connection string, service hostnames              | Environment variables, injected at deploy time, bound at startup through a single typed configuration class per service (never read raw `System.getenv` scattered through code) |
| **Business configuration**          | Priority/routing/escalation criteria, sensitive-communication definition | Served dynamically by `business-rules-store` via `business-rules-client` ([Section 3](#3-shared-libraries)) — never an environment variable, never baked into a deployment, since it must change without a redeploy |
| **Feature flags**                    | Whether `drafting-service` output may leave shadow mode | A dedicated flag lookup (implementation-time choice of mechanism) consulted at the point of action, not cached for the life of the process, so a flag flip takes effect immediately |

**Startup rule:** every service validates its required deployment configuration at startup and fails fast (does not start) if anything required is missing or malformed — a misconfigured service should never come up and fail requests one at a time in production.

**Naming convention for environment variables:** `<SERVICE_NAME>_<SETTING>` in upper snake case (e.g., `CLASSIFICATION_SERVICE_DB_URL`), namespaced per service even for settings that happen to share a value across services, so services can be reconfigured independently.

---

## 9. Error Handling

### Exception hierarchy (shared base, per-service specifics)

```text
ApplicationException (abstract)
├── ValidationException          → 400
├── NotFoundException             → 404
├── ConflictException              → 409
├── BusinessRuleViolationException  → 422
├── DownstreamServiceException       → 502/503, retryable
└── AiCapabilityException             → see below
```

- A global exception handler in each service's `api` package maps every exception in this hierarchy to the standard error envelope ([Section 5](#5-api-design-standards)); no controller method catches and formats errors individually.

### AI Capability failures

- Every call through `ai-capability-interface` is wrapped with a timeout and a circuit breaker. On timeout, breaker-open, or an `AiCapabilityException`, the caller does **not** retry indefinitely and does **not** drop the request — it routes the item to manual review (the same path used for low-confidence results) and emits the event as normal but flagged `requiresManualReview: true`.
- This is the code-level implementation of the architecture's graceful-degradation behavior: an AI outage degrades the pipeline to "everything needs a human," never to "nothing gets processed."

### Retry and backoff

- Synchronous downstream calls (to a shared library's remote dependency, or `escalation-service`'s call into `approval-gate-service`) use a bounded retry with exponential backoff and jitter, capped at 3 attempts, before surfacing a `DownstreamServiceException`.
- Event consumers follow the retry/DLQ policy defined in [Section 6](#6-event-design), not this synchronous policy.

### Circuit breakers

- Applied to: the `ai-capability-interface` implementation's outbound call, and `ingestion-gateway`'s outbound call to the existing support platform's write-back API. Both are the system's two external dependencies, and both are the two places a slow external system could otherwise cascade into pipeline-wide backpressure.

---

## 10. Logging

- **Format:** structured JSON, one event per line, not free-text. Every log entry from every service carries: `timestamp`, `service`, `level`, `correlationId`, and `ticketId` when applicable.
- **Levels:** `ERROR` — actionable failure requiring attention (DLQ entry, circuit breaker open, startup config failure). `WARN` — degraded but handled automatically (retry succeeded on attempt 2, manual-review fallback triggered). `INFO` — state transitions (event published, event consumed, decision recorded). `DEBUG` — verbose detail, disabled by default in production.
- **The one rule with no exceptions:** raw email content or any `@PiiField`-annotated value must never appear in a log line. Every DTO passed to a logging call must go through `pii-minimization.maskForLog()` first — this is enforced by code review checklist ([Section 15](#15-development-workflow)) and by the architecture-fitness test described in [Section 12](#12-testing-design).
- **Operational logs vs. audit records — not the same thing:** logs (this section) exist for engineers debugging a live issue and are not the compliance record. The compliance-grade record of every automated decision and human override is written by each service to `audit-logging-service` as a first-class, durable write (via the `AuditEvent` events every service publishes), not derived from log files. Losing logs is an operational inconvenience; losing an audit record is not acceptable.
- **Correlation:** because `correlationId` is generated once at `ingestion-gateway` and carried through every event and API call, a single ticket's complete journey across all eleven services can be reconstructed from logs alone by filtering on that one field.

---

## 11. Security Design

- **Service-to-service authentication:** every internal call carries a short-lived signed JWT identifying the calling service, issued by a central token issuer and validated by a shared authentication filter applied identically in every service's `api` package (implemented once, in a shared library, not reimplemented per service).
- **Human authentication:** agents authenticate to `agent-review-workspace`; the workspace attaches the resulting user token to every API call it makes on the agent's behalf, so downstream services see both "which service is calling" and "which human, if any, is behind this action."
- **Authorization:** role checks (`AGENT`, `TEAM_LEAD`, `COMPLIANCE_ADMIN`) are expressed as a declarative annotation on the endpoint (e.g., `@RequiresRole("COMPLIANCE_ADMIN")`) evaluated by the same shared filter that handles authentication — a developer adding a new endpoint declares the required role; they do not write authorization logic by hand.
- **The Approval Gate rule, restated as an implementation constraint:** no service other than `approval-gate-service` may call `ingestion-gateway`'s write-back endpoint for a drafted or sensitive action. This is enforced both by API-level authorization (only `approval-gate-service`'s service identity is authorized to call that endpoint) and by the architecture-fitness test in [Section 12](#12-testing-design) — two independent enforcement mechanisms for the one rule in this system with zero tolerance for exceptions.
- **Secrets:** every service reads secrets only through its typed configuration class ([Section 8](#8-configuration-strategy)), which resolves them from injected environment variables at startup; no secret is ever logged, and no secret is ever passed as a query parameter (headers or request body only).
- **Transport:** TLS on every connection, internal or external, with no plaintext fallback in any environment including local development.

---

## 12. Testing Design

- **Unit tests:** live alongside the code they test, one test class per production class in the `domain` and `service` packages. Minimum coverage gate: 80% line coverage on `domain` and `service` packages, enforced in CI; `api` and `repository` packages are covered primarily by integration and contract tests instead, not unit tests with heavy mocking.
- **Naming convention:** `should_<expectedBehavior>_when_<condition>` — a test name should be readable as a sentence describing the requirement it verifies.
- **Mocking the AI Capability Interface:** every service that depends on `ai-capability-interface` tests against a deterministic fake implementation (fixed inputs → fixed outputs, including a configurable-confidence mode and a configurable-failure mode), never against a live model call, so tests are fast, free, and reproducible.
- **Contract tests:** each service publishes a contract test suite verifying its API/event output matches the schema in `contracts/`; each consuming service runs the producer's contract tests against its own consumption logic before merge, so a breaking change is caught by the producer's CI, not discovered by the consumer in staging.
- **Architecture-fitness tests:** a dedicated, mandatory suite (run in every service's pipeline) that statically verifies structural rules from this document — no class outside `approval-gate-service` calls the write-back endpoint directly; no class outside the AI Capability implementation module imports a vendor LLM SDK; no log statement passes an un-masked `@PiiField`-annotated object. This suite is what makes the rules in this document enforceable rather than aspirational.
- **Test data:** synthetic and anonymized fixtures only, generated or scrubbed before being checked into the repository — no real customer email content or PII in any test fixture, golden-set file, or contract example, ever.
- **Golden-set evaluation:** classification, priority, and duplicate-detection accuracy are tracked against a versioned, human-labeled fixture set stored in `contracts/golden-sets/`; a drop in measured accuracy against the previous baseline fails the relevant service's evaluation job (informational at first, gating once a baseline exists).

---

## 13. CI/CD Design

- **Change scoping:** the pipeline detects which paths changed in a commit and builds/tests/deploys only the affected service(s) — plus every service that depends on a shared library, if the change touched `libs/`. A change confined to one service's `domain` package never triggers a full-monorepo build.
- **Build once, promote the artifact:** each service is built and containerized exactly once per change; the same container image is promoted from staging to production rather than rebuilt for each environment, so what was tested is exactly what ships.
- **Artifact naming:** `<service-name>:<git-sha>`, immutable — no `latest` tag is ever deployed.
- **Required checks before merge** (branch protection, not a suggestion): lint/static analysis, unit tests, contract tests, architecture-fitness suite ([Section 12](#12-testing-design)), security/dependency scan. A pull request cannot merge with any of these failing or skipped.
- **Deployment gate:** promotion from staging to production requires the automated staging smoke suite to pass and a manual approval step — this is a deployment-process gate, distinct from and in addition to the runtime Approval Gate service that governs individual customer-facing actions.
- No pipeline definition files are authored as part of this document — this section defines what a future pipeline configuration must implement.

---

## 14. Coding Standards

- **Naming:** classes `PascalCase`; methods and variables `camelCase`; DTOs suffixed by role (`ClassifyRequest`, `ClassificationResponse`, `EmailClassifiedEvent`) so a type's purpose is legible without opening the file.
- **Dependency injection:** constructor injection only; no field injection, so every class's dependencies are visible in its constructor signature and the class can be instantiated in a test without a framework.
- **Nullability:** `Optional<T>` for any value that may legitimately be absent in the `service`/`domain` layers; raw `null` is not a public API return value.
- **Immutability:** DTOs, event payloads, and domain value objects are immutable (records/final fields); mutation is confined to explicitly stateful domain entities where the state itself is the point (e.g., an `ApprovalRequest`'s status).
- **Layering:** `api` → `service` → `repository`/`domain`, one direction only. A controller never calls a repository directly; a domain class never depends on a framework annotation or a persistence type.
- **DTO/domain separation:** persistence entities never cross the `api` boundary directly — every controller maps to/from a dedicated request/response DTO, even when the mapping looks redundant today, because it decouples the public contract from internal schema changes.
- **Single responsibility:** a class with both "decide what to do" and "call another service to do it" logic is a signal to split it — orchestration and decision logic are kept in distinguishable classes even within the same `service` package.

---

## 15. Development Workflow

- **Branch naming:** `feature/<backlog-item-id>-<short-description>` (e.g., `feature/fr-04-priority-assignment`), so a branch's purpose and traceability are visible without opening the PR.
- **Commits:** Conventional Commits style (`feat:`, `fix:`, `test:`, `refactor:`), referencing the backlog item ID in the body.
- **Pull request checklist** (required in every PR description): linked backlog item ID; tests added/updated; API or event contract updated in `contracts/` if the change touches one; confirmation that no `@PiiField`-annotated data is newly exposed in a log or a response that shouldn't carry it; confirmation that no new call path bypasses `approval-gate-service` for a customer-facing action.
- **Definition of ready** (before a backlog item enters a sprint, per the Implementation Plan's Sprint Plan): the item's API/event contract exists (or is explicitly part of the item's own scope to define), its dependencies per the Implementation Plan's Dependency Graph are already built or are being built in the same sprint.
- **Definition of done** (per pull request, distinct from the Work Order's engagement-level Definition of Done): code reviewed and approved, all required CI checks green, contract and documentation updated, and — for anything touching the Approval Gate, PII handling, or business rules — reviewed by a second engineer familiar with that specific component, per [Section 6 of the Implementation Plan](implementation-plan.md#6-development-standards).

---

## 16. Implementation Sequence

This is the build order **within a single service**, followed identically regardless of which service or which sprint — it is what makes services consistent with each other.

1. **Confirm the contract.** The service's API and/or event contract exists in `contracts/` and matches [Section 5](#5-api-design-standards) / [Section 6](#6-event-design). If it doesn't exist yet, write it first and get it reviewed before writing implementation code.
2. **Domain model.** Define the domain types the service reasons about, with no framework or persistence annotations.
3. **Repository layer.** One repository per owned table ([Section 7](#7-database-ownership)), plus the migration that creates it.
4. **Service layer.** Core logic, calling shared libraries ([Section 3](#3-shared-libraries)) as needed; this is where AI calls, rule lookups, and PII handling happen — never in the `api` or `event` layers directly.
5. **Event publisher/consumer wiring.** Translate service-layer outcomes into `event-contracts` payloads and vice versa.
6. **API controller layer.** Thin — maps HTTP requests to service-layer calls and service-layer results to response DTOs; no business logic lives here.
7. **Error handling and logging wiring.** Apply the shared exception handler ([Section 9](#9-error-handling)) and confirm every log statement passes through `pii-minimization` where relevant ([Section 10](#10-logging)).
8. **Unit tests alongside each layer above** — not deferred to a final "write tests" step; a layer is not considered done until its tests exist.
9. **Contract tests** against the schema confirmed in step 1.
10. **Integration tests** against real or faked dependencies per [Section 12](#12-testing-design).
11. **Service README**, documenting the service's responsibility, its contract references, and anything specific to operating it.
12. **Pull request**, using the checklist in [Section 15](#15-development-workflow).

A service is not "started" until step 1 is complete for it, and is not "done" until step 12 merges with every required check green.

---

## 17. Engineering Handoff

A developer picking up any single backlog item from the Implementation Plan's Engineering Backlog needs, and should expect to find, exactly these things before writing code:

- This document, as the standing reference for contracts, conventions, and build order.
- The relevant service's entry in the [Service Catalog](#2-service-catalog), for its dependencies and owned schema.
- The relevant contract(s) in `contracts/` — existing, or to be authored as step 1 of [Section 16](#16-implementation-sequence).
- The [Implementation Plan's Dependency Graph](implementation-plan.md#15-dependency-graph), to confirm what this service's dependencies expect to already exist.

**What this document deliberately does not provide:** production code, infrastructure-as-code, or pipeline definitions. Those are the output of following this design, not part of it. Any ambiguity a developer finds that this document doesn't resolve should be raised as a design question against this document — not silently decided differently per service, which is precisely the inconsistency this document exists to prevent.
