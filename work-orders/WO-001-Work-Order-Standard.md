# WO-001 — Eyuna Work Order Standard

| Property            | Value                     |
| ------------------- | ------------------------- |
| Version             | 1.0                       |
| Status              | Approved                  |
| Category            | Governance                |
| Owner               | Chief Methodology Officer |
| Repository Location | `work-orders/`            |
| Applies To          | All Eyuna Artifacts       |
| Last Updated        | 2026-08-02                |

---

## Table of Contents

- [Purpose](#purpose)
- [Guiding Principle](#guiding-principle)
- [Work Order Categories](#work-order-categories)
  - [Governance Work Orders](#governance-work-orders)
  - [Delivery Work Orders](#delivery-work-orders)
- [Work Order Lifecycle](#work-order-lifecycle)
- [Work Order Identifier](#work-order-identifier)
- [Standard Work Order Structure](#standard-work-order-structure)
- [Relationship to ACM](#relationship-to-acm)
- [File Naming Convention](#file-naming-convention)
- [Repository Location](#repository-location)
- [Success Metrics](#success-metrics)
- [Future Enhancements](#future-enhancements)
- [Guiding Statement](#guiding-statement)

---

## Purpose

The Work Order (WO) is the standard mechanism used within Eyuna to initiate, assign, execute, review, and approve work.

Every artifact created within Eyuna—including documents, templates, personas, prompts, architectures, case studies, software implementations, and content—must begin with an approved Work Order.

The Work Order ensures every deliverable is:

- Business-driven
- Clearly scoped
- Traceable
- Reviewable
- Reusable
- Aligned with the ACM Methodology

---

## Guiding Principle

> We do not ask AI random questions.

> We assign work to consulting roles through structured Work Orders.

AI assists with execution.

Humans own the methodology, quality, and final approval.

---

## Work Order Categories

Eyuna defines two categories of Work Orders.

### Governance Work Orders

Governance Work Orders define how Eyuna itself operates.

Examples include:

- Repository Standards
- Constitution
- ACM Methodology
- Persona Standards
- Document Standards
- Definition of Done

Governance Work Orders are authored by the Eyuna methodology team and may be reviewed by AI tools for quality and consistency, but the methodology remains human-owned.

---

### Delivery Work Orders

Delivery Work Orders create client-facing or implementation artifacts.

Examples include:

- Discovery Documents
- Requirements Specifications
- Architecture Designs
- Claude Code Implementations
- AWS Deployments
- Website Case Studies
- LinkedIn Content

Delivery Work Orders are executed with AI assistance while remaining under human review and approval.

---

## Work Order Lifecycle

Every Work Order follows the same lifecycle.

```text
Draft
    ↓
Review
    ↓
Approved
    ↓
Assigned
    ↓
In Progress
    ↓
Completed
    ↓
Quality Review
    ↓
Accepted
    ↓
Published
```

A Work Order may not skip lifecycle stages.

---

## Work Order Identifier

Work Orders use sequential numbering.

Examples:

```
WO-001
WO-002
WO-003
```

Future versions of Eyuna may introduce specialized prefixes such as:

```
WO-DOC-001
WO-ARCH-001
WO-CODE-001
WO-CASE-001
```

For Version 1.x, sequential numbering is sufficient.

---

## Standard Work Order Structure

Every Work Order must contain the following sections.

### 1. Header

- Work Order ID
- Title
- Version
- Status
- Category
- Priority
- Estimated Effort
- Created By
- Assigned Persona
- Reviewer
- Date Created

---

### 2. Objective

Describe the desired outcome.

Example:

> Create the standard Discovery Document template used across all consulting engagements.

---

### 3. Business Context

Explain:

- Why this work exists
- Which business problem it supports
- Which ACM phase it belongs to
- Expected business value

---

### 4. Background

Provide all information required before work begins.

Include:

- Previous decisions
- Existing documentation
- Assumptions
- Related artifacts

---

### 5. Scope

Clearly define what is included.

Example:

Included:

- Discovery template
- Stakeholder analysis
- Process mapping
- Executive summary

---

### 6. Out of Scope

Clearly define what should NOT be produced.

Example:

Not Included:

- Requirements specification
- Architecture
- Software implementation

---

### 7. Inputs

Examples include:

- Constitution
- ACM Methodology
- Previous Work Orders
- Existing documentation
- Client information

---

### 8. Deliverables

List every expected output.

Example:

- Markdown document
- Template
- Checklist
- Repository updates

---

### 9. Acceptance Criteria

Define measurable success.

Example:

- Follows Eyuna document standards
- Supports ACM methodology
- Approved during quality review
- Ready for repository publication

---

### 10. Dependencies

List prerequisite work.

Examples:

- Constitution
- ACM Methodology
- Repository Structure

---

### 11. Assigned Persona

Every Work Order is owned by a consulting role.

Examples:

- Senior Business Analyst
- Solution Architect
- Cloud Architect
- Claude Code Engineer
- Technical Writer

The persona owns the outcome.

The AI tool assists with execution.

---

### 12. Recommended AI Tools

Examples:

- Claude
- Claude Code
- ChatGPT
- Gemini

Multiple tools may collaborate on the same Work Order.

---

### 13. References

List supporting artifacts.

Examples:

- Constitution
- ACM Methodology
- ADRs
- Architecture documents
- Previous Work Orders

---

### 14. Risks

Document known risks.

Examples:

- Ambiguous requirements
- Missing dependencies
- Technology uncertainty
- Stakeholder alignment

---

### 15. Review Checklist

Every Work Order must answer:

- [ ] Is the objective clear?
- [ ] Is the business context defined?
- [ ] Is the scope complete?
- [ ] Are deliverables measurable?
- [ ] Are dependencies identified?
- [ ] Is the assigned persona appropriate?
- [ ] Are acceptance criteria objective?

---

### 16. Definition of Done

A Work Order is complete only when:

- [ ] All deliverables are produced.
- [ ] Acceptance criteria are satisfied.
- [ ] Quality review is completed.
- [ ] Repository documentation is updated.
- [ ] Changes are committed.
- [ ] Lessons learned are captured (if applicable).

---

## Relationship to ACM

Every Work Order must explicitly identify the ACM phase it supports.

| ACM Phase | Typical Work Orders                                |
| --------- | --------------------------------------------------- |
| Assess    | Discovery, Business Case, Current State Assessment   |
| Create    | Requirements, Architecture, Development, Testing     |
| Modernize | Deployment, Monitoring, Optimization, Governance     |

---

## File Naming Convention

Use the following naming convention.

```
WO-001-Work-Order-Standard.md
WO-002-Persona-Standard.md
WO-003-Document-Standard.md
```

---

## Repository Location

```
work-orders/
```

Future versions may introduce lifecycle subdirectories if operational needs justify them.

---

## Success Metrics

A successful Work Order:

- Produces reusable assets.
- Advances the Eyuna methodology.
- Supports at least one consulting engagement.
- Can be reused across industries.
- Meets the Definition of Done.

---

## Future Enhancements

Potential future improvements include:

- Business value estimation
- Complexity score
- AI confidence rating
- Automation score
- Reuse score
- Traceability to ADRs
- Links to generated deliverables

---

## Guiding Statement

> Every meaningful outcome in Eyuna begins with a Work Order.

The Work Order is the foundation of execution, quality, governance, and continuous improvement throughout the Eyuna consulting methodology.
