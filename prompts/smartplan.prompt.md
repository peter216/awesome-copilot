---
mode: 'agent'
description: 'Create comprehensive refactoring and architecture migration plans with ambiguity resolution, decision documentation, and implementation-ready output'
tools: ['changes', 'search/codebase', 'edit/editFiles', 'problems', 'runCommands', 'usages']
---

# Smart Plan Generator

## Overview

Generate detailed refactoring and architecture migration plans that document current state, target architecture, ambiguities, and step-by-step implementation paths. Plans are optimized for human/AI collaborative execution.

## When to Use This Prompt

- Large-scale code refactoring projects
- Architecture migrations or transformations
- API consolidation or redesign
- Modernization initiatives (framework upgrades, pattern updates)
- Extracting components into libraries or separate projects
- Any complex code transformation requiring careful planning

## Primary Directive

Create a comprehensive plan that bridges current state to target architecture, documenting all decisions, trade-offs, and ambiguities for future implementation.

**State Management:** Planning progress, analysis findings, and decisions are logged to `/Copilot-Processing.md` at workspace root for recovery if interrupted. Verbose logging mode (#logverbose) is active and will remain on until explicitly disabled with #lognormal.

## Input Parameters

Gather these parameters before planning:
- **Goal**: ${input:What is the overall refactoring objective?}
- **Target Architecture**: ${input:What is the desired end state?}
- **Constraints**: ${input:What must be preserved or cannot change?}
- **Output File**: ${input:Where should the plan be saved? (default: docs/REFACTOR.md)}

## Planning Process

### Phase 1: Current State Analysis

1. **Code Inventory**
   - Identify all components that will be affected
   - Map dependencies between modules/files
   - Document existing patterns and conventions
   - Identify code duplication and technical debt

2. **Functionality Mapping**
   - List all current features and behaviors
   - Document edge cases and special handling
   - Identify vendor-specific or platform-specific code
   - Note any modules/libraries that must be kept vs. can be replaced

3. **Data Flow Analysis**
   - Trace how data moves through the system
   - Identify transformation points
   - Document input/output contracts
   - Map error handling and retry logic

### Phase 2: Target Architecture Design

1. **Define New Structure**
   - Design consolidated APIs or modules
   - Plan new file/directory organization
   - Specify interface contracts
   - Design extensibility points for future needs

2. **Simplification Opportunities**
   - Apply DRY (Don't Repeat Yourself) principles
   - Identify code that can be consolidated
   - Remove unnecessary complexity
   - Standard error handling patterns

3. **Preserve Critical Behaviors**
   - Document functionality that must be preserved exactly
   - Identify breaking vs. non-breaking changes
   - Plan backward compatibility strategies if needed

### Phase 3: Ambiguity and Decision Documentation

**For Each Ambiguity Discovered:**

1. **State the Ambiguity Clearly**
   - What is unclear or has multiple valid approaches?
   - Why does this matter to the refactoring?

2. **Present Options**
   - List 2-4 viable approaches
   - For each option, document:
     - Pros (benefits and advantages)
     - Cons (drawbacks and risks)
     - Effort required
     - Impact on existing code

3. **Provide Recommendation**
   - State your recommended approach
   - Explain why this option is preferred
   - Note any conditions or assumptions

4. **Document Rejected Options**
   - Briefly explain why other options were not chosen
   - This prevents revisiting the same debates later

**Template for Ambiguity Documentation:**

```markdown
### Ambiguity: [Clear Question Statement]

**Current State:** [How it works now]

**Question:** [What needs to be decided?]

**Options:**

1. **Option A: [Name]**
   - Pros: [Benefits]
   - Cons: [Drawbacks]
   - Effort: [Low/Medium/High]
   - Impact: [Scope of changes]

2. **Option B: [Name]**
   - Pros: [Benefits]
   - Cons: [Drawbacks]
   - Effort: [Low/Medium/High]
   - Impact: [Scope of changes]

**Recommendation:** Option [A/B] because [reasoning]

**Rejected Options:** Option [X] rejected because [reason]
```

### Phase 4: Migration Plan Creation

1. **Define Phases**
   - Break work into logical, testable phases
   - Each phase should be independently deployable if possible
   - Order phases to minimize risk (non-breaking first)

2. **Specify Phase Details**
   - List specific files to create/modify
   - Identify dependencies between phases
   - Define success criteria for each phase
   - Note rollback strategies

3. **Testing Strategy**
   - Unit test requirements
   - Integration test needs
   - Backward compatibility validation
   - Performance testing if applicable

### Phase 5: File Structure Documentation

Create clear before/after file structure diagrams:

```markdown
## File Structure After Refactoring

project/
├── new_module/
│   ├── __init__.py
│   ├── core.py              # NEW: Consolidated functionality
│   ├── handlers/            # NEW: Extensibility point
│   │   ├── base.py
│   │   └── specific.py
│   │
│   ├── # DEPRECATED - Remove after migration:
│   ├── old_module_1.py      # → core.py
│   └── old_module_2.py      # → core.py
│
└── tests/
    ├── test_core.py         # NEW
    └── test_handlers.py     # NEW
```

## Output Format

### Document Structure

The plan document must include:

1. **Executive Summary**
   - High-level goal and approach
   - Key decisions made
   - Estimated complexity/risk level

2. **Current Architecture Analysis**
   - Component inventory with status (keep/consolidate/remove)
   - Functionality mapping
   - Dependency analysis

3. **Proposed Architecture**
   - New component design
   - Interface specifications
   - Extensibility points

4. **Ambiguities and Recommendations**
   - All decision points documented
   - Recommended paths with rationale
   - Rejected alternatives with reasons

5. **Migration Plan**
   - Phase-by-phase breakdown
   - Dependencies and ordering
   - Testing strategy
   - Rollback approach

6. **File Structure Changes**
   - Before/after comparison
   - New files to create
   - Files to deprecate/remove

### Writing Guidelines

- **Write for Both Humans and AI**
  - Use clear, unambiguous language
  - Include code examples where helpful
  - Use tables for comparisons
  - Create diagrams for complex relationships

- **Be Implementation-Ready**
  - Provide enough detail for someone unfamiliar with the codebase
  - Include specific file paths and function names
  - Reference existing code patterns
  - Note any gotchas or edge cases

- **Challenge Assumptions**
  - Do a second pass to identify hidden assumptions
  - Question whether each decision is truly necessary
  - Verify no circular dependencies in the plan
  - Confirm all existing functionality is accounted for

## Quality Standards

### Completeness Checklist

- [ ] All current functionality is documented
- [ ] Target architecture is clearly specified
- [ ] All ambiguities are identified and resolved
- [ ] Migration plan has clear phases with success criteria
- [ ] Testing strategy is defined
- [ ] File structure changes are documented
- [ ] Dependencies and ordering are clear
- [ ] Rollback strategy is defined

### Simplicity Principles

- **DRY (Don't Repeat Yourself)**: Consolidate duplicated code
- **KISS (Keep It Simple)**: Choose simplest solution that meets requirements
- **YAGNI (You Aren't Gonna Need It)**: Don't add complexity for hypothetical future needs
- **Readability Over Cleverness**: Clear code beats clever code

### Risk Assessment

For each major decision or phase, assess:
- **Complexity**: How difficult to implement?
- **Risk**: What could go wrong?
- **Impact**: How much code affected?
- **Reversibility**: Can we easily roll back?

## Example Usage

**User Input:**
```
Create a plan to refactor our data access layer from multiple ORMs to a single
unified approach. Current state has Entity Framework, Dapper, and raw ADO.NET
scattered across 50+ repositories. Target is consolidated Entity Framework Core
with a shared base library. Save to docs/data-access-refactor.md.
```

**Agent Response Pattern:**
```
I'll create a comprehensive refactoring plan. Starting analysis:

[5min] Analyzing current state...
- Found 23 EF usage points
- Found 18 Dapper usage points
- Found 12 raw ADO.NET usage points

[10min] Mapping functionality...
- Standard CRUD: Can consolidate easily
- Bulk operations: Dapper has performance advantage - need to preserve
- Stored procedures: Mixed approaches - need decision

[15min] Documenting ambiguities...
Ambiguity 1: Should we keep Dapper for bulk operations?
  Option A: Pure EF Core with batching
  Option B: Hybrid EF Core + Dapper for bulk
  Recommendation: Option B because...

[20min] Creating migration plan...
Phase 1: Create base library
Phase 2: Migrate simple repositories
Phase 3: Migrate complex repositories
...

Plan written to docs/data-access-refactor.md
```

## Success Criteria

A successful plan includes:

- **Clarity**: Anyone can understand the current state and target
- **Completeness**: All functionality accounted for
- **Actionability**: Implementer knows exactly what to build
- **Traceability**: Every decision has documented reasoning
- **Testability**: Clear criteria for validating each phase
- **Flexibility**: Can adapt if requirements change
- **Simplicity**: No unnecessary complexity

## Common Pitfalls to Avoid

1. **Assumption Traps**: Making implicit assumptions about behavior
2. **Scope Creep**: Adding improvements beyond the stated goal
3. **Over-Engineering**: Designing for hypothetical future needs
4. **Under-Documenting**: Leaving decisions unexplained
5. **Missing Edge Cases**: Forgetting special handling or error scenarios
6. **Ignoring Existing Patterns**: Not following established conventions
7. **Skipping Test Strategy**: Not planning how to validate changes

## Templates and Patterns

### Phase Template

```markdown
### Phase [N]: [Phase Name]

**Goal:** [What this phase achieves]

**Changes:**
1. Create `path/to/file.py` incorporating:
   - Functionality from `old/file1.py`
   - Functionality from `old/file2.py`
   - New [specific capability]

2. Update `existing/file.py`:
   - Replace direct calls with new interface
   - Add error handling for [scenario]

**Testing:**
- Unit tests: [What to test]
- Integration tests: [What to validate]
- Backward compatibility: [How to verify]

**Success Criteria:**
- [ ] All tests passing
- [ ] No regression in [functionality]
- [ ] Documentation updated

**Rollback:**
- If issues found, revert commits [X, Y, Z]
- Restore original modules [list]
```

### Decision Record Template

```markdown
## Decision: [What was decided]

**Context:** [Why this decision was needed]

**Considered Options:**
1. [Option 1]: [Brief description]
2. [Option 2]: [Brief description]
3. [Option 3]: [Brief description]

**Decision:** [Chosen option]

**Rationale:** [Why this option]

**Consequences:**
- Positive: [Benefits]
- Negative: [Trade-offs]
- Neutral: [Other impacts]

**Review Date:** [When to revisit]
```

## Output File Naming

Default: `docs/REFACTOR.md`
Alternative patterns:
- `docs/migration-plan-[component].md`
- `docs/architecture-refactor-[date].md`
- `docs/[component]-consolidation-plan.md`

## Notes

- Plans are living documents - expect to update as implementation reveals new information
- Share plans with stakeholders for review before implementation
- Use the plan as a communication tool between team members
- Version control the plan alongside code changes
- Reference the plan in commit messages during implementation

---

**Remember**: The goal is not just to document "what" to do, but "why" each decision was made. Future maintainers (including yourself) will thank you.
