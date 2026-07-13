---
name: half-work
description: Run the HALF-Work Human–Agent workflow for real software, firmware, UI, hardware, and architecture tasks. Use when a task needs a two-step contract, explicit scope and ownership, separate task/resource/model levels, evidence gates, Agent delegation, external or device acceptance, Git stage metadata, or process metrics.
---

# HALF-Work v0.1

Use this skill to turn a natural-language engineering request into a bounded,
reviewable task with evidence and an explicit closure decision. Keep the human
intent broad in the first step; make the implementation contract precise only
after inspecting the real repository.

This is a Personal Pilot skill. Reuse its workflow across repositories, but
do not treat its DeskNest-derived examples as universal product rules.

## 1. Load the control plane

Read in order, when the files exist:

1. Global `AGENTS.md` and its safety rules.
2. The nearest project or module `AGENTS.md`.
3. Stable control files: `PROJECT_CONTROL.md`, `ACCEPTANCE.md`,
   `DECISIONS.md`, `CASELOG.md`, and acceptance examples.
4. The current task contract, normally `.tasks/ACTIVE_TASK.md`.

Treat the layers as an inheritance chain. A lower layer may add local facts or
narrow scope, but may not weaken a higher-layer safety constraint. If the
control plane is missing, report that fact and perform a narrow repository
audit; do not invent project rules.

Before editing, inspect the worktree, build entry point, current branch, and
relevant source-of-truth files. Classify existing changes as `user-owned`,
`task-owned`, or `unrelated`. Preserve user-owned and unrelated changes.

## 2. Keep the four dimensions independent

Record these separately in the task contract:

| Dimension | Values | Meaning |
|---|---|---|
| HALF-Work Task Class | `L0`, `L1`, `L2` | Scope and risk of the engineering work |
| Global Orchestration Level | project-defined `Level 1/2/3` | Planning and Agent-dispatch policy |
| Model Thinking Level | `Light`, `Standard`, `Deep` | Reasoning depth requested by the user |
| Resource Mode | `economy`, `balanced`, `maximum` | Task-local resource budget |

Do not use a project quota or model-thinking level as a substitute for the
HALF-Work task class.

Apply the task classes as follows:

- `L0`: one small fix, parameter, text, or low-risk behavior change. Preserve
  the existing boundary and use a fast path when evidence is proportionate.
- `L1`: one bounded page, module, interaction, or feature with stable data and
  architecture boundaries. Define the affected files and explicit non-goals.
- `L2`: architecture, state/data-flow change, reusable build tool, public
  contract, multi-module change, or a task with several independent gates.
  Plan the interfaces and sub-gates before implementation.

Use Resource Mode as a task-local choice:

- `economy`: reuse existing evidence, keep the scan narrow, and do not add
  reviewers or exploratory Agents automatically.
- `balanced`: use one lead/executor split when available; request one
  architecture gate only when the task genuinely needs it.
- `maximum`: reserve broader parallel work and independent design/review for
  high-risk releases or complex refactors.

Respect the project's model mapping. Do not call Sol or exploratory Agents
unless the contract, user, or a genuine architecture block requires it.

## 3. Use the two-step task contract

### Step 1 — Human Draft

Ask the user to select the Task Class and Model Thinking Level, then describe:

- desired result and observed symptom;
- context, preferences, constraints, preserved behavior, and non-goals;
- known unknowns the Agent should determine;
- whether a public artifact, board, browser, service, or other external gate is
  involved.

Do not require the user to guess filenames, APIs, tests, or Agent assignments.

### Step 2 — Agent Refinement / User Review

Inspect the real repository and complete the contract with:

1. repository context, data flow, historical decisions, and worktree ownership;
2. the four independent dimensions and their reasoning;
3. allowed changes, explicit non-goals, escalation conditions, and owner split;
4. at least two practical options when the choice is material;
5. static, runtime, and external/device verification inputs;
6. acceptance rows using `Pass`, `Fail`, `Not Run`, `Accepted Limitation`, or
   `Carried Risk`.

Wait for the user's selected option before implementation. A small L0 fast path
may skip a long option comparison when the scope and risk are genuinely clear,
but it must still state the objective, ownership, and verification.

## 4. Define evidence in layers

Separate these gates in the contract and final report:

- **Static:** source inspection, schema/manifest checks, exclusions,
  deterministic plans, geometry, and diff ownership.
- **Host/build:** unit tests, host tests, firmware compilation, generated
  artifact checks, and failure-path tests.
- **Runtime:** service, network, JSON, browser, or simulator behavior. State
  whether the data is live, cached, or fixture-based.
