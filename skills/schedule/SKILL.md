---
name: schedule
description: Compile READY Tasks into executable Work Units, sessions, ordering, and worker assignments.
---

# Schedule

Inputs:

`specs/<change-id>/spec.md`
`specs/<change-id>/tasks.md`

Both MUST be `READY`.

Create:

`specs/<change-id>/plan.md`

## Objective

Plan execution without changing the specification or Task decomposition.

A Work Unit is an ordered group of related Tasks executed by one worker session.

For each Work Unit define:

### WU<n>

Tasks:
Worker: SHORT | LONG
Dependencies:
Context sources:
Estimated peak prompt:
Session: NEW | CONTINUE
Validation:
Commit boundary:

## Worker selection

- SHORT uses `worker-short`.
- LONG uses `worker-long`.
- Prefer SHORT when the required execution context can stay safely below 100K input tokens.
- Target SHORT at <=80K estimated peak prompt.
- Use LONG when correct execution requires context that cannot be reduced below the SHORT boundary without losing necessary information.
- Worker choice MUST NOT change Task scope.

## Grouping

- Group Tasks only when they are related and materially reuse context.
- A session MAY execute multiple Tasks.
- Do not group unrelated Tasks to amortize context or startup cost.
- Estimated peak prompt applies per request, not to cumulative lifetime tokens.

## Parallelism

Parallelize only when independent Work Units unblock distinct dependency paths.
Do not parallelize solely for throughput.

## Gate

`plan.md` is `READY` only when:

- every Task belongs to one Work Unit;
- Task dependencies are respected;
- worker type and session boundary are explicit;
- SHORT Work Units are expected to remain below 100K peak prompt;
- validation and commit boundaries are explicit;
- parallelism is dependency-justified;
- the user approves the plan.

If planning exposes a Task Gap, return to `tasks`.
If it exposes a Specification Gap, return to `spec`.
