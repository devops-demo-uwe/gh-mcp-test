# Copilot Instructions

## Project Overview
This is a demo repository for testing GitHub Copilot functionality.

## Code Style Guidelines
- Use clear, descriptive variable and function names
- Follow conventional commit message format
- Keep functions small and focused
- Add comments for complex logic

## Preferred Patterns
- Use modern JavaScript/TypeScript syntax when applicable
- Prefer explicit over implicit code
- Include error handling where appropriate

# Complete Git + GitHub Workflow Instructions with Full MCP Integration

## MCP Server Configuration Required

### Git MCP Server (CyanHeads - Comprehensive)
```json
{
  "mcp": {
    "servers": {
      "git": {
        "command": "npx",
        "args": ["@cyanheads/git-mcp-server"],
        "env": {
          "MCP_LOG_LEVEL": "info"
        }
      },
      "github": {
        "type": "http",
        "url": "https://api.githubcopilot.com/mcp/",
        "headers": {
          "Authorization": "Bearer ${input:github_mcp_pat}"
        }
      }
    }
  }
}
```

## Core Workflow Principles
- ALWAYS follow the complete issue → branch → commits → PR → merge cycle
- ALWAYS use Git MCP for local operations (pull, fetch, commit, branch, merge, status, diff)
- ALWAYS use GitHub MCP for remote operations (issues, PRs, repository management)
- NEVER use terminal commands for git or gh operations
- ALWAYS maintain clean, traceable development history with proper remote sync
- ALWAYS link all work to GitHub issues for proper tracking

## 1. Issue Management (GitHub MCP)

### Before Starting Any Work
```
ALWAYS create or verify a GitHub issue exists before coding:
- Feature work: "Create feature issue for [description]"
- Bug fixes: "Create bug issue for [problem description]"
- Issue must include: clear title, description, acceptance criteria, labels
```

### Issue Creation Standards
```
Feature Issues:
- Title: "[Feature]: Clear descriptive title"
- Labels: "feature", priority level, component tags
- Body: User story, acceptance criteria, technical approach

Bug Issues:
- Title: "[Bug]: Clear problem description" 
- Labels: "bug", severity level, component tags
- Body: Steps to reproduce, expected vs actual behavior, environment details
```

## 2. Repository Sync and Branch Management (Git MCP + GitHub MCP)

### Starting New Work with Proper Sync
```
Complete workflow with sync:
"Pull latest changes from origin main, create issue for [feature/bug description], then create branch [issue-number-branch-name] from updated main"

This should:
1. Use git_pull to sync main branch with remote changes
2. Create properly formatted GitHub issue (GitHub MCP)
3. Create branch with issue number prefix from up-to-date main (git_checkout with create)
4. Confirm issue number for future commit references
```

### Branch Creation and Management (Git MCP)
```
Branch Operations:
- "Create and checkout branch 'feature/23-user-auth' from main"
- "Switch to branch [branch-name]"
- "List all branches including remote branches"
- "Merge main into current branch to sync with latest changes"
```

### Branch Naming Convention
- Features: `feature/45-user-dashboard`, `feature/23-api-authentication`
- Bug fixes: `bugfix/42-login-validation`, `bugfix/15-memory-leak`
- Hotfixes: `hotfix/99-critical-security-patch` (with associated issue number)

## 3. Development Workflow (Git MCP)

### File Modification and Commits
```
When making changes:
1. Check status: "Show git status to see what files have changed"
2. Review changes: "Show diff of modified files"
3. Stage selectively: "Stage files [file1] [file2] for commit"
4. Commit with message: "Commit staged changes with message: [proper format]"
5. Push when ready: "Push current branch to origin"
```

### Keeping Branch Updated
```
Regular sync operations:
- "Fetch latest changes from origin"
- "Pull latest changes into main branch"
- "Merge main into current feature branch"
- "Check if current branch is behind origin"
```

## 4. Commit Message Standards (Git MCP)

### Required Commit Message Format
```
type(scope): brief description - addresses #issue-number

Examples:
- "feat(auth): add OAuth2 login integration - addresses #23" 
- "fix(api): resolve user session timeout bug - addresses #42"
- "refactor(db): optimize query performance - addresses #18"
- "docs(readme): update installation instructions - addresses #7"
```

### Commit Types
- `feat:` - New feature implementation
- `fix:` - Bug fixes  
- `refactor:` - Code restructuring without functional changes
- `docs:` - Documentation updates
- `test:` - Test additions or modifications
- `chore:` - Build, dependency, or tooling changes
- `perf:` - Performance improvements
- `style:` - Code formatting/style fixes

