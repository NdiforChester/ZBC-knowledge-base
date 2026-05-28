# Troubleshooting Guide

This guide helps engineers diagnose and fix common Git and GitHub problems in a shared repository. The goal is not only to memorize commands, but to understand what happened before changing history.

## 1. You Committed to the Wrong Branch

Check recent commits:

```bash
git log --oneline -5
```

Create the correct branch at the current commit:

```bash
git checkout -b docs/correct-topic
```

Push the correct branch:

```bash
git push origin docs/correct-topic
```

Then return to the branch that should not contain the commit and ask the team lead before rewriting shared history.

## 2. Merge Conflict

A merge conflict happens when Git cannot automatically combine changes.

Open the conflicted file and look for conflict marker lines similar to this:

```text
[start marker with HEAD]
your version
[separator marker]
their version
[end marker with branch name]
```

Fix the file by keeping the correct final content and removing all conflict markers.

Then run:

```bash
git add path/to/file.md
git commit -m "fix: resolve merge conflict"
git push origin your-branch-name
```

## 3. Pull Request Rejected

A rejected PR is part of normal team review.

Steps:

1. Read reviewer comments carefully.
2. Make changes on the same branch.
3. Commit the corrections.
4. Push the branch again.

```bash
git add .
git commit -m "fix: address PR review feedback"
git push origin your-branch-name
```

The existing PR updates automatically.

## 4. Forgot to Pull Before Starting

Save your local work temporarily:

```bash
git stash
git checkout main
git pull origin main
git checkout your-branch-name
git merge main
git stash pop
```

If conflicts appear, resolve them as described in the merge conflict section.

## 5. Accidentally Deleted a File

If the deletion is not committed:

```bash
git restore path/to/file.md
```

If the deletion was committed, find the commit before deletion:

```bash
git log --oneline -- path/to/file.md
```

Restore from a previous commit:

```bash
git checkout <commit-hash>^ -- path/to/file.md
git add path/to/file.md
git commit -m "fix: restore deleted file"
```

## 6. Pushed to the Wrong Branch

Find the commit:

```bash
git log --oneline -5
```

Move it to the correct branch:

```bash
git checkout correct-branch-name
git cherry-pick <commit-hash>
git push origin correct-branch-name
```

Do not delete commits from a shared branch without discussing it with the team.

## 7. Emergency Hotfix

Create a hotfix branch from the latest `main`:

```bash
git checkout main
git pull origin main
git checkout -b hotfix/fix-broken-link
```

Make the fix:

```bash
git add .
git commit -m "fix: correct broken README link"
git push origin hotfix/fix-broken-link
```

Open a PR immediately, mark it urgent, and request review.

## 8. Useful Diagnostic Commands

```bash
git status
git branch
git log --oneline --graph --decorate -10
git diff
git diff --staged
git remote -v
```

## 9. Troubleshooting Mindset

- Stop and inspect before running destructive commands.
- Read the error message.
- Ask which branch you are on.
- Check whether changes are committed, staged, or unstaged.
- Communicate with teammates before rewriting shared history.
- Prefer a small, reviewed fix over a rushed command that loses work.
