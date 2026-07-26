# Agent Instructions

Start by reading this repository's README and the most specific local instructions for the area being changed.

## Reusable System Asset Layer

Use `docs/REUSABLE_SYSTEM_ASSETS.md` when repeated work in this repository should become a durable Skill, Agent, Checklist, SOP, schema, test, rule, or safe automation.

Rules for this layer:

- Inspect existing repository assets before creating new ones.
- Extend current assets instead of creating duplicates.
- Preserve this repository's highest-authority instructions, approval gates, security boundaries, release process, and rollback path.
- Include negative findings for searches or investigations, including no exact matches or no missing references.
- Do not publish, deploy, spend money, send external messages, change secrets, delete data, merge, or perform destructive cleanup without explicit owner approval for the exact action.

Repository scope: `advantageosmain-sudo/twentyMS`.

