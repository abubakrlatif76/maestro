---
name: maestro
description: Coordinate coding work with GPT-6 Astra at max effort planning and verifying, and GPT-6 Luna or Sol implementing at task-specific effort. Use for requested Astra-led delegation or cost-conscious mixed-model development.
---

# Maestro

Complete the requested coding task with Astra at `max` effort owning understanding, architecture, assignments, integration, and acceptance. Astra selects Luna or Sol and an effort level for each useful worker assignment. Optimize for the cost of a correct result.

## Establish the workflow

- The main task must be configured as `gpt-6-astra` with `max` reasoning effort for the requested profile. The user selects these settings; skill text and UI metadata cannot change the running model or effort. Check exposed runtime information once. Disclose known mismatches before delegation and explain the needed selection. If information is absent, do not claim confirmation. Useful work under another configuration is a disclosed fallback, not an Astra/max run. Do not change global defaults or create another user task to obtain this profile.
- Follow the project's instructions, stack, tests, conventions, and existing authorization. Inspect relevant code and preserve ongoing changes. Keep investigation proportional to the task.
- At first delegation, read [runtime.md](references/runtime.md). Explicitly request the selected worker model and effort through supported controls. Never inherit Astra/max accidentally or silently substitute another model. If a required capability is unavailable, disclose it and continue useful authorized work with an explicit fallback.
- Astra delegates directly to workers. Do not add a standing reviewer team, nested delegation, or worker `ultra` unless the user requests it. Use only the models needed; there is no requirement to use all three on every task.

## Understand and route

Before assigning work, establish intended behavior, affected interfaces, dependencies, important failure cases, and evidence of completion. Resolve architectural uncertainty with Astra before asking a worker to implement a design. Handle trivial work directly when delegation would cost more than it saves.

Choose **model and effort together**. Assess ambiguity, component coupling, failure impact, and how reliably correctness can be checked. File count alone is insufficient. Use this starting policy:

| Model / effort | Assignment |
| --- | --- |
| Luna `low` / `medium` | Mechanical edits, known-file extraction, documentation, or small changes following an established pattern with obvious checks. |
| Luna `high` | Bounded implementation with explicit behavior, settled interfaces, and meaningful tests or another reliable correctness check. Normal starting point for substantive Luna coding. |
| Luna `xhigh` / `max` | Reasoning-intensive but constrained implementation whose edge cases can be checked well. Choose when extra reasoning is more useful than broader judgment. |
| Sol `medium` / `high` | Work spanning interacting components, uncertain debugging, unfamiliar conventions, or implementation requiring judgment. Use `high` for subtle logic or costly mistakes. |
| Sol `xhigh` / `max` | Difficult integration, concurrency, persistent conceptual failures, or another demanding bounded assignment that warrants the expense. |
| Astra `max` | Planning, architectural tradeoffs, unclear or consequential decisions, final acceptance, and implementation takeovers when delegation stops helping. |

Prefer Luna when the task is well specified and verifiable. Prefer Sol when ambiguity, coupling, or difficult-to-detect errors dominate. Keep high-impact design decisions with Astra even when a change is one line; give Sol a narrowed implementation assignment where appropriate. Do not equate benchmark scores with universal capability, force a cheap-first retry ladder, or choose maximum effort automatically. A supported intermediate setting may be appropriate; explain the choice briefly.

For a close decision, benchmark context, or repeated routing failures, read [model-routing.md](references/model-routing.md). Its dated evidence informs a starting policy, not a price guarantee. Routine assignments do not need fresh web research. Prefer comparable project outcomes over aggregate benchmark rankings when such evidence exists.

## Assign and schedule

The number of assignments follows the meaningful subtasks. There is no fixed starting count, model quota, or skill-imposed total worker cap. Combine tiny or tightly coupled steps. Run ready, independent work up to the runtime's actual capacity; queue the rest and respect dependencies. Reuse workers when retaining context helps and their settings remain appropriate.

