# Maestro

**Purpose:** Maestro helps Codex deliver reliable coding changes while reducing avoidable model usage. It keeps GPT-6 Astra responsible for planning and final acceptance, assigns suitable implementation work to GPT-6 Luna or GPT-6 Sol, and reuses verified lessons within each project.

The aim is a lower cost per accepted result. Model choices, feedback, and memory support that aim; they do not guarantee equal quality, fixed savings, or a spending cap.

## How it works

The requested main-task profile is **GPT-6 Astra with `max` reasoning effort**. Select that model and effort in Codex yourself: a skill cannot change the running task's model, effort, or global settings. Maestro checks the runtime information it can see and reports any mismatch or missing confirmation. Work under another configuration is a disclosed fallback.

1. Astra establishes requirements and checks relevant lessons from the current project.
2. It chooses the worker model and effort together, based on ambiguity, coupling, impact, and how well the result can be verified. Luna fits clear, bounded work; Sol fits work needing more judgment. Trivial work can stay with Astra.
3. Workers return concise summaries with changed-file references, decisions, checks actually run, unresolved concerns, and candidate lessons. Large artifacts stay in files instead of being repeated in the main conversation.
4. Astra reviews the actual changes, verifies integration, and corrects, escalates, or takes over when necessary. It updates useful lessons only after checking the evidence.

Assignment count follows useful subtasks and runtime capacity. There is no model quota or requirement to use every model. Each writable area has one owner, and Astra keeps consequential design decisions and final acceptance.

## Install and use

Ask Codex:

```text
$skill-installer install Maestro from https://github.com/abubakrlatif76/maestro/tree/main/skills/maestro
```

Select **GPT-6 Astra / max**, then invoke `$maestro` on a coding task. A newly installed skill is available starting with the next turn. For example:

```text
$maestro Add CSV export to this project. Follow its existing conventions,
verify the behavior, and retain any useful project lessons.
```

For a project-specific copy, manually copy `skills/maestro` into that project's `.agents/skills/maestro` directory.

## Lessons are separate for each project

Shared skill instructions describe how to work. Learned project facts live in the working repository, outside the installed skill:

```text
your-project/
  .maestro/
    lessons.md    # Verified project knowledge, created when useful
    outcomes.md   # Substantive delegation outcomes, when useful for comparisons
```

For non-Git work, use the explicitly identified project root. An explicit project memory location or a request to disable persistence takes precedence over these defaults. Missing files are normal: Maestro creates no empty memory scaffolding and invents no lessons for routine work.

Each lesson records its scope, finding, evidence, and last verification date/revision. An example might be a project's export timestamp convention and the test that verifies it. This is a project-specific discovery, not a universal rule for other projects.

During later tasks, Astra reads only relevant lessons, checks that they still apply, merges duplicates, and corrects or retires stale guidance. Current user requests, project instructions, and code take precedence over historical notes. Monorepo lessons identify the relevant component; worktree notes are revalidated against the current branch. Worker suggestions become lessons only after the lead verifies them.

Notes from Project A are not automatically applied to Project B. Project lessons do not rewrite shared skill instructions. Promoting a finding into shared guidance is a separate, explicitly requested skill change.

Updates happen during normal Maestro runs as evidence warrants them. This is maintained project context, not model retraining or a background job. See the [project memory rules](skills/maestro/references/project-memory.md) for storage, examples, and the update process.

## Track useful outcomes and protect quality

For substantive delegated work, Maestro can keep task class, model/effort, acceptance result, correction rounds, and verification evidence in `outcomes.md`. Failures and unresolved work are retained along with successes. Comparable observations can improve later assignments; one successful task does not establish a general routing rule.

When usage is available, include Astra's planning and review as well as workers, retries, and takeovers. Keep unknown or partial measurements explicit and avoid double-counting. Tokens, elapsed time, billed API cost, and Codex allowances are different measurements; API prices do not establish Codex quota savings.

Evaluate changes against representative tasks with consistent quality checks before claiming an improvement. The [routing guidance](skills/maestro/references/model-routing.md) explains this approach. Astra's final review and acceptance requirements remain in place.

## Keep project notes under project control

Lessons should contain brief technical findings and relative evidence references, without secrets, personal data, source dumps, or conversation transcripts. Maestro does not automatically stage, commit, or publish `.maestro/` files or change ignore rules. Follow each project's existing policy and deliberately choose whether to share its notes.

## Updates

Installed copies are snapshots. Changes to this repository do not update existing installations automatically. Ask Codex to refresh the installed skill from this repository when you want an update, and tell it to preserve any local changes. Project lessons live outside the installed skill and should be preserved when the skill is refreshed; do not upload them to this repository with a skill update.
