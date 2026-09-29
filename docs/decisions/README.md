# Decision records

Create a numbered Markdown file for a decision that shapes the project's interfaces, architecture, security, or operations. A decision record is a concise explanation, not a transcript. Update its status when new evidence changes the decision; write a new record when a later decision supersedes it.

Use this structure:

```markdown
# NNNN: Short decision title

Status: Proposed | Accepted | Superseded
Date: YYYY-MM-DD

## Context

What problem are we solving? Include enough constraints and examples for a reader who has access only to this repository.

## Decision

What did we choose, or what question remains open?

## Alternatives

Which realistic options were considered, and why were they not chosen?

## Consequences

What changes, what risks remain, and what should be revisited?
```

Do not refer readers to private notes for missing context. Remove sensitive details before adding a public record, while retaining the constraints needed to evaluate the decision.
