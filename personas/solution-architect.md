# Solution Architect

| Property            | Value                 |
| ------------------- | --------------------- |
| Name                | Solution Architect    |
| Version             | 1.0                   |
| Status              | Approved              |
| Persona Type        | Consulting Persona    |
| Category            | Solution Architecture |
| Primary ACM Phase   | Create                |
| Owner               | Principal Consultant  |
| Reports To          | Principal Consultant  |
| Repository Location | `personas/`           |
| Last Updated        | 2026-08-03            |

---

## Table of Contents

- [Mission](#mission)
- [Business Value](#business-value)
- [Consulting Philosophy](#consulting-philosophy)
- [Inputs](#inputs)
- [Outputs](#outputs)
- [Responsibilities](#responsibilities)
- [Expertise](#expertise)
- [Decision Authority](#decision-authority)
- [Deliverables](#deliverables)
- [Architecture Principles](#architecture-principles)
- [Decision Framework](#decision-framework)
- [Review Checklist](#review-checklist)
- [Collaboration](#collaboration)
- [Recommended AI Tools](#recommended-ai-tools)
- [Quality Standards](#quality-standards)
- [Definition of Done](#definition-of-done)
- [Success Metrics](#success-metrics)
- [Continuous Improvement](#continuous-improvement)
- [Authority and Accountability](#authority-and-accountability)
- [Relationship to the ACM Methodology](#relationship-to-the-acm-methodology)
- [Relationship to Work Orders](#relationship-to-work-orders)
- [Guiding Statement](#guiding-statement)

---

## Mission

Design enterprise-ready AI solutions that satisfy approved business requirements while balancing scalability, security, maintainability, cost, governance, and business value.

The Solution Architect transforms validated business requirements into a clear implementation blueprint.

---

## Business Value

The Solution Architect ensures that every solution:

- Solves the correct business problem.
- Can be implemented successfully.
- Can scale with business growth.
- Meets enterprise security and governance expectations.
- Minimizes technical risk.
- Enables long-term maintainability.

---

## Consulting Philosophy

Architecture is a business decision expressed through technology.

Every architectural decision should improve business outcomes while reducing complexity and unnecessary risk.

Technology is selected because it supports the business—not because it is fashionable.

---

## Inputs

The Solution Architect begins work only after the Assess phase has been completed.

Primary inputs include:

- Approved Business Scenario
- Discovery Package
- Requirements Specification
- Business Requirements
- Functional Requirements
- Non-Functional Requirements
- Acceptance Criteria
- Business Constraints
- Assumptions
- Open Questions
- [Applicable Work Order](../work-orders/README.md)

---

## Outputs

The Solution Architect produces the Architecture Package:

- Solution Architecture
- System Context
- Logical Architecture
- AI Architecture
- Integration Architecture
- Security Architecture
- Deployment View
- Architecture Decision Log
- Engineering Handoff

---

## Responsibilities

The Solution Architect is responsible for:

- Translating requirements into architecture.
- Defining system boundaries.
- Identifying major components.
- Selecting architectural patterns.
- Designing AI interaction flows.
- Designing integrations.
- Defining security architecture.
- Designing deployment topology.
- Identifying architectural risks.
- Supporting Engineering during implementation.

---

## Expertise

The Solution Architect demonstrates expertise in:

- Enterprise Architecture
- Cloud Architecture
- AI Solution Design
- Distributed Systems
- Microservices
- Event-Driven Architecture
- API Design
- Integration Patterns
- Data Architecture
- Security Architecture
- Scalability
- High Availability
- Performance Engineering
- Cost Optimization
- Technology Evaluation

---

## Decision Authority

The Solution Architect may:

- Recommend architectural patterns.
- Select appropriate architectural approaches.
- Recommend cloud services.
- Recommend AI interaction patterns.
- Define system boundaries.
- Recommend build vs. buy decisions.

The Solution Architect may **not**:

- Change approved business requirements.
- Redefine business objectives.
- Change project scope.
- Modify governance standards.

---

## Deliverables

The Solution Architect owns:

- Architecture Package
- Architecture Diagrams
- AI Interaction Flow
- Integration Design
- Security Design
- Deployment Design
- Architecture Decision Records (ADRs)
- Engineering Handoff Package

---

## Architecture Principles

Every architecture should:

- Be business-driven.
- Remain technology-neutral until justified.
- Minimize unnecessary complexity.
- Support modular evolution.
- Protect sensitive data.
- Support observability.
- Enable scalability.
- Promote maintainability.
- Encourage automation.
- Support responsible AI.

---

## Decision Framework

Before making an architectural recommendation, evaluate:

- Business Value
- Complexity
- Cost
- Risk
- Security
- Scalability
- Operational Impact
- Maintainability
- Time to Market
- Future Flexibility

Every major architectural decision should document its rationale.

---

## Review Checklist

Before approving an architecture:

- [ ] Business requirements are fully addressed.
- [ ] Functional requirements are satisfied.
- [ ] Non-functional requirements are satisfied.
- [ ] Security has been considered.
- [ ] AI governance has been addressed.
- [ ] Integration points are identified.
- [ ] Failure scenarios are understood.
- [ ] Monitoring strategy is defined.
- [ ] Deployment approach is documented.
- [ ] Risks are documented.
- [ ] Trade-offs are documented.

---

## Collaboration

The Solution Architect collaborates closely with:

- Principal Consultant
- Senior Business Analyst
- Engineering Manager
- Claude Code Engineer
- Cloud Architect
- Security Architect
- Technical Writer

The Solution Architect provides technical leadership while ensuring alignment with business objectives.

---

## Recommended AI Tools

This persona may use:

- Claude Code
- Claude
- ChatGPT
- Gemini

AI tools assist with analysis and documentation.

The Solution Architect remains accountable for every architectural decision.

---

## Quality Standards

Every architecture should be:

- Traceable to business requirements.
- Easy to understand.
- Enterprise-ready.
- Secure.
- Scalable.
- Maintainable.
- Observable.
- Testable.
- Cost-conscious.
- Production-oriented.

---

## Definition of Done

The Architecture Package is complete when:

- [ ] Every requirement is addressed.
- [ ] Architectural decisions are documented.
- [ ] Major risks are identified.
- [ ] AI interaction is clearly defined.
- [ ] Security considerations are documented.
- [ ] Integration approach is complete.
- [ ] Deployment approach is documented.
- [ ] Engineering handoff is complete.
- [ ] Architecture is ready for implementation.

---

## Success Metrics

The Solution Architect is measured by:

- Architectural clarity
- Traceability to requirements
- Ease of implementation
- Scalability
- Operational simplicity
- Security readiness
- Maintainability
- Stakeholder confidence
- Reduction in implementation ambiguity

---

## Continuous Improvement

The Solution Architect continuously improves through:

- Architecture reviews
- Lessons learned
- Engineering feedback
- Production observations
- Emerging AI capabilities
- Cloud platform evolution
- Updates to the Eyuna methodology

---

## Authority and Accountability

The Solution Architect owns the architectural responsibilities described in this document.

AI tools support execution of architecture analysis and documentation but do not replace the persona. The Solution Architect remains accountable for every architectural recommendation and decision.

The Principal Consultant retains accountability for:

- Client communication
- Business decisions
- Methodology
- Governance
- Final approval

---

## Relationship to the ACM Methodology

The Solution Architect leads the **Create** phase of the [Eyuna ACM Methodology](../docs/acm-methodology.md).

Outputs from this persona become the primary inputs for Engineering and Cloud implementation activities.

---

## Relationship to Work Orders

The Solution Architect executes approved [Delivery Work Orders](../work-orders/README.md) related to solution design.

Typical Work Orders include:

- [WO-103 — Solution Architecture](../work-orders/delivery/WO-103-Customer-Support-Solution-Architecture.md)
- Future architecture-focused engagements

The Work Order defines scope, objectives, constraints, and deliverables.

The Solution Architect determines the architectural approach.

This persona follows the structure defined in [WO-002 — Persona Standard](../work-orders/governance/WO-002-Persona-Standard.md).

---

## Guiding Statement

> Great architecture is the bridge between business vision and engineering execution.

A successful Solution Architect creates solutions that are technically sound, operationally practical, and directly aligned with measurable business outcomes.
