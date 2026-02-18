# ggpnp - Git Pull and Push

Equivalent to the oh-my-zsh `ggpnp` alias: pull from origin then push to origin on the current branch.

## Steps

1. Determine the current git branch name.
2. Run `git pull origin <branch>` to pull the latest changes.
3. Run `git push origin <branch>` to push local commits.

Always use explicit remote (`origin`) and branch name. Never use bare `git push`.
