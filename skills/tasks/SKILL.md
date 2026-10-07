---
name: tasks
description: Decompose an approved specification into a complete Task Catalog with dependencies and acceptance coverage.
---

# Tasks

Input:

`specs/<change-id>/spec.md`

Require `Status: READY`.

Create:

`specs/<change-id>/tasks.md`

## Objective

Decompose the specification into bounded, verifiable logical changes.

A Task defines what must change.
It MUST NOT define worker type, model, session, wave, ordering, parallelism, or commit structure.

Use stable IDs: `T1`, `T2`, ...

For each Task:

## T<n> — <title>

Goal:
Scope:
Dependencies:
Acceptance:

- AC<n>

## Acceptance coverage

Map every Acceptance Criterion to the Tasks responsible for satisfying or verifying it.

## Gate

`tasks.md` is `READY` only when:

- every Change Outline item is represented;
- every Acceptance Criterion is covered;
- dependencies are explicit;
- no Task requires an unresolved material decision;
- no execution planning is introduced.

If decomposition exposes a Specification Gap, return to `spec`.
