Show help for the GitHub issue management system:

## GitHub Issue Management Commands

The issue system helps create detailed GitHub issues and implementation plans from simple descriptions.

### Available Commands:

**Issue Management:**
- `/project:issue-bug [description]` - Create detailed bug report with analysis
- `/project:issue-feature [description]` - Create comprehensive feature request  
- `/project:issue-list [options]` - List and select GitHub issues to work on
- `/project:issue-plan <issue-id>` - Create implementation plan with ultrathink analysis

**Git Workflow:**
- `/project:git-branch [name]` - Create git branch with smart naming from session context
- `/project:git-pr [title]` - Create pull request with AI-generated description
- `/project:git-review [pr-number]` - Ultrathink PR review before merging

**Help:**
- `/project:issue-help` - Show this help

### How It Works:

1. Commands use the `gh` CLI to interact with GitHub
2. AI analyzes your codebase for relevant context
3. Web search provides additional research when needed
4. Issues are created with appropriate labels and formatting
5. Implementation plans use TDD methodology

### Command Details:

**Bug Reports (`/project:issue-bug`)**
- Analyzes codebase for potential causes
- Creates structured reports with reproduction steps
- Includes environment details and impact assessment
- Auto-assigns appropriate labels (bug, priority, area)

**Feature Requests (`/project:issue-feature`)**
- Researches similar implementations
- Creates user stories and acceptance criteria
- Suggests technical approaches based on your architecture
- Includes implementation considerations and risks

**Issue Listing (`/project:issue-list`)**
- Fetches open issues with filtering options
- Displays numbered list for easy selection
- Shows full details for selected issues
- Integrates with planning and session commands

**Implementation Planning (`/project:issue-plan`)**
- Uses ultrathink methodology for deep analysis
- Creates TDD-focused step-by-step plans
- Identifies files to modify and testing strategy
- Requires approval before implementation starts

### Integration with Sessions:

All issue commands offer to start development sessions:

```
/project:issue-plan 42
# Review and approve plan
/project:session-start fix-auth-timeout-issue-42
# Begin TDD implementation following the plan
```

### Best Practices:

- Use descriptive titles that indicate the core problem/feature
- Let AI analyze the codebase before making assumptions
- Review generated plans carefully before approval
- Start sessions with issue numbers for traceability
- Follow TDD approach outlined in implementation plans

### Example Workflows:

**Bug Workflow:**
```
/project:issue-bug Users getting logged out randomly
# AI creates detailed GitHub issue #42
/project:issue-plan 42
# Review comprehensive implementation plan
/project:session-start fix-logout-bug-issue-42
/project:git-branch
# Creates branch: fix/issue-42-logout-bug
# ... code the fix ...
/project:git-pr
# Creates PR with detailed description
/project:git-review
# Ultrathink review before merging
```

**Feature Workflow:**
```
/project:issue-feature Add dark mode support
# AI creates detailed GitHub issue #43
/project:issue-list --label=enhancement
# Review related issues
/project:issue-plan 43
# Approve TDD implementation plan
/project:session-start dark-mode-feature-issue-43
/project:git-branch feature/dark-mode
# ... implement feature ...
/project:git-pr "Add dark mode toggle and theme switching"
/project:git-review
# Comprehensive review with ultrathink analysis
```

### Requirements:

- GitHub CLI (`gh`) must be installed and authenticated
- Project must be a GitHub repository
- Appropriate environment variables for AI models
- Labels should exist in your repository (auto-detected)

### Related Commands:

- `/project:session-help` - Help for session management
- `/project:session-start` - Start development sessions
- `/project:session-update` - Track implementation progress
- `/project:git-branch` - Create branches from session context
- `/project:git-pr` - Create pull requests with AI descriptions
- `/project:git-review` - Ultrathink PR review process 