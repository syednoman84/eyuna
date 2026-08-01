# Eyuna

**Eyuna is a Consulting Operating System for AI consulting engagements.**

It is not an application. It is the internal operating manual, methodology library, and reusable asset base for running world-class AI consulting engagements — repeatable, documented, and built to compound in value over years rather than sprints.

> **Status:** Foundation phase (v1.0). The repository structure, governance, and documentation scaffolding are being established before any methodology, persona, prompt, or case-study content is authored. See [PROJECT_STATUS.md](PROJECT_STATUS.md) for the live dashboard.

## Table of Contents

- [Project Vision](#project-vision)
- [Mission](#mission)
- [Repository Overview](#repository-overview)
- [Repository Structure](#repository-structure)
- [Getting Started](#getting-started)
- [Roadmap Summary](#roadmap-summary)
- [Current Release](#current-release)
- [Contribution Guide](#contribution-guide)
- [License](#license)

## Project Vision

Every AI consulting engagement re-invents the same wheel: discovery frameworks, personas, prompt patterns, architecture diagrams, and delivery templates get rebuilt from scratch, live in someone's local folder, and disappear when the engagement ends.

Eyuna exists to end that cycle. It is a single, versioned, continuously improving source of truth for how AI consulting is _done_ — so that every new engagement starts from accumulated organizational knowledge instead of a blank page.

## Mission

To provide a reusable, well-governed framework of methodologies, personas, prompts, templates, playbooks, architectures, and reference implementations that any consultant, team, or partner can pick up and apply to a real AI engagement — consistently, credibly, and quickly.

## Repository Overview

Eyuna is organized as a documentation-and-asset framework, not a codebase. Each top-level directory represents one category of consulting asset. Directories grow independently over successive releases (see [ROADMAP.md](ROADMAP.md)), but the structure itself is intended to remain stable for the life of the project.

Key principles behind the repository design:

- **One category, one directory.** No overlapping or ambiguous homes for content.
- **Documentation before content.** Every directory is explained before it is filled.
- **No premature depth.** Nesting is added only when a category's contents actually need it.
- **Traceable decisions.** Structural and methodological choices are logged in [DECISIONS.md](DECISIONS.md), not lost in chat history.

## Repository Structure

```text
eyuna/
├── docs/                  Foundational documentation: constitution, methodology, principles, governance, glossary
├── personas/              Consulting personas used across engagements
├── prompts/               Reusable prompt libraries
├── templates/             Engagement and deliverable templates
├── playbooks/             Industry- and scenario-specific playbooks
├── case-studies/          Documented engagement outcomes and lessons learned
├── architectures/         Reference architecture patterns
├── starter-projects/      Bootstrappable starting points for new engagements
├── reusable-components/   Cross-cutting building blocks used by multiple assets above
├── tools/                 Internal tooling that supports the consulting workflow
├── content/               External-facing content (website, LinkedIn, etc.)
├── assets/                Shared media and design assets (diagrams, logos, images)
└── scripts/               Automation and maintenance scripts for the repository itself
```

Every directory listed above contains its own `README.md` explaining its purpose, its contents, and how it fits into Eyuna as a whole. Start there before adding anything new.

## Getting Started

Eyuna has no build step, dependencies, or runtime — it is a documentation and asset framework. To get oriented:

1. Read this file, then [docs/README.md](docs/README.md) for the foundational documents (constitution, methodology, principles, governance, glossary).
2. Read [ROADMAP.md](ROADMAP.md) to understand what exists today versus what is planned.
3. Read [PROJECT_STATUS.md](PROJECT_STATUS.md) for the current state of work.
4. Read [CONTRIBUTING.md](CONTRIBUTING.md) before proposing or adding any content.
5. Browse the directory whose category matches what you're looking for — each has its own `README.md`.

## Roadmap Summary

Eyuna is delivered in numbered releases, each adding one major capability layer:

| Release | Theme                       |
| ------- | --------------------------- |
| 1.0     | Foundation                  |
| 2.0     | Consulting Personas         |
| 3.0     | Prompt Engine               |
| 4.0     | Templates                   |
| 5.0     | Customer Support Case Study |
| 6.0     | Industry Playbooks          |

Full milestone breakdowns live in [ROADMAP.md](ROADMAP.md).

## Current Release

**v1.0 — Foundation** (in progress). This release establishes the repository structure, governance model, and documentation scaffolding described above. No methodology, persona, prompt, or case-study content is authored yet — see [PROJECT_STATUS.md](PROJECT_STATUS.md) for exact completion status.

## Contribution Guide

Eyuna is intended to grow through disciplined, reviewed contributions rather than ad-hoc additions. Before contributing:

- Read [CONTRIBUTING.md](CONTRIBUTING.md) in full.
- Confirm your addition belongs in an existing directory before proposing a new one.
- Significant structural or methodological changes should be logged as a decision in [DECISIONS.md](DECISIONS.md).

## License

Eyuna is released under the [MIT License](LICENSE).
