# Spec Flow

Spec Flow is a model-agnostic workflow for turning intent into verified implementation.

## Project rules

All agent and skill instructions MUST be:

- minimal: include only information required for the role or phase;
- structured: rules, inputs, outputs, gates, and authority are explicit;
- use-agnostic: describe behavior without domain-specific scenarios;
- non-redundant: one rule should have one clear owner;
- operational: every instruction must change behavior, routing, authority, or validation.

Avoid example catalogs, exhaustive do/do-not lists, domain-specific cases, repeated policy, and explanatory prose that does not affect execution.

Every word consumes context. Prefer the smallest instruction set that preserves reproducible behavior.

## Separation of concerns

- `spec` defines the change.
- `tasks` decomposes the change into logical Tasks.
- `schedule` decides execution grouping, Worker type, session boundaries, ordering, and parallelism.
- Workers execute Work Units.
- `verify` evaluates the result against the specification.

Task decomposition MUST remain independent of execution planning. A Task does not select a Worker, session, model, wave, or commit boundary.

## Agents

- `lead` — decisions, routing, synthesis.
- `context` — broad read-only discovery and context compression.
- `worker-short` — bounded execution with a short-context worker.
- `worker-long` — bounded execution when required context is too large for the short-context budget.

## Context policy

Context is a resource and a design constraint.

- Prefer the smallest sufficient execution context.
- Reuse a session only for related Tasks with shared context.
- Do not group unrelated Tasks to amortize a session.
- Short-worker requests target <=80K input tokens and MUST remain below 100K.
- If required context cannot remain below that boundary without harming correctness, schedule a long worker.
- Large context alone does not justify combining Tasks.
- Parallelism exists to unblock dependency progress, not merely to increase throughput.
