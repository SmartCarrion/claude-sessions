List GitHub issues and allow the user to select one to work on.

Usage: `/project:issue-list [--label=<label>] [--assignee=<user>] [--milestone=<milestone>]`

The command should:
1. Use `gh issue list` to fetch open issues from the repository
2. Display issues in a numbered list with:
   - Issue number (for selection and GitHub reference)
   - Title
   - Labels (bug, enhancement, etc.)
   - Assignee (if any)
   - Creation date
   - Brief preview of description
3. Allow filtering by:
   - Labels (bug, enhancement, documentation, etc.)
   - Assignee
   - Milestone
   - State (open/closed)
4. Prompt user to enter the number/ID of the issue they want to work on
5. Display full issue details for the selected issue including:
   - Complete description
   - Comments
   - Related pull requests
   - Current assignee status

## Display Format:

```
Open Issues:

1. #42 - Fix authentication timeout bug [bug, priority-high]
   Created: 2 days ago | Assigned: unassigned
   Preview: Users are getting logged out unexpectedly after...

2. #41 - Add dark mode support [enhancement, ui]
   Created: 1 week ago | Assigned: @user
   Preview: Implement dark theme toggle for better user...

3. #40 - Update API documentation [documentation]
   Created: 2 weeks ago | Assigned: unassigned
   Preview: API docs are outdated and missing new endpoints...
```

## Filter Options:
- `/project:issue-list --label=bug` - Show only bugs
- `/project:issue-list --assignee=@me` - Show issues assigned to you
- `/project:issue-list --milestone="v1.2"` - Show issues in specific milestone

After selection:
1. Store the selected issue ID for potential use with session-start
2. Ask if user wants to:
   - Start a session to work on this issue
   - Create an implementation plan
   - Just view the issue details 