# Project Status

This is the live dashboard for Eyuna. It reflects what exists today, what is actively being worked on, and what is planned next. For the full multi-release plan, see [ROADMAP.md](ROADMAP.md).

**Last updated:** 2026-08-04

## Current Version

**v1.0.0 — Framework Complete**

The Work Order governance mechanism, the persona framework, and the Customer Support Email Automation case study's full Assess → Create planning lifecycle (Discovery, Requirements, Solution Architecture, and Engineering Planning) are complete. Engineering Execution is now the active phase. See [CHANGELOG.md](CHANGELOG.md) for full release notes.

## Completed

**Governance**

- [WO-001 — Eyuna Work Order Standard](work-orders/governance/WO-001-Work-Order-Standard.md) — `Approved`. The governance standard defining how all work in Eyuna is initiated, assigned, executed, reviewed, and approved.
- [WO-002 — Eyuna Persona Standard](work-orders/governance/WO-002-Persona-Standard.md) — `Approved`. The governance standard defining what a persona is, its lifecycle, and its required structure. Promoted from Draft to Approved now that three personas have been authored and reviewed against it.

**Persona Framework**

- [Senior Business Analyst](personas/senior-business-analyst.md) — `Approved`. Leads the ACM Assess phase.
- [Solution Architect](personas/solution-architect.md) — `Approved`. Leads the ACM Create phase.
- [AI Software Engineer](personas/ai-software-engineer.md) — `Approved`. Leads the ACM Modernize phase.

**Customer Support Email Automation — Planning Lifecycle**

- [WO-101 — Customer Support Discovery](work-orders/delivery/WO-101-Customer-Support-Discovery.md) — `Approved`. Discovery is complete: [discovery-document.md](case-studies/customer-support-email-automation/discovery/discovery-document.md).
- [WO-102 — Customer Support Requirements](work-orders/delivery/WO-102-Customer-Support-Requirements.md) — `Approved`. Requirements are complete: [requirements-specification.md](case-studies/customer-support-email-automation/requirements/requirements-specification.md).
- [WO-103 — Customer Support Solution Architecture](work-orders/delivery/WO-103-Customer-Support-Solution-Architecture.md) — `Approved`. Solution Architecture is complete: [solution-architecture.md](case-studies/customer-support-email-automation/architecture/solution-architecture.md).
- [WO-104 — Customer Support Implementation](work-orders/delivery/WO-104-Customer-Support-Implementation.md) — `Approved`. Engineering Planning is complete: [implementation-plan.md](case-studies/customer-support-email-automation/implementation/implementation-plan.md) and [engineering-design.md](case-studies/customer-support-email-automation/implementation/engineering-design.md).

## In Progress

- **Engineering Execution** — now the active phase for the Customer Support Email Automation case study: turning the approved Implementation Plan and Engineering Design into running software (repository scaffolding, shared libraries, Sprint 1). See the **Engineering Execution** section in [ROADMAP.md](ROADMAP.md).
- Repository Initialization — directory-level READMEs are complete; `docs/` foundational content is not (see Upcoming).

## Upcoming

- Constitution (`docs/constitution.md`) — placeholder, not yet authored.
- ACM Methodology narrative (`docs/acm-methodology.md`) — placeholder, not yet authored.
- Consulting Principles (`docs/consulting-principles.md`) — placeholder, not yet authored.
- Governance model (`docs/governance.md`) — placeholder, not yet authored. *(Distinct from the Work Order/Persona governance mechanism above, which is complete — this is the constitutional "how Eyuna itself is governed" document.)*
- Glossary (`docs/glossary.md`) — placeholder, not yet authored.
- Client-facing personas (sponsor, technical stakeholder, end user) — Release 2.0 remainder.
- Prompt Engine (Release 3.0), Templates (Release 4.0), Industry Playbooks (Release 6.0) — not started.
- Customer Support case study: production implementation, deployment, website case study, LinkedIn content, and lessons learned — not started.

## Notes

- "Framework Complete" describes the Work Order governance mechanism, the persona framework, and the case study's planning lifecycle — it does not mean every roadmap release is finished. The `docs/` constitutional layer and Releases 2.0 (remainder), 3.0, 4.0, and 6.0 remain open; see [ROADMAP.md](ROADMAP.md).
- Case study deliverables (Discovery, Requirements, Solution Architecture, Implementation Plan, Engineering Design) carry an internal document status of `Draft — Pending Client Review` — they are content-complete but have not been through a formal external client sign-off.
- Update this file whenever a milestone in [ROADMAP.md](ROADMAP.md) changes status.
