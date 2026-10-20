# Git Conventions

This guideline defines repository history and delivery metadata for Spec Flow. It does not replace `spec`, `tasks`, `schedule`, or `verify` authority.

## Branches

Format: `<type>/<short-kebab-case-description>`; optionally `<type>/<issue-id>-<description>`.

Allowed types: `feat`, `fix`, `refactor`, `perf`, `docs`, `test`, `build`, `ci`, `chore`.

Branches describe the change, not the agent, Work Unit, session, or execution phase. Follow repository-specific branch protection and base-branch rules.

## Commits

Use Conventional Commits:

```text
<type>(<scope>): <imperative summary>

[optional body explaining why and relevant constraints]

[optional footers]
```

Types: `feat`, `fix`, `refactor`, `perf`, `test`, `docs`, `build`, `ci`, `chore`, `revert`.

- Use lowercase types, a stable module-level scope when meaningful, and an English imperative summary without a trailing period.
- Prefer a concise subject (ideally <=72 characters). Put reasoning, migration notes, and limitations in the body.
- Mark breaking changes using `!` and a `BREAKING CHANGE:` footer when applicable.
- Each commit must be coherent and reviewable; neither one commit per Task nor one commit per Work Unit is required.
- Commit only within the approved scope and after the Work Unit's required gates pass. Stage explicit paths; never include unrelated changes.
- Do not rewrite published history unless explicitly authorized.

## Pull requests

PR title: `<type>(<scope>): <outcome-oriented summary>`, using the same type and scope conventions as commits. Describe the delivered change, not Task IDs or agent activity.

A PR represents a reviewable change, not necessarily one Work Unit. Its description must provide:

```markdown
## Summary
What changed and why.

## Changes
- Key behavior and integration changes.
- Relevant behavior intentionally preserved.

## Specification
- Spec: <path or link, if applicable>
- Tasks: <path or link, if applicable>
- Plan: <path or link, if applicable>
- Implementation: <commit SHA or range>

## Validation
- Lint: PASS / FAIL / NOT RUN
- Tests: PASS / FAIL / NOT RUN (include counts where useful)
- Type-check: PASS / FAIL / NOT RUN
- Build: PASS / FAIL / NOT RUN
- Acceptance criteria: VERIFIED / PARTIAL / NOT VERIFIED
- Manual checks: EXECUTED / NOT EXECUTED (specify coverage)

## Findings / Limitations
Open issues, unverified cases, environment constraints, and baseline comparisons.

## Impact
Breaking changes, schema/data changes, dependencies, configuration, or "None".

## Review Notes
Areas requiring focused review.
```

Use accurate evidence: a code trace is not an executed manual test. Do not claim an environmental failure is preexisting without a baseline comparison. Do not duplicate the full spec in the PR; link to its authoritative source.

## Workflow and authority

- `spec` owns requirements and acceptance criteria; `tasks` owns decomposition; `schedule` owns Work Units, sessions, dependencies, and commit boundaries.
- Workers follow the approved plan and report validation evidence. They must not silently expand scope or fix unrelated defects.
- `verify` owns the final assessment against the spec. A committed implementation, passing tests, or `PASS WITH FINDINGS` does not by itself mean verified or ready to merge.
- When a missing or changed requirement is discovered, route it through change control and revalidate affected artifacts before implementing the new scope.
- A failed mandatory gate blocks the corresponding commit or handoff unless the approved plan explicitly defines an alternative. Report failures rather than masking them.
- Do not push, open a PR, merge, tag, or release without the authorization required by the current plan and repository policy.

## Automation

Repositories may enforce commit messages with commitlint, PR titles with a title check, and required CI checks. These checks complement, but do not replace, review and the `verify` gate. Avoid requiring irrelevant PR fields for changes that do not use Spec Flow.
