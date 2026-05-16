Team Workflow Guide – ZBC Knowledge Base Project
Repository Workflow Rules

All team members must follow this workflow when contributing to the project.

Step 1 — Clone the Repository
git clone git@github.com:NdiforChester/ZBC-knowledge-base.git

Move into the project:

cd ZBC-knowledge-base
Step 2 — Pull Latest Changes

Before starting ANY work:

git checkout main
git pull origin main

Purpose:

Gets the latest approved updates
Prevents conflicts
Ensures everyone works on the newest version
Step 3 — Create Your Own Branch

NEVER work directly on main.

Create your own feature branch.

Examples:

git checkout -b docs/docker-fundamentals
git checkout -b docs/linux-networking
git checkout -b docs/kubernetes-basics
Step 4 — Add Your Documentation

Go to your assigned folder under docs/.

Examples:

cd docs/docker
touch docker-fundamentals.md

Add your notes/documentation inside the file.

Step 5 — Save Your Changes
git add .

Commit your work:

git commit -m "docs: add Docker fundamentals notes"

Use clear and professional commit messages.

Step 6 — Push Your Branch
git push origin docs/docker-fundamentals
Step 7 — Open Pull Request (PR)

On GitHub:

Open a Pull Request
Base branch → main
Compare branch → your feature branch

Example:

main ← docs/docker-fundamentals
Step 8 — Review & Approval

Only the Team Lead (Chester) can:

Review PRs
Approve PRs
Merge PRs into main

No team member should merge directly into main.

Pull Request Rejection Rules

A Pull Request (PR) may be REJECTED if:

1. Working Directly on Main

❌ Changes were made directly on main branch.

Every contribution must come from a feature branch.

2. No Pull Before Starting

❌ Team member did not run:

git pull origin main

before starting work.

This can create outdated work and merge conflicts.

3. Wrong Folder Structure

❌ Documentation added in the wrong folder.

Example:

Docker notes outside docs/docker
Linux notes outside docs/linux

4. Poor File Naming

❌ File names are unclear or inconsistent.

Bad example:

notes1.md

Good example:

docker-fundamentals.md

5. Empty or Low-Quality Documentation

❌ Notes are incomplete, copied without explanation, or missing important information.

Documentation must:

Be organized
Be readable
Include explanations/examples where possible

6. No Meaningful Commit Message

❌ Commit message is unclear.

Bad example:

update

Good example:

docs: add Docker fundamentals notes

7. Multiple Unrelated Topics in One PR

❌ One PR contains unrelated changes.

Example:

Docker notes
Linux notes
Kubernetes notes

All mixed in one PR.

Each PR should focus on ONE topic/task.

8. Merge Conflicts Not Resolved

❌ PR contains unresolved merge conflicts.

Team member must:

Pull latest changes
Resolve conflicts locally
Push updated branch

9. Unauthorized File Modifications

❌ Team member edits another contributor’s work without approval.

10. Missing Workflow Steps

❌ Team member skips:

branch creation
commit
push
PR creation

All workflow steps are mandatory.

Team Goal

The purpose of this project is to:

Practice real DevOps collaboration
Learn Git & GitHub workflow
Simulate real-world team contribution process
Build organized technical documentation collaboratively