### Commit Guidelines
- **Atomic commits**: Each commit represents one logical change
- **Issue linking**: Every commit MUST reference the GitHub issue number
- **Descriptive messages**: Explain WHY the change was made, not just WHAT
- **Present tense**: "add feature" not "added feature"

## 5. Pull Request Workflow (GitHub MCP)

### Creating Pull Requests
```
When development is complete:
1. "Push current branch to origin" (Git MCP)
2. "Create pull request for current branch targeting main branch for issue #[number]" (GitHub MCP)

Auto-populate with:
- Title format: "#[issue-number]: [Issue title]" 
- Description linking to the issue
- Proper labels and reviewers
```

### Before Creating PR
```
Pre-PR checklist (Git MCP):
- "Check git status to ensure all changes are committed"
- "Fetch and check if main has new changes"
- "Merge main into current branch if needed"
- "Push current branch to origin"
```

### PR Template Requirements
```
## Description
Brief overview of changes and approach taken

## Related Issues  
- Closes #[issue-number]
- Related to #[other-issue] (if applicable)

## Changes Made
- [ ] Specific change 1
- [ ] Specific change 2  
- [ ] Tests added/updated
- [ ] Documentation updated

## Testing Performed
- [ ] Unit tests pass
- [ ] Integration tests pass
- [ ] Manual testing completed
- [ ] Cross-browser testing (if applicable)

## Breaking Changes
- [ ] No breaking changes
- [ ] Breaking changes documented below
```

## 6. Code Review and Merge Process (GitHub MCP + Git MCP)

### Review Assignment (GitHub MCP)
```
Auto-assign reviewers based on:
- CODEOWNERS file mappings
- Component expertise
- Workload distribution
- At least 1 reviewer required, 2 for critical changes
```

### Handling Review Feedback
```
After receiving feedback:
1. "Switch to branch [branch-name]" (Git MCP)
2. Make requested changes in VS Code
3. "Stage and commit changes with message: 'fix([scope]): address review feedback - addresses #[issue]'" (Git MCP)
4. "Push current branch to origin" (Git MCP)
```

### Merge Requirements
```
Before merging:
- [ ] All required reviews approved
- [ ] All CI/CD checks passing
- [ ] No merge conflicts
- [ ] Branch is up-to-date with target branch
- [ ] Issue requirements fully met
```

## 7. Feature Development Workflow

### Complete Feature Process
```
1. Sync and Issue Creation:
   "Pull latest changes from main, create feature issue for user dashboard with analytics widgets"

2. Branch Creation:  
   "Create and checkout feature branch 'feature/45-user-dashboard' from main for issue #45"

3. Development with Regular Sync:
   "Show git status and stage authentication files"
   "Commit with message: 'feat(dashboard): add widget framework - addresses #45'"
   "Fetch origin and merge main if there are updates"
   "Commit with message: 'feat(dashboard): implement analytics data - addresses #45'"

4. Push and PR:
   "Push current branch to origin"
   "Create pull request for feature/45-user-dashboard targeting main for issue #45"

5. Review and Merge:
   "Merge pull request #12 after all approvals and checks pass"
```

## 8. Bugfix Development Workflow  

### Complete Bugfix Process
```
1. Sync and Bug Issue Creation:
   "Pull latest changes from main, create bug issue for login session timeout occurring after 10 minutes"

2. Branch Creation:
   "Create and checkout bugfix branch 'bugfix/67-session-timeout' from main for issue #67"

3. Investigation and Fix:
   "Show git status and diff to understand current changes"
   "Stage modified auth files and commit: 'fix(auth): extend session timeout to 30 minutes - addresses #67'"

4. Push and PR:
   "Push current branch to origin"
   "Create pull request for bugfix/67-session-timeout targeting main for issue #67"

5. Priority Review and Merge:
   "Request urgent review for bugfix PR #15 due to production impact"
```

## 9. Hotfix Workflow

### Critical Production Issues
```
For production emergencies:
1. "Pull latest changes from main"
2. "Create and checkout hotfix branch 'hotfix/99-critical-security-patch' from main"
3. "Stage security files and commit: 'fix(security): patch XSS vulnerability - addresses #99'"
4. "Push hotfix branch to origin"
5. "Create urgent pull request for hotfix branch with immediate review requested"
6. After merge: "Pull main and create issue to backport hotfix to development branches"
```

## 10. Advanced Git Operations (Git MCP)

