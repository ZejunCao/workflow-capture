---
name: workflow-capture
description: |
  Use this skill when the user explicitly wants to execute a complex or unfamiliar task AND capture the process as a reusable workflow. Triggers when the user says things like "help me do X and record the steps", "do this task and save it as a workflow", "capture this process for reuse", "record this as a skill", "do X and document it for next time", or any combination of executing a task + wanting to save the steps for future use.

  Do NOT trigger for ordinary tasks where the user just wants the result. ONLY trigger when the user explicitly signals they want the process recorded/captured/saved.
---

# Workflow Capture

This skill does two things in sequence:
1. **Execute** a task with interactive error recovery, tracking every step
2. **Crystallize** the experience into a reusable SKILL.md file

---

## Phase 1: Task Setup

Before starting, briefly confirm scope with the user (2-3 questions max):

- What is the end goal of this task?
- Any known constraints or environment details? (OS, language, file formats, etc.)
- What should the output Skill be named?

Then announce:
> _"Got it. I'll execute step by step and track everything. If something goes wrong, I'll pause and check with you. When we're done, I'll turn the whole experience into a reusable Skill."_

---

## Phase 2: Execution with Step Tracking

Maintain an internal **Step Log** as you work:

```
Step N: [what you're doing]
Status: ✅ success / ❌ failed / ⚠️ workaround
Notes: [important context, caveats, or parameter values]
Error (if any): [exact error or failure description]
Fix Applied: [what resolved it]
```

### Error Handling Protocol

When a step fails, **pause immediately** and surface it:

> ❌ **Step N failed**
> Problem: [concise description]
> Likely cause: [1-2 guesses]
> My suggestion: [recommended fix]
> How would you like to proceed?

User options:
- Confirm suggested fix → apply and continue
- Provide their own fix → apply it, note it in the log
- "Skip this step" → mark skipped, continue
- "Stop here" → proceed to Phase 3 with partial results

**Never silently retry more than once.** Always surface to the user after the first failed auto-retry.

### Progress Updates

After each successful step:
> ✅ Step N done: [one-line summary] | Next: [what's coming]

---

## Phase 3: Skill Generation

Once the task is complete (or the user decides to stop):

> 🎉 Done! Let me turn this experience into a reusable Skill.

Generate a `SKILL.md` based on the Step Log:

```markdown
---
name: [task-name-in-kebab-case]
description: |
  Use this skill when the user wants to [task description].
  Triggers on phrases like: [3-5 example trigger phrases].
---

# [Task Name]

## Prerequisites
[Environment, tools, and parameters needed before starting — learned from this session]

## Steps

### Step 1: [Name]
[What to do]

⚠️ **Common pitfall**: [document any error + fix encountered here]
💡 **Note**: [caveats or conditions]

### Step 2: [Name]
...

## Reusable Snippets
[Commands, code, or configs used verbatim — ready to copy-paste]

## Troubleshooting

| Symptom | Cause | Fix |
|---------|-------|-----|
| ...     | ...   | ... |

## Variants
[Variations based on OS, file type, environment, etc.]
```

### Quality Rules

- **Be specific, not generic** — reflect what actually happened, not textbook theory
- **Errors are first-class content** — every error + fix must appear both inline and in the troubleshooting table
- **Make parameters explicit** — replace specific values with `[REPLACE: description]`
- **Keep steps atomic** — one action per step; use sub-bullets for sub-actions

---

## Phase 4: Review & Save

Present the draft and ask:

> Here's the Skill generated from this session. You can:
> - Save it as-is
> - Tell me what to change
> - Ask me to expand any step

After confirmation, save as `[skill-name]/SKILL.md` and offer download.

> _"Next time, upload this file at the start of a conversation and I'll follow the workflow directly — no more trial and error."_

---

## Notes for Claude

- **The skill is a side-effect, not the goal.** Complete the task well first; logging is secondary.
- **Log internally, surface selectively.** Only show the user status updates and error pauses — don't dump raw logs.
- **Generalize on generation.** Specific values from execution (e.g., `192.168.1.1`) become `[REPLACE: server IP]` in the output skill.
- **One skill per task type.** If two distinct tasks were run, offer two separate Skill files.
- **Language matching.** Generate the output Skill in the same language the user communicated in.
