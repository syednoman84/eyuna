# Work Orders

## Purpose

This directory contains all Work Orders used within Eyuna.

A Work Order is the standard mechanism used to initiate, assign, execute, review, and approve every meaningful piece of work performed within the Eyuna framework.

Every artifact—whether it is a governance document, consulting persona, architecture, implementation, case study, or client deliverable—must originate from an approved Work Order.

The governing standard for all Work Orders is:

- [`governance/WO-001-Work-Order-Standard.md`](governance/WO-001-Work-Order-Standard.md)

---

# Directory Structure

```text
work-orders/

├── governance/
│   ├── WO-001-Work-Order-Standard.md
│   ├── WO-002-Persona-Standard.md
│   └── ...
│
└── delivery/
    ├── WO-101-Customer-Support-Discovery.md
    ├── WO-102-Customer-Support-Requirements.md
    └── ...
```

---

# Governance Work Orders

Governance Work Orders define how Eyuna itself operates.

These documents evolve the consulting methodology, governance model, standards, and reusable operating framework.

## Current Governance Work Orders

| Work Order                                           | Status   | Description                                                                                               |
| ---------------------------------------------------- | -------- | --------------------------------------------------------------------------------------------------------- |
| [`WO-001`](governance/WO-001-Work-Order-Standard.md) | Approved | Defines the Work Order lifecycle, structure, governance model, and relationship to the ACM Methodology.   |
| [`WO-002`](governance/WO-002-Persona-Standard.md)    | Approved | Defines the standard structure, responsibilities, and lifecycle for all consulting personas within Eyuna. |

Future governance work orders continue within the **WO-001 – WO-099** range.

Examples:

- Document Standard
- Definition of Done
- Review Standard
- Governance Policies

---

# Delivery Work Orders

Delivery Work Orders represent consulting engagements and implementation activities.

These Work Orders produce client-facing deliverables such as:

- Discovery Documents
- Requirements Specifications
- Architecture Designs
- Software Implementations
- Deployments
- Case Studies
- Website Content
- LinkedIn Content

Delivery Work Orders are organized by engagement using reserved numbering ranges.

| Range           | Engagement                      |
| --------------- | ------------------------------- |
| WO-100 – WO-199 | Customer Support                |
| WO-200 – WO-299 | Healthcare _(Reserved)_         |
| WO-300 – WO-399 | Retail _(Reserved)_             |
| WO-400 – WO-499 | Financial Services _(Reserved)_ |

## Current Delivery Work Orders

| Work Order                                                     | Status   | Description                                                                     |
| ---------------------------------------------------------------- | -------- | ---------------------------------------------------------------------------------- |
| [`WO-101`](delivery/WO-101-Customer-Support-Discovery.md) | Approved | Discovery engagement for the Customer Support Email Automation case study (Assess phase). |

---

# Numbering Convention

Eyuna separates governance from delivery work.

| Range           | Purpose    |
| --------------- | ---------- |
| WO-001 – WO-099 | Governance |
| WO-100 – WO-999 | Delivery   |

Number ranges for Delivery Work Orders may be reserved by engagement or solution domain as the framework evolves.

---

# Work Order Lifecycle

Every Work Order follows the lifecycle defined in:

- [`governance/WO-001-Work-Order-Standard.md`](governance/WO-001-Work-Order-Standard.md)

The lifecycle applies equally to Governance and Delivery Work Orders.

---

# Relationship to the ACM Methodology

Every Work Order explicitly identifies the ACM phase it supports.

- **Assess** – Discovery, Business Analysis, Current-State Assessment
- **Create** – Requirements, Architecture, Development, Testing
- **Modernize** – Deployment, Optimization, Governance, Continuous Improvement

For additional details, refer to the ACM Methodology documentation:

- [`../docs/acm-methodology.md`](../docs/acm-methodology.md)

---

# How This Fits Into Eyuna

Work Orders are the operational entry point for all work performed within Eyuna.

The workflow is intentionally consistent:

```text
Business Need
        ↓
Work Order
        ↓
Assigned Persona
        ↓
AI-Assisted Execution
        ↓
Human Review
        ↓
Approved Deliverable
        ↓
Repository Artifact
```

This approach ensures every artifact within Eyuna is:

- Traceable
- Repeatable
- Reviewable
- Governed
- Reusable

Work Orders provide the connection between business intent, consulting methodology, AI-assisted execution, and the final deliverables stored throughout the repository.

---

# Related Directories

- [`../personas/`](../personas/README.md)
- [`../prompts/`](../prompts/README.md)
- [`../templates/`](../templates/README.md)
- [`../architectures/`](../architectures/README.md)
- [`../playbooks/`](../playbooks/README.md)
- [`../case-studies/`](../case-studies/README.md)
- [`../docs/`](../docs/README.md)
