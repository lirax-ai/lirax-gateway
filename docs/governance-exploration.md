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

## Initial product references

The following primary sources were read on 2026-10-04. They inform exploration and are not compatibility commitments or a comprehensive comparison.

- Microsoft's [Agent 365 identity documentation](https://learn.microsoft.com/en-us/microsoft-agent-365/developer/identity) distinguishes an agent identity blueprint, an individual agent identity, and an optional agent user account. [Entra governance documentation](https://learn.microsoft.com/en-us/entra/id-governance/agent-id-governance-overview) describes owners and sponsors requesting access packages for agents, with configured approval and expiration. [Permission inheritance documentation](https://learn.microsoft.com/en-us/entra/agent-id/concept-inheritable-permissions) distinguishes declarations, consent, and inherited grants. These references show that shared templates, individual identities, and distributed human participation can coexist with enterprise controls; they do not settle this project's identity model or business-level authorization. The specific Agent 365 capability for AI-assisted permission planning was not confirmed in this limited review.
- OOMOL's [OpenConnector](https://github.com/oomol-lab/open-connector) already describes credential isolation, runtime tokens, Action policies, and redacted logs. Limited static reading of its [Action policy code](https://github.com/oomol-lab/open-connector/blob/8d01e5468773e64a79c187c39f8ace4751efc879/src/core/action-policy.ts) found layered deployment, runtime, and token checks, plus connection restrictions. Its [runtime reference](https://github.com/oomol-lab/open-connector/blob/8d01e5468773e64a79c187c39f8ace4751efc879/docs/runtime-api.md) describes those controls. This establishes a concrete comparison baseline; it does not validate enforcement across all call paths. Further comparison should examine delegation, data and task constraints, management roles, configuration effort, and audit evidence rather than assume connector projects lack authorization controls.

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

Continue exploring these needs before choosing an initial release scope, implementation, or acceptance criteria. The project has no runnable release.
