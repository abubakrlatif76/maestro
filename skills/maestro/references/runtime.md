# Runtime selection and handoffs

Use the active tool schemas as the source of truth. These notes describe common Codex interfaces; they do not create tools or change account access.

## Explicit worker selection

When `collaboration.spawn_agent` is available with `model`, `reasoning_effort`, and `fork_turns`, explicitly set `model` to the selected `"gpt-6-luna"` or `"gpt-6-sol"`, `reasoning_effort` to the chosen supported effort, and `fork_turns: "none"`. Include the necessary context in the task brief. In this interface, a full-history fork inherits the parent's model and effort and cannot accept overrides. A short partial fork is possible when genuinely needed and supported.

The main task's requested profile is `gpt-6-astra` / `max`. Worker spawn parameters do not configure the main task. Neither the skill's frontmatter nor `agents/openai.yaml` has a model/effort enforcement field. Do not invent one or start a nested Astra manager to conceal a root mismatch. Report absent confirmation or a known mismatch accurately.

For other delegation tools, use their documented equivalent model and effort fields. Do not paste unsupported parameters. A custom agent configuration can override spawn settings: avoid a role pinned to a conflicting model or effort. Prefer an explicit per-worker selection over changing global defaults.

Check returned model/effort metadata when provided. If absent, describe the settings as requested rather than independently confirmed. Never infer the model from an agent's self-description. If a request is rejected, resolve the reported compatibility problem or disclose a supported alternative, such as Sol for unavailable Luna, before using it; do not retry with an unspecified model. Use local work when delegation itself is unavailable. Published API effort values may differ from those exposed by a particular Codex runtime; the live schema wins.

## Scheduling capacity

Read the active runtime's capacity rules: a limit may count active turns across the entire agent tree or open worker sessions, and may include the main agent. Do not hard-code a worker count or change global limits to bypass capacity. Schedule ready subtasks as slots become available. When capacity is temporarily full, queue work rather than treating delegation as unsupported or repeatedly retrying spawns. Reuse or close completed workers only through supported tools when session limits require it.

## Continuing work

In the collaboration interface, `send_message` steers an active worker and `followup_task` starts or resumes a worker turn. Neither exposes model or effort changes. Use these for corrections at the same settings. For a changed setting, finish or interrupt the existing worker, confirm it is no longer writing, then spawn a replacement with explicit settings and a concise handoff. An interruption is not a rollback: inspect existing changes first.

Use the runtime's result/wait mechanisms and keep a single owner for writable files. Prefer a shared checkout with disjoint ownership when the runtime shares files; isolated worktrees require explicit integration before verification. Do not confuse subagents with tools that create separate user-visible tasks.

Official reference: [Codex subagents](https://learn.chatgpt.com/docs/agent-configuration/subagents). Recheck documentation only if actual runtime behavior requires it.
