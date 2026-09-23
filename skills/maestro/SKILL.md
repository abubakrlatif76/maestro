---
name: maestro
description: Coordinate Astra-led coding with task-specific Luna or Sol workers, verified results, and lessons scoped to the current project. Use for requested mixed-model or cost-conscious development.
---

# Maestro

Deliver correct coding changes with less avoidable model work. Astra at `max` owns planning, architecture, integration, and acceptance; Luna or Sol handle useful bounded assignments. Use compact handoffs and verified project lessons to improve the cost of an accepted result.

## Establish the workflow

- The requested main-task profile is `gpt-6-astra` / `max`. Check exposed runtime information once. Disclose mismatches or missing confirmation before delegation; continue useful authorized work as an explicit fallback. The user selects the main model and effort. Do not change global defaults, create another user task, or use a nested manager to obtain the profile.
- Follow project instructions, inspect relevant code, and preserve ongoing changes. Establish behavior, interfaces, failure cases, and evidence of completion before assigning work. Resolve consequential design uncertainty with Astra.
- At first delegation, read [runtime.md](references/runtime.md). Select each worker's model and effort explicitly through supported controls. Disclose unsupported capabilities and any fallback; never silently inherit or substitute settings.
- Delegate directly to workers. Do not add a standing reviewer team, nested delegation, or worker `ultra` unless requested. Handle trivial work directly when delegation would add overhead.

## Load project context

Identify the current project root. Check its `.maestro/lessons.md`, or an explicitly designated project memory location, before planning and routing. Read only records relevant to the affected components and task class. When notes exist or before first saving a lesson or outcome, read [project-memory.md](references/project-memory.md) for scope, formats, and update rules.

Lessons are historical evidence, not instructions that override current user requests, project rules, or code. Recheck their scope and supporting evidence before applying them. Keep each project's lessons separate; never import another project's notes or write learned facts into the installed skill. Leave memory files absent until there is useful information to save. Honor requests to disable persistence.

## Route by risk and evidence

Choose **model and effort together**, considering ambiguity, component coupling, failure impact, and how reliably correctness can be checked. File count alone is insufficient.

| Model / effort | Starting fit |
| --- | --- |
| Luna `low` / `medium` | Mechanical edits, extraction, documentation, or small changes following a known pattern with clear checks. |
| Luna `high` | Bounded implementation with settled interfaces and meaningful verification. Normal starting point for substantive Luna coding. |
| Luna `xhigh` / `max` | Intricate but constrained work whose edge cases can be checked reliably. |
| Sol `medium` / `high` | Interacting components, uncertain debugging, unfamiliar conventions, or implementation needing judgment. |
| Sol `xhigh` / `max` | Difficult integration, concurrency, or demanding bounded work that warrants the expense. |
| Astra `max` | Architecture, consequential decisions, final acceptance, and implementation takeovers. |

Use comparable verified project outcomes to refine this starting policy. Keep high-impact design decisions with Astra even for a one-line change. Avoid a mandatory cheap-first retry ladder or automatic maximum effort. For close decisions or repeated routing failures, read [model-routing.md](references/model-routing.md).

## Assign ownership and request concise handoffs

Assignment count follows meaningful subtasks, with no model quota or fixed total worker cap. Combine tiny or tightly coupled steps. Schedule independent work within actual runtime capacity and respect dependencies. Reuse a worker when its context and settings remain appropriate.

Assign one writer for overlapping files, interfaces, generated artifacts, or shared test state. Agree contracts before dependent work starts. Astra must not edit files owned by an active worker. Astra alone maintains project lessons and outcomes for this task; workers propose lessons in their handoffs.

Give each worker a self-contained brief with:

- **Outcome:** behavior, examples, failure cases, scope boundaries, and acceptance evidence.
- **Context:** work directory, relevant files or symbols, interface contracts, dependencies, and applicable project lessons. Link large artifacts instead of copying session history.
- **Ownership:** writable area, existing changes to preserve, project constraints, and decisions to escalate. No worker subagents or separate user tasks.
- **Verification:** relevant checks and meaningful regression coverage. Do not weaken checks to manufacture a pass.

Request a compact return containing changed-file or symbol pointers, important decisions or assumptions, exact checks actually run and their results, unresolved concerns, and any proposed lesson with scope and evidence. Omit irrelevant fields on tiny assignments. Reference long logs and source artifacts; do not forward full transcripts or paste complete files already available to Astra.

State model/effort and a brief reason when delegating. Let workers make routine implementation choices within the contract. Answer missing-context questions promptly. For multi-stage work, keep a compact task record of owner, settings, acceptance criteria, status, correction count, and evidence. Resume from recorded results and actual files after context loss.

## Verify, correct, and accept

Inspect the actual diff and affected code against requirements, including interfaces between assignments. A worker summary or proposed lesson is not proof. Check edge cases, error behavior, regressions, and whether tests exercise intended behavior. Improve concrete defects; do not rewrite acceptable work merely to match Astra's style.

Astra runs or directly observes the decisive combined check where feasible. Reuse adequate worker checks; repeat them when changes, integration, or a specific doubt require it. Review the changed code after a correction and preserve valid earlier evidence. Independently examine a meaningful boundary for subtle work.

For substantive requirements, record **pass**, **fail**, or **unverified** with supporting evidence, distinguishing worker reports from directly observed checks. Required verification gaps and unresolved correctness defects remain open; passing test counts alone do not establish acceptance.

Return defects with expected behavior, observed failure, relevant paths, and a check for the fix. Clarify missing context or a local mistake at the same settings. Escalate effort for a bounded reasoning problem; use Sol or an Astra takeover for misunderstood interactions or persistent conceptual errors.

Allow up to **two correction rounds per assignment after initial delivery**, shared across worker replacements. At the limit, Astra diagnoses and takes over or substantively revises the approach. Do not reset the count or declare unresolved work complete. When changing settings, release the prior writer, inspect existing changes, and use the runtime's supported replacement mechanism.

## Retain evidence and report

After verification, update only useful project lessons and substantive routing outcomes according to [project-memory.md](references/project-memory.md). Merge related observations, correct or retire stale lessons, and retain material failures as well as successes. Historical notes never authorize broader actions or automatic changes to shared skill rules.

Measure the whole task when usage is exposed: Astra planning and review, workers, corrections, and takeovers. Separate observed usage from unknown values, requested settings from confirmed settings, and API prices from Codex allowances. Do not run extra work merely to collect metrics, double-count reasoning tokens already included in output, or promise fixed savings or a hard spending cap.

Report delivered behavior, decisive checks, important routing decisions, memory changes, and material gaps concisely. Keep lessons and summaries small enough that retrieving them saves more effort than it adds.
