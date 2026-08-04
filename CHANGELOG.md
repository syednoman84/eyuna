# Changelog

All notable changes to Eyuna are documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/), and this project follows the release numbering defined in [ROADMAP.md](ROADMAP.md) rather than strict Semantic Versioning, since Eyuna is a documentation and asset framework, not versioned software.

## [Unreleased]

Work toward Release 1.0's remaining Foundation milestone (authoring the Constitution, ACM Methodology narrative, Consulting Principles, Governance model, and Glossary content in `docs/`) and toward Release 2.0's remaining client-facing personas.

## [1.0.0] - 2026-08-04

### Summary

This release marks the completion of the first version of the Eyuna Consulting Operating System: the Work Order governance mechanism is approved and proven, three reference consulting personas are authored and approved, and a complete Assess → Create engagement lifecycle (Discovery, Requirements, Solution Architecture, Implementation Plan, and Engineering Design) has been produced end-to-end for the Customer Support Email Automation reference case study using that mechanism. Engineering Execution — turning the approved implementation plan and engineering design into running software — is the next active phase and is explicitly out of scope for this release.

### Major Capabilities Delivered

- A proven, end-to-end Work Order lifecycle (Draft → Review → Approved → Assigned → In Progress → Completed → Quality Review → Accepted → Published) exercised across five real Work Orders (WO-001, WO-002, WO-101–WO-104).
- A repeatable Assess → Create engagement pattern: Discovery → Requirements → Solution Architecture → Implementation Plan → Engineering Design, each with full traceability back to the previous phase's findings.
- Three approved, reusable consulting personas spanning the Assess, Create, and Modernize ACM phases.
- A first full reference case study (Customer Support Email Automation) demonstrating the entire framework in practice, ready to hand off to Engineering Execution.

### Governance Artifacts

- [WO-001 — Eyuna Work Order Standard](work-orders/governance/WO-001-Work-Order-Standard.md) — `Approved`. Defines the Work Order lifecycle, structure, and governance model used by every other artifact in this release.
- [WO-002 — Eyuna Persona Standard](work-orders/governance/WO-002-Persona-Standard.md) — `Approved`. Defines the standard structure, responsibilities, and lifecycle for all consulting personas; promoted from Draft to Approved as part of this release now that three personas have been authored and reviewed against it.
- [WO-101 — Customer Support Discovery](work-orders/delivery/WO-101-Customer-Support-Discovery.md), [WO-102 — Customer Support Requirements](work-orders/delivery/WO-102-Customer-Support-Requirements.md), [WO-103 — Customer Support Solution Architecture](work-orders/delivery/WO-103-Customer-Support-Solution-Architecture.md), [WO-104 — Customer Support Implementation](work-orders/delivery/WO-104-Customer-Support-Implementation.md) — all `Approved`.

### Personas

- [Senior Business Analyst](personas/senior-business-analyst.md) — `Approved`. Leads the Assess phase; authored WO-101 and WO-102's deliverables.
- [Solution Architect](personas/solution-architect.md) — `Approved`. Leads the Create phase; authored WO-103's Solution Architecture.
- [AI Software Engineer](personas/ai-software-engineer.md) — `Approved`. Leads the Modernize phase; authored WO-104's Implementation Plan and Engineering Design.

### Customer Support Case Study Artifacts

- [Discovery Document](case-studies/customer-support-email-automation/discovery/discovery-document.md) — business problem, current-state assessment, stakeholder analysis, AI opportunity assessment, and executive recommendations.
- [Requirements Specification](case-studies/customer-support-email-automation/requirements/requirements-specification.md) — 13 business requirements, 23 functional requirements, 10 non-functional requirements, full traceability to Discovery.
- [Solution Architecture](case-studies/customer-support-email-automation/architecture/solution-architecture.md) — logical architecture, AI architecture, data flow, security, deployment, scalability, and ADR summary, all traced to approved requirements.
- [Implementation Plan](case-studies/customer-support-email-automation/implementation/implementation-plan.md) — service decomposition, repository strategy, sprint plan, engineering backlog, dependency graph, and delivery roadmap.
- [Engineering Design](case-studies/customer-support-email-automation/implementation/engineering-design.md) — service catalog, shared library contracts, API/event/database design standards, and per-service implementation sequence.

### Repository Improvements

- Corrected Markdown navigation defects across the delivery Work Orders and newer personas: non-functional Tables of Contents converted to working anchor links, and duplicate heading text that caused anchor collisions (most notably an `Assigned Persona` grouping label silently shadowing the real `Assigned Persona` section) resolved throughout WO-102, WO-103, WO-104, and `solution-architect.md`.
- Added missing cross-references (to `WO-002`, the ACM Methodology, and relevant Work Orders) across personas and delivery Work Orders that previously had no outbound links.
- Added the standard Authority and Accountability statement to `solution-architect.md` and `ai-software-engineer.md`, aligning both with the pattern established in `senior-business-analyst.md`.
- Kept `personas/README.md` and `work-orders/README.md` indexes current as each new persona and Work Order was added.
- Corrected this changelog's own version history: the original `[1.0.0]` entry documented only the initial repository scaffold and did not correspond to the `v0.1.0` git tag actually cut at that point — it has been relabeled `[0.1.0]` below so the changelog and git tag history agree.

### Known Limitations

- The `docs/` foundational documents — Constitution, ACM Methodology narrative, Consulting Principles, Governance model, and Glossary — remain unauthored placeholders. "Governance" in this release refers specifically to the Work Order and Persona standards (WO-001, WO-002), not this constitutional layer, which is still tracked as an open Release 1.0 milestone in [ROADMAP.md](ROADMAP.md).
- Case study deliverables under `discovery/`, `requirements/`, `architecture/`, and `implementation/` carry a document status of `Draft — Pending Client Review` — they are complete and internally consistent, but have not gone through a formal external client sign-off step.
- Client-facing personas (sponsor, technical stakeholder, end user) are not yet authored; only internal/delivery personas exist.
- No source code, infrastructure-as-code, or CI/CD pipeline definitions exist yet anywhere in the repository — this is intentional and explicitly out of scope through WO-104.
- Prompts, Templates, and Playbooks (Releases 3.0, 4.0, 6.0) remain unstarted.

### Next Milestone — Engineering Execution

The next phase turns [WO-104](work-orders/delivery/WO-104-Customer-Support-Implementation.md)'s Implementation Plan and Engineering Design into running software: repository scaffolding, the shared libraries (`ai-capability-interface`, `pii-minimization`, `business-rules-client`, `event-contracts`), and Sprint 1 of the phased delivery sequence defined in the [Implementation Plan](case-studies/customer-support-email-automation/implementation/implementation-plan.md#13-sprint-plan). See the new **Engineering Execution** section in [ROADMAP.md](ROADMAP.md) for the full breakdown.

## [0.1.0] - 2026-08-01

### Added

- Initial repository structure: `docs/`, `personas/`, `prompts/`, `templates/`, `playbooks/`, `case-studies/`, `architectures/`, `starter-projects/`, `reusable-components/`, `tools/`, `content/`, `assets/`, `scripts/`
- Root documentation: `README.md`, `ROADMAP.md`, `PROJECT_STATUS.md`, `DECISIONS.md`, `CONTRIBUTING.md`
- `LICENSE` (MIT)
- `.gitignore`
- `README.md` in every major directory explaining its purpose, contents, and role within Eyuna
- Placeholder documents in `docs/` for the Constitution, ACM Methodology, Consulting Principles, Governance, and Glossary
