# Architecture Decision Records (ADR)

This file is the log of significant decisions made about Eyuna's structure, methodology, and governance. It exists so that future contributors understand *why* something is the way it is, not just what it is.

Every structural, methodological, or governance decision with lasting consequences should be recorded here — additions to content within an established structure (a new prompt, a new persona) generally do not need an ADR.

## Table of Contents

- [How to Use This Log](#how-to-use-this-log)
- [ADR Template](#adr-template)
- [Decision Log](#decision-log)
  - [ADR-0001: Initial Repository Structure](#adr-0001-initial-repository-structure)

## How to Use This Log

1. Copy the [ADR Template](#adr-template) below.
2. Assign the next sequential decision number.
3. Fill in every field — do not leave `Context` or `Consequences` blank; they are the most valuable part of the record.
4. Add an entry to the [Decision Log](#decision-log) table of contents.
5. Set `Status` to `Proposed` until the decision is agreed, then update it to `Accepted`, `Rejected`, `Superseded`, or `Deprecated`.

## ADR Template

```markdown
### ADR-XXXX: <Title>

- **Status:** Proposed | Accepted | Rejected | Superseded | Deprecated
- **Date:** YYYY-MM-DD

**Context**

What problem or situation prompted this decision? What constraints or forces were in play?

**Decision**

What was decided, stated plainly and unambiguously.

**Consequences**

What becomes easier or harder as a result? What follow-up work, risks, or trade-offs does this introduce?
```

## Decision Log

### ADR-0001: Initial Repository Structure

- **Status:** Accepted
- **Date:** 2026-08-01

**Context**

Eyuna needed a repository structure that could support many years of growth across methodologies, personas, prompts, templates, playbooks, case studies, architectures, starter projects, reusable components, tools, and external-facing content — without requiring a restructure as it scales.

**Decision**

Adopt a flat, category-based top-level structure where each major asset type (`personas/`, `prompts/`, `templates/`, `playbooks/`, `case-studies/`, `architectures/`, `starter-projects/`, `reusable-components/`, `tools/`, `content/`, `assets/`, `scripts/`) has exactly one home directory at the repository root, alongside a `docs/` directory for foundational governance and methodology documents. Nesting within a category is deferred until that category's content actually requires it.

**Consequences**

Contributors have an unambiguous, discoverable location for any new asset. The structure is stable enough to support the multi-year roadmap in [ROADMAP.md](ROADMAP.md) without early restructuring. The trade-off is that some categories will start as a single `README.md` with no content, which is intentional — see [PROJECT_STATUS.md](PROJECT_STATUS.md) for what remains to populate them.
