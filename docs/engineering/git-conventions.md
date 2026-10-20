# Git Conventions

Recommended, project-agnostic conventions for readable Git history and reviewable changes. Repository-specific policies, tooling, and explicit project instructions take precedence. Examples and formats below are defaults, not exhaustive vocabularies or mandatory wording.

## Principles

- Prefer clear, concise descriptions of the outcome and intent over rigid wording.
- Preserve traceability from a change to its relevant requirements, implementation, and validation when those artifacts exist.
- Record what was actually checked; distinguish automated results, manual execution, and code inspection.
- Respect the project's branching, review, security, and release policies.

## Branch names

Suggested pattern: `<category>/<short-description>`, optionally including a tracking identifier.

Examples: `feat/onboarding-card`, `fix/upload-timeout`, `docs/git-guidelines`.

Choose a category that communicates intent. Common categories include `feat`, `fix`, `docs`, `refactor`, and `chore`, but other names are valid. Prefer describing the work rather than the agent, session, or execution unit. Existing repository conventions take precedence.

## Commit messages

Conventional Commits is a useful default where the project has no established format:

```text
<type>[(optional-scope)]: <summary>

[optional context and rationale]

[optional footers]
```

Common types include `feat`, `fix`, `docs`, `refactor`, `perf`, `test`, `build`, `ci`, `chore`, and `revert`. This is illustrative, not an allowed-type whitelist.

- Choose natural language, tense, and verbs that best communicate the change, unless project tooling requires a specific style.
- Prefer a concise subject; add a body when rationale, constraints, or consequences are not obvious.
- Use a scope when it adds useful context; do not invent one solely to satisfy a template.
- Describe breaking changes explicitly and follow the project's release conventions.
- Group commits by coherent, reviewable changes. Tasks, execution units, and commits need not map one-to-one.
- Stage only intended files and honor required checks and commit boundaries.
- Do not rewrite shared history without authorization.

## Pull requests

A PR title should summarize the delivered outcome. Reusing the project's commit convention is a reasonable default, not a requirement.

A PR description should communicate the relevant information without duplicating other authoritative artifacts. Adapt or omit sections that do not apply:

```markdown
## Summary
What changed and why.

## Changes
Notable behavior, integration, and intentional non-changes.

## References
Relevant issue, specification, tasks, plan, design, or implementation links, if available.

## Validation
Checks performed and their actual results; identify checks not run.

## Findings / Limitations
Open issues, uncertainties, environmental constraints, or follow-up work.

## Impact
Breaking changes, data/schema changes, dependencies, configuration, or operational impact, if relevant.

## Review Notes
Areas that warrant attention, if any.
```

A code-path review is not a manual test. Do not label an issue preexisting without supporting comparison. Use links rather than reproducing large specifications.

## Agent workflow and authority

When a project uses structured phases, roles, or work plans, follow their documented ownership and approval gates. In Spec Flow, these are defined by `spec`, `tasks`, `schedule`, and `verify`; other projects may use different processes or none.

- Follow the approved scope and report deviations instead of silently expanding work.
- If requirements change or ambiguity materially affects implementation, request clarification or follow the project's change-control process.
- A commit or passing automated checks does not independently establish that all acceptance criteria were verified.
- Report failed required checks and respect any approved alternatives; do not conceal failures.
- Push, PR creation, merge, tagging, and release follow the authority granted by the project and current instructions.

## Optional automation

Projects may use commitlint, PR title checks, templates, or CI gates when beneficial. Configure enforcement to match the project's conventions, not this document's examples. Automation supports review and verification; it does not replace them.
