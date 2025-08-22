# Contributing Guide

Welcome to the agentic-layer project! This guide will help you contribute effectively to our codebase.

----

## Table of Contents

- [Commit Message Conventions](#commit-message-conventions)
- [Pull Request Workflow](#pull-request-workflow)
- [Issue Tracking Integration](#issue-tracking-integration)
- [Developer Notes](#developer-notes)

----

## Commit Message Conventions

We follow the [Conventional Commits](https://www.conventionalcommits.org/en/v1.0.0/) standard for commit messages.
This helps us maintain a clean history and generate automated release notes in the future.

### Format

```
<type>: <description>
```

If you have an issue, include the issue key:

```
<type>: <issue-key> <description>
```

### Types

We primarily use these commit types:

- `feat`: A new feature
- `fix`: A bug fix that does not change the logical behavior of the code
- `chore`: Maintenance tasks (dependencies, tooling, etc.)

Other conventional commit types are also allowed (docs, style, refactor, test, etc.), if above types do not fit.

### Examples

```bash
feat: Add user authentication system
fix: Resolve database connection timeout
chore: Update dependencies to latest versions
feat: PAAL-1234 Add new feature
fix: PAAL-567 Fix login validation bug
```

### Important Notes

- We do not use scopes or breaking change indicators
- `feat` and `fix` commits may be used for automated release notes in the future
- Always include the Jira issue key when working on a ticket

## Pull Request Workflow

We use a rebase-based workflow to maintain a clean, linear commit history.

### Before Creating a Pull Request

1. Rebase your branch against the latest main branch:
   ```bash
   git checkout main
   git pull --rebase origin main
   git checkout your-feature-branch
   git rebase main
   ```

2. Ensure all commits follow our commit message conventions

Note: When fellow developers have potentially already checked out your branch (like when they have started a review),
prefer to use merge instead of rebase to avoid rewriting history.
You can rebase your branch later, after all developers have finished their reviews, right before merging the pull
request.

### Pull Request Process

1. Create a pull request from your feature branch to main
2. Ensure all CI checks pass
3. Request review from team members
4. Address any feedback with additional commits
5. Once approved, the pull request will be rebased and merged
   - As an internal developer, you merge the pull request yourself
   - As an external contributor, a team member will merge your pull request

### Git Configuration

Configure your Git to use rebase for pulls:

```bash
git config pull.rebase true
```

This ensures that `git pull` uses rebase instead of merge by default.

## Issue Tracking Integration

We support both Jira and GitHub issues for tracking work. Choose the appropriate format based on your issue type.

### Jira Issues

If you're working on a Jira ticket:

1. Include the issue key in all relevant commit messages
2. Use the format: `PAAL-XXXX` where XXXX is the ticket number
3. Example: `feat: PAAL-1234 Add user dashboard component`

### GitHub Issues

If you're working on a GitHub issue:

1. Include the issue number in all relevant commit messages
2. Use the format: `#XXX` where XXX is the issue number
3. Example: `feat: #123 Add user dashboard component`
4. You can also use GitHub's closing keywords to automatically close issues:
   - `fix: #456 Resolve login validation bug` (closes issue #456)
   - `feat: #789 Add search functionality` (closes issue #789)

### Format Examples

```bash
# Jira issues
feat: PAAL-1234 Add new feature
fix: PAAL-567 Fix login validation bug

# GitHub issues  
feat: #123 Add new feature
fix: #456 Fix login validation bug
```

This helps with traceability and project management across both platforms.

## Developer Notes

- Install pre-commit hooks for the respective repository  (mandatory for all repos with pre-commit configs)
  ```bash
  pre-commit install
     ```
- Always ensure your code is well-tested before submitting a pull request
