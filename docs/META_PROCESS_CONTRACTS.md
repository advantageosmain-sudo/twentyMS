# Reusable Meta-Process Contracts

Status: active; activation: explicit/manual

This file turns the inventory in `docs/REUSABLE_SYSTEM_ASSETS.md` into a discoverable contract. The inventory is not an executable command by itself. Use the canonical converter [Advantage.OS `skills/convert-repeatable-process/SKILL.md`](https://github.com/advantageosmain-sudo/Advantage.OS/blob/main/skills/convert-repeatable-process/SKILL.md).

## Invocation contract

Required input:
- `scope`: repository paths and the repeatable process under review;
- `source`: existing SOP, checklist, code path, transcript, or other evidence;
- `existing_assets`: search results, including negative findings;
- `requested_process`: one registered process id;
- `approval_context`: applicable owner, security, release, and external-action gates.

Procedure:
1. Inspect current assets and authoritative instructions.
2. Normalize the source into facts, rules, decisions, examples, assumptions, and unknowns.
3. Compile only the smallest justified asset set.
4. Validate inputs, outputs, permissions, failure behavior, tests, and duplicate identity.
5. Emit a draft package and validation report for review.

Outputs:
- `process_id` and source/version identity;
- selected asset paths;
- input/output/permission/failure contracts;
- validation results;
- negative findings, unresolved inputs, risks, and approval requirements;
- activation status, which defaults to `DRAFT` or `BLOCKED_INPUT`.

Validation:
- every selected asset declares trigger, inputs, outputs, permissions, failure behavior, and tests;
- missing or contradictory business rules produce `BLOCKED_INPUT`;
- external actions are default-deny and retain their existing approval gate;
- no duplicate asset is created for the same process/version;
- repository tests, schema checks, and secret/private-data checks pass.

Failure behavior:
- fail closed on missing or conflicting inputs, unverified evidence, failed QA, changed hashes, duplicate execution, or missing approval;
- preserve partial work as a draft;
- never publish, deploy, spend, send messages, change secrets, delete data, merge, or mutate customer/runtime data as part of conversion.


## Asset destination

Process conversion produces draft assets in the canonical converter's governed paths. A consumer repository may add a repository-local asset only when its own instructions define the destination and a reviewed pull request records the source `process_id` and version. Do not create duplicate converters or place product prompts in automation-only directories.

## Process registry

| Process id | Required input | Contracted output | Minimum validation |
| --- | --- | --- | --- |
| process-to-skill | repeatable process and target skill system | typed skill draft | trigger, inputs, outputs, permissions, tests |
| process-to-agent | autonomous steps, owner, permissions, escalation | agent contract | least privilege, handoffs, failure behavior |
| process-to-sop | end-to-end stages and approvals | versioned SOP | ordered steps, approvals, recovery |
| process-to-checklist | bounded verification sequence | pass/fail/blocked checklist | objective evidence and stop conditions |
| repository-gap-analyzer | scope and asset inventory | gap report | negative findings and evidence paths |
| repository-maturity-auditor | maturity criteria and repository snapshot | maturity report | reproducible scoring and blockers |
| missing-documentation-detector | target behavior and docs search | missing-doc report | exact search scope and no-match result |
| knowledge-coverage-auditor | required topics and sources | coverage matrix | source mapping and unresolved gaps |
| knowledge-gap-detector | current knowledge set and expected coverage | gap list | evidence-backed missing items |
| rule-consistency-validator | authority files and dependent rules | conflict report | precedence and contradiction checks |
| business-os-completeness-auditor | operating contracts and gates | completeness report | required stages, gates, and paths |
| agent-responsibility-validator | agent registry and ownership model | responsibility report | overlap, omission, and escalation checks |
| duplicate-documentation-finder | candidate docs and identity hints | duplicate report | content/identity evidence before consolidation |
| automation-opportunity-analyzer | repeatable work and risk profile | opportunity report | preserve human approvals and risk boundaries |
| continuous-improvement-agent | prior findings and approved scope | improvement draft | bounded change, regression checks, rollback |

## Activation gate

A contract becomes `ACTIVE` only after repository validation and the required owner/release approval. This document authorizes inspection and drafting only; it does not authorize external side effects.
