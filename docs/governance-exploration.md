# Identity and permission governance for agents

Updated: 2026-10-04.
Status: Open exploration. This document records the intended problem direction and governance needs, not an implemented feature list or an initial release commitment. No technology stack or product acceptance criteria have been selected.
Tracked in [G-0001](tasks/G-0001-define-first-release.md).

## Purpose and intended participants

The project aims to help enterprises adopt AI with confidence by approaching agent governance through identity, permissions, and accountability. An agent can provide useful results while still making mistakes or acting on manipulated instructions. Organizations need an enforceable authorization boundary and a way to understand who acted through which agent.

External agent developers need to address customers' concerns about internal system access and sensitive information exposure. Internal developers need to agree on access with system operators and security teams, which may belong to different departments. System owners need to preserve their business rules, while security teams need a consistent management surface across integrations.

The intended deployment is inside the enterprise, between agents and business systems. Enterprises may seek the gateway directly, or developers may recommend it to address their customers' governance concerns. These adoption paths are hypotheses, not validated market outcomes.

## Agent usage patterns under discussion

| Pattern | Described usage | Identity and delegation questions |
| --- | --- | --- |
| Employee-operated general-purpose tools | Employees use readily available tools to perform work | How are the application, running instance, and actual user distinguished? |
| Shared enterprise-developed services | One agent service connects to business systems and serves many users | How does each call retain its represented user and authorized task? |
| Third-party digital workers | A person initiates work; the agent performs stages of a task before a person intervenes | Does intervention mean reviewing, approving, changing the task, taking over, or authorizing continuation? |

These are usage patterns to explore, not measured adoption rankings or compatibility commitments. An application's provider, asset owner, task initiator, represented user, approver, and person taking over may be different. The patterns do not settle a single identity granularity. Third-party agents' execution locations and integration boundaries remain open.

Human intervention can have different business meanings. Illustrative recruitment workflows include an agent handing scheduling to a person after initial screening, a person deciding progression after an automated interview, and an agent requesting assistance when uncertain. These can be understood as handoff, a decision gate, and assistance. None automatically implies that additional permissions are granted.

Explore how workflow state and authorization relate without assuming the gateway owns the entire workflow or approval interface. Agent-reported confidence can signal a need for assistance, but it cannot alone establish an authorization boundary; a mistaken action may occur without a report of uncertainty.

A third-party workflow may operate mostly within the provider's own system. Enterprise integration becomes relevant when it calls an internal resource, such as recording information in an HR system. This does not imply enterprise security teams define the provider's internal workflow. Responsibilities at the enterprise resource boundary still need to be established.

## Governance needs expressed so far

| Dimension | Intended need | Synthetic example |
| --- | --- | --- |
| Agent identity | Identify the agent involved and associate it with relevant people | Relate a sales assistant's calls to the person using it |
| Systems and interfaces | Control which systems and interfaces an agent may call | A sales assistant may query CRM records but not invoke an administrative interface |
| User delegation | Preserve the represented user's permissions when an agent acts on their behalf | A regional representative can read their region's summary; a director may read a wider summary |
| Cross-application authorization | Support mechanisms such as ID-JAG / XAA to coordinate delegated access with enterprise identity systems | Obtain authorization for a target application through an established identity-provider trust relationship; supported roles and versions remain open |
| Data | Express table, column, and row restrictions where applicable | Permit selected fields and records without granting unrestricted database access |
| Task and action | Constrain actions according to an authorized task | Preparing an analysis does not automatically authorize modifying records or submitting a transaction |
| Human approval | Keep human-approved access temporary and appropriately bounded | Approval for a particular operation does not grant permanent unrestricted access |
| Audit | Relate an operation to its initiating user and executing agent | Preserve enough context to investigate who used which agent to perform an operation |
| Connectors | Expose non-MCP systems to agents through MCP and connect existing MCP servers | Adapt a business API while retaining its relevant authorization semantics |
| Management | Provide a consistent enterprise governance surface across systems | Allow governance to be managed across integrations maintained by different teams |
| Employee permission management | Let employees set permissions for agents they own and for those agents' users | An employee configures an agent's allowed operations and access for its users; the employee's authority to grant that access remains to be defined |

These needs have been expressed as project directions. Their priority, detailed behavior, compatibility scope, and inclusion in an initial release remain open.

## Employee participation in permission management

Employee permission management is an explicitly expressed project need. A related hypothesis is that agent owners and users will increasingly configure permissions because they understand their agents' tasks and centrally administering every agent may become difficult. This is a hypothesis about governance and adoption, not an established market trend.

A shared control surface can support distributed permission configuration; it need not imply that security administrators configure every agent individually. The division of authority among employees, resource owners, and security teams remains open.

