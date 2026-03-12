---
name: research-plan
description: Research the codebase with a fast model, output a structured context dump, then prompt you to switch to a powerful model for planning. Accepts a task description as argument.
---

# research-plan — Research First, Then Plan

Task: **$ARGUMENTS**

## Phase 1: Context Research (running now)

Spawn a Haiku subagent to comprehensively research the codebase for the task above. The subagent must:

1. Analyze what areas of the codebase are relevant to the task
2. Find and READ every relevant file completely — source code, configs, schemas, tests, docs, READMEs
3. Identify: existing patterns, key APIs, dependencies, naming conventions, architectural constraints
4. Return a detailed RESEARCH REPORT structured as:

```
## RESEARCH REPORT

### Relevant Files
- <path>: <what it does and why it matters>

### Key Code
<most important functions, types, schemas, interfaces — paste verbatim from files>

### Patterns to Follow
<existing conventions in the codebase relevant to this task>

### Constraints & Complications
<anything that will affect implementation — auth, dependencies, test patterns, etc.>

### What Already Exists
<anything already implemented that overlaps with or is adjacent to the task>
```

After receiving the subagent's report, output it in full. Then display this exact message:

---

**Research complete.** All relevant context is loaded above.

**Switch to Opus for planning:**
1. Run `/model opus`
2. Say: **`Plan the task`**

Opus will review the research above and produce a detailed step-by-step implementation plan with exact file paths and function signatures.

---
