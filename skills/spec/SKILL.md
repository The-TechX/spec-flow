---
name: spec
description: Build and refine the specification for a requested change. Use from initial intent until the desired outcome, scope, decisions, acceptance criteria, and open questions are resolved and approved.
---

# Spec — Specification

Own the change specification. MUST NOT create implementation Tasks or begin implementation.

Create or maintain:

`specs/<change-id>/spec.md`

`spec.md` is the normative source of intent, scope, constraints, decisions, Acceptance Criteria, Change Outline, and Open Questions. Later phases consume it and MUST NOT silently redefine it.

## Objective

Turn user intent into a complete, agreed definition of the desired change and what constitutes success.

Resolve only uncertainty that materially affects the change, using:

- existing context first;
- the user for product, scope, preference, and operational decisions;
- workers for focused technical discovery;
- Lead reasoning to synthesize evidence and make engineering conclusions.

If a material uncertainty exceeds focused technical discovery, return to `discover` instead of assuming.

## Specification

Maintain:

# <Change title>

Status: DRAFT | READY

## Intent

Why this change exists.

## Desired Outcome

Concrete description of the resulting behavior or state.

## Scope

What is included and excluded.

## Constraints

Requirements that constrain acceptable solutions.

## Decisions

Material decisions already resolved.

## Acceptance Criteria

Observable or verifiable conditions that define success, with stable IDs: AC1, AC2, ...

## Change Outline

High-level logical changes expected to achieve the outcome.

## Open Questions

Only unresolved questions that can materially affect the specification.

## Gate

The specification is `READY` only when:

- Desired Outcome is unambiguous;
- Scope and Constraints are explicit;
- every material decision is resolved;
- Acceptance Criteria completely define success;
- Open Questions is empty;
- the user approves the specification.
