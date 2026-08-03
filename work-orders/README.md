# Work Orders

## Purpose

This directory holds Eyuna's Work Orders — the standard mechanism used to initiate, assign, execute, review, and approve every piece of work in the framework, whether it produces a governance artifact (methodology, standards) or a delivery artifact (client-facing documents, architectures, implementations).

The standard governing this directory is [WO-001 — Eyuna Work Order Standard](WO-001-Work-Order-Standard.md). It defines the Work Order lifecycle, the required document structure, and the naming convention used for every Work Order in this directory.

## Contents

| File | Description |
|---|---|
| [`WO-001-Work-Order-Standard.md`](WO-001-Work-Order-Standard.md) | The governance standard defining what a Work Order is, its lifecycle, its required structure, and its relationship to the ACM Methodology. |

Future Work Orders are added here sequentially (`WO-002`, `WO-003`, ...), following the naming convention defined in WO-001.

## How This Fits Into Eyuna

Work Orders are the entry point for all work in Eyuna: per [WO-001](WO-001-Work-Order-Standard.md#purpose), every artifact created within Eyuna — documents, templates, personas, prompts, architectures, case studies, software implementations, and content — must begin with an approved Work Order. Each Work Order explicitly declares the [ACM](../docs/acm-methodology.md) phase it supports, so this directory is where an engagement's intent is captured and made traceable before any artifact lands in [`personas/`](../personas/README.md), [`prompts/`](../prompts/README.md), [`templates/`](../templates/README.md), [`playbooks/`](../playbooks/README.md), [`case-studies/`](../case-studies/README.md), or elsewhere in the repository.
