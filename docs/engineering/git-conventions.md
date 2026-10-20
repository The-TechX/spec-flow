# Git Conventions

Recommended, project-agnostic conventions for readable Git history and reviewable changes. Repository-specific policies, tooling, and explicit project instructions take precedence. Examples and formats below are defaults, not exhaustive vocabularies. English is the default language for Git metadata; repository-specific policies take precedence.

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

- Write commit messages in English. Choose clear, natural verbs and phrasing; no fixed verb vocabulary is required.
- Prefer a concise subject; add a body when rationale, constraints, or consequences are not obvious.
- Use a scope when it adds useful context; do not invent one solely to satisfy a template.
- Describe breaking changes explicitly and follow the project's release conventions.
- Group commits by coherent, reviewable changes. Tasks, execution units, and commits need not map one-to-one.
- Stage only intended files and honor required checks and commit boundaries.
- Do not rewrite shared history without authorization.

## Pull requests

A PR title should summarize the delivered outcome in English. Using the project's commit convention is a reasonable default.

### Minimum PR description

Every PR should use these three sections, in this order. Keep them concise, but do not omit them:

```markdown
## Summary
What changed and why.

## Changes
- Key modifications and relevant behavior.

## Validation
- Check or review performed: PASS / FAIL / NOT RUN, with evidence when relevant.
- Explicitly identify meaningful checks that were not executed.
```

### Conditional sections

Add the following sections only when their information is relevant:

- `## References` — issue, specification, tasks, plan, design, or implementation links.
- `## Findings / Limitations` — unresolved issues, uncertainties, environment constraints, or follow-up work.
- `## Impact` — breaking changes, schema/data changes, dependencies, configuration, migration, or operational impact.
- `## Review Notes` — areas requiring special reviewer attention.

### Additional sections

Agents may add other sections when the change warrants them (for example, `## Migration`, `## Rollback`, or `## Screenshots`). Use the same `## Title` Markdown heading level and concise, evidence-based content as the standard sections. Avoid redundant or empty sections. Keep the three minimum sections in their defined order; place conditional or custom sections where they best support review.

A code-path review is not an executed manual test. Do not label an issue preexisting without supporting comparison. Link to authoritative artifacts rather than duplicating large specifications. PR creation and verification status remain subject to project approval gates.

## Agent workflow and authority

When a project uses structured phases, roles, or work plans, follow their documented ownership and approval gates. In Spec Flow, these are defined by `spec`, `tasks`, `schedule`, and `verify`; other projects may use different processes or none.

- Follow the approved scope and report deviations instead of silently expanding work.
- If requirements change or ambiguity materially affects implementation, request clarification or follow the project's change-control process.
- A commit or passing automated checks does not independently establish that all acceptance criteria were verified.
- Report failed required checks and respect any approved alternatives; do not conceal failures.
- Push, PR creation, merge, tagging, and release follow the authority granted by the project and current instructions.

## Optional automation

Projects may use commitlint, PR title checks, templates, or CI gates when beneficial. Configure enforcement to match the project's conventions, not this document's examples. Automation supports review and verification; it does not replace them.
