# Pillar 2  -  Contextual Signature Mapping

> The model's runtime context, made visible and tunable.

## 2025 claim

A feedback loop between user context (history, location, time, model parameters) and the answer, with the parameters tunable per call.

## 2026 status

- **Shipped, operator-side.** The runtime knobs exist: prompt cache, structured tools, top-p, temperature, thinkingBudget.
- **Under-shipped, user-side.** The 2025 vision was that the knobs surface to the user, not just the operator. In 2026 most providers expose them only as developer settings.

## Stack placement

Layer 2 (runtime validation) is the home for context engineering. The framework requires Layer 2 to surface every knob back to the user, with rationale.

## Remaining gap

Per-segment calibration. A model can be calibrated on its evaluation set and miscalibrated on a new customer segment. Context engineering alone does not surface that drift.

## What lives here when the framework ships

- The context-engineering interface contract
- The user-visible knob surface
- The per-segment drift report

Currently: placeholder.
