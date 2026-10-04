# Current status

Updated: 2026-10-04.

## Project phase

Early research and open exploration. The intended direction is enterprise agent governance through identity, permissions, and accountability, with MCP integration. Intended participants and expressed governance needs are recorded in [Governance exploration](governance-exploration.md). Initial release scope, technology stack, and license remain undecided. There is no runnable gateway release.

## Confirmed working conventions

- Shared documentation and maintenance records use English.
- People and AI assistants use the same task records, acceptance criteria, and evidence standards.
- Repository files preserve the context needed for a handoff. GitHub is an optional collaboration channel.
- Machine-specific materials belong in the Git-ignored `.local/` directory.
- During this early research phase, edits and validation remain local unless the user explicitly requests a commit or push.

## Active task and next step

[G-0001: Define the initial use case and scope](tasks/G-0001-define-first-release.md) is in progress. Explore agent identity, user delegation, trusted task boundaries, temporary approval, and governance across systems. Current exploration also considers employee permission management across multiple authority arrangements and ways to simplify configuration. Initial Microsoft and OpenConnector references provide context, with explicit validation limits. Expressed needs are not an initial release commitment; scope and acceptance criteria will be discussed later.

On 2026-10-04, the initiator authorized committing and pushing the exploration and navigation updates. This publishes research documentation, not an implemented release; Git history and remote branch state establish the actual publication result.

After that push, exploration added ID-JAG / XAA as an expressed integration direction and reviewed LiteLLM's documented support. Draft versions, gateway roles, and interoperability remain open.

A standards-based approach where feasible is now a confirmed preference. Related IETF and OpenID Foundation work is being reviewed with explicit maturity and validation limits; no implementation has been selected.

Know Your Agent (KYA) is now an expressed research direction. The exploration distinguishes identity/authorization perspectives, behavioral evaluation, and KYAPay's individual drafts, and examines identity, delegation, lifecycle, and behavioral evidence. No single KYA definition or implementation is assumed.

The initiator subsequently authorized committing and pushing these additions and the search-rule update prioritizing Chinese search engines for information about China. They are included in this documentation publication; Git history and remote branch state establish its result. Future work remains local by default.

## Handoff entry points

- [Workflow](workflow.md)
- [Task index](tasks/README.md)
- [Roadmap](roadmap.md)
- [Collaboration decision](decisions/0002-directory-based-collaboration.md)

This file provides navigation and a phase summary. Task records hold detailed progress. File presence does not establish whether a change has been committed or published.
