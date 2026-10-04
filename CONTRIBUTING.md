# Contributing

The project is in its initial planning phase. Start with the [current status](docs/status.md), [workflow](docs/workflow.md), and [task records](docs/tasks/README.md). Check the [roadmap](docs/roadmap.md) before starting implementation.

You can work directly with the project directory. A GitHub account, a particular AI tool, and access to past chats are not required. Hosting platforms are optional channels for discussion and review; lasting project knowledge is kept in repository files.

English is the primary language for shared documentation, project templates, and maintenance records. Write commit and PR descriptions in English so public contributors can follow the work.

## Reporting problems or proposing improvements

- Describe the problem, use case, and expected outcome.
- For bug reports, include the version, reproduction steps, actual result, and expected result. There is no runnable release yet.
- For feature proposals, explain the need, acceptance criteria, and alternatives you considered.
- Use synthetic examples. Remove secrets and sensitive information from logs, requests, and configuration before sharing them.

## Submitting changes

1. Read the [collaboration rules](AGENTS.md) and relevant documentation. For substantial work, create or update a local [task record](docs/tasks/TEMPLATE.md) with scope and acceptance criteria before implementation. An issue can supplement that discussion.
2. Keep each change focused on one problem, and record behavior changes and actual validation results in the task or affected documentation. Changes can be shared as files or patches, or reviewed through a PR.
3. Update affected documentation and handoff details. Record important design tradeoffs using the [decision template](docs/decisions/TEMPLATE.md).
4. Once the technology stack is selected, this guide will include actual development, run, and test commands.

Follow the [repository foundations](docs/repository-basics.md) for file handling and text formatting. Git ignore rules do not replace content review.

## Local materials

Use `mkdir -p .local` to create a personal workspace for machine-specific paths, network settings, temporary scripts, or notes. Git ignores the entire `.local/` directory. Each maintainer manages it locally; its contents are not committed.

Local instructions for AI assistants can be written in `.local/AGENTS.md`. The collaboration rules require assistants to read this file when it exists. Shared project documentation must be usable independently of any maintainer's local materials.

## Knowledge from discussions

Keep conclusions needed for maintenance in repository task records, documentation, and design decisions. Issues, PRs, and chats can supplement those files. When external discussions change a requirement or decision, update the local record and identify any unresolved conflict.

Rewrite conclusions from non-public discussions in English, with sensitive information removed. Public readers must be able to understand the problem, constraints, rationale, and validation method without access to the original materials.

## License status

The project license has not been selected yet. Once it is selected, the repository will include a `LICENSE` file and updated contribution terms.
