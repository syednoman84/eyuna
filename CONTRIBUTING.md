# Contributing to Eyuna

Thank you for your interest in contributing to Eyuna. This document explains how to propose and add content to the framework so that it stays consistent, well-governed, and useful over many years of growth.

## Table of Contents

- [Before You Contribute](#before-you-contribute)
- [What Belongs Where](#what-belongs-where)
- [Contribution Workflow](#contribution-workflow)
- [Documentation Standards](#documentation-standards)
- [Proposing Structural Changes](#proposing-structural-changes)
- [Code of Conduct](#code-of-conduct)

## Before You Contribute

Eyuna is a consulting operating system, not an application — most contributions are documentation, methodology, prompts, templates, or reference content rather than code. Before opening a contribution:

1. Read the root [README.md](README.md) to understand the project's vision and structure.
2. Read [ROADMAP.md](ROADMAP.md) and [PROJECT_STATUS.md](PROJECT_STATUS.md) to understand what is currently in scope.
3. Check [DECISIONS.md](DECISIONS.md) to see if a relevant decision has already been made.
4. Per [WO-001](work-orders/WO-001-Work-Order-Standard.md), every artifact in Eyuna — documents, templates, personas, prompts, architectures, case studies, implementations, and content — begins with an approved Work Order in [`work-orders/`](work-orders/README.md). Open or reference the relevant Work Order before starting substantive work.

## What Belongs Where

Each top-level directory has a single, well-defined purpose, documented in its own `README.md`:

| Directory | Purpose |
|---|---|
| [`work-orders/`](work-orders/README.md) | Work Orders — the standard mechanism for initiating, assigning, and approving all work |
| [`docs/`](docs/README.md) | Foundational governance and methodology documents |
| [`personas/`](personas/README.md) | Consulting personas used across engagements |
| [`prompts/`](prompts/README.md) | Reusable prompt libraries |
| [`templates/`](templates/README.md) | Engagement and deliverable templates |
| [`playbooks/`](playbooks/README.md) | Industry- and scenario-specific playbooks |
| [`case-studies/`](case-studies/README.md) | Documented engagement outcomes |
| [`architectures/`](architectures/README.md) | Reference architecture patterns |
| [`starter-projects/`](starter-projects/README.md) | Bootstrappable engagement starting points |
| [`reusable-components/`](reusable-components/README.md) | Cross-cutting building blocks |
| [`tools/`](tools/README.md) | Internal tooling supporting the consulting workflow |
| [`content/`](content/README.md) | External-facing content (website, LinkedIn) |
| [`assets/`](assets/README.md) | Shared media and design assets |
| [`scripts/`](scripts/README.md) | Repository automation and maintenance scripts |

If you are unsure where something belongs, open a discussion or issue before adding it — do not create a new top-level directory without going through the process in [Proposing Structural Changes](#proposing-structural-changes).

## Contribution Workflow

1. **Open an issue first** for anything beyond a small fix (typo, broken link) — describe what you want to add and why.
2. **Fork and branch** using a descriptive branch name (e.g., `add-discovery-prompt-set`).
3. **Follow existing conventions** in the target directory — naming, structure, and formatting should match what is already there.
4. **Update related documentation.** If your change affects a directory's contents, update that directory's `README.md`. If it completes or advances a roadmap milestone, update [PROJECT_STATUS.md](PROJECT_STATUS.md) and check off the milestone in [ROADMAP.md](ROADMAP.md).
5. **Open a pull request** with a clear description of what was added or changed and why.
6. **Respond to review feedback.** Contributions are reviewed for fit, quality, and consistency with the framework's methodology and governance.

## Documentation Standards

- Use Markdown throughout, following standard best practices (one `H1` per document, logical heading hierarchy, a table of contents for longer documents).
- Use relative links between files within the repository (e.g., `[Roadmap](../ROADMAP.md)`) rather than absolute URLs.
- Use `kebab-case` for file and directory names.
- Keep prose clear and consulting-grade: precise, professional, and free of filler.
- Avoid unnecessary nesting — a new subdirectory should only be created when a category's contents genuinely require it.

## Proposing Structural Changes

Any change to the top-level repository structure, the governance model, or the core methodology (ACM) requires an Architecture Decision Record. See [DECISIONS.md](DECISIONS.md) for the template and process. Open a pull request that adds the ADR before or alongside the structural change itself.

## Code of Conduct

Contributors are expected to engage respectfully and professionally, consistent with Eyuna's purpose as a framework for consulting excellence. Disagreements should be resolved through discussion, referencing the project's documented principles and governance model in [`docs/`](docs/README.md).
