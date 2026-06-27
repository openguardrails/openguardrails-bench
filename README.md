# openguardrails-bench

**The neutral leaderboard for AI agent safety & security detectors.**

This is the part of OpenGuardrails that OpenTelemetry has no analogue for. OGR
does not build detection capability — it **referees**. Any
[OGR-conformant](https://github.com/openguardrails/openguardrails-spec) detector
(config-based or model-based) can be run against shared corpora here and ranked
on a level field.

> Your homepage today says "OpenGuardrails beats LlamaGuard / Qwen3Guard." Under
> this positioning OGR is no longer a contestant in that table — it **runs** the
> table, and LlamaGuard, Qwen3Guard, OpenAI, Anthropic, and every vendor appear
> in it.

## Why a benchmark is the wedge

- A `score` from one vendor is **not** comparable to another's — except through
  a common harness on common data. That incomparability is the entire reason the
  leaderboard must exist, and why it is defensible neutral ground.
- It gives users a reason to adopt the standard: *pick vendors by measured
  ability, compose them, switch freely.*
- It gives vendors a reason to adopt the standard: *one integration, ranked
  distribution to every agent.*

## Structure (planned)

```
suites/
  security/
    prompt_injection/      # direct + indirect (tool-result / web / MCP origin)
    malicious_command/     # pipe-to-shell, obfuscation, destructive ops
    data_exfiltration/
    secret_leak/
    tool_poisoning/        # malicious MCP/tool DEFINITIONS
  safety/
    toxicity/  self_harm/  pii/  ...
harness/                   # runs any OGR-conformant detector over a suite
  run.py                   # detector → GuardEvents → Verdicts → scored
leaderboard/               # published results (feeds openguardrails.com)
```

Each case is a `GuardEvent` (often with `provenance`, since indirect injection is
only meaningful with an untrusted origin) plus a labeled expected outcome. The
harness reports per-category **precision / recall / F1**, latency, and
calibration — the same axes vendors compete on.

## Conformance vs. benchmark

- **Conformance** (separate, pass/fail): does the detector correctly accept a
  `GuardEvent` and return a schema-valid `Verdict`? A prerequisite to being
  listed.
- **Benchmark** (this repo, ranked): how *good* is it?

## Status

`v0` — scaffolding. Seed suites and the harness interface land next, built on the
`GuardEvent`/`Verdict` types proven in
[`openguardrails-poc`](https://github.com/openguardrails/openguardrails-poc).
Submissions and governance of the corpora will be foundation-neutral.
