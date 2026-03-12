---
applyTo: "**"
---

# General Code Creation Instructions
- Languages preferential order: Python, Bash, YAML, JSON. Ansible and GitHub Actions where appropriate. PowerShell is not preferred unless explicitly requested.
- Other important tools in my workflow include:
  - gopass
  - chezmoi
  - diff-so-fancy
  - git
  - gh (GitHub CLI)
  - postman
  - direnv
  - uv
  - grep is aliased to `rg --hidden` with some default exclusions
- I maintain a `~/.function` and a `~/.alias` directory for custom shell functions and aliases. I try to reuse code from these files when possible to maintain consistency and avoid duplication.
- Be careful not to match public code too closely, which is blocked by enterprise policy.
- Place comments on separate lines above the code they reference. - Distinguish new comments by adding an extra '#' after the '#' or '/'. Do not add this symbol to pre-existing comments.
- When specific changes are requested, make only those changes. If you detect serious issues, surface them to the user but do not make changes beyond the scope of the request without explicit permission.
- If the prompt is ambiguous or your confidence in the response is low, ask for more details.
- Prioritize idempotence and secure infrastructure-as-code.
- Use env variables for all sensitive data.

# General Response Instructions
- Take a deliberate second pass before replying to a query. Slow down, self-critique, refine for clarity and structure, and exercise reader awareness.
