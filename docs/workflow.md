# Working with people and AI

The project directory should let a person or AI assistant understand the current phase, task, rationale, and validation method without reconstructing chats or logging in to a hosting platform. This public workspace is sufficient for public maintenance.

## Start work

1. Read `AGENTS.md` and `.local/AGENTS.md` if the latter exists.
2. Read [current status](status.md), the [task index](tasks/README.md), and the relevant task record. Read only the research and decisions needed for the task; the entire history is not required for every session.
3. Confirm the objective and current stage. During open exploration, distinguish vision, expressed needs, hypotheses, and conflicts; defer the initial feature set and product acceptance criteria. Define scope and acceptance criteria before implementation. Record missing input explicitly instead of treating assumptions as confirmed requirements.
4. Inspect existing work. When Git is available, use `git status` and `git diff`. With a file-only copy, inspect the files and preserve copies before editing; Git metadata is not required to read or organize project knowledge.

## Record and execute

Use a [task record](tasks/TEMPLATE.md) for substantial research, requirements work, or changes across files. Small corrections can update the relevant document directly.

Task records hold scope and execution progress. Requirements and interface documentation describe intended behavior. Decision records explain important accepted tradeoffs. Link these records rather than maintaining several full copies of the same information. The roadmap provides milestone-level direction.

People can describe use cases, expected outcomes, and constraints without writing code or opening an issue. Turn those descriptions into verifiable requirements and identify questions that still need an answer.

AI assistants may help with research, implementation, documentation, and review. Their output uses the same acceptance criteria and evidence standards as human work. Record observable validation results and limitations; an assertion that an AI reviewed the work is not evidence that it passes. No particular model, tool, or chat transcript is required for a handoff.

If several contributors work concurrently, record ownership and editing scopes in the task. Avoid overlapping edits and leave a clear state before handing off unfinished work. Mark a task complete only when its acceptance criteria are satisfied and validation is recorded.

## Optional hosting workflows

Issues and PRs can gather feedback, support review, and distribute changes. Capture lasting requirements, rationale, and validation conclusions in repository files. When platform discussions change a record, update it; explicitly identify conflicts that remain unresolved.

Changes can also be reviewed as files or patches. A task's relative path identifies the work independently of an issue number or PR URL. Machine-specific notes remain in `.local/`; shared context must not depend on them.

## Validate and hand off

Validate against the task's acceptance criteria. Documentation changes require content, link, and consistency checks. Implementations should use the actual commands in the development guide once it exists. No build, run, or code-test commands are defined yet because the technology stack has not been selected.

Before ending a work stage, update completed work, actual checks and results, unresolved questions, and an actionable next step in the task. Update the status entry point when the phase or active tasks change. A new contributor should be able to continue from those files alone.

During early research, keep edits and validation local by default. Commit, push, or publish only within the explicit authorization for the current task.

## Network and runtime requirements

Record conclusions, source summaries, and decision rationale locally so existing work can be understood from the directory. New research, dependency installation, or external service validation may require network access. Report access limits and continue work that can be done locally. Runtime and dependency requirements will be documented when the technology stack is selected.
