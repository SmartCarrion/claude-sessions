Show help for the session management system:

## Session Management Commands

The session system helps document development work for future reference.

### Available Commands:

- `/project:session-start [name]` - Start a new session with optional name
- `/project:session-resume` - Resume an existing unfinished session
- `/project:session-update [notes]` - Add notes to current session  
- `/project:session-end` - End session with comprehensive summary
- `/project:session-list` - List all session files
- `/project:session-current` - Show current session status
- `/project:session-help` - Show this help
- `/project:issue-help` - Help for GitHub issue management

### How It Works:

1. Sessions are markdown files in `.claude/sessions/`
2. Files use `YYYY-MM-DD-HHMM-name.md` format
3. Only one session can be active at a time
4. Sessions track progress, issues, solutions, and learnings

### Best Practices:

- Start a session when beginning significant work
- Update regularly with important changes or findings
- End with thorough summary for future reference
- Review past sessions before starting similar work

### Example Workflows:

**Starting a New Session:**
```
/project:session-start refactor-auth
/project:session-update Added Google OAuth restriction
/project:session-update Fixed Next.js 15 params Promise issue  
/project:session-end
```

**Resuming an Existing Session:**
```
/project:session-resume
# Shows numbered list of unfinished sessions
# Select session number to resume
/project:session-update Continued work on authentication
/project:session-end
```

### Integration with GitHub Issues:

Sessions work seamlessly with the GitHub issue management system:

```
/project:issue-bug Authentication timeouts
# Creates GitHub issue #42
/project:issue-plan 42
# Creates implementation plan
/project:session-start fix-auth-timeout-issue-42
# Tracks implementation progress
```

For GitHub issue management help, use `/project:issue-help`.