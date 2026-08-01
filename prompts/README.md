# Prompts

## Purpose

This directory holds Eyuna's reusable prompt libraries — the versioned, tested prompts used to carry out AI consulting work consistently across engagements, rather than being reinvented ad hoc in each project.

## Contents

This directory is currently empty of prompt content — it is scaffolded ahead of Release 3.0 (Prompt Engine), per [ROADMAP.md](../ROADMAP.md). When populated, it will contain:

- A prompt library taxonomy and metadata standard (purpose, phase, inputs/outputs, evaluation notes)
- Discovery-phase prompt sets
- Analysis- and design-phase prompt sets
- Delivery- and QA-phase prompt sets

## How This Fits Into Eyuna

Prompts are the operational layer of the [ACM Methodology](../docs/acm-methodology.md) — each ACM phase will reference the specific prompt sets used to carry it out. Prompts are written to be used by, or on behalf of, the personas defined in [`../personas/`](../personas/README.md), and their outputs frequently feed the templates in [`../templates/`](../templates/README.md). Industry playbooks ([`../playbooks/`](../playbooks/README.md)) may extend or specialize base prompts from this library rather than duplicating them.