- **External/device:** upload, boot, physical interaction, visual output, or
  explicit user observation.

Never report compile success as device acceptance. If a device or external gate
was not run, mark it `Not Run` or `Carried Risk` and name the owner and trigger.
Convert `Carried Risk` to `Pass` only after the named evidence is observed and
recorded. A negative observation can be `Accepted Limitation` when it matches a
declared boundary; it must produce a follow-up task if the product needs more.

For dynamic input, distinguish these states explicitly: present, absent,
unknown, stale, and failed. Do not infer an unlimited or healthy state from a
zero value, an empty field, or a missing reset time alone.

## 5. Apply level-specific gates

For stateful L0 input, define the trigger, held behavior, and re-arm behavior.
Add at least one negative held-state test and one positive re-arm test when the
bug involves repeated input.

For L1 UI or product work, define the accepted page and geometry, keep preview
and renderer hierarchy aligned, and separate preview evidence from physical
visual acceptance. Keep unrelated pages, state-machine changes, and protocol
changes out of scope unless the contract expands.

For L2 work, split the parent into named gates such as core, generator,
integration, independent review, and device acceptance. Keep the parent open
until its required gates are complete. A static scanner does not prove coverage
of arbitrary runtime text; runtime vocabulary, fallback policy, or an explicit
accepted boundary must be named.

## 6. Review, rework, and metrics

After implementation, perform the lead review even when an executor was used.
Check architecture consistency, API and data ownership, duplicate logic,
regressions, product behavior, resource limits, and declared non-goals.

Record process metrics using a stable definition:

- start time: user confirmation of the implementation option;
- review time: host/build evidence and integration review complete;
- final acceptance time: external/device or user acceptance complete;
- end-to-end time: start to final acceptance, when that gate exists;
- Agent calls: count the declared top-level tool/subagent rounds and state
  whether waits or failed calls are included;
- rework rounds: implementation revisions made after the first verification;
- human decisions: explicit option choices and final acceptance decisions,
  counted separately;
- changed files, test totals, build result, and unresolved risks.

Do not backfill invented precision. If a historical case lacks a metric, mark
it unavailable and keep the case useful for qualitative workflow evidence.

## 7. Use Git as a process checkpoint

Keep commit subjects short and implementation-focused while exposing the task
class and workflow stage, for example:

```text
[L1][Review] fix weekly-only quota mapping
```

Use trailers when a meaningful checkpoint is committed:

```text
HALF-Work-Level: L1
HALF-Work-Stage: Review
HALF-Work-Task: short-task-id
HALF-Work-Evidence: tests/build/device result
```

Add metric trailers only when they are defined for the task. Do not create
empty commits merely to announce a phase. Stage files explicitly, verify the
staged file list, run `git diff --cached --check`, scan for sensitive content,
and leave user-owned changes unstaged.

## 8. Close or carry the task

Close only after every acceptance row is `Pass`, or after every remaining
boundary is explicitly accepted with an owner and follow-up trigger. Record
both the Review checkpoint and the final external acceptance when they occur at
different times. Archive or replace a closed `ACTIVE_TASK.md` before starting
another task; never let a closed contract remain the active source of truth.

When a task exposes a process defect, record the correction and feed the rule
back into the template or Skill. Keep product changes and framework changes as
separate commits when possible.

## 9. Case-derived guidance

Read [case-evidence.md](references/case-evidence.md) when you need examples of
the v0.1 decisions and failure modes. The cases establish these reusable rules:

- edge-triggered input needs an explicit re-arm state;
- L1 scope, artifact ownership, preview evidence, and board risk must be
  separate;
- L2 parents need sub-gates and must not silently close on a partial gate;
- real external acceptance is a distinct human decision and timestamp;
- metrics are useful only when their counting definitions are recorded.

## 10. Invocation examples

Use the skill explicitly for a new contract:

```text
Use $half-work to turn this request into a two-step task contract, inspect the
repository, propose options and evidence, then wait for my decision.
```

Use it for an implementation with an existing contract:

```text
Use $half-work to implement the accepted task, preserve unrelated worktree
changes, verify the declared gates, record metrics, and prepare the checkpoint.
```

Do not invoke this skill for a trivial explanation, translation, or code review
that does not require task-contract and evidence management.

## v0.1 boundaries

This version does not automate metric collection, replace project-specific
`AGENTS.md` rules, require a particular model, or publish private control files.
Use the next real tasks to test its trigger precision, metric consistency, and
closure behavior before promoting it to v1.
