# G-0001: Define the initial use case and scope

Status: In progress
Updated: 2026-10-04
Owner and editing scopes: Unassigned; current work records problem exploration and public documentation.

## Problem and objective

Understand enterprise agent governance needs and the roles of developers, system operators, and security teams before selecting an initial release or implementation. The intended direction is identity, permissions, and accountability, with MCP integration.

## Scope and acceptance criteria

The current stage is open exploration. Record expressed needs, rationale, hypotheses, and conflicts without selecting a technology stack or implementing features. Product acceptance criteria and an initial release feature set are deferred.

Future scope definition may address core use cases, exclusions, implementation constraints, and verification. Those are future discussion topics, not mandatory outcomes of the present exploration. Public records must remain understandable independently of other workspaces and previous chats.

## Progress, evidence, and decisions

On 2026-10-04, the project initiator described external and internal agent developers' governance needs, including user delegation, system/interface/data/action permissions, temporary human authorization, audit, and connectors. Enterprise deployment between agents and business systems is the intended direction. Detailed needs, rationale, research references, and limitations are maintained in [Governance exploration](../governance-exploration.md).

These directions do not establish an initial release scope or implemented capability. Direct enterprise adoption and developer recommendations are possible adoption paths, not validated outcomes.

Further input describes employee-operated tools, shared enterprise services, and third-party digital workers with staged human intervention. The exploration document records these patterns and distinguishes intervention from an assumed permission approval. Identity granularity, execution location, and delegation across stages remain unresolved. No additional external research was performed for this update.

Further workflow examples distinguish handoff, a human decision before progression, and assistance when an agent is uncertain. These examples clarify intervention semantics without assigning the gateway ownership of business workflows or treating every intervention as a permission grant. No additional external research or product validation was performed.

The initiator clarified the boundary between a provider's internal workflow and enterprise resource access, and explicitly requested employee permission management for agents they own and for those agents' users. The related move toward employee autonomy remains a governance hypothesis. Grantable authority and the roles of employees, resource owners, and security teams remain open. No additional external research was performed for this update.

Further exploration confirms that multiple employee-authority arrangements can coexist and treats configuration complexity as a product opportunity. Official Microsoft identity/governance references and limited OpenConnector policy code inspection are recorded in the exploration document. AI assistance remains a candidate approach; the specific Microsoft AI configuration feature was not confirmed. Existing connector controls provide a comparison baseline, not evidence of complete governance or missing capabilities.

## Validation results

Read primary sources on delegation, detailed authorization, MCP security, and excessive agency. The exploration document records source access and research limits. Checked document consistency, relative links, section anchors, and whitespace in the local changes. No gateway functionality, identity binding, backend compatibility, or temporary approval behavior has been validated. This task remains in progress.

## Handoff and next step

The latest documentation update passed whitespace, relative-link, and section-anchor checks, including new Markdown files. Product references were reviewed as documentation and limited source code only; no AI permission planning or runtime enforcement behavior was tested.

Explore how employees express and understand permission plans across different authority arrangements, and how those plans relate to resource owners and enterprise constraints. Continue examining agent identity granularity, user delegation, trusted task constraints, and temporary authorization. Investigate configuration assistance and compare concrete governance controls when relevant. Do not prematurely convert all expressed needs into an initial release checklist.

On 2026-10-04, the initiator authorized committing and pushing this documentation update. The task remains in progress; publication does not establish implemented capabilities or an initial release scope. Future edits remain local by default unless separately authorized.

## Related records

- [Current status](../status.md)
- [Governance exploration](../governance-exploration.md)
- [Roadmap](../roadmap.md)
- [Workflow](../workflow.md)
