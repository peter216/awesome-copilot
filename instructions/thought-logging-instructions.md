---
applyTo: '**'
name: 'Thought Logging Instructions'
description: These instructions guide the thought logging process for handling user requests, ensuring structured planning, execution, and documentation of progress in the `Copilot-Processing.md` file.
---

# Thought logging instructions

Patterns for effective AI assistant communication and user experience. The keyword to emphasize that this instruction should be moved to the **top** of the priority list is #logverbose. That emphasis will continue for the entirety of the thread unless the user enters #lognormal, which will turn it off.

## Initialization and Log File Management

- Create file `Copilot-Processing.md` in workspace root.
  - If the file already exists, rename it /Copilot-Processing-<datetime>.md (where datetime is the file modification time) and create a new `/Copilot-Processing.md`.
  - If you do not have writing permissions, ask the user to grant them or manually move the file.
  - Maximum size of the file should not exceed 1MB; archive older entries if necessary.
  - Maximum number of archived files: 5; delete oldest if exceeded.
- Populate `Copilot-Processing.md` with user request details

## Planning

- Generate an action plan into the `Copilot-Processing.md` file.
- Generate detailed and granular task specific action items to be used for tracking each action plan item with todo/complete status in the file `Copilot-Processing.md`.
- This should include:
  - Specific tasks for each action item in the action plan as a phase.
  - Clear descriptions of what needs to be done
  - Any dependencies or prerequisites for each task
  - Ensure tasks are granular enough to be executed one at a time

## Periodic Progress Updates

- Save work-in-progress to `Copilot-Processing.md` after each task, tool call, or other short unit of work.
- Provide status updates as described in the "Provide Progress Feedback During Long Operations" section below.
- If interrupted, try to ensure that `Copilot-Processing.md` documents current state and next steps for resumption of work.

**Progress Update Format:**

```log
[Timestamp] Progress Update:
- Completed: [Section name]
- Currently analyzing: [Component/decision]
- Next: [What's coming]
- Questions to resolve: [Any blockers]
```

## Provide Progress Feedback During Long Operations

When running long processes (API calls, searches, file operations taking >30 seconds), run it through a task/script that:

- Emits progress updates or a heartbeat every 30-60 seconds
- Include estimated percentage complete when possible
- States current operation phase clearly
- Prints a final sentinel __DONE__ message upon completion

Example feedback pattern:

```log
[1m elapsed] Reading file 5 of 20 (25%)...
[2m elapsed] Processing search results (60%)...
[3m elapsed] Finalizing output (90%)...
```

This prevents user uncertainty about whether the agent is stuck or still working.

## Phase 4: Summary

- Add summary of work done to `Copilot-Processing.md`
- Execute this step only when ALL actions complete
- Emit message: "Added final summary to `Copilot-Processing.md`."
