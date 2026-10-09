# Pillar 3  -  Chain of Evidence

> The structured audit trail that links output back to inputs and reasoning steps.

## 2025 claim

For every model output, automatically generate a chain of evidence  -  supporting data points and contextual factors, linked to the initial data and prompts. Structured summaries or knowledge graphs.

## 2026 status

- **Shipped.** The "System One" pattern (e.g. Jev from TypeSafe AI) makes the chain of evidence structurally true: a typed question with a declared answer shape is, by construction, an evidence-anchored decision.
- **Generalized.** Same pattern ships under different names in OpenAI's Decisions API (early Oct 2026) and in the LangChain / LlamaIndex adapter layer.

## Stack placement

Layers 1, 3, and 4 share this pillar's responsibility. Layer 1 emits; Layer 3 references; Layer 4 persists.

## Remaining gap

Evidence is structural. Judgment is contextual. A decision that fits every declared option can still be the wrong decision for the situation. The framework separates evidence from judgment by routing the two through different layers.

## What lives here when the framework ships

- The COTS `evidence` schema
- The evidence-aware feedback primitive (Layer 2 surface)
- The audit-trail evidence chain constructor

Currently: placeholder.