Assign one writer for overlapping files, public interfaces, generated artifacts, or shared test state. Agree interface contracts before dependent work starts. Astra must not edit files while a worker owns their changes. Read-only access to shared code is fine.

Give every worker a concise, self-contained brief:

- **Outcome and acceptance:** required behavior, meaningful examples and failure cases, scope boundaries, and concrete evidence needed for completion.
- **Context and contract:** exact work directory, relevant paths or symbols, input/output or API contracts, dependencies, and existing patterns to follow. Link large artifacts instead of copying session history.
- **Ownership and constraints:** writable area, existing changes to preserve, project rules, and decisions that must be escalated. Workers must not spawn agents or create user tasks.
- **Validation and return:** relevant checks; permission to inspect surrounding code and add meaningful regression coverage; report changed files, key decisions, commands actually run and results, and unresolved issues. Do not weaken checks to manufacture a pass.

State the selected model/effort and a short reason in the delegation update. Provide precise requirements without prewriting an entire implementation unnecessarily; let workers make routine choices within the contract. Answer missing-context questions promptly and update affected assignments if requirements change.

For multi-stage work, keep a compact record in the project's existing task notes, or a task-local scratch file: assignment, owner, model/effort, acceptance criteria, status, correction count, and evidence. Resume from recorded results and actual files after context loss; do not repeat completed work. Avoid elaborate tracking for a tiny change.

## Verify, correct, and accept

Worker reports are evidence to inspect, not approval. Astra reviews the actual diff and affected code against the original requirements, including interfaces between assignments. Check meaningful edge cases, error behavior, regressions, and fit with project conventions. Verify that tests exercise the intended behavior rather than merely reproduce the implementation.

Use appropriate existing tests, focused regression checks, builds, or user-flow inspection. Astra runs or directly observes the decisive combined check where feasible. Do not repeat an adequate check merely because another agent ran it; repeat when code changed, integration matters, or evidence leaves a concrete doubt. Add tests for meaningful behavior changes, not every reversible edit. For subtle work, independently examine a boundary or interaction the worker's report did not establish.

For each substantive requirement, record **pass**, **fail**, or **unverified**, with the supporting file/check and result. Distinguish worker-reported checks from Astra-observed evidence. Final acceptance requires satisfied requirements and no unresolved correctness or integration defects. A passing test count alone is insufficient. If a required check cannot run, disclose the gap and do not describe that requirement as verified. Do not invent a numerical quality score.

Return concrete defects with expected behavior, observed failure, relevant paths, and checks for the fix. Diagnose before escalating:

- Missing context or a clear local mistake: clarify and reuse the worker at its current settings.
- Insufficient reasoning on a well-bounded problem: select a justified higher effort directly.
- Misunderstood interactions, repeated conceptual errors, or weak verifiability: transfer Luna work to Sol, or let Astra settle the hard decision and narrow the assignment.

Allow up to **two correction rounds per assignment after initial delivery**, shared across all worker/model/effort replacements. Do not reset the count by relabeling the same unresolved work. At the limit, Astra diagnoses and takes over or substantively revises the approach; unresolved requirements remain open. Never treat the limit as permission to declare success.

When settings change, follow the runtime's real mechanism. If none exists for a running worker, stop or finish it, confirm ownership is released, inspect existing changes, and launch a replacement with the remaining problem and evidence. Preserve useful work; a message to “think harder” does not change configured effort.

## Report and improve

Give a concise final account of delivered behavior, acceptance results, decisive checks, and material gaps. Use a short requirement/evidence/status table when it helps the user assess completion; otherwise use plain prose. Include the important routing or escalation decisions without an agent activity transcript.

For recurring comparable tasks, retain lightweight observations of acceptance, defects, correction rounds, and verification gaps to improve future choices. Record time, tokens, and cost only when observed, including Astra orchestration and review. Distinguish requested from confirmed settings. Do not promise equal quality, fixed savings, a hard spending cap, or API-price-equivalent Codex quota savings.
