Perform a comprehensive self-review of the current pull request using ultrathink methodology before merging.

Usage: `/project:git-review [pr-number]` or `/project:git-review` (uses current branch's PR)

The command should:
1. Identify the current PR (from current branch or specified number)
2. Apply ultrathink analysis to deeply examine all changes
3. Display PR details and file changes with critical analysis
4. Guide through systematic self-review process with deep thinking
5. Check for common issues, edge cases, and subtle problems
6. Verify testing and deployment status thoroughly
7. Provide detailed merge recommendation with reasoning

## Ultrathink Self-Review Process:

### Deep Code Analysis
- **Diff Analysis**: Examine every changed line with critical thinking
- **Logic Deep Dive**: Trace through complex logic paths and state changes
- **Assumption Validation**: Question assumptions made during implementation
- **Side Effect Analysis**: Consider unintended consequences of changes
- **Code Standards**: Check formatting, naming, patterns, and maintainability
- **Performance Impact**: Analyze algorithmic complexity and resource usage
- **Security Implications**: Deep examination of security vulnerabilities and attack vectors

### Ultrathink Functional Review  
- **Requirements Alignment**: Verify all acceptance criteria truly met, not just superficially
- **Edge Case Exploration**: Think through boundary conditions, null values, empty states
- **Error Scenarios**: Consider what happens when things go wrong
- **Integration Impact**: Deep analysis of how changes ripple through the system
- **User Experience**: Think about actual user interaction and potential confusion
- **Backwards Compatibility**: Analyze breaking changes and migration paths
- **Future Extensibility**: Consider how changes affect future development

### Comprehensive Testing Analysis
- **Test Coverage Gaps**: Identify untested code paths and scenarios
- **Test Quality**: Evaluate if tests actually validate the right behaviors
- **Manual Testing Depth**: Verify comprehensive manual testing was performed
- **Regression Risk**: Analyze potential for breaking existing functionality
- **Performance Testing**: Consider if performance testing is needed
- **Integration Testing**: Evaluate need for end-to-end testing

### Documentation & Communication Review
- **Code Readability**: Ensure complex code has clear explanations
- **API Documentation**: Verify interface changes are properly documented
- **README Accuracy**: Check if setup/usage docs reflect reality
- **Commit Messages**: Review if commit history tells a clear story
- **PR Description**: Ensure PR thoroughly explains the "why" not just "what"

## Ultrathink Review Process:

1. **Context Deep Dive**
   - Analyze PR title, description, and linked issues
   - Review implementation against original plan/requirements
   - Understand the problem space and solution approach
   - Examine commit history for implementation decisions

2. **Change Impact Analysis**
   - Critical examination of all file modifications
   - Trace data flow and control flow changes
   - Identify potential ripple effects throughout codebase
   - Analyze new functions/components for correctness and design
   - Review deleted code for dependency implications

3. **Quality Deep Think**
   - Think through edge cases not covered in tests
   - Consider performance implications under load
   - Analyze security vulnerabilities and attack vectors
   - Evaluate code maintainability and readability
   - Check for anti-patterns or technical debt introduction

4. **Deployment & Risk Assessment**
   - Preview deployment testing and validation
   - Risk analysis of production deployment
   - Rollback strategy consideration
   - Performance impact under real-world conditions
   - User experience impact evaluation

5. **Comprehensive Recommendation**
   - Detailed analysis of readiness to merge
   - Specific, actionable items if changes needed
   - Risk assessment and mitigation strategies
   - Merge strategy with reasoning
   - Post-merge monitoring recommendations

## Examples:

```
# Review current branch's PR
/project:git-review

# Review specific PR
/project:git-review 42

# After making changes to address review feedback
/project:git-review --recheck
```

## Ultrathink Integration Features:

- Documents comprehensive analysis in session notes
- Updates issue status with detailed review outcomes
- Tracks review depth and quality in session history
- Provides evidence-based merge recommendation
- Identifies lessons learned for future development

After ultrathink review completion:
1. Update session with detailed review analysis and insights
2. Document any architectural insights or patterns discovered
3. Log specific action items with priority and reasoning
4. Update issue with review results and closure criteria
5. Suggest merge command with confidence level if approved
6. Record any technical debt or future improvement opportunities identified 