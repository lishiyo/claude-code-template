---
allowed-tools: Bash(git *:*), Bash(cp:*), Bash(mkdir:*), Read, Write, LS
argument-hint: <remote-branch-name> [worktree-name]
description: Create a git worktree from a remote branch with .env files copied from current directory
---

## Context
- Current directory: !`pwd`
- Current git remote: !`git remote get-url origin 2>/dev/null || echo "No git remote found"`
- Available remote branches: !`git ls-remote --heads origin 2>/dev/null | sed 's/.*refs\/heads\///' | head -10 || echo "Could not list remote branches"`
- Env files in current directory: !`ls -la .env* 2>/dev/null || echo "No .env files found"`

## Your task

Create a git worktree for the remote branch specified in the arguments. The arguments should be:
1. First argument (required): The remote branch name to checkout
2. Second argument (optional): Custom name for the worktree directory (defaults to branch name)

Steps to complete:
1. Parse the arguments to get the branch name and optional worktree name
2. Determine the repository URL from the current directory's git remote
3. Create a worktree directory (use ../worktrees/<branch-name> or ../worktrees/<custom-name> as the path)
4. Add the worktree and fetch the remote branch: `git worktree add -b <local-branch> <path> origin/<remote-branch>`
5. Copy all .env* files from the current directory to the new worktree
6. List what was set up and provide the cd command to navigate to the new worktree

Arguments provided: $ARGUMENTS

Important notes:
- If the worktree already exists, remove it first with `git worktree remove`
- Make sure to fetch the latest remote branches before creating the worktree
- Preserve the exact contents and permissions of .env files when copying
- If no .env files exist, just note that but continue with worktree creation