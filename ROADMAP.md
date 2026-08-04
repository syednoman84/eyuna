# Roadmap

This roadmap tracks Eyuna's development in numbered releases. Each release adds one major capability layer on top of a stable foundation. Releases are additive — later releases assume earlier ones are complete and stable.

Status legend: `Not Started` · `In Progress` · `Complete`

## Table of Contents

- [Release 1.0 — Foundation](#release-10--foundation)
- [Release 2.0 — Consulting Personas](#release-20--consulting-personas)
- [Release 3.0 — Prompt Engine](#release-30--prompt-engine)
- [Release 4.0 — Templates](#release-40--templates)
- [Release 5.0 — Customer Support Case Study](#release-50--customer-support-case-study)
- [Engineering Execution](#engineering-execution)
- [Release 6.0 — Industry Playbooks](#release-60--industry-playbooks)

---

## Release 1.0 — Foundation

**Status:** In Progress

Establish the repository itself: structure, governance, and documentation scaffolding that every future release depends on.

**Milestones**

- [x] Define top-level repository structure
- [x] Create root documentation (README, ROADMAP, CHANGELOG, DECISIONS, PROJECT_STATUS, CONTRIBUTING, LICENSE)
- [x] Create `docs/` placeholders (Constitution, ACM Methodology, Consulting Principles, Governance, Glossary)
- [x] Create README documentation for every major directory
- [ ] Author the Eyuna Constitution
- [ ] Author the ACM (AI Consulting Methodology) framework
- [ ] Author Consulting Principles
- [ ] Author Governance model
- [ ] Author Glossary of terms

## Release 2.0 — Consulting Personas

**Status:** In Progress

Define the reusable consulting personas (client-facing and internal) used consistently across engagements.

**Milestones**

- [x] Define persona taxonomy and template — defined in [WO-002 — Persona Standard](work-orders/governance/WO-002-Persona-Standard.md) (persona categories and the standard 15-section document structure)
- [x] Author core internal personas (e.g., engagement lead, AI architect, delivery consultant) — three authored: [Senior Business Analyst](personas/senior-business-analyst.md), [Solution Architect](personas/solution-architect.md), [AI Software Engineer](personas/ai-software-engineer.md)
- [ ] Author core client-facing personas (e.g., sponsor, technical stakeholder, end user)
- [x] Document persona usage guidance in `personas/README.md`

## Release 3.0 — Prompt Engine

**Status:** Not Started

Build the reusable prompt library that powers engagement work.

**Milestones**

- [ ] Define prompt library taxonomy and metadata standard
- [ ] Author discovery-phase prompt sets
- [ ] Author analysis and design-phase prompt sets
- [ ] Author delivery and QA-phase prompt sets
- [ ] Document versioning and evaluation approach for prompts

## Release 4.0 — Templates

**Status:** Not Started

Produce standardized engagement and deliverable templates.

**Milestones**

- [ ] Define template taxonomy (proposal, SOW, discovery, architecture, delivery, retrospective)
- [ ] Author core engagement lifecycle templates
- [ ] Author deliverable and reporting templates
- [ ] Document template usage guidance in `templates/README.md`

## Release 5.0 — Customer Support Case Study

**Status:** In Progress

Document a full, end-to-end reference case study applying the ACM methodology, personas, prompts, and templates to a customer support AI engagement.

**Milestones**

- [ ] Define case study documentation standard
- [ ] Author the customer support case study end-to-end — Discovery, Requirements, Solution Architecture, Implementation Plan, and Engineering Design are complete; production implementation, deployment, and content deliverables continue under **Engineering Execution** below
- [ ] Cross-link case study to the methodology, personas, prompts, and templates it uses
- [ ] Capture lessons learned and refinements back into earlier releases

---

## Engineering Execution

**Status:** Not Started

Turn the Customer Support Email Automation case study's approved [Implementation Plan](case-studies/customer-support-email-automation/implementation/implementation-plan.md) and [Engineering Design](case-studies/customer-support-email-automation/implementation/engineering-design.md) into running software. This is the active next phase following v1.0.0 — planning is complete, execution has not started.

**Milestones**

- [ ] Repository scaffolding — monorepo structure, module layout, and CI pipeline skeleton per the Implementation Plan's [Repository Strategy](case-studies/customer-support-email-automation/implementation/implementation-plan.md#3-repository-strategy)
- [ ] Shared libraries — `ai-capability-interface`, `pii-minimization`, `business-rules-client`, `event-contracts`
- [ ] Sprint 1 — foundation libraries, `business-rules-store`, `audit-logging-service`, and shadow-mode `classification-service`
- [ ] Sprint 2 — shadow-mode `priority-service`; begin capturing baseline metrics
- [ ] Sprints 3–8 — human-approved routing and escalation, then AI-assisted drafting, per the [Sprint Plan](case-studies/customer-support-email-automation/implementation/implementation-plan.md#13-sprint-plan)
- [ ] Production implementation — full Implementation Package delivered and promoted beyond shadow mode

## Release 6.0 — Industry Playbooks

**Status:** Not Started

Generalize the methodology into repeatable, industry-specific playbooks.

**Milestones**

- [ ] Define playbook taxonomy and template
- [ ] Author first industry playbook
- [ ] Author second industry playbook
- [ ] Document playbook usage guidance in `playbooks/README.md`

---

For the current in-flight status of these milestones, see [PROJECT_STATUS.md](PROJECT_STATUS.md). For the reasoning behind major structural or methodological choices, see [DECISIONS.md](DECISIONS.md).
