Create a detailed GitHub bug report from a simple description using the `gh` CLI.

Usage: `/project:issue-bug [description]` or `/project:issue-bug` (will prompt for description)

The command should:
1. Take the user's simple bug description as input (from argument or prompt)
2. Analyze the codebase to understand relevant components and potential causes
3. Use web search if needed to research similar issues or solutions
4. Create a comprehensive bug report with:
   - Clear, descriptive title
   - Detailed description with steps to reproduce
   - Expected vs actual behavior
   - Environment details (OS, browser, versions, etc.)
   - Relevant code snippets or file references
   - Potential impact assessment
   - Suggested investigation areas

## Bug Report Template Structure:

```markdown
## Bug Description
[Clear summary of the issue]

## Steps to Reproduce
1. [Step 1]
2. [Step 2] 
3. [Step 3]

## Expected Behavior
[What should happen]

## Actual Behavior
[What actually happens]

## Environment
- OS: [Operating system]
- Browser: [If applicable]
- Node.js: [Version]
- Package versions: [Relevant packages]

## Code References
[Relevant files/functions/components]

## Potential Causes
[AI analysis of likely causes]

## Impact
[Severity and user impact assessment]

## Investigation Areas
[Suggested areas to investigate]
```

After creating the issue:
1. Fetch available labels with `gh label list` to ensure accurate labeling
2. Use `gh issue create` with appropriate labels (bug, priority level, area labels if applicable)
3. Common labels to consider: bug, priority:high/medium, area:* (based on affected components)
4. Display the created issue URL
5. Ask if user wants to start a session to work on this bug 