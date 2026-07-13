# Active Task — Human Draft Template

> A two-step contract for Human–Agent collaboration. The Agent must complete
> Step 2 from the real repository context and wait for user review before
> entering implementation.

## Step 1 — Human Draft

### Task Profile

#### HALF-Work Task Class

- [ ] **L0 — Small fix**: local bug, parameter, text, or low-risk adjustment
- [ ] **L1 — Standard task**: page, module, interaction, or bounded feature
- [ ] **L2 — Architecture task**: state, data flow, core architecture, or high-regression change

#### Model Thinking Level

- [ ] **Light**: reuse known context and propose the smallest viable path
- [ ] **Standard**: inspect the repository, risks, and 2–3 practical options
- [ ] **Deep**: inspect history, cross-module dependencies, alternatives, and regression boundaries

### Task Overview

Describe the desired result in one or two sentences.

### Task Description

Describe the idea, symptom, target behavior, reference, or expected result in
natural language. Do not guess the files, API, tests, or Agent split yet.

### Task Preferences

- Prefer the smallest change:
- Prefer visible device/product behavior:
- Allow a new module:
- Preserve existing interaction:
- Preferred visual or technical direction:
- Allow a separate public-repository artifact:
- Other preference:

### User Known Constraints

Write constraints, preserved behavior, non-goals, or privacy requirements.

### User Unknowns

Write what the Agent should determine: task class, files, options, tests,
regression risk, hardware acceptance, or public/private boundary.

## Step 2 — Agent Refinement / User Review

### Repository Context

- Relevant modules:
- Entry point and data flow:
- Historical decisions:
- Relevant case log:
- Current worktree state:
- Baseline commit/version:

### Proposed Classification

- HALF-Work Task Class:
- Global Orchestration Level:
- Model Thinking Level:
- Resource Mode: `economy` / `balanced` / `maximum`
- Reasoning:

### Proposed Scope

- Allowed changes:
- Explicit non-goals:
- Existing change ownership: `task-owned` / `user-owned` / `unrelated`
- Escalation conditions:

### Proposed Options

#### Option A

- Approach:
- Benefit:
- Risk:
- User decision:

#### Option B

- Approach:
- Benefit:
- Risk:
- User decision:

#### Option C (optional)

- Approach:
- Benefit:
- Risk:
- User decision:

### Verification Contract

#### Static Inputs

- Inputs to inspect:
- Generated or excluded directories:

#### Runtime Inputs

- Network, JSON, user, or dynamic strings:
- Vocabulary, manifest, or fallback requirement:

#### External / Device Evidence

- Browser, board, service, or human observation:
- Checks intentionally not run:

### Acceptance Outcomes

Each item must use one result:
`Pass`, `Fail`, `Not Run`, `Accepted Limitation`, or `Carried Risk`.

| Acceptance item | Result | Evidence | Note / follow-up |
|---|---|---|---|
|  |  |  |  |

### User Review Decision

- [ ] Accept the proposed option and enter implementation
- [ ] Choose another option and request a revised contract
- [ ] Narrow the scope and review again
- [ ] Pause the task

User decision:

## Lifecycle

```text
Draft → Refinement → Awaiting User Review → Active → Verify → Review → Closed
```

If a risk is carried, the task may close only when its owner and follow-up
trigger are recorded. The completed contract must be archived or replaced.

## Public / Private Boundary

Do not place credentials, private URLs, machine-local paths, generated secrets,
or unsanitized project history in a public template or commit.
