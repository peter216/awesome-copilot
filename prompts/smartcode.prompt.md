---
mode: 'agent'
description: 'Structured approach for implementing complex refactoring, migration, or feature development following a documented plan with incremental progress, testing, and checkpoints'
tools: ['changes', 'search/codebase', 'edit/editFiles', 'problems', 'runCommands', 'testFailure', 'usages', 'web']
---

# Smart Code Implementation

## Overview

Execute complex code changes systematically following a documented plan, using incremental progress with git checkpoints, comprehensive testing strategies, and continuous validation against best practices.

## When to Use This Prompt

- Implementing multi-phase refactoring plans
- Migrating code between architectures or frameworks
- Large-scale feature development with detailed specifications
- Code transformations that require careful step-by-step execution
- Any development work with a documented implementation plan

## Primary Directive

Follow the documented plan step-by-step, validate at each checkpoint, and maintain code quality throughout the implementation process.

**State Management:** Progress, decisions, and phase completions are logged to `/Copilot-Processing.md` at workspace root for recovery if interrupted. Verbose logging mode (#logverbose) is active and will remain on until explicitly disabled with #lognormal.

## Input Parameters

Before starting, gather:
- **Goal**: ${input:What is the overall objective?}
- **Plan Document**: ${input:Path to the implementation/migration plan document}
- **Git Branch**: ${input:Branch name for this work}
- **Best Practice Instructions**: ${input:Paths to coding standards/instruction files}

## Execution Workflow

### Phase 1: Planning and Context Gathering

1. **Read the Complete Plan**
   - Read the entire plan document referenced
   - Understand all phases, dependencies, and success criteria
   - Identify any ambiguities or missing information

2. **Gather Repository Context**
   - Examine existing code structure and patterns
   - Identify files and components that will be affected
   - Check for related documentation, tests, and configuration

3. **Validate Understanding**
   - Ask clarifying questions about unclear aspects
   - Confirm assumptions about the approach
   - Propose alternative solutions if appropriate

### Phase 2: Incremental Implementation

1. **Work Phase-by-Phase**
   - Take one phase of the plan at a time
   - Do not skip ahead or combine phases without explicit approval
   - Complete each phase fully before moving to the next

2. **Implement with Best Practices**
   - Follow referenced coding standards and instruction files
   - Apply DRY (Don't Repeat Yourself) principles
   - Maximize readability over cleverness
   - Simplify code structure where possible
   - Use clear, descriptive names for functions, variables, and files

3. **Create Test Infrastructure**
   - Implement stub/mock data for unit testing
   - Create a test mode flag (e.g., `LOCALTEST`, `STUB_MODE`) to enable testing without external dependencies
   - Design tests to validate functionality at each phase

4. **Challenge Your Implementation**
   - Do a second pass to verify no hidden assumptions
   - Question whether the approach is the simplest solution
   - Validate that the code is testable and maintainable

### Phase 3: Validation and Checkpointing

1. **Test Thoroughly**
   - Run stub/mock tests to verify functionality
   - If live system testing is needed, stop and request specific test instructions
   - Validate that all success criteria for the phase are met

2. **Code Quality Checks**
   - Run linters and syntax checkers
   - Verify code follows best practice instructions
   - Check for potential issues or edge cases

3. **Git Checkpoint**
   - Create a descriptive commit message explaining what was implemented
   - Include reference to the phase or step from the plan
   - Tag with any relevant issue/ticket numbers

4. **Review with User**
   - Summarize what was completed in this phase
   - Highlight any decisions made or trade-offs
   - Request approval before proceeding to next phase

### Phase 4: Communication and Progress Tracking

1. **Provide Periodic Updates**
   - Give progress updates at least every 5 minutes of work
   - Explain what you're doing and why
   - Note if you encounter unexpected complexity or blockers

2. **Record State Periodically**
   - Update `/Copilot-Processing.md` with current progress for recovery if interrupted
   - Note any deferred decisions or future considerations
   - Track completed phases and remaining work with status updates

3. **Ask Questions Proactively**
   - Don't proceed with guesses when information is missing
   - Request clarification on ambiguous requirements
   - Flag if you lack access to a needed tool or resource

## Quality Standards

### Code Quality

- **Readability First**: Code should be self-documenting with clear intent
- **Consistency**: Follow existing patterns and conventions in the codebase
- **Modularity**: Break complex logic into smaller, focused functions/modules
- **Error Handling**: Include appropriate error handling and validation
- **Documentation**: Add comments explaining WHY, not WHAT (code should show what)

### Testing Strategy

- **Stub/Mock Testing**: Create test data that simulates real scenarios
- **Progressive Testing**: Test after each phase, not just at the end
- **Test Mode Toggle**: Implement a way to run tests without external dependencies
- **Edge Cases**: Consider and test boundary conditions and error scenarios

### Git Hygiene

- **Atomic Commits**: Each commit represents one complete logical change
- **Clear Messages**: Commit messages explain what and why
- **Checkpoint Strategy**: Commit after each successful phase
- **Branch Management**: Keep work isolated on feature/refactoring branches

## Templates and Patterns

### Test Mode Pattern

Implement a test mode flag that enables stub data usage:

```python
# Example in Python
if os.getenv('LOCALTEST') == 'true' or stub_mode:
    # Use stub/mock data
    data = load_stub_data()
else:
    # Use real system
    data = fetch_from_api()
```

### Progress Tracking Pattern

Keep a simple checklist of phases:

```markdown
## Implementation Progress

- [x] Phase 1: Foundation - COMPLETE (commit abc123)
- [x] Phase 2: Core Logic - COMPLETE (commit def456)
- [ ] Phase 3: Integration - IN PROGRESS
- [ ] Phase 4: Cleanup - NOT STARTED
```

### Validation Checklist Pattern

After each phase, verify:

```markdown
## Phase Validation Checklist

- [ ] All planned changes implemented
- [ ] Code passes syntax checks and linters
- [ ] Tests created and passing (stub mode)
- [ ] Documentation updated
- [ ] Best practices followed
- [ ] Git commit created with clear message
- [ ] User review requested
```

## Common Pitfalls to Avoid

1. **Skipping Ahead**: Don't jump to later phases before completing current work
2. **Assuming Understanding**: Always ask when requirements are unclear
3. **Over-Engineering**: Keep solutions simple and focused on the stated goal
4. **Neglecting Tests**: Create test infrastructure early, not as an afterthought
5. **Silent Assumptions**: Make assumptions explicit and validate them
6. **Batch Changes**: Make incremental changes with frequent checkpoints
7. **Ignoring Existing Patterns**: Follow established conventions in the codebase

## Example Usage

**User Input:**
```
Use smartcode.prompt.md to implement the refactoring plan in docs/API_REFACTOR.md.
We're working on the 'api-v2-migration' branch and should follow the standards
in .github/instructions/*.md. Create TESTMODE variable for stub testing.
```

**Agent Response Pattern:**
```
I'll implement the API refactoring plan systematically. Let me start by:

1. Reading docs/API_REFACTOR.md completely
2. Examining current API structure
3. Reviewing coding standards in .github/instructions/

[After reading]

I've analyzed the plan which has 4 phases:
- Phase 1: Create new API endpoints
- Phase 2: Update client code
- Phase 3: Deprecate old endpoints
- Phase 4: Remove old code

I have a clarifying question about Phase 2: Should we support both old and
new endpoints during migration, or do a hard cutover?

[Continue with incremental implementation...]
```

## Success Criteria

Implementation is successful when:

- All phases of the plan are completed
- Code passes all quality checks and tests
- Each phase has a git checkpoint commit
- Documentation is updated
- User has approved each phase before proceeding
- Final code is production-ready and maintainable

## Notes

- This prompt emphasizes **incremental progress** over speed
- **Communication** is prioritized - ask questions rather than guess
- **Testing** is built in from the start, not added later
- **Code quality** is never sacrificed for expediency
- **Checkpoints** provide rollback points and progress visibility
