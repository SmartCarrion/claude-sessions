Create a detailed GitHub feature request from a simple description using the `gh` CLI.

Usage: `/project:issue-feature [description]` or `/project:issue-feature` (will prompt for description)

The command should:
1. Take the user's simple feature idea as input (from argument or prompt)
2. Analyze the codebase to understand current architecture and implementation patterns
3. Research similar features or implementations using web search if needed
4. Create a comprehensive feature request with:
   - Clear, compelling title
   - User story and problem statement
   - Detailed feature description
   - Acceptance criteria
   - Technical approach suggestions
   - Implementation considerations
   - Potential challenges and risks
   - Related components or dependencies

## Feature Request Template Structure:

```markdown
## User Story
As a [user type], I want [functionality] so that [benefit/value].

## Problem Statement
[What problem does this solve? Why is it needed?]

## Feature Description
[Detailed description of the proposed feature]

## Acceptance Criteria
- [ ] [Criterion 1]
- [ ] [Criterion 2]
- [ ] [Criterion 3]

## Technical Approach
[Suggested implementation approach based on codebase analysis]

## Implementation Considerations
- Architecture: [How it fits with current architecture]
- Dependencies: [Required packages or services]
- Database: [Schema changes if needed]
- API: [New endpoints or modifications]
- UI/UX: [Interface considerations]

## Code References
[Relevant existing files/functions/components to modify or reference]

## Potential Challenges
[Technical risks or complex areas to consider]

## Testing Strategy
[How to verify the feature works correctly]

## Documentation
[What documentation will need updates]
```

After creating the issue:
1. Fetch available labels with `gh label list` to ensure accurate labeling
2. Use `gh issue create` with appropriate labels (enhancement, type:enhancement, priority level, area labels if applicable)
3. Common labels to consider: enhancement, type:enhancement, priority:high/medium, area:* (based on affected components)
4. Display the created issue URL
5. Ask if user wants to start a session to work on this feature 