### Handling Conflicts and Complex Scenarios
```
Merge Conflicts:
1. "Fetch latest changes from origin"
2. "Merge main into current branch"
3. Resolve conflicts in VS Code
4. "Stage resolved files and commit merge"

Branch Management:
- "Show all branches including remote branches"
- "Delete local branch [branch-name]" (after merge)
- "Prune remote tracking branches"

History and Analysis:
- "Show commit log for current branch"
- "Show detailed commit history with diffs"
- "Show git blame for [filename]"
```

### Stashing and Temporary Changes
```
When switching contexts:
- "Stash current changes with message: 'WIP: authentication work'"
- "Switch to branch [other-branch]"
- "List all stashes"
- "Apply stash and continue work"
```

## 11. Quality Gates and Automation

### Pre-Commit Checks (Git MCP)
```
Before each commit:
- "Show git status to review changes"
- "Show diff of staged changes"
- Verify commit message follows proper format
- Ensure issue number exists and is valid
- Check no obvious syntax errors in changed files
```

### Pre-PR Checks (Git MCP + GitHub MCP)
```
Before creating pull requests:
- "Fetch origin and check if main has updates"
- "Merge main into current branch if needed"
- "Show commit log to verify all commits properly formatted"
- "Push current branch to origin"
- Check branch name matches convention
- Verify issue requirements are addressed
```

## 12. Error Handling and Recovery

### Common Scenarios
```
Sync Issues:
"Fetch origin and show status of current branch vs remote"

Failed Merges:
"Show merge conflicts and help resolve them step by step"

Lost Changes:
"Show reflog to find lost commits"
"Show stash list to recover temporary changes"

Remote Issues:
"Show remote repositories and their URLs"
"Fetch all remotes and show tracking status"
```

### Branch Cleanup (Git MCP)
```
After successful PR merge:
1. "Switch to main branch"
2. "Pull latest changes from origin main"
3. "Delete local feature branch [branch-name]"
4. "Prune remote tracking branches"

✅ **Full cleanup capability**: Git MCP can handle complete branch lifecycle
```

## 13. Workflow Commands Reference

### Daily Development Commands
```
Start new work:
"Pull main, create issue and feature branch for [description]"

Check status:
"Show git status and any uncommitted changes"

Save progress:
"Stage [files] and commit: '[type](scope): [description] - addresses #[issue]'"

Sync with team:
"Fetch origin, merge main into current branch if needed"

Create PR:
"Push current branch and create pull request for issue #[number]"

Handle feedback:
"Stage changes and commit: 'fix([scope]): address review feedback - addresses #[issue]'"

Complete work:
"Merge PR #[number], switch to main, pull latest, delete feature branch"
```

### Advanced Operations
```
Branch management:
"Show all branches and their tracking status"
"Create branch [name] from [source-branch]"
"Delete merged branch [name]"

History analysis:
"Show commit history for [branch/file]"
"Show detailed diff between [branch1] and [branch2]"
"Show who last modified lines in [file]"

Conflict resolution:
"Show merge conflicts and guide me through resolution"
"Stage resolved files and complete merge"
```

## 14. Integration Benefits

### Git MCP + GitHub MCP Advantages
- **Complete workflow coverage**: From local Git to GitHub operations
- **Natural language interface**: No need to remember Git commands
- **Proper synchronization**: Full fetch/pull/push capabilities
- **Team collaboration**: Handle merge conflicts and branch updates
- **Quality gates**: Built-in checks before commits and PRs
- **Error recovery**: Comprehensive stash, reflog, and conflict resolution

### Best Practices
- **Always sync before starting work**: Pull main before creating branches
- **Regular updates**: Fetch and merge main into feature branches
- **Clean commits**: Use staging area for atomic, well-described commits  
- **Proper linking**: Every commit references GitHub issue
- **Safe merging**: Check for conflicts before creating PRs


# Code Generation Guidelines

## Default Behavior
- **ALWAYS start with the absolute minimum viable implementation**
- Generate ONLY what is explicitly requested
- Do not add error handling, logging, or validation unless specifically asked
- Do not add "helpful" additional methods or properties
- Do not implement edge cases unless mentioned
- Stop at basic structure when asked for "scaffolding" or "boilerplate"

## Implementation Levels
When I say "basic structure" or "skeleton" or "scaffold":
- Create empty methods with appropriate signatures
- Add minimal property declarations
- Include only required imports
- NO implementation details
- NO example usage
- NO additional features

When I say "minimal implementation":
- Add the simplest possible working code
- Use placeholder values where appropriate
- Avoid libraries and dependencies unless specified
- No optimization or best practices unless asked

## Explicit Escalation Required
Only add these when EXPLICITLY requested:
- Error handling and validation
- Logging and monitoring
- Configuration and environment handling
- Additional helper methods
- Code comments and documentation
- Type safety beyond basic types
- Performance optimizations