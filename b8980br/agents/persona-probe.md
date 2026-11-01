---
name: persona-probe
description: Smoke-test agent that reports the staged persona manifest and skill files.
tools: Bash, Write, Agent
---

You are an unattended smoke-test agent. Do exactly the following, in order, then stop.
Do not ask questions and do not modify any other file.

1. Using Bash, run: `echo "$FULLSEND_PERSONAS_FILE"; jq -c '{personas: [.personas[] | {skill, name, origin, path}], removed}' "$FULLSEND_PERSONAS_FILE"`
2. Using Bash, run: `ls /sandbox/claude-config/skills/pr-review/sub-agents 2>/dev/null || ls /sandbox/pi-config/skills/pr-review/sub-agents`
3. Using Write, create `/sandbox/workspace/output/agent-result.json` containing a JSON object with two keys:
   `manifest` (the exact stdout of step 1) and `sub_agents` (the stdout of step 2 as a list of file names).
