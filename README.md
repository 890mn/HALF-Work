# HALF-Work

**Human Agent Live in Framework**

**Language:** English (default) · [中文介绍](docs/README.zh-CN.md)

HALF-Work is a lightweight Human–Agent collaboration framework for real
software and hardware projects. It keeps the human's intent broad enough to
describe naturally, then asks the Agent to refine scope, evidence, risks, and
only the decisions that materially affect implementation.

> Status: **v0.2 Personal Pilot** — the first engineering trials and one
> self-hosted usage review are complete; external-project acceptance remains.

## Why HALF-Work

An Agent can produce code quickly while still missing the actual product
boundary, the board-level acceptance target, or the ownership of an existing
dirty worktree. HALF-Work treats the task contract, evidence, and review as
first-class work products.

## Four independent dimensions

These dimensions must not be collapsed into one overloaded “level” field:

| Dimension | Meaning |
| --- | --- |
| HALF-Work Task Class | `L0` small fix, `L1` standard task, `L2` architecture task |
| Global Orchestration Level | Host-defined planning and Agent-dispatch policy, or `Not Defined` |
| Model Thinking Level | `Light`, `Standard`, `Deep`, or `Not Defined` |
| Resource Mode | `economy`, `balanced`, or `maximum` task-local resource budget |

The task class describes the work. The other dimensions describe how the work
is coordinated and verified.

## Two-step task contract, without duplicate ceremony

1. **Human Draft** — describe the goal, context, preferences, constraints, and
   unknowns naturally. The Agent reuses the conversation instead of requiring a
   form.
2. **Agent Refinement / User Review** — inspect the real repository, propose
   scope, define evidence and acceptance outcomes, and pause only when a
   material decision or new authority is required.

The reusable template is [`templates/ACTIVE_TASK_EXAMPLE.md`](templates/ACTIVE_TASK_EXAMPLE.md).

## Skill v0.2

The current reusable process synthesis is [`skills/half-work/SKILL.md`](skills/half-work/SKILL.md).
Invoke it explicitly as `$half-work` when a non-trivial task needs workspace
inspection, scope and ownership, evidence gates, review, or honest closure.
v0.2 adds four operating tracks (`Refine`, `Execute`, `Review`, and `Close`), a
material-decision checkpoint, portable role names, aligned Host/build evidence,
and proportionate metrics.

For a Chinese onboarding guide, see [`docs/README.zh-CN.md`](docs/README.zh-CN.md).

## v0.2 status

v0.2 is a compatibility-focused Personal Pilot revision. Existing v0.1
contracts remain readable, while new tasks no longer require the user to repeat
known context, compare artificial options, or wait at a checkpoint when the
requested implementation is already clear. It remains a lightweight workflow,
not a universal governance standard or an automated metrics system.

## Workflow

```text
Observe → Plan → Implement → Verify → Review → Close or Carry Risk
```

Small tasks can use a fast path. Architecture tasks must expose boundaries,
sub-gates, ownership, and independent review evidence in proportion to risk.

## Acceptance outcomes

Every gate records one explicit result:

- `Pass` — the declared contract was met;
- `Fail` — the contract was not met;
- `Not Run` — the check was not executed;
- `Accepted Limitation` — a declared boundary was observed and accepted;
- `Carried Risk` — the item remains open with a named follow-up trigger.

An accepted limitation is evidence, not a disguised pass. If it changes a
required accepted result, it must be pre-accepted in the contract or explicitly
accepted by the human after observation. A closed task must be archived or
replaced before another task becomes current.

## Public and private boundary

The first public seed intentionally contains only reusable workflow material.
It does not contain:

- private pilot planning history;
- local control files or active task contracts;
- working copies such as `templates/ACTIVE_TASK.md`;
- editor state or machine-local configuration;
- credentials, tokens, private URLs, or generated secrets;
- DeskNest or CNFontNest product code.

The initial private planning documents `HALF-Work-ROADMAP.md` and
`design-draft.md` remain local and are excluded by `.gitignore`.

## Current direction

Version 0.2 should now be exercised in a project outside the original pilot.
The next evaluation should ask whether the Skill selects the right operating
track, avoids unnecessary pauses, preserves worktree ownership, and closes
required gates honestly. Collect timing or Agent-call metrics only when those
measurements answer a real process question.
