---
applyTo: '**'
name: 'Environment-Specific Instructions'
description: 'Instructions that are specific to the user\'s environment, such as operating system, installed software, or hardware capabilities. These instructions should be followed when they are relevant to the task at hand.'
---

# Environment-Specific Instructions

## Tools for Understanding the Environment

- `~/bin/system-report.sh`: Provides detailed information about the current system environment, including OS, installed software, and hardware specifications.

## User Setup Details

- **Operating System**: On host `HDQBELT1006036` the user is running `Ubuntu 24.04.1 LTS` on `WSL2` with `Windows 11 Pro`
- **Hardware**: Host `HDQBELT1006036` is a Lenovo ThinkPad G14 Gen 3 with 48GB RAM.
- **NOTE**: Always check the host before assuming which environment we are in as this repository is shared across user's environments.
- For python packaging, we use `uv`
- `.envrc` and `.env` files are used to set environment variables and load them into the shell environment via direnv
- The user has a custom `~/bin/` directory with various scripts for system information and task management
- Functions are store in the `~/function/` directory, which may contain additional environment-specific logic
- Aliases are defined in the `~/.alias` directory, which may include shortcuts for environment-specific commands
- The user has `gopass` installed and uses it to retrieve secrets into the environment using functions `gopassget` and `gopassload`
- The user uses `chezmoi` to manage dotfiles across environments, which may include environment-specific configurations
- For linting and error-checking, we use pre-commit hooks defined in `~/.pre-commit-config.yaml`. The only installed hook is `pre-push`
