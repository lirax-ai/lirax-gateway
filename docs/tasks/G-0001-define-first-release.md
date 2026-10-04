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

Further input explicitly requests cross-application authorization mechanisms such as ID-JAG / XAA. The exploration now records the relationship between these concepts, the active IETF draft, and LiteLLM's documented `oauth2_id_jag` support with related source paths and limitations. Protocol roles, versions, and compatibility remain open; no runtime integration was tested. This addition was initially prepared locally after the earlier push.

The initiator further confirmed a preference for standards-based approaches where feasible. Official IETF and OpenID Foundation sources were reviewed to distinguish standards work, published specifications, working drafts, and interoperability initiatives. AuthZEN references are candidates for further research, not selected implementations. No conformance or interoperability test was performed.

Further input requests absorbing Know Your Agent (KYA) ideas. Primary publisher sources and KYAPay's individual token and exchange drafts were read on 2026-10-04. The exploration distinguishes terminology, governance questions, behavioral evaluation, and protocol maturity. This is a research direction, not an agreed KYA implementation or initial feature scope. No verification method or protocol interoperability was tested.

The initiator requested prioritizing Chinese search engines when researching information about China, and subsequently authorized committing and pushing the current documentation changes. The maintenance rules and research/navigation updates are included in this publication; actual commits and remote state establish its result.

## Validation results

Before the current publication, documentation whitespace, final-newline, duplicate-heading, local-link, and section-anchor checks passed. Public content was reviewed and checked for private-context and credential markers. No runnable gateway or protocol integration was tested.

Read primary sources on delegation, detailed authorization, MCP security, and excessive agency. The exploration document records source access and research limits. Checked document consistency, relative links, section anchors, and whitespace in the local changes. No gateway functionality, identity binding, backend compatibility, or temporary approval behavior has been validated. This task remains in progress.

## Handoff and next step

At the KYA review stage, the addition and existing local research changes passed checks for whitespace, final newlines, duplicate headings, and local links/anchors across nine Markdown files. Public content was reviewed for private context and machine-specific details. No product capability, identity binding, or interoperability was tested. The additions were local at that stage and are now included in the authorized publication.

Continue applying the KYA perspective to existing shared-agent scenarios: distinguish registration/discovery evidence, authority to configure access, and identity/delegation information verifiable at invocation. Revisit specific KYA sources if supplied; keep verification methods and protocol choices open.

At the earlier ID-JAG / XAA and standards-preference review stage, the documentation additions passed whitespace, local-link, section-anchor, and duplicate-heading checks. No protocol conformance, deployed-version compatibility, or interoperability testing was performed.

The latest documentation update passed whitespace, relative-link, and section-anchor checks, including new Markdown files. Product references were reviewed as documentation and limited source code only; no AI permission planning or runtime enforcement behavior was tested.

Explore how employees express and understand permission plans across different authority arrangements, and how those plans relate to resource owners and enterprise constraints. Continue examining agent identity granularity, user delegation, trusted task constraints, and temporary authorization. Investigate configuration assistance and compare concrete governance controls when relevant. Do not prematurely convert all expressed needs into an initial release checklist.

Continue examining cross-application authorization roles and how gateway, identity-provider, resource-side, and employee-configured rules interact. Supported versions and interoperability require future verification.

On 2026-10-04, the initiator authorized the earlier documentation push and later authorized publication of the additional research and search-rule updates. The task remains in progress; publication does not establish implemented capabilities or an initial release scope. Future edits remain local by default unless separately authorized.

## Related records

- [Current status](../status.md)
- [Governance exploration](../governance-exploration.md)
- [Roadmap](../roadmap.md)
- [Workflow](../workflow.md)
