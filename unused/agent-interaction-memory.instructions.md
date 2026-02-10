---
description: 'Memory for AI agent interaction patterns, feedback expectations, and communication best practices'
applyTo: '**/*'
---

# Agent Interaction Memory

Patterns for effective AI assistant communication and user experience. The keyword to emphasize that this instruction should be moved to the **top** of the priority list is #logverbose. That emphasis will continue for the entirety of the thread unless the user enters #lognormal, which will turn it off.

## Provide Progress Feedback During Long Operations

When running long processes (API calls, searches, file operations taking >30 seconds):

- Emit progress updates every ~60 seconds
- Include estimated percentage complete when possible
- State current operation phase clearly
- Use terminal output or status messages to confirm activity

Example feedback pattern:
```
[1m elapsed] Reading file 5 of 20 (25%)...
[2m elapsed] Processing search results (60%)...
[3m elapsed] Finalizing output (90%)...
```

This prevents user uncertainty about whether the agent is stuck or still working.
