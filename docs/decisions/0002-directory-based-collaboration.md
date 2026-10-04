# 0002: Keep collaboration context in repository files

Date: 2026-10-04
Status: Accepted

## Problem and constraints

The project will use AI extensively alongside human contributors. Either must be able to continue work from the project directory. Requiring a hosting account, a particular AI tool, past chats, or non-public access would make handoffs fragile.

## Decision

Keep durable working context in ordinary repository files:

- `AGENTS.md` defines maintenance conventions.
- `docs/status.md` provides the current phase and entry points.
- `docs/tasks/` records objectives, scope, acceptance criteria, progress, validation, and next steps.
- Requirements and interface documentation define behavior as the project develops.
- `docs/decisions/` preserves important design rationale.

Hosting platforms and chats supplement these files. Synchronize lasting conclusions back into repository records. Machine-specific materials remain in the ignored `.local/` directory.

## Rationale and alternatives

Platform-only task tracking makes context unavailable when the platform cannot be accessed. Chat-only handoffs require recovering a specific conversation. Tool-specific memory makes the project depend on one assistant. Plain files can be read, edited, reviewed, and transferred with the project by people and different AI tools.

## Consequences

Contributors must keep task and handoff records current, and resolve or document conflicts with external discussions. Use small records and links to avoid maintaining duplicate sources of progress.

This provides local access to existing project knowledge. It does not promise offline dependency installation, fresh external research, or service validation. No runnable implementation or technology stack exists yet.

## Validation

Read a file-only copy of the public directory without GitHub, Git metadata, private materials, chat history, or local machine configuration. Confirm that a new contributor can identify the phase, relevant task, scope, acceptance criteria, known limitations, and next step.
