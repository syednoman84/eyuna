# Reusable Components

## Purpose

This directory holds cross-cutting building blocks used by multiple other assets in Eyuna — reference implementations, modules, or patterns that are too concrete to live in [`../architectures/`](../architectures/README.md) (which documents patterns, not implementations) but too general-purpose to belong to any single starter project.

## Contents

This directory does not yet contain component content. It is scaffolded during Release 1.0 (Foundation) so the category exists ahead of the content itself; population will follow as common needs are identified across starter projects and case studies (see [ROADMAP.md](../ROADMAP.md)). When populated, it will contain:

- A component documentation standard (purpose, interface, dependencies, which architectures/starter projects use it)
- Individual reusable components, organized by function

## How This Fits Into Eyuna

Reusable components are the shared implementation layer beneath [`../starter-projects/`](../starter-projects/README.md) and [`../architectures/`](../architectures/README.md) — when the same building block would otherwise be duplicated across multiple starter projects, it belongs here instead. This keeps starter projects thin and consistent, and keeps improvements to a shared component from requiring changes in many places at once.
