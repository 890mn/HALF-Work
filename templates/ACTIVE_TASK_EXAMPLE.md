# Active Task — v0.2 Template

> Use the smallest sections the task needs. The Agent may infer the Human Draft
> from the conversation; the user does not need to copy existing context into
> this file.

## Human Draft

- Desired result:
- Observed symptom or context:
- Preferences and constraints:
- Preserved behavior and non-goals:
- Known unknowns for the Agent to investigate:
- External, public, or device gate involved:

## Agent Refinement

### Operating Track

- Primary track (select one):
- [ ] Refine
- [ ] Execute
- [ ] Review
- [ ] Close
- Secondary tracks, if the request combines lifecycle stages:

### Classification

- HALF-Work Task Class: `L0` / `L1` / `L2`
- Global Orchestration Level: host-defined or `Not Defined`
- Model Thinking Level: `Light` / `Standard` / `Deep` / `Not Defined`
- Resource Mode: `economy` / `balanced` / `maximum`
- Reasoning:

### Repository and Ownership

- Root, branch, and baseline:
- Relevant entry point, modules, and data flow:
- Applicable rules and historical decisions:
- Worktree state:
- Task-owned changes:
- User-owned changes:
- Unrelated changes:

### Scope

- Outcome:
- Selected direction:
- Allowed changes:
- Explicit non-goals:
- Escalation conditions:

### Decision Checkpoint

- Material alternatives:
- Recommended direction:
- User decision required: `Yes` / `No`
- Reason or recorded user decision:

Include multiple options only when they materially change behavior, public
contracts, risk, cost, or irreversible work.

## Verification Contract

| Claim | Gate | Required | Result | Evidence | Owner / follow-up trigger |
| --- | --- | --- | --- | --- | --- |
|  | Static / Host/build / Runtime / External/device | Yes / No | Not Run |  |  |

Allowed results: `Pass`, `Fail`, `Not Run`, `Accepted Limitation`, and
`Carried Risk`. A required `Not Run` or `Fail` keeps the task open. A required
`Accepted Limitation` must be pre-accepted in the contract or explicitly
accepted by the human after observation. A required `Carried Risk` needs
explicit human acceptance plus an owner and trigger.

## Implementation and Review

- Lead:
- Executor or reviewer, if useful and permitted:
- Changed files:
- Rework after first verification:
- Non-goal and regression review:

## Metrics

Required: changed files, checks and outcomes, unresolved risks, and material
human decisions.

Optional when reliably measurable: start/review/final-acceptance time,
end-to-end duration, Agent or tool-call count with counting definition, and
rework rounds. Use `unavailable` rather than invented precision.

## Closure

- Final state: `Open` / `Closed` / `Closed with accepted carried risk`
- Human acceptance required and recorded:
- Remaining owner and trigger:
- Archive or replacement location:

## Public / Private Boundary

Do not place credentials, private URLs, machine-local paths, generated secrets,
or unsanitized project history in a public template or commit.
