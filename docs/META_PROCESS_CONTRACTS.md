# Reusable Meta-Process Contracts

Status: DRAFT; activation: explicit/manual

This inventory is backed by the canonical [Advantage.OS convert-repeatable-process skill](https://github.com/advantageosmain-sudo/Advantage.OS/blob/d9519411284a1d109023d9c99df6b540c4c60582/skills/convert-repeatable-process/SKILL.md). That skill is the only converter of record for process-to-Skill, process-to-Agent, process-to-SOP, and process-to-Checklist work.

## Invocation contract

Select a registry entry, then build a `request` object that satisfies the authoritative `schemas/process_operations_request.schema.json` in Advantage.OS. The request requires exactly these top-level fields:

- `process_name`, `outcome`, `trigger`, `performer`, `tools`;
- `inputs`: objects with `name`, `description`, and `required` (optional `type` and `source`);
- `current_steps`: objects with `id` and `action` (optional `owner`, `decision`, `output`);
- `decision_rules`: objects with `if` and `then` (optional `else`, `priority`);
- `expected_output`, `exceptions`, `required_approvals`, `done_definition`, `risk_level`, and `external_actions`;
- optional `process_id`, matching `^process-[a-z0-9]+(?:-[a-z0-9]+)*$`, and optional `example`.

Do not add wrapper fields to the schema-validated request. Keep repository scope, selected registry id, source references, and approval notes in the surrounding review record.

## Procedure

1. Inspect authoritative instructions and existing assets, recording exact matches and negative findings.
2. Normalize the source process into facts, rules, decisions, examples, assumptions, and unknowns.
3. Build the schema-valid request and select the smallest justified asset set.
4. Compile a draft package using the canonical `process_operations_package.schema.json`.
5. Validate every selected asset's inputs, outputs, permissions, quality checks, tests, approvals, and failure behavior.
6. Open a reviewable change; activation remains blocked until required repository and owner approvals exist.

## Contracted package output

A package must contain `process_id`, `version`, `status`, `source_sha256`, `classification`, `assets`, `missing_inputs`, `risks`, `validation`, and `approval`. Each asset must declare `kind`, `path`, `purpose`, `inputs`, `outputs`, `permissions`, `failure_behavior`, `quality_checks`, and `tests`.

## Validation and failure behavior

- Parse the request and package schemas before conversion.
- Require `process_id` values to use the `process-` prefix.
- Return `BLOCKED_INPUT` for missing or contradictory behavior, permissions, evidence, approvals, or done criteria.
- Fail closed for missing evidence, failed QA, changed hashes, duplicate execution, or unverified provider results.
- Preserve partial work as a draft; external actions remain default-deny.
- Never publish, deploy, spend, send messages, change secrets, delete data, perform destructive cleanup, merge, or mutate customer/runtime data during conversion.
 
## Asset destination

The selected asset kind determines the governed path in the canonical converter. Consumer repositories must record the source process id/version in any local draft and must not create a duplicate converter.

## Registered processes

| Registry id | Required request focus | Draft output |
| --- | --- | --- |
| `process-process-to-skill` | bounded capability and target skill system | skill asset |
| `process-process-to-agent` | autonomous steps, owner, permissions, escalation | agent contract |
| `process-process-to-sop` | end-to-end stages, approvals, recovery | SOP |
| `process-process-to-checklist` | bounded verification sequence | checklist |
| `process-repository-gap-analyzer` | scope and existing-asset inventory | gap report |
| `process-repository-maturity-auditor` | maturity criteria and repository snapshot | maturity report |
| `process-missing-documentation-detector` | target behavior and documentation search | missing-doc report |
| `process-knowledge-coverage-auditor` | required topics and source map | coverage matrix |
| `process-knowledge-gap-detector` | expected coverage and current knowledge | gap list |
| `process-rule-consistency-validator` | authority files and dependent rules | conflict report |
| `process-business-os-completeness-auditor` | operating contracts and gates | completeness report |
| `process-agent-responsibility-validator` | agent registry and ownership model | responsibility report |
| `process-duplicate-documentation-finder` | candidate docs and identity evidence | duplicate report |
| `process-automation-opportunity-analyzer` | repeatable work and risk profile | opportunity report |
| `process-continuous-improvement-agent` | approved scope and prior findings | improvement draft |

## Activation gate

The default status is `DRAFT` or `BLOCKED_INPUT`. A contract becomes `ACTIVE` only after repository validation and the required owner/release approval. This document authorizes inspection and drafting only; it does not authorize external side effects.
