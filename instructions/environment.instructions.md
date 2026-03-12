---
applyTo: '**'
name: 'Environment-Specific Instructions'
description: 'Instructions that are specific to the user\'s environment, such as operating system, installed software, or hardware capabilities. These instructions should be followed when they are relevant to the task at hand.'
---

# Environment-Specific Instructions

## User Setup Details

- **NOTE**: Always check the host before assuming which environment we are in as this repository is shared across user's environments.
- `~/bin/system-report.sh`: Provides detailed information about the current system environment, including OS, installed software, and hardware specifications.
- For python packaging, we use `uv`
- `.envrc` and `.env` files are used to set environment variables and load them into the shell environment via `direnv`
- The user has a custom `~/bin/` directory with various scripts for system information and task management
- Functions are store in the `~/.function/` directory, which may contain additional environment-specific logic
- Aliases are defined in the `~/.alias` directory, which may include shortcuts for environment-specific commands
- The user has `gopass` installed and uses it to retrieve secrets into the environment using functions `gopassget` and `gopassload`
- The user uses `chezmoi` to manage dotfiles across environments, which may include environment-specific configurations
- For linting and error-checking, we use pre-commit hooks defined in `~/.pre-commit-config.yaml`. The only installed hook is `pre-push` for most of the linters, but the gitleaks linter runs on `pre-commit` to check for secrets before any commit is made.
- diff-so-fancy replaces the default `diff` output with a more human-readable format, making it easier to understand changes in code or text files.
- gh (GitHub CLI) is available for interacting with GitHub repositories, issues, and pull requests directly from the command line.
- grep is aliased to `rg --hidden` with some default exclusions

## General Code Creation Instructions
- Languages preferential order: Python, Bash, YAML, JSON. Ansible and GitHub Actions where appropriate. PowerShell is not preferred unless explicitly requested.
- Be careful not to match public code too closely, which is blocked by enterprise policy.
- Place comments on separate lines above the code they reference. - Distinguish new comments by adding an extra '#' after the '#' or '/'. Do not add this symbol to pre-existing comments.
- When specific changes are requested, make only those changes. If you detect serious issues, surface them to the user but do not make changes beyond the scope of the request without explicit permission.
- If the prompt is ambiguous or your confidence in the response is low, ask for more details.
- Prioritize idempotence and secure infrastructure-as-code.
- Use bash environment variables for all sensitive data.
- Take a deliberate second pass before replying to a query. Slow down, self-critique, refine for clarity and structure, and exercise reader awareness.
