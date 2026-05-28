# Git and GitHub Guide

Git is a version control system. GitHub is a cloud platform for hosting Git repositories and collaborating through issues, branches, pull requests, reviews, and project boards.

Together, Git and GitHub allow engineering teams to work on the same project without overwriting each other and while keeping a clear history of decisions.

## 1. Git vs GitHub

| Git | GitHub |
| --- | --- |
| Installed locally | Accessed through web and Git remotes |
| Tracks file history | Hosts repositories online |
| Works offline | Enables collaboration online |
| Creates commits and branches | Provides pull requests, reviews, issues, and project boards |

## 2. Core Git Terms

| Term | Meaning |
| --- | --- |
| Repository | A project tracked by Git |
| Commit | A saved snapshot of changes |
| Branch | A separate line of work |
| Merge | Combining one branch into another |
| Remote | Online copy of a repository |
| Clone | Download a repository |
| Pull | Fetch and integrate remote changes |
| Push | Upload local commits |

## 3. Core GitHub Terms

| Term | Meaning |
| --- | --- |
| Issue | A task, bug, question, or improvement |
| Pull request | A request to merge branch changes |
| Review | Feedback on a pull request |
| Project board | Visual task tracking |
| Label | Category marker for issues and PRs |
| Milestone | Group of work tied to a goal or release |

## 4. Basic Workflow

Clone the repository:

```bash
git clone https://github.com/example/ZBC-knowledge-base.git
cd ZBC-knowledge-base
```

Update your local `main`:

```bash
git checkout main
git pull origin main
```

Create a branch:

```bash
git checkout -b docs/linux-permissions
```

Make changes, then inspect them:

```bash
git status
git diff
```

Commit:

```bash
git add docs/linux/linux-notes.md
git commit -m "docs: add Linux permissions guide"
```

Push:

```bash
git push origin docs/linux-permissions
```

Open a pull request on GitHub and request review.

## 5. Branch Naming

Use names that describe the work:

```text
docs/linux-permissions
docs/aws-storage-notes
feature/project-board-setup
fix/broken-markdown-links
hotfix/readme-error
```

Avoid vague names:

```text
update
my-work
new-file
changes
```

## 6. Pull Request Expectations

A good pull request includes:

- Clear title.
- Summary of changes.
- Related issue number.
- Screenshots or examples when useful.
- Specific review request.

Example:

```text
Title: docs: add Docker Compose guide

Summary:
- Added Docker Compose explanation.
- Added sample compose file.
- Added common commands and mistakes.

Closes #12
```

## 7. Review Etiquette

Reviewers should:

- Be specific and respectful.
- Comment on the content, not the person.
- Explain why a change is needed.
- Approve only when standards are met.

Contributors should:

- Read comments carefully.
- Ask questions when feedback is unclear.
- Push follow-up commits to the same branch.
- Avoid opening a new PR for the same review corrections.

## 8. Commit Message Standard

Use short, meaningful commit messages:

```text
docs: add AWS IAM overview
fix: correct Kubernetes service typo
refactor: reorganize Docker notes
chore: add PR template
```

Common prefixes:

- `docs`: documentation changes.
- `fix`: corrections.
- `feat`: new capability or section.
- `refactor`: reorganizing without changing meaning.
- `chore`: maintenance work.

## 9. Intermediate Practices

- Pull from `main` before starting work.
- Keep PRs focused on one topic.
- Avoid editing unrelated files.
- Resolve conflicts locally and test the result.
- Use issues and project boards to make work visible.
- Never commit credentials or private keys.

## 10. Practice Tasks

1. Create an issue for a missing topic.
2. Create a branch for the issue.
3. Add or improve a documentation file.
4. Open a PR.
5. Request a review.
6. Address reviewer feedback.
7. Merge only after approval.
