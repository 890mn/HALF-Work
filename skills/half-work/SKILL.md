---
name: half-work
description: Run a lightweight Human-Agent contract for non-trivial software, firmware, UI, hardware, architecture, or public workflow changes. Use when Codex must inspect a real workspace, preserve worktree ownership, refine scope, choose whether a human decision is actually required, separate build/runtime/device evidence, coordinate delegated roles, or close work with explicit risks and acceptance. Also use to execute or review an existing HALF-Work task contract. Do not trigger for ordinary explanations or tiny edits that need no durable contract.
---

# HALF-Work v0.2

Turn an engineering request into bounded work with proportionate evidence. Reuse
what the user already said; do not make them complete a form or repeat a decision
that is already clear.

HALF-Work is a Personal Pilot. Apply its control and evidence rules across
projects, but keep project-specific architecture and model names local.

## 1. Select the operating track

Choose one primary track before doing work; add secondary tracks when the
request combines lifecycle stages:

- **Refine:** inspect a new or ambiguous request and produce a task contract.
- **Execute:** implement an explicit request or an already accepted contract.
- **Review:** diagnose, inspect, or verify without changing implementation.
- **Close:** reconcile evidence, risks, metrics, and task state.

A user may combine tracks, such as “review the current defects and improve the
skill.” Treat that as authorization to review and execute within the stated
boundary. Do not pause merely because a Human Draft file is absent.

## 2. Load the control plane and workspace

Read existing layers in this order:

1. global safety and Agent rules;
2. the nearest project or module `AGENTS.md`;
3. stable project control files, such as `PROJECT_CONTROL.md`, `ACCEPTANCE.md`,
   `DECISIONS.md`, `CASELOG.md`, and acceptance examples;
4. the current task contract, normally `.tasks/ACTIVE_TASK.md`.

Lower layers may add facts or narrow scope, but may not weaken higher safety
rules. Report missing layers briefly and continue with a narrow repository
audit. Do not invent a control plane just to satisfy the Skill.

Before editing, inspect the repository root, branch, worktree, build or document
entry point, relevant history, and source-of-truth files. Classify changes as
`user-owned`, `task-owned`, or `unrelated`; preserve the first and third.

## 3. Refine a minimum viable contract

Infer the Human Draft from the conversation. Ask only for information that
cannot be discovered and would materially change scope, authority, safety, or
the accepted result.

Record the four dimensions separately when the host supports them:

| Dimension | Typical values | Purpose |
| --- | --- | --- |
| HALF-Work Task Class | `L0`, `L1`, `L2` | engineering scope and risk |
| Global Orchestration Level | host-defined `Level 1/2/3` | coordination policy |
| Model Thinking Level | `Light`, `Standard`, `Deep` | requested reasoning depth |
| Resource Mode | `economy`, `balanced`, `maximum` | task-local resource budget |

Never substitute one dimension for another. If the host does not define a
dimension, use `Not Defined`; do not manufacture model or orchestration policy.

- `L0`: a small local fix or low-risk adjustment that preserves boundaries.
- `L1`: a bounded module, page, interaction, or feature with stable boundaries.
- `L2`: architecture, state/data flow, public contract, reusable tooling,
  multi-module work, or work with several independent gates.

The contract must state the outcome, selected direction, allowed changes,
non-goals, ownership, escalation conditions, and verification gates. Use the
smallest durable representation the project supports; a concise commentary
contract is enough for a fast path, while L2 work should use a task file when
the project has one.

## 4. Use a material decision checkpoint

Present multiple options only when they lead to materially different product
behavior, public contracts, risk, cost, or irreversible work. Recommend one.

Pause for the user when:

- authority for a side effect or scope expansion is missing;
- two viable directions change the accepted result;
- a destructive, public, costly, or external action needs consent;
- an unresolved acceptance tradeoff belongs to the human.

Do not pause when repository evidence resolves the question, the user already
selected the direction, or one bounded implementation is clearly implied by
“fix,” “implement,” “update,” or equivalent wording. For L2 work, state the
chosen direction and gates before editing even when no pause is needed.

## 5. Scale coordination to the task

