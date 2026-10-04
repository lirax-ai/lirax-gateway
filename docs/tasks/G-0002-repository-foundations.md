# G-0002: Improve ignore rules and text conventions

Status: Done
Updated: 2026-10-04
Owner and editing scopes: Unassigned; an AI assistant prepared this update at the project initiator's request.

## Problem and objective

Provide consistent file handling and formatting conventions for people and AI assistants. Exclude machine-specific materials while retaining shared documentation, configuration examples, and other project assets.

## Scope and acceptance criteria

Improve `.gitignore`, add `.editorconfig` and `.gitattributes`, and document [repository foundations](../repository-basics.md). Verify ignored and shareable paths, text normalization, and binary handling. Technology selection and build configuration are outside this task.

## Progress, evidence, and decisions

Added environment example exceptions, common credential filenames, editor state, operating system files, and root-level temporary output rules. Documentation, lockfiles, images, and office documents remain trackable. The foundations guide explains the rules and local checks.

## Validation results

Git checks passed for 39 ignored paths, 33 shareable paths, and 11 text or binary attribute cases. EditorConfig settings were inspected for encoding, newlines, indentation, and Markdown whitespace handling.

## Handoff and next step

Once the technology stack is selected, add actual dependency, build, and test outputs and check for unintended exclusions. Completion of this task does not establish initial feature requirements.

## Related records

- [Repository foundations](../repository-basics.md)
- [Workflow](../workflow.md)

Implementation and validation are complete. Commit and publication status should be checked against the actual repository state.
