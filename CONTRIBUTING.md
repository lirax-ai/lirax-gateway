# Contributing

The project is in its initial planning phase. Use issues to discuss use cases, initial scope, documentation, and design proposals. Check the [roadmap](docs/roadmap.md) before starting implementation.

English is the primary language for shared documentation, project templates, and maintenance records. Write commit and PR descriptions in English so public contributors can follow the work.

## Reporting problems or proposing improvements

- Describe the problem, use case, and expected outcome.
- For bug reports, include the version, reproduction steps, actual result, and expected result. There is no runnable release yet.
- For feature proposals, explain the need, acceptance criteria, and alternatives you considered.
- Use synthetic examples. Remove secrets and sensitive information from logs, requests, and configuration before sharing them.

## Submitting changes

1. Read the [collaboration rules](AGENTS.md) and relevant documentation. Discuss requirements in an issue before undertaking a substantial implementation.
2. Keep each PR focused on one problem, and explain behavior changes and validation results.
3. Update affected documentation. Record important design tradeoffs using the [decision template](docs/decisions/TEMPLATE.md).
4. Once the technology stack is selected, this guide will include actual development, run, and test commands.

## Local materials

Use `mkdir -p .local` to create a personal workspace for machine-specific paths, network settings, temporary scripts, or notes. Git ignores the entire `.local/` directory. Each maintainer manages it locally; its contents are not committed.

Local instructions for AI assistants can be written in `.local/AGENTS.md`. The collaboration rules require assistants to read this file when it exists. Shared project documentation must be usable independently of any maintainer's local materials.

## Knowledge from discussions

Conclusions needed for maintenance belong in issues, PRs, or repository documentation. Put lasting requirements and design conventions in documents rather than leaving them only in chats.

Rewrite conclusions from non-public discussions in English, with sensitive information removed. Public readers must be able to understand the problem, constraints, rationale, and validation method without access to the original materials.

## License status

The project license has not been selected yet. Once it is selected, the repository will include a `LICENSE` file and updated contribution terms.
