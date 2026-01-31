---
description: 'Lessons learned from Ansible development, debugging, and best practices'
applyTo: '**/*.yaml, **/*.yml, **/ansible.cfg'
---

# Ansible Memory

Hard-won lessons from debugging Ansible projects, avoiding common pitfalls, and building robust automation.

## AnsiballZ Module Packaging and Imports

**Problem:** Custom Ansible modules fail at runtime with `No module named 'package_name'` even though the package exists in `library/`.

**Root Cause:** Ansible's AnsiballZ module wrapper only packages and includes files that are imported using the `ansible.module_utils.*` namespace. Arbitrary packages in `library/` (like `library/handlers/`) are not accessible to modules at runtime.

**Solution:**
1. Move custom packages from `library/package_name/` to `library/module_utils/package_name/`
2. Update all imports to use the ansible.module_utils namespace:
   ```python
   # Before (fails at runtime)
   from handlers import get_handler

   # After (works correctly)
   from ansible.module_utils.handlers import get_handler
   ```
3. Add `module_utils = ./library/module_utils` to `ansible.cfg`
4. Add `__all__` declarations to module_utils files for explicit symbol exports

**Validation:** Test with `LOCALTEST=true` for structure validation, then with live devices to catch import errors that only appear during AnsiballZ packaging.

## Boolean Extra Variables Protection Pattern

**Problem:** Command-line boolean extra vars like `-e WRITEMODE=false` create a string `'false'` which evaluates as truthy in Ansible, causing unexpected behavior.

**Root Cause:** Shell argument parsing treats everything as strings unless explicitly formatted as JSON.

**Protection Idiom:** Add this task at the start of playbooks that accept boolean extra vars:

```yaml
- name: Catch and stop a common input error
  ansible.builtin.fail:
    msg: "{{ var_name }} is set to the string 'false' which evaluates as true! Use JSON format: -e '{\"{{ var_name }}\": false}'"
  when:
    - var_name | type_debug == 'str'
    - var_name | lower == 'false'
```

**Correct Usage:** Always use JSON format for boolean extra vars:
```bash
# Wrong - creates string 'false' (truthy!)
ansible-playbook playbook.yml -e WRITEMODE=false

# Correct - creates boolean false
ansible-playbook playbook.yml -e '{"WRITEMODE": false}'

# Also correct - use a YAML file
ansible-playbook playbook.yml -e @extravars.yml
```

## Testing Documentation Standard

**Pattern:** Maintain a `docs/TESTING.md` file in Ansible projects with:
- **Prerequisites** - Required tools, credentials, virtual environments
- **Step-by-step instructions** - Exact commands to run tests
- **Credential management** - How to load secrets securely (e.g., gopass)
- **Expected outputs** - What success looks like
- **Troubleshooting** - Common issues and solutions

**Example Structure:**
```markdown
# Testing Guide

## Prerequisites
- gopass configured with credentials
- Python virtual environment active
- Test inventory configured

## Step 1: Verify Environment
[commands to verify setup]

## Step 2: Load Credentials
[commands to load secrets]

## Step 3: Run Tests
[test execution commands]

## Expected Output
[what success looks like]

## Troubleshooting
[common issues]
```

**Integration:** The ansible.instructions.md should direct developers to check for `docs/TESTING.md` first when working on Ansible projects.

## Module Testing Strategy

**Pattern:** Use a `LOCALTEST` boolean variable to enable stub/mock mode for testing module structure without connecting to real devices.

**Benefits:**
- Test module imports and packaging without network access
- Validate playbook logic locally
- Catch AnsiballZ packaging issues before live testing
- Safe development without risk of affecting production devices

**Implementation:**
```yaml
vars:
  LOCALTEST: true  # Default to safe mode

tasks:
  - name: LOCALTEST - Simulate module execution
    when: LOCALTEST | bool
    # Use stub data and set_fact

  - name: LIVE - Execute on real device
    when: not (LOCALTEST | bool)
    # Call actual custom module
```

**Testing Flow:**
1. Local testing: `ansible-playbook test.yml -e LOCALTEST=true`
2. Live testing: `ansible-playbook test.yml -e '{"LOCALTEST": false}'`
