---
name: implement
description: Execute an approved Execution Plan by delegating its Work Units to workers, respecting dependencies, boundaries, and escalation rules.
---

# Implement — Implementation

Inputs:

`specs/<change-id>/spec.md`
`specs/<change-id>/tasks.md`
`specs/<change-id>/plan.md`

All MUST be `READY`.

## Execute

Run the Execution Plan wave by wave.

For each Work Unit, delegate one self-contained assignment to a Worker containing:

- Work Unit ID;
- Task IDs;
- relevant specification decisions;
- scope;
- acceptance criteria;
- constraints;
- validation;
- commit expectation.

Provide only context useful to that Work Unit.

## Blockers

When a Worker returns BLOCKED, classify it:

- **Execution Blocker** — the specification and Task remain valid but execution cannot proceed. Resolve or reassign it without changing the specification.
- **Task Gap** — return to `tasks`.
- **Specification Gap** — stop the affected execution path and return to `spec`.

## Completion

Implementation is complete only when every planned Work Unit is complete or explicitly blocked.

MUST NOT declare the change complete.