Treat Agent names as host-local mappings. Assign responsibilities such as lead,
executor, architecture reviewer, or acceptance owner; never require a named
model that the environment does not provide.

- `economy`: keep work with the primary Agent unless delegation is required.
- `balanced`: use one bounded executor or reviewer only when allowed, available,
  and likely to improve speed or independence.
- `maximum`: use broader parallel work and independent review only when scope or
  risk justifies it.

The primary Agent owns integration and final review. Delegation never overrides
user scope, host policy, tool availability, or concurrency limits.

## 6. Define evidence as claims

Separate the following gates in the contract and final report:

- **Static:** source, schema, manifest, geometry, exclusions, diff ownership.
- **Host/build:** unit or host tests, compilation, deterministic artifacts,
  failure paths.
- **Runtime:** browser, service, network, JSON, simulator, or live/cached/fixture
  behavior.
- **External/device:** upload, boot, physical interaction, visual output, or
  explicit human observation.

Each acceptance row should contain: claim, whether it is required, result,
evidence, and owner or follow-up trigger. Use only these results:

- `Pass`: evidence supports the claim.
- `Fail`: evidence contradicts the claim.
- `Not Run`: no evidence was collected; this cannot close a required gate.
- `Accepted Limitation`: observed behavior matches a boundary or non-goal that
  the accepted contract already names. If it changes a required accepted
  result, record explicit human acceptance before closure.
- `Carried Risk`: a desirable or required claim remains unresolved; name its
  owner and trigger. Closing a required carried risk needs explicit human
  acceptance.

Never use compilation as proof of runtime or device behavior. For dynamic data,
distinguish present, absent, unknown, stale, and failed; zero or empty is not
automatically healthy or unlimited.

Apply domain gates only when relevant. Stateful input needs trigger, held, and
re-arm tests. UI work needs accepted geometry and separate preview/physical
evidence. L2 parents need named sub-gates and remain open until required gates
are resolved or explicitly carried.

## 7. Review and record proportionate metrics

After implementation, review architecture, ownership, duplicate logic,
regressions, resource limits, product behavior, and non-goals.

Always report the changed files, checks and outcomes, unresolved risks, and
material human decisions. Record timing, Agent/tool-call counts, rework rounds,
or end-to-end duration only when the project or user needs them and the values
can be measured consistently. Define the counting method; otherwise use
`unavailable`. Do not create work solely to improve a metric.

Read [case-evidence.md](references/case-evidence.md) when a task needs the pilot
failure modes behind these rules. Use
[ACTIVE_TASK_EXAMPLE.md](../../templates/ACTIVE_TASK_EXAMPLE.md) when a durable
contract is appropriate.

## 8. Use Git and external actions deliberately

Do not commit, push, publish, flash hardware, contact production, or send
messages unless authorized by the user or active contract. Before staging,
inspect status, stage explicit files, review the staged list, run the repository
checks, and scan for secrets. Leave user-owned and unrelated changes unstaged.

When commits are authorized, keep subjects short and implementation-focused.
Project conventions may add task class, stage, and evidence trailers; do not
create empty phase commits.

## 9. Close honestly

Close when every required gate is `Pass`; an `Accepted Limitation` may also
close its gate only when it was pre-accepted in the contract or explicitly
accepted by the human after observation. A required `Carried Risk` needs
explicit human acceptance with an owner and trigger. Keep the task open for any
required `Fail` or `Not Run` result.

Archive or replace a closed active contract before another task becomes
current. Feed proven process defects back into the Skill or template without
mixing framework changes into product commits.

## Invocation examples

```text
Use $half-work to inspect this repository, infer a minimal task contract from
my request, pause only for material decisions, then implement and verify it.
```

```text
Use $half-work to review and close the current task without changing product
code. Separate build evidence from device acceptance and list carried risks.
```

If a repository copy is not installed or linked into the Codex Skill directory,
a new conversation may not discover `$half-work`. Install or link it, or provide
the local `SKILL.md` path; a README link is not an invocation.

## v0.2 boundaries

This version does not automate metrics, require a named model, replace project
rules, publish private contracts, or initialize a full control plane. It
prioritizes proportional ceremony, material decision gates, portable roles,
and honest closure while retaining v0.1 contract compatibility.
