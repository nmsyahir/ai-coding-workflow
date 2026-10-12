# AI Coding Agent Rules

## Purpose

This file defines how AI coding agents should work in this repository. An agent may assist with analysis, implementation, testing, and documentation, but it must not make product, security, or release decisions independently.

## Before Making Changes

1. Read the relevant code, tests, and repository documentation.
2. Inspect the current Git status and preserve unrelated work.
3. Confirm the requested scope and identify affected components.
4. State assumptions that could change behaviour or expand scope.
5. Prefer the smallest complete change that satisfies the requirement.

## Implementation Rules

- Follow the existing architecture, naming, and formatting conventions.
- Do not introduce unrelated refactors.
- Do not hide errors or weaken validation to make tests pass.
- Preserve backwards compatibility unless a breaking change is explicitly approved.
- Treat authorization, data exposure, and input validation as security-sensitive.
- Add regression tests for every confirmed bug fix.
- Never bypass repository hooks with options such as `--no-verify`.

## Testing and Validation

Run the checks relevant to the changed component, including:

- unit and integration tests;
- type checking or compilation;
- linting and formatting;
- static analysis;
- a production build, where applicable; and
- focused manual testing for user-facing behaviour.

Report the exact commands, exit codes, and results. A command that exits unsuccessfully must not be described as passing. Separate environmental failures from feature-test results clearly.

## Git and Pull Requests

The agent may prepare code and commits when requested, but it must not perform the following actions without explicit human approval:

- force-push;
- merge or close pull requests;
- push directly to protected or production branches;
- change a pull request's base branch;
- deploy to production;
- modify release versions;
- create external tickets; or
- contact reviewers.

Keep commits focused and use descriptive messages. Before requesting review, inspect the final diff and confirm that it contains no unrelated files.

## Responding to Review Feedback

Address review findings individually. For each finding:

1. Explain the root cause.
2. Describe the actual code or documentation change.
3. Add or update relevant tests.
4. Run the required validation.
5. Update the pull-request description if its scope or behaviour changed.

Do not claim that all feedback is addressed while an item remains unresolved.

Use this format when requesting re-review:

> I've addressed the latest review comments:
>
> 1. **Finding** — Summary of the implemented fix.
> 2. **Finding** — Summary of the implemented fix.
>
> **Validation completed:**
> - `exact command` — result
>
> Could you please re-review when available?

## Multi-Repository Changes

When a task affects multiple repositories:

1. Identify dependencies and the required merge order.
2. Keep each repository's change independently reviewable.
3. Do not duplicate release commits across multiple pull requests.
4. Verify each pull request's base and head branch.
5. Stop for approval before changing the release or deployment flow.

## Security and Privacy

- Never expose credentials, tokens, private keys, or production customer data.
- Do not copy sensitive production values into tests, logs, or documentation.
- Use read-only access when investigating production data unless write access is explicitly required and approved.
- Apply least-privilege authorization.
- Do not infer backend security rules solely from frontend behaviour.

## Communication

- Distinguish verified facts from assumptions.
- Be concise while including enough evidence for another developer to verify the work.
- Surface blockers early.
- Ask before making product, security, release, or cross-team decisions.
