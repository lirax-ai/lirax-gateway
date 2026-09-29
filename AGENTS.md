# Instructions for contributors and agents

- Use English for the primary README, documentation, work items, code reviews, and maintenance discussions. Keep protocol names and code identifiers in their original form; optional translations must not replace the English source of truth.
- During the project's early stage, AI assistants may edit files for review but must not run `git commit`, `git push`, or publish to a hosting platform without explicit approval from the user directing the task. Report uncommitted changes at the end of the task; revise this rule when the project workflow matures.
- Start with `README.md`, `WORK.md`, and `CONTRIBUTING.md`, then read the relevant code and decision records. Keep the work list and durable documentation current as the task progresses; do not rely on chat history or a hosting platform for missing context.
- Treat this public repository as the complete context needed to maintain Lirax Gateway. Do not depend on access to private planning material.
- Preserve the intent of existing code and documents. When changing behavior or a public contract, update the relevant documentation in the same change.
- Put actionable open questions in `WORK.md` or a linked repository document. Use platform issues for discussion when available. Record decisions with lasting architectural or operational impact in `docs/decisions/` using the format described there.
- If a discussion began in private, write a new public account of the problem and its technical constraints. Sanitize examples and identifiers; preserve the reasoning and unresolved tradeoffs.
- Check public diffs for credentials, personal or customer data, private URLs, and internal identifiers before publishing.
- Do not invent an API, language, framework, or deployment requirement before the project scope is defined.
