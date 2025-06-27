Create a comprehensive implementation plan for a selected GitHub issue using ultrathink methodology.

Usage: `/project:issue-plan <issue-id>` or `/project:issue-plan` (will prompt for issue ID)

The command should:
1. Take an issue ID (from issue-list or direct input, from argument or prompt)
2. Fetch the full issue details using `gh issue view <id>`
3. Analyze the codebase to understand:
   - Current architecture and patterns
   - Relevant existing code and components
   - Dependencies and related systems
   - Testing patterns and requirements
4. Research best practices if needed using web search
5. Apply ultrathink analysis to deeply understand the problem and solution space
6. Create a detailed TDD-focused step-by-step implementation plan
7. Present the plan for user approval before starting work

## Implementation Plan Structure:

```markdown
# Implementation Plan: [Issue Title]

## Issue Summary
- **Issue #**: [GitHub issue number]
- **Type**: [Bug/Feature/Enhancement]
- **Priority**: [Based on labels]
- **Estimated Complexity**: [Simple/Medium/Complex]

## Current State Analysis
[Analysis of relevant existing code and architecture]

## Implementation Strategy
[High-level approach and reasoning]

## Step-by-Step Implementation Plan

### Phase 1: Analysis & Preparation
- [ ] [Analyze existing code and architecture]
- [ ] [Identify dependencies and integration points]
- [ ] [Research best practices and similar implementations]
- [ ] [Define acceptance criteria and success metrics]

### Phase 2: Test Strategy Planning
- [ ] [Identify what behaviors need to be tested]
- [ ] [Plan unit tests for core functionality]
- [ ] [Plan integration tests for component interactions]
- [ ] [Define test data and fixtures needed]

### Phase 3: Implementation Approach
- [ ] [Core implementation steps]
- [ ] [File modifications and new components needed]
- [ ] [API/interface design decisions]
- [ ] [Data flow and state management approach]

### Phase 4: Validation & Documentation
- [ ] [Manual testing scenarios]
- [ ] [Documentation updates required]
- [ ] [Code review considerations]
- [ ] [Deployment/release considerations]

## Files to Modify/Create
- `[file1.ts]` - [Purpose of changes]
- `[file2.tsx]` - [Purpose of changes]
- `[new-file.ts]` - [New file purpose]

## Testing Strategy
**TDD Approach - Tests will be written first during implementation:**
- Define expected behaviors through tests before coding
- Focus on unit tests for core logic
- Integration tests for component interactions
- Edge cases and error conditions

**Test Coverage Plan:**
- Unit tests: [Specific functions/methods to test]
- Integration tests: [Component interactions to verify]
- End-to-end tests: [User workflows if applicable]
- Performance tests: [If performance is a concern]

## Potential Risks & Mitigations
[Known challenges and how to address them]

## Success Criteria
[How to verify the implementation is complete and correct]

## Estimated Timeline
[Rough time estimate for completion]
```

## Approval Process:
1. Present the complete plan to the user
2. Allow them to:
   - Approve and start implementation
   - Request modifications to the plan
   - Ask questions about specific steps
   - Cancel if the scope is too large

After approval:
1. Offer to start a session with the issue title/number
2. Begin implementation following the approved plan
3. Update the GitHub issue with a comment linking to the implementation plan 