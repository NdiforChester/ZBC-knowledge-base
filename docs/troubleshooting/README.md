# Troubleshooting Guide

This guide helps engineers diagnose and fix the most common issues
encountered when working with Git and GitHub in a team environment.

---

## 1. Accidentally Committed to Main

**Problem:**
You forgot to create a branch and committed directly to main.

**Fix:**
```bash
git checkout -b feature/my-fix
git checkout main
git reset --hard HEAD~1
git push origin main --force
```

---

## 2. Merge Conflict

**Problem:**
Two people edited the same file and Git does not know which version to keep.

**Fix:**
Open the conflicted file and look for these markers:
<<<<<<< HEAD
your version
their version







their-branch







Delete the markers, keep the correct content, then:
```bash
git add .
git commit -m "fix: resolve merge conflict"
git push origin your-branch-name
```

---

## 3. Pushed to the Wrong Branch

**Problem:**
You pushed your changes to the wrong branch by mistake.

**Fix:**
```bash
git log --oneline -3
git checkout correct-branch-name
git cherry-pick <commit-hash>
git push origin correct-branch-name
```

---

## 4. Accidentally Deleted a File

**Problem:**
You deleted a file and need to recover it.

**Fix:**
```bash
git log --oneline --diff-filter=D -- path/to/file.md
git checkout <commit-hash>^ -- path/to/file.md
git add .
git commit -m "fix: restore accidentally deleted file"
git push origin your-branch-name
```

---

## 5. Pull Request Was Rejected

**Problem:**
Your PR was rejected by a reviewer who requested changes.

**Fix:**
1. Read the reviewer comments carefully on GitHub
2. Make the requested changes locally
3. Then:
```bash
git add .
git commit -m "fix: address PR review feedback"
git push origin your-branch-name
```
Your PR updates automatically — no need to open a new one.

---

## 6. Forgot to Pull Before Starting Work

**Problem:**
You worked on outdated code because you forgot to pull the latest changes.

**Fix:**
```bash
git stash
git pull origin main
git stash pop
```
If conflicts appear after stash pop, resolve them the same way as section 2.

---

## 7. Emergency Hotfix Needed

**Problem:**
A critical issue is found mid-project and needs an immediate fix.

**Fix:**
```bash
git checkout main
git pull origin main
git checkout -b hotfix/describe-the-issue
# make your fix
git add .
git commit -m "fix: describe what you fixed"
git push origin hotfix/describe-the-issue
```
Then open a PR immediately and flag it as urgent for your Team Lead.

