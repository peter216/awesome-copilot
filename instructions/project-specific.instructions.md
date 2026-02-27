---
applyTo: '**'
name: Project-specific reminders for Copilot
description: This file contains project-specific reminders and guidance for working with Copilot, including implementation plans, testing practices, and documentation updates. If you are not sure what project you are working on, ask the user.
---

# FS Switches POC-1 Implementation Plan

This note records the workflow reminders for working through the
`FS Switches POC-1 Implementation Plan` (branch: `feature/refactoring`).

Guidance (apply after each implementation step):

- Create or update unit/integration/e2e tests covering the behavior added or changed.
- Run the full test suite and ensure all tests pass locally before committing.
- Commit changes with a clear message (e.g. `feat(poc1): <short description>`).
- Run pre-commit hooks (they will run on commit and push) and fix any linter/formatter errors (e.g. Ruff, ruff-format).
- Update `docs/refactor/implementation-plan-poc-1.md` to add check-marks for the corresponding acceptance criteria for the completed step.
- Push when the local branch is green and tests/linting pass.
- Ask the user whether to open a PR after each Phase is complete and tested.

Notes:

- Keep changes small and focused per step in the plan — one logical change per commit.
- When adding time-sensitive behavior (timeouts, retries, circuit-breakers), include unit tests that simulate failures and timing behavior where possible.
- If pre-commit auto-fixes change many files, re-run tests before committing the final state.

Reference files to update after each step:

- `docs/refactor/implementation-plan-poc-1.md`
- Tests under `tests/unit/`, `tests/integration/`, and `tests/e2e/`
