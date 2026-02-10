---
applyTo: '**'
name: 'Instruction Priority & Conflict Resolution'
description: 'Defines the order of precedence when instructions conflict'
---

# Instruction Priority Matrix

## General Guidance

When instructions conflict, the following hierarchy determines which instruction takes precedence. Higher items override lower ones. If there is still ambiguity or the result seems suboptimal, the user should be informed of the conflict and asked for clarification.

## Instruction Hierarchy

When instructions conflict, apply in this order:

1. **Direct User Commands** (highest)
   - Explicit instructions in current conversation
   - Includes prompts imported from file like `prompts/smartplan.prompt.md`
   - Override ALL other instructions

2. **Specific to this User (peter216)**
   - `copilot-instructions.md`
   - `agent-interaction-memory.instructions.md`
   - `sanity-check-mode.md`
   - `thought-logging-instructions.md`

3. **Safety & Security**
   - `no-heredoc.instructions.md`
   - `security-and-owasp.instructions.md`

4. **Code Quality**
   - `performance-optimization.instructions.md`
   - `self-explanatory-code-commenting.instructions.md`

5. **Platform-Specific**
   - OS-specific instructions (when applicable)
   - Language-specific instructions (when applicable)
   - Tool-specific instructions (when applicable)

6. **General Guidance**
   - `taming-copilot.instructions.md`
   - DevOps principles
   - Code review guidelines

## Conflict Resolution Examples

**Example 1: Security vs. Simplicity**
- User asks for "quick file write to test something"
- No-heredoc rule (safety) **blocks** terminal heredoc despite simplicity preference
- **Resolution**: Use file editing tool instead

**Example 2: Verbose Logging vs. Minimal Response**
- `#logverbose` is active (explicit user activation)
- Taming Copilot normally prefers concise responses
- **Resolution**: Full verbose logging takes precedence (user command)

**Example 3: Platform-Specific vs. Code Quality**
- Arch Linux instructions suggest `pacman -Syu`
- Performance optimization suggests checking package sizes first
- **Resolution**: Both apply—run performance check, then use platform command

## Active Keywords & Modes

| Keyword | Effect | Duration | Deactivation |
|---------|--------|----------|--------------|
| `#logverbose` | Enable detailed thought logging | Until `#lognormal` | `#lognormal` |
| `#sanitycheck` | Deep thinking for better responses | Session unless disabled | `fastmode` |
