---
description: Analyze and restructure a repository for AI-native development by establishing the 5 pillars — root CLAUDE.md, skills, hooks, progressive docs, and local context files
---

# organize - Structure a Repository for AI-Native Development

Analyze the current repository and restructure it so AI coding assistants behave like project-native engineers rather than chatbots. This means establishing the 5 pillars: root CLAUDE.md, skills, hooks, progressive docs, and local context files.

## Steps

### Phase 1: Audit

1. Read the existing `CLAUDE.md` (if any) at the repo root.
2. List the top-level directory structure and key subdirectories (src, lib, app, etc.).
3. Check for existing `.claude/`, `.opencode/`, `.agents/` directories and their contents.
4. Check for a `docs/` directory and its contents.
5. Look for local `CLAUDE.md` files in subdirectories.
6. Read `package.json`, `Cargo.toml`, `go.mod`, `pyproject.toml`, or equivalent to understand the project type, dependencies, and scripts.
7. Read `README.md` if it exists to understand the project purpose.
8. Run `git log --oneline -20` to understand recent development activity.

### Phase 2: Present Findings

Present a concise audit report to the user:

```
## Repository Audit

### What exists
- <list what's already in place>

### What's missing
- <list which of the 5 pillars are absent or incomplete>

### Recommendations
- <prioritized list of what to create/improve>
```

Ask the user to confirm before proceeding. Wait for their response.

### Phase 3: Create/Update Root CLAUDE.md

Create or update the root `CLAUDE.md` with exactly three sections. Keep it SHORT — clarity beats size. If a `CLAUDE.md` already exists, preserve any existing rules and merge new content.

```markdown
# <Project Name>

## Purpose
<1-3 sentences: what the system does and why it exists>

## Repo Map
<brief directory tree with one-line descriptions of each top-level directory>

## Rules & Commands
<key constraints, forbidden patterns, required commands (build, test, lint, format)>
```

Do NOT make CLAUDE.md long. If it exceeds ~50 lines, it's too long. Move details to docs/ instead.

### Phase 4: Set Up Skills Directory

If `.claude/commands/` does not already exist with project-specific skills (ignore skills that came from this repo), suggest 2-4 skills based on what the project actually does. Common candidates:

- **review**: Code review checklist tailored to the project's patterns
- **debug**: Debugging workflow using the project's logging/testing setup
- **refactor**: Refactoring playbook following the project's conventions
- **deploy**: Release/deployment procedure
- **test**: How to write and run tests in this project

Only create skills the project would genuinely use. Ask the user which ones they want before creating them.

### Phase 5: Set Up Hooks (Suggest Only)

Hooks must be configured by the user, not created automatically. Suggest specific hooks based on what the project uses:

- If the project has a formatter (prettier, black, rustfmt, gofmt): suggest a post-edit formatting hook
- If the project has tests: suggest a post-edit test hook for core modules
- If the project has sensitive directories (auth, billing, migrations, infra): suggest guard hooks

Present the suggestions as a list. Do NOT create hook files.

### Phase 6: Set Up Progressive Documentation

If `docs/` does not exist or is sparse, create a minimal structure:

- `docs/architecture.md` — high-level system overview, key components, data flow
- `docs/decisions/` — directory for ADRs (Architecture Decision Records), with a template `docs/decisions/000-template.md`

Only populate these files with content you can confidently derive from the codebase. For anything uncertain, leave a `TODO: <describe what should go here>` placeholder.

### Phase 7: Add Local CLAUDE.md Files

Identify directories with hidden complexity — places where mistakes are expensive or conventions are non-obvious. Common candidates:

- Authentication/authorization modules
- Database/persistence layers
- Infrastructure/deployment configs
- Payment/billing code
- Migration files

For each identified directory, create a local `CLAUDE.md` with:
- What this module does
- Key constraints and gotchas
- What NOT to do

Only create these for directories that genuinely need them. Ask the user to confirm which ones before creating.

### Phase 8: Summary

Output a final summary of everything that was created or modified, formatted as a checklist:

```
## What was done

- [x] Root CLAUDE.md — created/updated
- [x] docs/architecture.md — created
- [x] docs/decisions/000-template.md — created
- [ ] Hooks — suggestions provided (user must configure)
- [x] src/auth/CLAUDE.md — created
- ...
```
