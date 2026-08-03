# WO-002 — Eyuna Persona Standard

| Property            | Value                     |
| ------------------- | ------------------------- |
| Version             | 1.0                       |
| Status              | Draft                     |
| Category            | Governance                |
| Owner               | Chief Methodology Officer |
| Repository Location | `work-orders/`            |
| Applies To          | All Eyuna Personas        |
| Last Updated        | 2026-08-02                |

---

## Table of Contents

- [Purpose](#purpose)
- [Guiding Principles](#guiding-principles)
- [What is a Persona?](#what-is-a-persona)
- [Persona Categories](#persona-categories)
  - [Business Consulting](#business-consulting)
  - [Architecture](#architecture)
  - [Engineering](#engineering)
  - [AI Engineering](#ai-engineering)
  - [Delivery](#delivery)
- [Persona Lifecycle](#persona-lifecycle)
- [Standard Persona Structure](#standard-persona-structure)
- [Authority and Accountability](#authority-and-accountability)
- [Relationship to the ACM Methodology](#relationship-to-the-acm-methodology)
- [Relationship to Work Orders](#relationship-to-work-orders)
- [Repository Location](#repository-location)
- [Definition of Done](#definition-of-done)
- [Standard Success Metrics](#standard-success-metrics)
- [Future Enhancements](#future-enhancements)
- [Guiding Statement](#guiding-statement)

---

## Purpose

This document defines the standard structure for every consulting persona within Eyuna.

A persona represents a consulting role—not an AI model.

Personas encapsulate professional responsibilities, decision boundaries, expected deliverables, and collaboration patterns.

AI tools execute work on behalf of personas.

Humans remain accountable for methodology, business decisions, governance, and final approval.

---

## Guiding Principles

Every persona must:

- Represent a real consulting role.
- Have clearly defined responsibilities.
- Produce measurable outputs.
- Support one or more phases of the [ACM Methodology](../docs/acm-methodology.md).
- Collaborate with other personas.
- Remain independent of any specific AI model.
- Be reusable across industries and client engagements.

---

## What is a Persona?

A persona is a reusable consulting role that defines **how work should be performed**, regardless of which AI tool assists with execution.

A persona is **not**:

- A prompt
- An AI agent
- A chatbot
- A software component

A persona is a professional role that can be supported by AI.

Examples include:

- Senior Business Analyst
- AI Strategy Consultant
- Solution Architect
- Cloud Architect
- Engineering Manager
- Claude Code Engineer
- QA Engineer
- Technical Writer

---

## Persona Categories

Eyuna personas are organized into consulting disciplines.

### Business Consulting

Examples:

- Senior Business Analyst
- Strategy Consultant
- Process Consultant
- ROI Consultant

---

### Architecture

Examples:

- Enterprise Architect
- Solution Architect
- Cloud Architect
- Security Architect

---

### Engineering

Examples:

- Engineering Manager
- Backend Engineer
- Frontend Engineer
- DevOps Engineer
- QA Engineer

---

### AI Engineering

Examples:

- Prompt Engineer
- Claude Code Engineer
- Agent Engineer
- RAG Specialist
- Evaluation Engineer

---

### Delivery

Examples:

- Technical Writer
- Documentation Specialist
- Project Manager
- Scrum Master

---

## Persona Lifecycle

Every persona follows the same lifecycle.

```text
Designed
    ↓
Reviewed
    ↓
Approved
    ↓
Available
    ↓
Assigned to Work Order
    ↓
Executed
    ↓
Evaluated
    ↓
Improved
```

Personas evolve based on lessons learned from real engagements.

---

## Standard Persona Structure

Every persona must include the following sections.

### 1. Persona Overview

- Name
- Version
- Status
- Owner
- Category
- Primary ACM Phase
- Last Updated

---

### 2. Mission

A concise statement explaining the persona's purpose.

---

### 3. Business Value

Describe how the persona contributes to successful consulting engagements.

---

### 4. Responsibilities

Clearly define the activities owned by the persona.

Responsibilities should be outcome-focused rather than task-focused.

---

### 5. Expertise

Describe the professional knowledge expected of the persona.

Examples:

- Business analysis
- Enterprise architecture
- Cloud engineering
- Software delivery
- AI implementation

---

### 6. Inputs

List the information required before work begins.

Examples:

- Approved Work Order
- Discovery documents
- Business objectives
- Existing architecture
- Client documentation

---

### 7. Outputs

List all expected deliverables.

Examples:

- Discovery Document
- Requirements Specification
- Architecture Diagram
- Implementation Plan

---

### 8. Deliverables

Identify the primary artifacts owned by the persona.

---

### 9. Decision Authority

Clearly define decisions the persona is authorized to make.

Examples:

- Recommend improvements
- Identify risks
- Propose architecture
- Prioritize requirements

Business approval remains with the client and principal consultant.

---

### 10. Collaboration

List the personas this role typically collaborates with.

Example:

Senior Business Analyst collaborates with:

- Strategy Consultant
- Solution Architect
- Engineering Manager

---

### 11. Recommended AI Tools

Examples:

- Claude
- Claude Code
- ChatGPT
- Gemini

AI tools assist the persona.

They do not replace the persona.

---

### 12. Quality Standards

Every persona must define measurable quality expectations for its deliverables.

---

### 13. Review Checklist

Every persona includes a checklist that validates:

- Objectives achieved
- Deliverables complete
- Risks identified
- Assumptions documented
- Recommendations supported by evidence

---

### 14. Success Metrics

Every persona defines measurable indicators of success.

Examples:

- Quality of deliverables
- Stakeholder satisfaction
- Reusability
- Business impact
- Delivery efficiency

---

### 15. Continuous Improvement

Each persona should evolve based on:

- Project retrospectives
- Lessons learned
- New technologies
- Updated consulting practices

---

## Authority and Accountability

Personas own consulting responsibilities.

AI tools support execution.

The Principal Consultant retains accountability for:

- Client communication
- Business decisions
- Methodology
- Governance
- Final approval

---

## Relationship to the ACM Methodology

Every persona must identify its primary [ACM](../docs/acm-methodology.md) responsibility.

| ACM Phase | Example Personas                                              |
| --------- | --------------------------------------------------------------- |
| Assess    | Senior Business Analyst, Strategy Consultant                    |
| Create    | Solution Architect, Engineering Manager, Claude Code Engineer   |
| Modernize | DevOps Engineer, Technical Writer, AI Evaluation Engineer       |

---

## Relationship to Work Orders

Every persona performs work only through an approved [Work Order](WO-001-Work-Order-Standard.md).

The Work Order defines:

- Scope
- Objectives
- Deliverables
- Success Criteria

The persona determines **how** the work should be completed.

---

## Repository Location

```
personas/
```

Individual persona documents are published under [`personas/`](../personas/README.md) once approved. See [`personas/README.md`](../personas/README.md) for how that directory is organized.

---

## Definition of Done

A persona is considered complete when:

- [ ] Standard structure is followed.
- [ ] Responsibilities are clearly defined.
- [ ] Inputs and outputs are documented.
- [ ] Deliverables are measurable.
- [ ] Collaboration model is defined.
- [ ] Quality standards exist.
- [ ] Success metrics are identified.
- [ ] Relationship to ACM is documented.
- [ ] Relationship to Work Orders is documented.

---

## Standard Success Metrics

A successful persona:

- Can be reused across multiple engagements.
- Produces consistent consulting outputs.
- Clearly defines ownership.
- Works independently of any specific AI model.
- Supports the ACM Methodology.
- Improves delivery efficiency.

---

## Future Enhancements

Potential future additions include:

- Competency matrix
- Experience levels
- Estimated effort guidelines
- AI capability mapping
- Training recommendations
- Example engagements

---

## Guiding Statement

> Personas define consulting expertise. AI tools provide execution. Together, they deliver consistent, scalable, and high-quality consulting outcomes.
