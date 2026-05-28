# Team Workflow Guide

All team members must follow this workflow when contributing to the ZBC Knowledge Base.

## 1. Start With an Issue

Every task should begin as a GitHub Issue.

The issue should include:

- Clear title.
- Short description.
- Assigned contributor.
- Label such as `docs`, `fix`, `review`, or `hotfix`.
- Project board status.

## 2. Clone the Repository

```bash
git clone git@github.com:NdiforChester/ZBC-knowledge-base.git
cd ZBC-knowledge-base
```

## 3. Pull the Latest Main Branch

Before starting work:

```bash
git checkout main
git pull origin main
```

This keeps your branch current and reduces conflicts.

## 4. Create a Feature Branch

Never work directly on `main`.

Examples:

```bash
git checkout -b docs/linux-permissions
git checkout -b docs/aws-compute-notes
git checkout -b docs/devops-kubernetes-basics
git checkout -b fix/broken-readme-link
```

## 5. Add or Update Documentation

Use the approved structure:

```text
docs/
|-- linux/
|-- aws/
`-- devops/
```

Put each topic in the correct directory.

Examples:

- Linux permissions: `docs/linux/linux-notes.md`
- AWS storage: `docs/aws/aws-storage-services.md`
- Docker: `docs/devops/docker-fundamentals.md`
- Kubernetes: `docs/devops/kubernetes-basics.md`

## 6. Commit Changes

Inspect your work:

```bash
git status
git diff
```

Stage and commit:

```bash
git add docs/devops/docker-fundamentals.md
git commit -m "docs: improve Docker fundamentals guide"
```

Use meaningful commit messages.

Good examples:

```text
docs: add Linux permissions guide
docs: improve AWS storage notes
fix: correct broken markdown link
refactor: reorganize DevOps docs
```

## 7. Push Your Branch

```bash
git push origin docs/devops-kubernetes-basics
```

## 8. Open a Pull Request

On GitHub:

1. Open a pull request.
2. Set base branch to `main`.
3. Set compare branch to your feature branch.
4. Add a title and summary.
5. Link the issue.
6. Request at least one reviewer.

## 9. Review and Approval

Every pull request needs at least one reviewer before merge.

Reviewers should check:

- Correct folder placement.
- Clear writing.
- Accurate examples.
- Working links.
- Professional formatting.
- No committed secrets.

## 10. Pull Request Rejection Rules

A PR can be rejected when:

- Work was done directly on `main`.
- The contributor did not start from the latest `main`.
- Files are in the wrong directory.
- File names are unclear.
- Documentation is incomplete or copied without explanation.
- Commit messages are vague.
- The PR mixes unrelated topics.
- Merge conflicts are unresolved.
- A contributor edits another person's section heavily without communication.
- Required workflow steps were skipped.

## 11. Merge Conflict Practice

When conflicts happen:

1. Communicate with the other contributor.
2. Pull or merge the latest target branch.
3. Open conflicted files.
4. Remove conflict markers.
5. Keep the correct final content.
6. Commit the resolution.
7. Push the branch again.

## 12. Team Goal

The purpose of this project is to:

- Practice real DevOps collaboration.
- Learn Git and GitHub workflow.
- Simulate team contribution in a shared repository.
- Build organized technical documentation collaboratively.
- Learn how to recover from mistakes safely.
