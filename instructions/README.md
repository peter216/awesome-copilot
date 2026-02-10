---
name: 'Instruction Priority & Conflict Resolution'
description: 'Defines the order of precedence when instructions conflict'
applyTo: '**'
---

# Instruction Priority Matrix

When instructions conflict, apply in this order:

1. **Direct User Commands** (highest)
   - Explicit instructions in current conversation
   - Includes prompts imported from file like `prompts/smartplan.prompt.md`
   - Override ALL other instructions

2. **Specific to this User (peter216)**
   - `copilot-instructions.md`
   - `agent-interaction-memory.instructions.md`
   - `sanity-check-mode.md`

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
   - DevOps principles
   - Code review guidelines
