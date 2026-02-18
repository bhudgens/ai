---
description: Commit all changes, pull from origin, then push to origin
---

# ggpnp - Commit, Pull, and Push

Commit all current changes, pull from origin, then push to origin on the current branch.

## Steps

1. Run `git status` (no `-uall` flag) to see untracked and modified files.
2. Run `git diff` to see staged and unstaged changes.
3. Run `git log --oneline -5` to see recent commit message style.
4. Analyze all changes and draft a concise commit message:
   - Summarize the nature of the changes (new feature, enhancement, bug fix, refactoring, etc.)
   - Focus on the "why" rather than the "what"
   - Keep it to 1-2 sentences
   - NEVER add Co-Authored-By lines
   - Do not commit files that likely contain secrets (.env, credentials, etc.)
5. Stage relevant files by name (prefer specific files over `git add -A`).
6. Create the commit using a HEREDOC for the message.
7. Determine the current git branch name.
8. Run `git pull origin <branch>` to pull latest changes.
9. Run `git push origin <branch>` to push local commits.

Always use explicit remote (`origin`) and branch name. Never use bare `git push` or `git pull`.
