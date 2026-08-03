# WO-101 — Customer Support Discovery

| Property            | Value                              |
| ------------------- | ----------------------------------- |
| Work Order ID       | WO-101                              |
| Title               | Customer Support Discovery          |
| Version             | 1.0                                 |
| Status              | Approved                            |
| Category            | Delivery                            |
| Priority            | High                                |
| Estimated Effort    | 3–5 Consulting Days                 |
| Created By          | Principal Consultant                |
| Assigned Persona    | Senior Business Analyst             |
| Reviewer            | Chief Methodology Officer           |
| Date Created        | 2026-08-03                          |
| Owner               | Principal Consultant                |
| Repository Location | `work-orders/delivery/`             |
| ACM Phase           | Assess                              |
| Last Updated        | 2026-08-03                          |

---

## Table of Contents

- [Objective](#objective)
- [Business Context](#business-context)
- [Background](#background)
- [Scope](#scope)
- [Out of Scope](#out-of-scope)
- [Business Objectives](#business-objectives)
- [Inputs](#inputs)
- [Deliverables](#deliverables)
- [Acceptance Criteria](#acceptance-criteria)
- [Dependencies](#dependencies)
- [Risks](#risks)
- [Constraints](#constraints)
- [Assigned Persona](#assigned-persona)
- [Recommended AI Tools](#recommended-ai-tools)
- [Execution Instructions](#execution-instructions)
- [Definition of Done](#definition-of-done)
- [Expected Outputs](#expected-outputs)
- [Success Metrics](#success-metrics)
- [Related Artifacts](#related-artifacts)
- [Guiding Statement](#guiding-statement)

---

## Objective

Conduct a comprehensive discovery engagement for the Customer Support Email Automation initiative.

The objective is to understand the client's current support operation, identify business pain points, evaluate AI opportunities, and produce the business artifacts required to proceed into solution design.

No architecture or implementation decisions are made during this Work Order.

---

## Business Context

The client is a growing SaaS organization handling approximately **8,000 customer support emails per day**.

Support agents manually:

- Read every email
- Categorize requests
- Determine priority
- Route tickets
- Draft responses
- Escalate complex cases

As support volume has increased, response times, operational costs, and customer satisfaction have become strategic concerns.

Leadership wants to determine whether AI can improve operational efficiency while maintaining governance, quality, and human oversight.

---

## Background

This Work Order is based on the business scenario documented in [`case-studies/customer-support-email-automation/README.md`](../../case-studies/customer-support-email-automation/README.md).

The engagement follows the Eyuna [Assess • Create • Modernize (ACM)](../../docs/acm-methodology.md) methodology and represents the first delivery engagement executed using the Eyuna consulting framework.

---

## Scope

The discovery engagement includes:

- Business problem definition
- Stakeholder identification
- Current-state assessment
- Current support workflow analysis
- Pain point identification
- Business objective validation
- Success metric definition
- AI opportunity assessment
- Risk identification
- Assumption documentation
- Executive recommendations

---

## Out of Scope

This Work Order does **not** include:

- Solution architecture
- Technical design
- Technology selection
- Vendor evaluation
- Software implementation
- Infrastructure deployment
- Cost estimation
- Project planning

Those activities are addressed in subsequent Work Orders.

---

## Business Objectives

The discovery effort should validate the client's goals, including:

- Reduce first response time
- Improve customer satisfaction
- Increase support agent productivity
- Reduce repetitive manual work
- Improve routing accuracy
- Introduce AI responsibly with appropriate human oversight

---

## Inputs

The Senior Business Analyst should use:

- [Customer Support Case Study README](../../case-studies/customer-support-email-automation/README.md)
- [WO-001 — Work Order Standard](../governance/WO-001-Work-Order-Standard.md)
- [WO-002 — Persona Standard](../governance/WO-002-Persona-Standard.md)
- [Senior Business Analyst Persona](../../personas/senior-business-analyst.md)
- Existing business assumptions
- Industry best practices for customer support

---

## Deliverables

This Work Order must produce:

1. Executive Summary
2. Business Problem Statement
3. Current-State Assessment
4. Stakeholder Analysis
5. Current Process Overview
6. Pain Point Analysis
7. Business Objectives
8. Success Metrics
9. AI Opportunity Assessment
10. Risks and Constraints
11. Assumptions
12. Executive Recommendations

---

## Acceptance Criteria

This Work Order is considered complete when:

- The business problem is clearly documented.
- Current-state operations are understood.
- Stakeholders are identified.
- Business objectives are measurable.
- AI opportunities are prioritized.
- Risks and assumptions are documented.
- Recommendations are actionable.
- The engagement is ready to transition into solution architecture.

---

## Dependencies

This Work Order depends on:

- [WO-001 — Work Order Standard](../governance/WO-001-Work-Order-Standard.md)
- [WO-002 — Persona Standard](../governance/WO-002-Persona-Standard.md)
- [Customer Support Case Study](../../case-studies/customer-support-email-automation/README.md)
- [Senior Business Analyst Persona](../../personas/senior-business-analyst.md)

---

## Risks

Potential risks include:

- Incomplete understanding of current processes
- Assumptions not validated
- Stakeholder alignment issues
- Regulatory or compliance constraints
- Unrealistic automation expectations

---

## Constraints

The assessment should assume:

- Human approval is required for sensitive customer communications.
- Personally identifiable information (PII) must remain protected.
- Existing customer support platforms remain in place.
- Recommendations should be technology-neutral unless necessary.

---

## Assigned Persona

**Primary Owner**

[Senior Business Analyst](../../personas/senior-business-analyst.md)

Responsibilities include:

- Leading discovery
- Performing business analysis
- Producing all required deliverables
- Preparing the engagement for the Create phase

---

## Recommended AI Tools

This Work Order may be supported by:

- Claude
- Claude Code
- ChatGPT
- Gemini

AI tools assist with execution.

The Senior Business Analyst owns the consulting outcome.

---

## Execution Instructions

Execute this Work Order as the **Senior Business Analyst**.

Focus on understanding the business before proposing solutions.

Recommendations should be evidence-based, practical, measurable, and aligned with business objectives.

Do not design the solution during this phase.

---

## Definition of Done

- [ ] All discovery deliverables are completed.
- [ ] Business objectives are validated.
- [ ] Stakeholders are identified.
- [ ] Current-state assessment is documented.
- [ ] Risks and assumptions are captured.
- [ ] AI opportunities are prioritized.
- [ ] Executive recommendations are complete.
- [ ] Deliverables are approved for transition to the Create phase.

---

## Expected Outputs

Execution of this Work Order will produce:

- `discovery/discovery-document.md`
- `discovery/executive-summary.md`
- `discovery/stakeholder-analysis.md`
- `discovery/ai-opportunity-assessment.md`

These outputs become primary inputs for the next Work Order.

---

## Success Metrics

The discovery engagement is successful when:

- Business stakeholders have a shared understanding of the problem.
- AI opportunities are clearly identified.
- The business case is well defined.
- The project is ready for solution architecture.
- Downstream ambiguity is minimized.

---

## Related Artifacts

**Case Study**

- [`case-studies/customer-support-email-automation/README.md`](../../case-studies/customer-support-email-automation/README.md)

**Governance**

- [`work-orders/governance/WO-001-Work-Order-Standard.md`](../governance/WO-001-Work-Order-Standard.md)
- [`work-orders/governance/WO-002-Persona-Standard.md`](../governance/WO-002-Persona-Standard.md)

**Persona**

- [`personas/senior-business-analyst.md`](../../personas/senior-business-analyst.md)

---

## Guiding Statement

> The quality of every AI solution is determined by the quality of the discovery that precedes it.

A successful discovery engagement creates clarity, alignment, and measurable business outcomes before any technology decisions are made.
