# Maintenance rules for people and AI assistants

## Getting started

- Read `.local/AGENTS.md` first if it exists. This file is specific to the current machine and is not distributed with the repository.
- Read `README.md`, `CONTRIBUTING.md`, `docs/README.md`, and the design records relevant to the task.
- The project is defining its requirements. Do not assume a language, framework, protocol, deployment model, or unimplemented feature.
- Follow the network, permission, and data handling rules supplied by the user and runtime environment. Do not make personal configuration a project prerequisite.
- Check existing changes, preserve the user's work, and avoid destructive Git operations.

## Language

- Use English for shared documentation, project templates, code comments, user-facing text, and maintenance records, including commit and PR descriptions.
- Keep project names, paths, commands, code identifiers, and necessary source quotations unchanged.
- Rewrite conclusions from non-public discussions in English after removing sensitive information. Public contributors must be able to understand them independently.

## Local workspace

- `.local/` holds personal paths, network settings, local scripts, and other machine-specific materials. Git ignores the entire directory.
- Local instructions can be written in `.local/AGENTS.md`. Other maintainers do not need to create or share the same configuration.
- Do not force-add, commit, publish, or copy the directory's contents into shared documentation.
- Put knowledge needed by the team into regular documentation, with personal environment details removed.

## Maintainable changes

- Keep changes focused. Define expected behavior and acceptance criteria before implementation.
- Update documentation when requirements, interfaces, configuration, deployment, or architecture change. Record important tradeoffs in `docs/decisions/`.
- Explain the problem, constraints, rationale, consequences, and validation method. Inaccessible discussions or materials cannot replace an explanation.
- Add new documents to the index. Distinguish completed work, plans, assumptions, and unverified conclusions.
- Run checks relevant to implemented features or bug fixes. Report actual results and anything that could not be verified.
- Tests should check observable behavior. For documentation-only changes, check links, consistency, and the diff.
- Do not invent run commands, test results, performance figures, or compatibility promises.

## Search and research

- Use Google first. Report connection failures explicitly, including the stage of failure and any observable cause.
- Empty responses, parsing failures, CAPTCHAs, rate limits, and access restrictions do not mean that relevant information does not exist. Inspect response status and content, then retry with revised search terms.
- If Google repeatedly returns empty results, try Bing. If Bing also produces no usable results, try other search engines and record why you switched.
- Distinguish information not found in this search, tool or network limitations, and absence confirmed by a source. Empty search results do not prove absence.
- Prefer official documentation, source code, and other primary sources. Treat search snippets as leads.
- When citing research conclusions, record public sources, dates, search coverage, limitations, and anything still unverified.

## Public materials

- All commits must be suitable for publication. Use synthetic examples; do not commit credentials, personal information, internal addresses, or real user data.
- When preparing conclusions from non-public materials, retain publishable technical rationale and limitations, and remove sensitive context and private links.
- Do not copy raw chat transcripts or entire internal research reports.

## Delivery

Explain what changed, why, how it was verified, and any outstanding issues. Follow the current task's authorization for commits and publication.

During this early research phase, keep edits and validation local by default. Commit or push only when the user explicitly requests it. A request to commit does not authorize a push.
