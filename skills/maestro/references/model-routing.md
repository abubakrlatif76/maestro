# Routing difficult worker assignments

Choose the worker model and effort together. Use ambiguity, component coupling, failure impact, and the strength of available checks. Astra at the user-selected `max` profile retains architectural decisions and final acceptance.

A well-specified parser fix with explicit inputs, outputs, compatibility rules, and testable edge cases can suit Luna at `high` or above. Extra reasoning can be useful when the boundary is settled and correctness is easy to check. Give the worker the decisive cases without prescribing an entire implementation.

A state or concurrency bug crossing components often needs Sol at `high` or above after Astra establishes the ownership and interface contracts. Small changes can still carry consequential risks. Keep unsettled design or policy decisions with Astra and narrow the implementation assignment before delegation.

Avoid trying every effort level serially. Start with the least expensive plausible model/effort for the risk and evidence available. Clarify a concrete mistake at the same settings; change effort or model when the observed failure warrants it. A worker handoff is evidence to inspect, not final acceptance.

## Use project outcomes to improve routing

Read only comparable records in the current project's `.maestro/outcomes.md` when they can inform a close decision. Follow [project-memory.md](project-memory.md) for scope and accounting. Include failures, correction rounds, takeovers, and verification gaps. Separate a bad assignment or missing contract from a worker's implementation failure.

Optimize the cost of an accepted result, including Astra's planning and review. A smaller worker that repeatedly needs repairs may cost more overall. Parallelism can reduce elapsed time while increasing total usage. Reuse sufficient checks and relevant context; do not cut acceptance criteria to make a cheaper route appear successful.

Evaluate a proposed routing change against representative tasks using consistent acceptance checks and cases outside the examples used to formulate it. Compare defects, corrections, total measured usage, and completion time where available. Preserve material failures in the comparison. Keep the lighter route only when it meets the required quality bar. Do not make a universal rule from one smoke test or a benchmark tie.

Published model guidance is a starting point. Use current [OpenAI model-selection guidance](https://developers.openai.com/api/docs/guides/model-selection) when external guidance is needed; routine assignments do not need fresh research. [Workflow evaluation guidance](https://developers.openai.com/api/docs/guides/agent-evals) describes using observed failures and repeatable tasks to evaluate changes. API prices and benchmark costs do not establish Codex allowance savings.
