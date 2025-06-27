List existing development sessions from `.claude/sessions/` and allow the user to resume an unfinished session by selecting its number.

The command should:
1. Scan the `.claude/sessions/` directory for session files (format: `YYYY-MM-DD-HHMM*.md`)
2. Parse each session file to determine if it's unfinished (no "## Session End" section or end timestamp)
3. Display a numbered list of unfinished sessions showing:
   - Session number (for selection)
   - Date/time
   - Session name (if provided)
   - Brief preview of goals or current status
4. Prompt user to enter the number of the session they want to resume
5. Update `.claude/sessions/.current-session` to track the selected session filename
6. Confirm which session has been resumed

Session status determination:
- **Unfinished**: No "## Session End" section or missing end timestamp
- **Finished**: Contains "## Session End" section with completion timestamp

If no unfinished sessions exist, offer to start a new session instead.

After resuming, remind the user they can:
- Update it with `/project:session-update`
- End it with `/project:session-end`
- View current session with `/project:session-status`