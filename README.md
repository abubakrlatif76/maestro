# Maestro

Maestro is a reusable Codex skill for coordinating coding work across models. It keeps GPT-6 Astra at the center of planning, architecture, integration, and acceptance, while routing bounded implementation tasks to GPT-6 Luna or GPT-6 Sol when delegation is useful.

## How it works

The requested main-task profile is **GPT-6 Astra with `max` reasoning effort**. Select that model and effort in Codex yourself: a skill cannot change the running task's model, effort, or global settings. Maestro checks the runtime information it can see and reports any mismatch or missing confirmation. Work under another configuration is a disclosed fallback.

Before delegation, Astra maps the behavior, interfaces, risks, and evidence needed for acceptance. It chooses a worker model and effort together based on ambiguity, coupling, impact, and how well the result can be checked. Luna is a starting fit for clear, bounded work; Sol is a starting fit when work crosses components or needs more judgment. Astra keeps consequential design decisions, integration, and final acceptance.

Workers receive clear ownership, scope, acceptance criteria, and verification instructions. Astra inspects the delivered changes and evidence, then corrects, escalates, or takes over when needed. Assignment count follows the useful subtasks: there is no fixed total worker cap or requirement to use every model. Actual runtime capacity and task dependencies determine scheduling. Model and effort choices guide the workflow; they do not guarantee quality or savings.

## Install

Ask Codex:

```text
$skill-installer install Maestro from https://github.com/abubakrlatif76/maestro/tree/main/skills/maestro
```

Then invoke it with `$maestro` on a coding task. A newly installed skill is available starting with the next turn.

For a project-specific copy, manually copy `skills/maestro` into that project's `.agents/skills/maestro` directory.

## Updates

Installed copies are snapshots. Changes to this repository do not update existing installations automatically. Ask Codex to refresh the installed skill from this repository when you want an update, and tell it to preserve any local changes.
