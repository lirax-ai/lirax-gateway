# 0001: Preserve maintenance knowledge in the public repository

Date: 2026-10-04
Status: Accepted

## Problem and constraints

People and AI assistants need to maintain the project over time. Requirements and design discussions may take place outside this repository, and some context cannot be published. If conclusions remain only in those discussions, contributors cannot understand why the implementation behaves as it does.

## Decision

Keep the requirements, interface conventions, important design tradeoffs, and validation methods needed for maintenance in the public repository. Rewrite conclusions from non-public discussions as independently understandable documents, issues, or PR descriptions, with sensitive information removed.

Record important design decisions in `docs/decisions/` and update the documentation index. Distinguish facts, plans, assumptions, and unverified conclusions.

## Rationale and alternatives

Keeping only code loses requirements and tradeoffs. Keeping only discussion links does not guarantee access. Publishing all source materials would expose non-public context. Prepare public records of the information needed for maintenance instead.

## Consequences

Contributors can participate without access to non-public materials. Requirements and design changes must include documentation updates; preparing those records is part of the change.

Do not publish credentials, identifying information, internal addresses, real user data, or materials without permission to publish. Removing sensitive information must preserve technical limitations that affect use and maintenance.

## Validation

During review, use only the public repository and publicly accessible sources. Check whether readers can understand the change's objective, rationale, scope, and validation method.
