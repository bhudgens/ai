# AI Coding Assistant Commands

Reusable commands (slash commands, skills, prompts) for AI-powered coding CLIs. Each command is maintained in the native format for each supported tool.

## Supported Tools

| Tool | Config Directory | Invocation | Format |
|------|-----------------|------------|--------|
| [Claude Code](https://docs.anthropic.com/en/docs/claude-code) | `.claude/commands/` | `/command-name` | Markdown, no frontmatter |
| [OpenCode](https://opencode.ai) | `.opencode/command/` | `/command-name` | Markdown with YAML frontmatter |
| [Codex CLI](https://developers.openai.com/codex/cli/) | `.agents/skills/<name>/` | `$skill-name` | `SKILL.md` with YAML frontmatter |

## Commands

| Command | Description | Claude Code | OpenCode | Codex CLI |
|---------|-------------|:-----------:|:--------:|:---------:|
| `gca` | Commit everything in a single commit, pull, then push to origin | `/gca` | `/gca` | `$gca` |
| `ggpnp` | Commit all changes, pull, then push to origin | `/ggpnp` | `/ggpnp` | `$ggpnp` |

## Directory Structure

```
.claude/commands/          # Claude Code slash commands
  gca.md
  ggpnp.md
.opencode/command/         # OpenCode slash commands
  gca.md
  ggpnp.md
.agents/skills/            # Codex CLI agent skills
  gca/
    SKILL.md
  ggpnp/
    SKILL.md
```

## Adding a New Command

To add a new command, create the corresponding file in each tool's directory:

1. **Claude Code**: `.claude/commands/<name>.md` -- plain Markdown, no frontmatter
2. **OpenCode**: `.opencode/command/<name>.md` -- Markdown with YAML frontmatter (`description` field)
3. **Codex CLI**: `.agents/skills/<name>/SKILL.md` -- Markdown with YAML frontmatter (`name` and `description` fields)

The prompt body (steps, instructions) should be identical across all three files. Only the frontmatter and file location differ.
