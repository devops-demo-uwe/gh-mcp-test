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

# Standard Feature and Bugfix GitHub Workflow Instructions

## Core Workflow Principles
- ALWAYS follow the complete issue → branch → commits → PR → merge cycle
- ALWAYS use GitHub MCP for ALL operations (both local and remote)
- NEVER use terminal commands for git or gh operations
- ALWAYS maintain clean, traceable development history
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

## 2. Branch Management (GitHub MCP)

### Branch Creation Rules
```
ALWAYS create branches through GitHub MCP:
- Feature branches: "feature/brief-description-max-3-words"
- Bug fix branches: "bugfix/issue-number-brief-description"
- Example: "Create branch 'feature/user-authentication' from main for issue #23"
```

### Branch Naming Convention
- Features: `feature/user-dashboard`, `feature/api-authentication`
- Bug fixes: `bugfix/42-login-validation`, `bugfix/15-memory-leak`
- Hotfixes: `hotfix/critical-security-patch`

## 3. Development Workflow (GitHub MCP)

### Starting New Work
```
Complete workflow command:
"Create issue for [feature/bug description], then create branch [branch-name] from main"

This should:
1. Create properly formatted GitHub issue
2. Create branch linked to the issue
3. Confirm issue number for future commit references
```

### File Modification and Commits
```
When making changes:
1. Modify files in VS Code normally
2. When ready to commit: "Push changes to current branch with commit message: [proper format]"
3. GitHub MCP handles: staging, committing, and pushing in one operation
```

## 4. Commit Message Standards (GitHub MCP)

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
"Create pull request for current branch targeting main branch for issue #[number]"

Auto-populate with:
- Title matching the issue title
- Description linking to the issue
- Proper labels and reviewers
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

## 6. Code Review and Merge Process (GitHub MCP)

### Review Assignment
```
Auto-assign reviewers based on:
- CODEOWNERS file mappings
- Component expertise
- Workload distribution
- At least 1 reviewer required, 2 for critical changes
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
1. Issue Creation:
   "Create feature issue for user dashboard with analytics widgets"

2. Branch Creation:  
   "Create feature branch 'feature/user-dashboard' from main for issue #45"

3. Development Iterations:
   "Push current changes with commit: 'feat(dashboard): add widget framework - addresses #45'"
   "Push current changes with commit: 'feat(dashboard): implement analytics data - addresses #45'"

4. Pull Request:
   "Create pull request for feature/user-dashboard targeting main for issue #45"

5. Review and Merge:
   "Merge pull request #12 after all approvals and checks pass"
```

## 8. Bugfix Development Workflow  

### Complete Bugfix Process
```
1. Bug Issue Creation:
   "Create bug issue for login session timeout occurring after 10 minutes"

2. Branch Creation:
   "Create bugfix branch 'bugfix/67-session-timeout' from main for issue #67"

3. Investigation and Fix:
   "Push current changes with commit: 'fix(auth): extend session timeout to 30 minutes - addresses #67'"

4. Pull Request:
   "Create pull request for bugfix/67-session-timeout targeting main for issue #67"

5. Priority Review and Merge:
   "Request urgent review for bugfix PR #15 due to production impact"
```

## 9. Hotfix Workflow

### Critical Production Issues
```
For production emergencies:
1. "Create hotfix branch 'hotfix/critical-security-patch' from main"
2. "Push fix with commit: 'fix(security): patch XSS vulnerability - addresses #99'"
3. "Create urgent pull request for hotfix branch with immediate review requested"
4. After merge: "Create issue to backport hotfix to development branches"
```

## 10. Quality Gates and Automation

### Pre-Commit Checks
```
Before each commit, GitHub MCP should verify:
- Commit message follows proper format
- Issue number exists and is valid
- No obvious syntax errors in changed files
- Changes align with issue description
```

### Pre-PR Checks  
```
Before creating pull requests:
- All commits properly formatted and linked
- Branch name matches convention
- No merge conflicts with target branch
- Issue requirements are addressed
```

## 11. Error Handling and Recovery

### Common Scenarios
```
Merge Conflicts:
"Resolve merge conflicts in [branch-name] with main and update PR"

Failed CI Checks:
"Investigate failed checks in PR #[number] and push fixes"

Review Feedback:
"Address review comments in PR #[number] with additional commits"
```

### Branch Cleanup
```
After successful merge:
1. Switch back to main branch locally for future work
2. Pull latest changes to update local main branch

⚠️ **Note**: GitHub MCP currently does not support automatic branch deletion.
After merging a PR, notify the user that they can manually delete the feature branch through GitHub UI:
1. Go to repository → Branches tab
2. Find the merged branch
3. Click the delete (trash) icon

Issue will be automatically closed when PR is merged if properly linked.
```

## 12. Workflow Commands Reference

### Daily Development Commands
```
Start new feature:
"Create feature issue and branch for [description]"

Save progress:
"Push changes with commit: '[type](scope): [description] - addresses #[issue]'"

Create PR:
"Create pull request for current branch with issue #[number]"

Handle feedback:
"Push review fixes with commit: 'fix([scope]): address review feedback - addresses #[issue]'"

Complete work:
"Merge PR #[number] after approval"

Post-merge cleanup:
1. Switch to main branch locally
2. Pull latest changes
⚠️ **Manual step**: Delete merged branch through GitHub UI (Branches tab → delete icon)
```