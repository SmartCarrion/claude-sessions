# Claude Code Session Management Commands

Custom slash commands for Claude Code that provide comprehensive development session tracking and documentation. Based on [Claude Code's custom slash command system](https://docs.anthropic.com/en/docs/claude-code/slash-commands).

## 🎯 Overview

This is a set of custom slash commands for Claude Code that helps developers maintain continuity across multiple coding sessions with Claude by:

- **Documenting Progress**: Capture what was done, how it was done, and why decisions were made
- **Tracking Changes**: Monitor git changes, todo items, and implementation details  
- **Knowledge Transfer**: Enable future sessions to understand past work without re-analyzing the entire codebase
- **Issue Resolution**: Document problems encountered and their solutions for future reference

These commands extend Claude Code's built-in functionality with project-specific session management capabilities.

## 🚀 Quick Start

### Session Management
```bash
# Start a new session (with optional name)
/project:session-start authentication-refactor
# Or without a name
/project:session-start

# Resume an existing unfinished session
/project:session-resume

# Update progress during development (with optional notes)
/project:session-update Implemented OAuth with Google
# Or without notes (auto-summarizes recent activity)
/project:session-update

# End session with comprehensive summary
/project:session-end

# View current session status
/project:session-current

# List all past sessions
/project:session-list
```

### GitHub Issue Management
```bash
# Create detailed bug reports from simple descriptions
/project:issue-bug Users getting logged out randomly
# Or prompt for description
/project:issue-bug

# Create detailed feature requests
/project:issue-feature Add dark mode support
# Or prompt for description  
/project:issue-feature

# List and select GitHub issues to work on
/project:issue-list
# With filtering
/project:issue-list --label=bug

# Create implementation plan for selected issue
/project:issue-plan 42
# Or prompt for issue ID
/project:issue-plan
```

### Git Workflow Integration
```bash
# Create git branch with smart naming from session context
/project:git-branch
# Or with custom name
/project:git-branch feature/user-profiles

# Create pull request with AI-generated description
/project:git-pr
# Or with custom title
/project:git-pr "Fix authentication timeout issues"

# Perform ultrathink PR review before merging
/project:git-review
# Or review specific PR
/project:git-review 42
```

## 📁 File Structure

```
commands/                       # Custom command directory
├── session-start.md           # Command for starting a new session
├── session-update.md          # Command for updating current session
├── session-end.md             # Command for ending and summarizing
├── session-current.md         # Command for viewing current status
├── session-list.md            # Command for listing all sessions
├── session-help.md            # Command for showing help
├── issue-bug.md               # Command for creating bug reports
├── issue-feature.md           # Command for creating feature requests
├── issue-list.md              # Command for listing GitHub issues
├── issue-plan.md              # Command for creating implementation plans
├── git-branch.md              # Command for creating git branches
├── git-pr.md                  # Command for creating pull requests
└── git-review.md              # Command for ultrathink PR reviews

sessions/                      # Session storage directory
├── .current-session          # Tracks the active session filename
├── 2025-01-16-1347.md       # Example session file
└── [YYYY-MM-DD-HHMM-name].md  # Session naming format
```

## 🛠️ Installation

1. Clone this repository or copy the folders to your project:
   
   ```bash
   git clone git@github.com:iannuttall/claude-sessions.git
   # Or copy the commands and sessions folders to your project root
   ```

2. Create the sessions tracking file:
   
   ```bash
   mkdir -p sessions
   touch sessions/.current-session
   ```

3. Add to `.gitignore` if you don't want to track sessions:
   
   ```
   sessions/
   ```

## 📝 How It Works

This system provides custom slash commands inspired by [Claude Code's custom slash commands](https://docs.anthropic.com/en/docs/claude-code/slash-commands#custom-slash-commands) feature. While Claude Code typically looks for commands in `.claude/commands/`, this repository provides a standalone implementation with commands in the `commands/` directory.

- **Prefix**: All commands use the `/project:` prefix (for project-specific commands)
- **Arguments**: Commands support arguments using the `$ARGUMENTS` placeholder
- **Execution**: Claude reads the command file and executes the instructions within
- **Note**: These commands are designed to work with Claude but can be adapted for other AI coding assistants

## 📋 Command Reference

### Session Management Commands

#### `/project:session-start [name]`

Starts a new development session with an optional descriptive name.

#### `/project:session-resume`

Lists existing unfinished development sessions and allows resuming by selecting a number.

**What it does:**

- Scans `.claude/sessions/` for session files
- Identifies unfinished sessions (no "## Session End" section)
- Displays numbered list with dates, names, and goal previews
- Updates `.current-session` to track the resumed session
- Offers to start a new session if no unfinished sessions exist

**Examples:**

```
# Resume from list of unfinished sessions
/project:session-resume
```

**Parameters:**

- `[name]` (optional) - A descriptive name for the session. If omitted, creates a session with just the timestamp.

**What it does:**

- Creates a new markdown file with timestamp (format: `YYYY-MM-DD-HHMM.md` or `YYYY-MM-DD-HHMM-name.md`)
- Sets up session structure with goals and progress sections
- Updates `.current-session` to track active session
- Prompts for session goals if not clear from context

**Examples:**

```
# With a descriptive name
/project:session-start refactor-auth-system

# Without a name (just timestamp)
/project:session-start
```

#### `/project:session-update [notes]`

Adds timestamped updates to the current session.

**Parameters:**

- `[notes]` (optional) - Custom notes about the update. If omitted, automatically summarizes recent activities.

**What it does:**

- Appends progress notes with timestamp
- Captures git status and changes
- Tracks todo list progress
- Documents issues and solutions
- Records implementation details
- Auto-generates summary if no notes provided

**Examples:**

```
# With custom notes
/project:session-update Fixed Next.js 15 params Promise issue

# Without notes (auto-summarizes)
/project:session-update
```

#### `/project:session-end`

Ends the current session with a comprehensive summary.

**What it does:**

- Generates complete session summary including:
  - Duration and timing
  - Git changes summary
  - Todo items completed/remaining
  - Key accomplishments
  - Problems and solutions
  - Dependencies and configuration changes
  - Lessons learned
  - Tips for future developers
- Clears `.current-session` file

#### `/project:session-current`

Shows the status of the current active session.

**What it does:**

- Displays session name and duration
- Shows recent updates
- Lists current goals and tasks
- Reminds of available commands

#### `/project:session-list`

Lists all session files with summaries.

**What it does:**

- Shows all session files sorted by date
- Displays session titles and timestamps
- Highlights currently active session
- Shows brief overview of each session

#### `/project:session-help`

Displays help information about the session system.

### GitHub Issue Management Commands

#### `/project:issue-bug [description]`

Creates a comprehensive GitHub bug report from a simple description.

**Parameters:**

- `[description]` (optional) - Brief description of the bug. If omitted, prompts for input.

**What it does:**

- Analyzes codebase to understand relevant components and potential causes
- Uses web search if needed to research similar issues
- Creates detailed bug report with:
  - Clear, descriptive title
  - Steps to reproduce
  - Expected vs actual behavior
  - Environment details
  - Code references and potential causes
  - Impact assessment
- Creates GitHub issue with appropriate labels (bug, priority, area)
- Offers to start a development session

**Examples:**

```
# With description
/project:issue-bug Users getting logged out after 5 minutes

# Prompt for description
/project:issue-bug
```

#### `/project:issue-feature [description]`

Creates a comprehensive GitHub feature request from a simple idea.

**Parameters:**

- `[description]` (optional) - Brief description of the feature. If omitted, prompts for input.

**What it does:**

- Analyzes current codebase architecture and patterns
- Researches similar features and best practices
- Creates detailed feature request with:
  - User story and problem statement
  - Detailed feature description
  - Acceptance criteria
  - Technical approach suggestions
  - Implementation considerations
  - Potential challenges and testing strategy
- Creates GitHub issue with appropriate labels (enhancement, type:enhancement, priority, area)
- Offers to start a development session

**Examples:**

```
# With description
/project:issue-feature Add dark mode toggle

# Prompt for description
/project:issue-feature
```

#### `/project:issue-list [options]`

Lists GitHub issues and allows selection of one to work on.

**Parameters:**

- `--label=<label>` (optional) - Filter by specific label
- `--assignee=<user>` (optional) - Filter by assignee
- `--milestone=<milestone>` (optional) - Filter by milestone

**What it does:**

- Fetches open issues from GitHub repository
- Displays numbered list with issue details:
  - Issue number and title
  - Labels (bug, enhancement, etc.)
  - Assignee and creation date
  - Brief description preview
- Allows selection by number/ID
- Shows full issue details for selected issue
- Offers to start session or create implementation plan

**Examples:**

```
# List all open issues
/project:issue-list

# Filter by bugs
/project:issue-list --label=bug

# Filter by assignee
/project:issue-list --assignee=@me
```

#### `/project:issue-plan <issue-id>`

Creates a comprehensive implementation plan for a selected GitHub issue using ultrathink methodology.

**Parameters:**

- `<issue-id>` (optional) - GitHub issue number. If omitted, prompts for input.

**What it does:**

- Fetches full issue details from GitHub
- Analyzes codebase for relevant components and architecture
- Applies ultrathink analysis to deeply understand problem space
- Creates detailed TDD-focused implementation plan with:
  - Current state analysis
  - Step-by-step phases (Analysis, Test Planning, Implementation, Validation)
  - Files to modify/create
  - Testing strategy with TDD approach
  - Risk assessment and timeline
- Presents plan for user approval
- Offers to start development session after approval

**Examples:**

```
# With issue ID
/project:issue-plan 42

# Prompt for issue ID
/project:issue-plan
```

### Git Workflow Commands

#### `/project:git-branch [name]`

Creates a git branch for current development work with smart naming based on session context.

**Parameters:**

- `[name]` (optional) - Custom branch name. If omitted, suggests name from session context.

**What it does:**

- Analyzes current session for context (issue numbers, session names)
- Suggests appropriate branch name with standard prefixes (feature/, fix/, improve/)
- Creates and switches to new branch
- Sets up remote tracking with push
- Updates session with branch creation

**Examples:**

```
# Smart naming from session context
/project:git-branch

# Custom branch name
/project:git-branch feature/user-profiles
```

#### `/project:git-pr [title]`

Creates a GitHub pull request with AI-generated description based on session context and changes.

**Parameters:**

- `[title]` (optional) - Custom PR title. If omitted, generates from context.

**What it does:**

- Analyzes current session for PR context
- Reviews git changes and commit history
- Generates comprehensive PR description with:
  - Summary of changes and related issues
  - Testing performed and deployment notes
  - Professional PR template formatting
- Creates PR using GitHub CLI
- Updates session with PR reference

**Examples:**

```
# Auto-generated from context
/project:git-pr

# Custom title
/project:git-pr "Add user profile customization"
```

#### `/project:git-review [pr-number]`

Performs comprehensive self-review of pull request using ultrathink methodology.

**Parameters:**

- `[pr-number]` (optional) - GitHub PR number. If omitted, uses current branch's PR.

**What it does:**

- Applies ultrathink analysis to deeply examine all changes
- Guides through systematic review process:
  - Deep code analysis and logic validation
  - Comprehensive functional and integration review
  - Testing analysis and coverage evaluation
  - Documentation and communication review
- Verifies deployment and risk assessment
- Provides detailed merge recommendation with reasoning
- Documents insights in session for future reference

**Examples:**

```
# Review current branch's PR
/project:git-review

# Review specific PR
/project:git-review 42
```

## 🎯 Best Practices for Claude Code

### Command Usage

- These commands work only within Claude Code interactive sessions
- Commands are project-specific and available to all team members
- Arguments are passed directly after the command name

### Session Management

- Sessions help Claude maintain context across conversations
- Review past sessions before starting related work
- Session files serve as documentation for your development process

## 🔧 Customization

### Adapting for Standard Claude Code Setup

If you want to use these with Claude Code's standard directory structure:

1. Copy the `commands` folder to `.claude/commands/` in your project
2. Update paths in command files from `sessions/` to `.claude/sessions/`

### Creating Your Own Commands

- Modify command files to change behavior
- Create additional session-related commands
- Organize commands in subdirectories for namespacing (e.g., `/project:session:feature:start`)
- Create personal versions in `~/.claude/commands/` with `/user:` prefix

## 📚 References

- [Claude Code Slash Commands Documentation](https://docs.anthropic.com/en/docs/claude-code/slash-commands)
- [Claude Code Memory Management](https://docs.anthropic.com/en/docs/claude-code/memory-management)
- [Claude Code Overview](https://docs.anthropic.com/en/docs/claude-code/overview)

## 🎯 Best Practices

### Starting Sessions

- Use descriptive names that indicate the main focus
- Start sessions for significant features or bug fixes
- Define clear goals at the beginning

### During Development

- Update regularly when completing significant tasks
- Document unexpected issues and their solutions
- Track breaking changes or important discoveries
- Note any dependencies added or configuration changes

### Ending Sessions

- Always end sessions with `/project:session-end`
- Review the generated summary for completeness
- Add any missing context before closing

### Knowledge Transfer

- Review relevant past sessions before starting similar work
- Reference session files in commit messages for context
- Use session summaries for standup updates or reports

## 💡 Use Cases

### 1. Feature Development

```
/project:session-start user-authentication
# Implement auth logic
/project:session-update Added middleware and login page
# Fix issues
/project:session-update Resolved Next.js 15 async cookie issue
/project:session-end
```

### 2. Bug Fixing

```
/project:session-start fix-email-bounce-handling
# Investigate issue
/project:session-update Found AWS SNS webhook misconfiguration
# Implement fix
/project:session-update Updated webhook handler and added logging
/project:session-end
```

### 3. Refactoring

```
/project:session-start database-service-refactor
# Plan refactoring
/project:session-update Created new DB service class architecture
# Execute changes
/project:session-update Migrated all queries to new service
/project:session-end
```

### 4. GitHub Issue Workflow

```
# Report a bug
/project:issue-bug Authentication timeouts after login
# Created issue #42

# Plan the fix
/project:issue-plan 42
# Review and approve plan

# Start implementation
/project:session-start fix-auth-timeout-issue-42
# Implement following the plan
/project:session-update Identified root cause in session middleware
/project:session-update Fixed timeout configuration and added tests
/project:session-end
```

### 5. Feature Request Workflow

```
# Request a feature
/project:issue-feature Add user profile customization
# Created issue #43

# Browse existing work
/project:issue-list --label=enhancement

# Plan the feature
/project:issue-plan 43
# Review comprehensive implementation plan

# Start development
/project:session-start user-profile-customization-issue-43
# Follow TDD approach from plan
/project:git-branch
# Creates: feature/issue-43-user-profiles
/project:session-update Wrote tests for profile settings component
/project:session-update Implemented basic profile editing with validation
/project:git-pr
# Creates PR with comprehensive description
/project:git-review
# Ultrathink review before merging
/project:session-end
```

### 6. Complete Development Workflow

```
# Full workflow from issue to deployment
/project:issue-bug Authentication timeouts after login
# Creates issue #44

/project:issue-plan 44
# Ultrathink implementation planning

/project:session-start fix-auth-timeout-issue-44
# Begin development session

/project:git-branch
# Creates: fix/issue-44-auth-timeout

# ... implement following TDD approach ...
/project:session-update Identified root cause in session middleware
/project:session-update Wrote tests for timeout scenarios
/project:session-update Implemented configurable timeout logic

/project:git-pr
# Creates PR with session context and git analysis

/project:git-review
# Comprehensive ultrathink review process

# After review approval
/project:session-end
# Complete session with full documentation
```

## 🤖 Benefits for AI Agents

1. **Context Preservation**: Sessions provide rich context about past work
2. **Decision History**: Understand why certain approaches were taken
3. **Issue Awareness**: Know about problems already encountered and solved
4. **Code Evolution**: Track how the codebase has changed over time
5. **Dependency Tracking**: Awareness of what packages and tools are used

## 🔍 Tips and Tricks

1. **Searchable Sessions**: Use consistent terminology in updates for easy searching
2. **Link Issues**: Reference ticket numbers or GitHub issues in updates
3. **Code Snippets**: Include important code changes in session updates
4. **Screenshots**: Reference screenshot paths for UI changes
5. **Testing Notes**: Document test scenarios and results

## ⚙️ Configuration

### Customizing Commands

Edit the command files in `commands/` to:

- Change session file format
- Add custom sections
- Modify summary generation
- Adjust git tracking details

### Session Storage

- Default: `sessions/`
- Can be changed by updating command files
- Consider version control needs

## 🚨 Troubleshooting

**No active session found**

- Start a new session with `/project:session-start`
- Check `sessions/.current-session` exists

**Session updates not working**

- Ensure a session is active
- Check file permissions in `sessions/`

**Missing git information**

- Verify you're in a git repository
- Check git is properly initialized

## 📚 Examples

### Complete Feature Implementation Session

```markdown
# Development Session - 2025-01-16 13:47 - campaign-editor

## Goals
- [x] Create dedicated campaign editor
- [x] Add markdown support
- [x] Implement auto-save

## Progress
[Multiple detailed updates documenting the implementation]

## Session Summary
Successfully implemented a full-featured campaign editor with markdown support,
live preview, and auto-save functionality. Resolved Next.js 15 compatibility
issues and added proper error handling.
```

## 🤝 Contributing

To improve this system:

1. Enhance command instructions for better AI comprehension
2. Add new commands for specific workflows
3. Improve session file formatting
4. Create utilities for session analysis

## 📄 License

This session management system is open source and available for use in any project.

---

*Remember: Good documentation today saves hours of debugging tomorrow!*