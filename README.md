# ZBC Knowledge Base

The ZBC Knowledge Base is a collaborative documentation project built to help new engineers learn the foundations of Linux, AWS, and DevOps practice. It also serves as a team Git and GitHub workflow exercise: every contribution should come through issues, branches, pull requests, review comments, and approved merges.

This repository is not a software application. Its value is in clear technical writing, organized documentation, and evidence that the team practiced professional collaboration.

## Project Scope

The knowledge base covers three major learning areas:

- Linux fundamentals, command line usage, permissions, processes, networking, and Bash scripting.
- AWS cloud concepts, compute, storage, databases, identity, monitoring, and cloud best practices.
- DevOps workflows, Git and GitHub collaboration, Docker, Kubernetes, CI/CD, troubleshooting, and release practices.

Each topic should take a beginner from first principles to practical intermediate understanding. Good documentation should explain what a concept is, why it matters, how it works, common commands or examples, and mistakes to avoid.

## Repository Structure

```text
ZBC-knowledge-base/
|-- README.md
|-- docs/
|   |-- linux/
|   |-- aws/
|   `-- devops/
|-- assets/
`-- team/
```

## Documentation Map

- [Linux Documentation](docs/linux/README.md)
- [AWS Documentation](docs/aws/README.md)
- [DevOps Documentation](docs/devops/README.md)
- [Team Information](team/README.md)
- [Team Workflow Guide](team/workflow-guide.md)

## Contribution Workflow

All contributors must follow the shared GitHub workflow:

1. Create or assign a GitHub Issue before starting work.
2. Create a branch from the latest `main` branch.
3. Use a clear branch name such as `docs/linux-permissions`, `feature/aws-storage-notes`, or `fix/broken-links`.
4. Commit with a professional message such as `docs: add Linux permissions guide`.
5. Push the branch and open a pull request.
6. Request at least one reviewer.
7. Address review comments before merge.
8. Do not push directly to `main`.

## Review Standards

Reviewers should check:

- Content is accurate and useful for beginners.
- Markdown headings, lists, tables, and code blocks are readable.
- Files are placed in the correct directory.
- Links work.
- Commit messages and pull request descriptions are clear.
- No secrets, passwords, or private access keys are committed.

## Learning Outcomes

By completing this project, the team should be able to:

- Work safely in a shared Git repository.
- Use branches and pull requests correctly.
- Review technical documentation respectfully.
- Resolve merge conflicts.
- Recover from accidental mistakes with Git.
- Organize an internal engineering knowledge base.
- Communicate progress through issues and project boards.

## Project Status

This repository is a living knowledge base. New sections, diagrams, examples, and corrections should continue to be added through the same pull request workflow.
