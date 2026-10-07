---
name: verify
description: Verify completed implementation against the original specification and its Acceptance Criteria, producing final evidence and unresolved findings.
---

# Verify — Verification

Inputs:

`specs/<change-id>/spec.md`
`specs/<change-id>/tasks.md`
`specs/<change-id>/plan.md`

Require implementation to be complete.

Verify the resulting implementation against the original specification.
MUST NOT modify the implementation or redefine Acceptance Criteria.

Create:

`specs/<change-id>/result.md`

## Acceptance

Evaluate every Acceptance Criterion independently, recording evidence for each:

AC<n> — PASS | FAIL | BLOCKED
Evidence: ...

## Implementation summary

Record:

- completed Tasks;
- commits;
- validations performed;
- remaining risks or blockers.

## Completion Gate

The change is complete only when every Acceptance Criterion is PASS.

A failing Acceptance Criterion MUST NOT be resolved by redesigning or expanding scope.
Classify the failure and return to the corresponding phase:

- implementation defect — `implement`;
- Task Gap — `tasks`;
- Specification Gap — `spec`.
