# Reusable System Assets

Status: Active

This repository uses the standard reusable-system asset model so repeated work becomes durable repository infrastructure instead of remaining a one-off prompt.

## Asset Types

- **Skills**: adaptable job-to-be-done workflows with clear triggers, inputs, outputs, validation, and failure behavior.
- **Agents**: ongoing responsibilities with ownership, boundaries, cadence, and escalation paths.
- **Checklists**: repeatable pass/fail verification gates with evidence and negative findings.
- **SOPs**: complete start-to-finish workflows with prerequisites, procedure, validation, archive, and recovery.
- **Meta Processes**: repository-improvement workflows that detect repeatable work and convert it into Skills, Agents, Checklists, SOPs, schemas, tests, rules, or safe automation.

## Meta Process Contracts (explicit activation)

See [META_PROCESS_CONTRACTS.md](META_PROCESS_CONTRACTS.md) for the invocation contract, process registry, validation, failure behavior, and negative-finding requirements. These processes are available only through explicit activation; the list below is an inventory, not an autonomous command.

- Process-to-Skill converter
- Process-to-Agent converter
- Process-to-SOP converter
- Process-to-Checklist converter
- Repository gap analyzer
- Repository maturity auditor
- Missing documentation detector
- Knowledge coverage auditor
- Knowledge gap detector
- Rule consistency validator
- Business OS completeness auditor
- Agent responsibility validator
- Duplicate documentation finder
- Automation opportunity analyzer
- Continuous improvement agent

## Operating Rules

1. Inspect existing assets before creating new ones.
2. Extend the closest current asset instead of creating a duplicate.
3. Preserve the repository's highest-authority instructions, approval gates, security boundaries, release process, and rollback path.
4. Include negative findings when a search or investigation finds no exact matches, no missing references, or no actionable gaps.
5. Keep secrets, credentials, customer data, runtime data, generated private artifacts, and approval records out of Git.
6. Do not publish, deploy, send external messages, spend money, change secrets, delete data, merge, or perform destructive cleanup unless this repository's authority files and the owner explicitly approve the exact action.

## Default Output

Any reusable-system pass should report:

- inspected scope;
- existing assets found;
- missing assets or gaps;
- negative findings;
- files created or updated;
- validation performed;
- protected actions intentionally not taken.

## Repository Scope

Repository: `advantageosmain-sudo/twentyMS`