Being associated with an agent provides management and investigation context. It does not alone establish legal responsibility or authority to grant other people access to enterprise resources. Permission to use a resource, delegate its use to an agent, and grant another user access are distinct questions.

An employee's grantable authority may come from their own delegable permissions, a resource owner's delegated management scope, enterprise policy, or another arrangement. Multiple arrangements can coexist; explore their context and interactions without requiring one universal model or escalation rule.

Permission configuration complexity is a product problem to explore. Employees may understand a business task without knowing every API permission or data constraint. Templates, grouping, inheritance, and AI assistance are possible ways to reduce that burden. AI could help explain or propose a permission plan, but a suggestion, a person's confirmation, and effective runtime authorization are distinct. No AI-assisted capability or implementation has been selected or validated.

## Standards preference

Prefer standards-based approaches where feasible. This is a confirmed design preference, not a commitment to implement every agent-related specification. Further research should distinguish published specifications, working drafts, and vendor-specific implementations, identifying their versions, roles, and interoperability evidence. Where an extension is needed, document the gap and its interoperability consequences before selecting an approach.

Related work spans distinct organizations. The [IETF OAuth working group](https://datatracker.ietf.org/wg/oauth/documents/) develops specifications including the ID-JAG draft. The OpenID Foundation's [AIIM community group](https://openid.net/call-for-participation-demonstrate-mcp-based-ai-agent-security-with-open-identity-standards-2/) has announced MCP identity interoperability work. Its [AuthZEN specification index](https://openid.net/wg/authzen/specifications/) lists Authorization API 1.0 as Final and access-request/approval and COAZ / MCP bindings as Working Group Drafts. These are research references, not selected dependencies or evidence that this project has participated in testing.

[Authorization API 1.0](https://openid.net/specs/authorization-api-1_0.html) provides an interface between authorization decision and enforcement components. The [Access Request and Approval Profile draft](https://openid.github.io/authzen/authzen-access-request-approval-profile-1_0.html) addresses requestable denials and re-evaluation after approval; COAZ references address mapping operations into authorization requests. Explore their relationship to the expressed needs without assuming they establish all task, data, temporary-approval, or workflow semantics. Standard interfaces can support interoperability while resource-specific rules still require explicit meaning and enforcement.

## Cross-application authorization under discussion

Supporting mechanisms such as ID-JAG and Cross App Access (XAA) is an expressed integration direction. The [Identity Assertion JWT Authorization Grant draft -04](https://www.ietf.org/archive/id/draft-ietf-oauth-identity-assertion-authz-grant-04.html) describes obtaining an ID-JAG through OAuth Token Exchange and redeeming it at a resource authorization server through a JWT authorization grant. [Okta's XAA concept](https://developer.okta.com/docs/concepts/xaa/) describes the cross-application flow built on that mechanism. These are related concepts, not two independent protocol switches. ID-JAG remains an Internet-Draft; no compatibility commitment or implementation has been selected.

The requesting application acts for a user, the identity provider brokers access under configured trust and policy, and the resource authorization server decides what resource access token to issue under local policy. This can extend existing federated identity relationships into delegated API access. Existing SSO alone does not establish that every participant implements the required flow. User context, requesting-client identity, and an individual agent instance must also be distinguished.

Protocol support does not establish application-specific row, column, task, action, or human-approval enforcement. Explore how enterprise connection rules, resource permissions, and employee-configured constraints interact. Distributed employee participation and enterprise control of trusted connections may coexist; their combination is still under exploration.

Further work should establish the gateway's roles in each call path, trust-domain boundaries, supported draft versions, identity mapping, and the behavior of cached access after permissions change. No authorization server or identity-provider implementation has been chosen or tested.

## Know Your Agent as a governance perspective

Absorbing Know Your Agent (KYA) ideas is an expressed research direction. Current primary sources use the term differently: [Sumsub](https://sumsub.com/blog/know-your-agent/) describes risk-based identity, authentication, authorization, and accountability; [1Kosmos](https://www.1kosmos.com/resources/blog/know-your-agent-kya-securing-autonomous-ai) emphasizes checks at execution time; [Deepchecks](https://deepchecks.com/know-your-agent-strengths-weaknesses-report/) uses KYA for behavioral testing and evaluation. These are the publishers' perspectives, not a single agreed specification or independently validated product claims.

For this exploration, KYA provides questions about an agent's provenance, identity, relevant people, delegated authority, lifecycle, and observed behavior. Distinguish an application's provider and asset owner from the principal represented in a particular call. Registration, an agent's declared purpose, granted permissions, an attempted operation, and its outcome provide different evidence. Explore how that evidence stays relevant when agents, owners, or permissions change. This is a research lens, not an accepted identity model or a new release checklist.

An identified agent can still behave incorrectly. Owner association does not establish legal liability, grantable authority, or authorization for a particular request. Verification and intervention should reflect the environment and risk; payment-oriented liveness checks, wallets, or biometric schemes are not assumed requirements for enterprise employees. Behavioral evaluation may provide additional evidence but does not replace runtime authorization. A gateway's evidence is limited to the paths and outcomes it can observe.

[KYAPay](https://kyapay.org/) is a concrete protocol initiative related to agent identity and commerce. As checked on 2026-10-04, [KYAPay Token -02](https://datatracker.ietf.org/doc/draft-skyfire-oauth-kyapay-token/) and [KYAPay Token Exchange -01](https://datatracker.ietf.org/doc/draft-skyfire-oauth-kyapay-token-exchange/) are active **individual Internet-Drafts**, without IETF endorsement or formal standing. The token draft distinguishes principal, platform, and agent information and discusses minimal disclosure and bearer versus proof-of-possession semantics. Signed identity claims alone do not prove that the intended agent is presenting a bearer token. The exchange draft describes obtaining an OAuth resource access token, including an MCP use case, through RFC 7523's JWT bearer grant; it explicitly differs from RFC 8693's separate subject/actor token exchange. KYA, KYAPay, and ID-JAG / XAA must not be treated as interchangeable mechanisms.

These sources were read on 2026-10-04. No KYA protocol, verification method, payment capability, evaluation platform, or compatibility target has been selected or tested. Follow the existing standards preference while continuing to establish which governance questions each mechanism actually addresses.

## Initial product references

The following primary sources were read on 2026-10-04. They inform exploration and are not compatibility commitments or a comprehensive comparison.

- Microsoft's [Agent 365 identity documentation](https://learn.microsoft.com/en-us/microsoft-agent-365/developer/identity) distinguishes an agent identity blueprint, an individual agent identity, and an optional agent user account. [Entra governance documentation](https://learn.microsoft.com/en-us/entra/id-governance/agent-id-governance-overview) describes owners and sponsors requesting access packages for agents, with configured approval and expiration. [Permission inheritance documentation](https://learn.microsoft.com/en-us/entra/agent-id/concept-inheritable-permissions) distinguishes declarations, consent, and inherited grants. These references show that shared templates, individual identities, and distributed human participation can coexist with enterprise controls; they do not settle this project's identity model or business-level authorization. The specific Agent 365 capability for AI-assisted permission planning was not confirmed in this limited review.
- OOMOL's [OpenConnector](https://github.com/oomol-lab/open-connector) already describes credential isolation, runtime tokens, Action policies, and redacted logs. Limited static reading of its [Action policy code](https://github.com/oomol-lab/open-connector/blob/8d01e5468773e64a79c187c39f8ace4751efc879/src/core/action-policy.ts) found layered deployment, runtime, and token checks, plus connection restrictions. Its [runtime reference](https://github.com/oomol-lab/open-connector/blob/8d01e5468773e64a79c187c39f8ace4751efc879/docs/runtime-api.md) describes those controls. This establishes a concrete comparison baseline; it does not validate enforcement across all call paths. Further comparison should examine delegation, data and task constraints, management roles, configuration effort, and audit evidence rather than assume connector projects lack authorization controls.
- LiteLLM's [MCP ID-JAG Auth (Okta)](https://docs.litellm.ai/docs/mcp_id_jag) documents `oauth2_id_jag`: exchange a user identity assertion for an ID-JAG, redeem it for a resource access token, and use that token for upstream MCP calls. Limited reading of its [configuration](https://github.com/BerriAI/litellm/blob/a2bf67a03707e474be41e07806ee4fd9791ca7cd/litellm/types/mcp_server/mcp_server_manager.py), [SSO assertion capture](https://github.com/BerriAI/litellm/blob/a2bf67a03707e474be41e07806ee4fd9791ca7cd/litellm/proxy/management_endpoints/sso/id_jag_assertion_capture.py), and MCP manager found corresponding paths. The documentation and code identify prerequisites and limitations, including assertion capture and different subject sources for tool discovery and invocation. This confirms documented support and related code, not deployed-version coverage, complete XAA conformance, or tested interoperability. LiteLLM should be compared across its actual MCP and identity capabilities as well as model routing.

No referenced product was deployed or tested. Limited documentation and code inspection cannot establish the absence of capabilities elsewhere in those products.

## Why explore a gateway

Implementing governance separately in every agent and every MCP server can require coordination across teams and inconsistent permission models. Some systems do not expose MCP interfaces at all. A gateway could provide a common place to manage access, integrate systems, and correlate audit evidence.

This is the rationale for exploring a gateway, not a claim that a gateway alone provides complete enforcement. System-side authorization and cooperation from connectors may still be necessary. A resource registered in the gateway remains accessible through other paths unless those paths are independently restricted.

## Research considerations and unresolved questions

The following are research findings and questions, not accepted architecture decisions:

- **Identity and delegation:** the user and the executing agent are distinct participants. [RFC 8693](https://www.rfc-editor.org/rfc/rfc8693.html) distinguishes delegation from impersonation and defines actor information. How are user identity, agent identity, and delegated authority established and verified? A unique bearer credential alone does not prove that its original holder is making a request.
- **Task constraints:** agent-provided intent cannot itself authorize an action. [RFC 9396](https://www.rfc-editor.org/rfc/rfc9396.html) provides a way to express detailed resources and actions; it does not establish the truth of an agent's task description. Who establishes an authorized task, and how is it related to actual calls?
- **Temporary approval:** approval needs a defined subject, agent, operation, resource, and validity boundary. Expiration, cancellation, repeated execution, and changes to approved arguments require further exploration. A human approval interaction alone does not establish these guarantees.
- **Human intervention:** handoff, a decision gate, and assistance may affect delegated authority differently. Who defines and enforces intervention conditions? Which actions remain authorized after confirmation or handoff, and what happens if a different person intervenes? A business confirmation may satisfy a prerequisite without expanding permissions.
- **MCP authorization:** the [2025-11-25 specification](https://modelcontextprotocol.io/specification/2025-11-25/basic/authorization) defines transport-level authorization for HTTP. The [security guidance](https://modelcontextprotocol.io/docs/2025-11-25/tutorials/security/security_best_practices) prohibits token passthrough and cautions against treating token scopes as sufficient without server-side authorization. Authentication does not by itself implement application-specific data and action rules; STDIO has a different credential model.
- **Enforcement:** [OWASP Excessive Agency guidance](https://genai.owasp.org/llmrisk/llm062025-excessive-agency/) calls for least privilege, user-context execution, human approval for high-impact operations, and downstream authorization independent of the LLM's decision. Which checks belong in the gateway, connectors, and business systems? How are conflicting rules and bypass paths handled?
- **Audit and accountability:** identifying an actor is useful evidence, but it does not automatically establish organizational or legal responsibility. Which evidence is necessary, and how can it be retained without exposing secrets or unnecessary sensitive data?
- **Employee authority:** what may employees configure for their agents and their agents' users? How are these settings related to resource-side permissions and enterprise constraints, and what happens when ownership or employment changes?

System access control can constrain tool-mediated exposure and actions. It does not by itself cover every model-provider, local file, credential-sharing, or other data-egress path. Claims about coverage must be tied to actual deployment and enforcement boundaries.

## Evidence and validation limits

The linked official standards and security guidance were read on 2026-10-04. They inform the questions above; no agent framework, identity provider, or implementation approach has been selected. No gateway capability, backend compatibility, identity binding, or approval enforcement has been tested.

General web searches were limited: Google returned JavaScript retry pages rather than usable results; revised queries did not resolve this. Bing returned broad results unrelated to the detailed questions, and a subsequent DuckDuckGo HTML search required a CAPTCHA. The research therefore relied on direct access to primary sources and is not a comprehensive survey of implementations or competing products.

A subsequent identity and configuration review obtained usable DuckDuckGo results for `Microsoft Agent 365 AI permissions blueprint`; other queries still encountered CAPTCHAs. Microsoft Learn search API results for Agent 365 / Security Copilot permissions and Entra permission recommendations did not establish a specific AI configuration feature. Direct Microsoft Learn and GitHub source access succeeded; a Microsoft Agent 365 GA blog returned HTTP 403 and was not used as evidence.

The ID-JAG / XAA review used Google queries for `LiteLLM ID-JAG XAA`, `ID-JAG XAA Okta specification`, and `site:docs.litellm.ai "XAA"`; these returned retry pages. Bing returned unrelated or broad results and DuckDuckGo required a CAPTCHA. Official sitemaps, GitHub's tree API, and IETF references provided source locations. Initial guessed IETF and Okta paths returned 404; the corrected official paths were read successfully. No end-to-end token exchange or release-version compatibility was tested.

The KYA review initially encountered Google retry pages, irrelevant Bing responses, and DuckDuckGo CAPTCHAs. Brave queries for `"Know Your Agent" KYA` and `"KYA" "agent" "identity" "Okta"` provided useful leads. Sumsub, 1Kosmos, Deepchecks, KYAPay, and two IETF Datatracker documents were read directly. Persona, Trulioo, and Entrust pages returned HTTP 403 access restrictions and were not used as verified evidence. This was a limited review of terminology and protocol status, not a comprehensive vendor, regulatory, or interoperability assessment.

Continue exploring these needs before choosing an initial release scope, implementation, or acceptance criteria. The project has no runnable release.
