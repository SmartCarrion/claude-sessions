Create a GitHub pull request from the current branch with AI-generated description based on session context.

Usage: `/project:git-pr [title]` or `/project:git-pr` (will generate title from context)

The command should:
1. Analyze current session for PR context
2. Review git changes and commit history 
3. Generate comprehensive PR description including:
   - Summary of changes
   - Related issue links
   - Testing performed
   - Deployment notes (if applicable)
4. Create PR using `gh pr create`
5. Update session with PR link

## PR Description Template:

```markdown
## Summary
[Brief description of what this PR does]

## Related Issues
- Fixes #[issue-number]
- Addresses [session-name]

## Changes Made
- [List of key changes from commit analysis]
- [File modifications]
- [New features/fixes]

## Testing
- [Manual testing performed]
- [Test cases added/updated]
- [Verification steps]

## Deployment Notes
- [Preview deployment available at...]
- [Environment considerations]
- [Configuration changes needed]

## Review Checklist
- [ ] Code follows project standards
- [ ] Tests added/updated for changes
- [ ] Documentation updated if needed
- [ ] No breaking changes (or properly documented)
```

## Integration with Sessions:

- Uses session details for context
- References GitHub issues if working on specific issues
- Includes implementation notes from session updates
- Links back to session documentation

## Examples:

```
# Auto-generated from session context
/project:git-pr
# Creates PR with title from issue and session

# Custom title
/project:git-pr "Add user profile customization features"

# Working on bug fix
/project:git-pr "Fix authentication timeout in middleware"
```

After creating the PR:
1. Display PR URL and number
2. Update current session with PR reference
3. Suggest next steps (self-review, testing, deployment)
4. Remind about review checklist 