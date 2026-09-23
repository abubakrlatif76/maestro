# Routing difficult worker assignments

The user-selected `gpt-6-astra` at `max` remains the orchestrator. Astra frames the problem, resolves uncertain design choices, sets acceptance criteria, integrates changes, and accepts the final code after inspecting the diff and evidence. A worker's self-report is a handoff, not acceptance. Select the worker **model and effort together** for each bounded assignment; a higher effort on Luna can be a better fit than a lower effort on Sol for some tasks, but neither name nor setting guarantees an outcome. Use the runtime's supported settings.

Judge the assignment by ambiguity, coupling to other components, impact of a wrong answer, ease of verifying the result, and observed results on comparable work. A well-specified parser fix with clear inputs, outputs, and testable edge cases can go to Luna at `high` or `max`: the reasoning may be intricate, but the task boundary and oracle are strong. Give the worker representative malformed inputs, compatibility expectations, and the decisive tests. If it cannot satisfy those checks, inspect whether the issue is a missing requirement, a bad interface assumption, or insufficient worker capability before changing settings.

A state or concurrency bug crossing components has a weaker oracle and may require changes to shared contracts. Astra should first map the state transitions and ownership boundaries, then give a bounded implementation to Sol at `high` or above when the scope supports it. A tiny permission check can carry severe failure impact despite touching one line. With an incomplete security oracle, keep policy and threat reasoning with Astra and assign the concrete implementation to Sol. File count alone does not make Luna the economical choice.

Avoid serially trying every effort level. Start with the least costly **plausible** model and effort for the risk profile, use a targeted correction at the same setting when the problem is concrete, and escalate only when the evidence points to a reasoning limit. If the hard part is an unresolved product or architecture decision, Astra should settle it before worker implementation. [OpenAI's model-selection guide](https://developers.openai.com/api/docs/guides/model-selection) provides general guidance; local acceptance evidence decides this workflow's routing.

## Dated evidence note — 2026-09-22

Published [same-family coding results](https://openai.com/index/introducing-gpt-6-sol-and-luna/#coding) show why benchmark ties are not general equivalence:

| Benchmark | Luna | Sol |
| --- | --- | --- |
| FrontierCode | `high` 37.3%, $0.067 | `low` 37.3%, $0.45 |
| DeepSWE | `high` 59.3%, $0.084 | `medium` 56.6%, $0.38 |
| DeepSWE | `max` 66.6%, $0.22 | `xhigh` 66.6%, $1 |

On FrontierCode, Luna `max` reaches 42.4%, below Sol `medium` at 45.9%. Standard short-context [API prices](https://developers.openai.com/api/docs/pricing) per million input/output tokens are Astra $10/$50, Sol $2/$10, and Luna $0.10/$0.50. These are API costs, not Codex quotas. [Reasoning tokens](https://developers.openai.com/api/docs/guides/reasoning) are billed as output even though they are not visible answer text; higher effort can consume more. The published examples do not promise equal quality or a fixed saving on this project.

For future calibration, record the task class, worker model and effort, acceptance result, corrections, and gaps in the verification evidence. Record time or cost only when the runtime exposes it. Compare similar task classes with similar oracles, then adjust the next assignment accordingly. A single successful smoke test or benchmark tie is too little evidence for a permanent routing rule.
