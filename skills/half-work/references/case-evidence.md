# HALF-Work v0.2 Case Evidence

This reference is a sanitized synthesis of the Phase 1 control-plane rollout,
four DeskNest pilot cases, and the v0.2 self-hosted usage review. Use it to
understand why the workflow contains its gates; do not copy project-specific
paths, secrets, or product assumptions into another repository.

## Case 1 — L0 held-tilt navigation re-arm

The firmware emitted repeated page-switch events while a left/right tilt stayed
above the threshold. A cooldown delayed the repeat but did not require the
input to leave its active zone.

The fix added a wait-neutral state: emit once, require stable baseline-relative
samples, then re-arm. Host tests and a firmware build passed; board feel stayed
an explicit risk.

Reusable rule: even an L0 stateful-input fix needs a trigger contract, a held
negative test, and a positive re-arm test. Do not escalate it to L2 unless the
state-machine boundary itself changes.

## Case 2 — L1 homepage sequence and reflection

The homepage task reused existing render-model data, established a fixed 240x320
3:2 hierarchy, and kept gesture, sensor state-machine, navigation, orientation,
and TokenNest protocol changes out of scope. Later bounded follow-ups corrected
the logical Codex label, filled the primary card, applied sensor compensation,
and rotated existing advice.

The main process failure was not implementation complexity but contract drift:
the first task mixed several UI concerns, preview evidence was not always
reproducible, dirty-worktree ownership was checked too late, and board visual
acceptance was only prose.

Reusable rule: define the accepted page and geometry, identify current versus
historical previews, separate renderer/model/data-source boundaries, and make
board visual acceptance an evidence row with a trigger.

## Case 3 — L2 CNFontNest staged architecture gates

The font-tool task was divided into discovery/core, generator, real converter and
PlatformIO integration, independent review, and device acceptance. The core
scanner proved deterministic source discovery but did not claim arbitrary
runtime network text coverage. Generator and build gates added ownership,
no-write behavior, staged replacement, converter-version checks, no-op behavior,
and deterministic output.

Review found concrete defects: a header include mismatch, nondeterministic
staging bytes, loose converter-version matching, and skipped converter probing on
no-op profiles. Device evidence later showed that dynamic web-menu Chinese text
remained outside the static font contract, so the parent closed with an explicit
accepted boundary rather than an implicit fix.

Reusable rule: an L2 parent remains open until its named gates are complete;
build, boot, visual rasterization, and runtime text completeness are separate
claims. A negative device observation is valid evidence when it maps to a
declared boundary.

## Case 4 — L1 weekly-only quota semantics

The upstream sometimes returned one quota window, which had been assigned to
the 5h field. The accepted Option A normalized a single window to weekly,
added explicit window-availability signals, selected the effective percentage
from 5h or weekly, and kept dual-window behavior unchanged.

The first verification exposed legacy payload compatibility failures. A later
review exposed that stale data could still claim availability. Both corrections
were recorded as rework. Host tests, full firmware build, and then K10
burn-and-observe acceptance completed the chain.

The recorded process sample contains separate Review and final acceptance
timestamps, 45 top-level tool-call rounds, 2 rework rounds, and 2 human
decisions. It demonstrates why a compile result cannot replace a device gate,
why metric definitions must state whether waits and failed calls count, and
why `Carried Risk` needs a named closure trigger.

## Case 5 — v0.1 usage and upgrade review

Using v0.1 to review and upgrade itself exposed portability and interaction
defects that the product cases did not show. The user had already requested a
review and implementation, but the old flow still implied a mandatory form,
multiple options, and another confirmation. Its public instructions also named
specific Agent roles supplied by one host environment, while the contract
template omitted the Host/build gate defined by the Skill. The installed copy
could drift from the repository copy because discovery and synchronization are
separate concerns.

Reusable rule: infer the Human Draft from the conversation, pause only for a
material decision, use portable responsibility names, keep the template aligned
with every evidence layer, and verify repository and installed copies
separately. Process metrics are optional unless they answer a real evaluation
question.

Two isolated v0.2 forward tests then exercised the new tracks. An explicit JSON
default change executed without an artificial user pause, preserved the other
key, passed a direct parse check, and did not commit. A read-only release review
kept the task open because device upload was `Not Run`, despite passing host
tests and firmware compilation.

Independent contract review then found that a required gate could be relabeled
`Accepted Limitation` and closed without human acceptance. v0.2 now permits that
closure only when the limitation was pre-accepted in the contract or explicitly
accepted after observation. The same review aligned formal dimension values,
primary/secondary tracks, and the default prompt's read-only behavior.

## Phase 1 control-plane lesson

The preceding Phase 1 rollout established the inheritance model: global rules,
project rules, stable control files, acceptance examples, and a current
task contract. It also established `economy` and `balanced` as task-local
Resource Modes. A new conversation must load the available control plane
read-only before changing product files, but a missing layer is evidence to
report rather than a reason to invent files.

## Evidence limits for v0.2

The cases prove that the workflow handles small fixes, bounded product work,
architecture gates, and hardware acceptance. They do not establish a universal
call-count baseline, automatic metric extraction, universal orchestration
mapping, or a release-grade public governance model. v0.2 adds interaction and
portability corrections; it still needs external-project use before v1.
