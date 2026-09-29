---
name: warn-system-commands
description: Trigger this skill whenever suggesting a system command (like terminal, cmd, or WSL commands) to warn the user about what the command actually does and its potential side effects or security risks.
---
# Warn System Commands

## Summary
Whenever you suggest a command to be run in a terminal, command prompt, or WSL environment, you must explicitly explain what the command does under the hood and warn the user of any potential security risks, state changes, or side effects.

## When to Use
- You are providing a shell command, script, or executable command for the user to run.
- The command modifies system state, opens ports, changes permissions, deletes files, or installs software.
- The user asks for a command to achieve a specific administrative or system-level task.

## Steps
1. **Provide the command**: Give the user the exact command they asked for or need.
2. **Break it down**: Briefly explain what the command and its specific flags/arguments do. 
3. **Provide a clear warning**: Add a bolded warning section explaining the exact consequences of running the command. Mention any security implications (e.g., "This opens a port that any software on your machine can access") or destructive actions (e.g., "This will permanently delete files without moving them to the trash").

## Examples
**User:** How do I open Chrome with remote debugging on port 8444?
**Agent:** 
You can do this by running the following command in your terminal:
`"C:\Program Files\Google\Chrome\Application\chrome.exe" --remote-debugging-port=8444`

**What this does:**
This launches Google Chrome and opens a WebSocket connection on port 8444 that allows external tools (like an AI agent or developer tools) to control the browser.

**⚠️ WARNING: Security Risk**
Running this command means **any software running on your computer** can potentially connect to that port and take full control of your Chrome session. This includes reading your open tabs, injecting scripts, or accessing your logged-in sessions. Only run this if you completely trust the application you are using it for, and close the browser when you are done.
