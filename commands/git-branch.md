Create a git branch for the current development work, with smart naming based on session context.

Usage: `/project:git-branch [branch-name]` or `/project:git-branch` (will suggest name from session)

The command should:
1. Check if there's an active session to get context from
2. Suggest branch name based on:
   - Current session name
   - Active GitHub issue number (if working on an issue)
   - Current work description
3. Create and checkout the new branch
4. Push the branch to origin to set up tracking

## Branch Naming Conventions:

**For features:**
- `feature/description-of-feature`
- `feature/issue-42-add-dark-mode`

**For bugs:**
- `fix/description-of-bug`
- `fix/issue-42-auth-timeout`

**For small improvements:**
- `improve/description`
- `refactor/auth-middleware`

## What it does:

- Analyzes current session for context clues
- Suggests appropriate branch name with prefix
- Creates and switches to the new branch
- Sets up remote tracking with `git push -u origin branch-name`
- Updates session notes with branch creation

## Examples:

```
# Working on issue #42 in session "fix-auth-timeout-issue-42"
/project:git-branch
# Suggests: "fix/issue-42-auth-timeout"

# Custom branch name
/project:git-branch feature/user-profiles

# Working on general improvements
/project:git-branch improve/performance-optimization
```

After creating the branch:
1. Confirm branch creation and current branch status
2. Remind about branch deployment options (Vercel, etc.)
3. Suggest next steps in the workflow 