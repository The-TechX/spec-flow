---
name: discover
description: Reduce material uncertainty through evidence. Use when the current state, constraints, or options must be understood before the surrounding work can continue.
---

# Discover — Discovery

Discovery produces evidence and understanding, not decisions.

## Objective

Answer the question with the evidence it requires.
Scope MUST be proportional to the question.

## Rules

- Discovery is read-only. Inspect any evidence source. MUST NOT modify code, configuration, infrastructure, data, or external systems, or use a side-effecting tool when a read-only alternative exists. Only the user can change the task to mutation.
- Delegated investigation MUST be read-only.
- Broad repository, system, or evidence discovery SHOULD be delegated to the Context Agent. The Lead synthesizes its findings; the Context Agent does not make decisions.
- Discovery SHOULD produce the smallest downstream context packet that preserves the evidence needed for the next decision.
- SHOULD use the strongest available evidence and the narrowest inspection that suffices.
- MUST validate assumptions against evidence and trace actual behavior rather than infer it.
- MUST label every claim: **Fact** (observed, with evidence), **Inference** (with reasoning), **Hypothesis** (unvalidated), **Recommendation** (only when evidence supports one), or **Unresolved**. MUST NOT present an inference or hypothesis as fact.
- MAY iterate. MUST stop when further investigation is unlikely to change the next decision, or when what remains requires user input or unavailable information.
- If the question proves wrong or incomplete, MUST return to the user instead of answering a different one.
- MUST NOT select or enter another phase. On completion, return control to the Lead.

## Output

Respond directly.
MUST NOT create an artifact unless preserving the investigation materially helps later work:

`specs/<change-id>/discovery.md`

An artifact records evidence and understanding. It is not normative and defines no scope, decisions, or Acceptance Criteria.

Every discovery MUST state:

- Question;
- Findings, each labeled and evidenced;
- Assumptions;
- Constraints;
- Risks;
- Options, when requested;
- Recommendation, when supported;
- Open Questions;
- Status and Outcome.

An artifact begins with:

# <Subject> — Discovery

Status: DRAFT | READY

Outcome: MORE_DISCOVERY_NEEDED | USER_INPUT_NEEDED | DISCOVERY_COMPLETE | NO_CHANGE_NEEDED

Use stable IDs: `F1`, ... for Findings; `Q1`, ... for Open Questions.

## Outcome

- `MORE_DISCOVERY_NEEDED` — `DRAFT`. Investigation that could change the next decision remains.
- `USER_INPUT_NEEDED` — `DRAFT`. Progress requires a decision or information only the user can provide.
- `DISCOVERY_COMPLETE` — `READY`. The question is answered.
- `NO_CHANGE_NEEDED` — `READY`. The findings show that no change is warranted.

## Gate

Discovery is `READY` only when the question is sufficiently answered for the surrounding work to continue without unsupported assumptions, and:

- the question is stated;
- findings are labeled and evidenced;
- material assumptions are identified;
- every remaining unknown is an Open Question with its effect on the next decision;
- constraints and significant risks are recorded;
- requested options are described.
