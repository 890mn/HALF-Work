# HALF-Work

**Human Agent Live in Framework**

**Language:** English (default) · [中文介绍](docs/README.zh-CN.md)

HALF-Work is a lightweight Human–Agent collaboration framework for real
software and hardware projects. It keeps the human's intent broad enough to
describe naturally, then asks the Agent to refine scope, evidence, risks, and
options before implementation begins.

> Status: **Personal Pilot** — the first DeskNest engineering trials are
> complete; framework acceptance is still under revision.

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
| Global Orchestration Level | The host project's Level 1/2/3 planning and Agent-dispatch rules |
| Model Thinking Level | `轻量`, `标准`, or `深入` reasoning depth requested by the user |
| Resource Mode | `economy`, `balanced`, or `maximum` task-local resource budget |

The task class describes the work. The other dimensions describe how the work
is coordinated and verified.

## Two-step task contract

1. **Human Draft** — choose the task class and thinking level, then describe the
   goal, context, preferences, constraints, and unknowns in natural language.
2. **Agent Refinement / User Review** — inspect the real repository, propose
   scope and options, define evidence and acceptance outcomes, and wait for
   user confirmation before implementation.

The reusable template is [`templates/ACTIVE_TASK_EXAMPLE.md`](templates/ACTIVE_TASK_EXAMPLE.md).

## Skill v0.1

The current reusable process synthesis is [`skills/half-work/SKILL.md`](skills/half-work/SKILL.md).
Invoke it explicitly as `$half-work` when a task needs a two-step contract,
evidence gates, review, and closure metrics. This is still a Personal Pilot;
the next real tasks should forward-test its trigger precision and metric
definitions before a v1 revision.

For a Chinese onboarding guide, see [`docs/README.zh-CN.md`](docs/README.zh-CN.md).

## v0.1 status

v0.1 is a usable Personal Pilot baseline synthesized from four DeskNest
engineering cases. It includes the executable Skill, the two-step task
template, bilingual onboarding, explicit evidence outcomes, and a private
active-contract boundary. It is ready for forward-testing, but it is not yet
a universal governance standard or an automated metrics system.

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

An accepted limitation is evidence, not a disguised pass. A closed task must
be archived or replaced before another task becomes current.

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

Version 0.1 is now a usable pilot baseline. The next improvement should come
from a fresh real task: invoke the Skill, exercise the two-step contract,
record elapsed time, Agent calls, rework rounds, changed files, and human
decisions, then revise only the rules that the evidence actually exposes. A
public template should grow from another real project, not from publishing
the entire private planning history at once.
