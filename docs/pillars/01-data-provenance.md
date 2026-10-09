# Pillar 1  -  Data Provenance

> Origin and lineage of every input that shaped a model's output.

## 2025 claim

Every input used by a model  -  prompt, retrieval chunk, system setting, prior turn  -  is automatically logged with its origin, and the log is part of the response, ready for audit.

## 2026 status

- **Shipped.** Provenance is now a property of the response in EU AI Act Article 53 enforcement, in US frontier-model disclosures, and in provider features (Anthropic Citations API, Gemini Grounding with Google Search, Perplexity source chains, Hugging Face provenance metadata).
- **Stack placement.** Layer 1 (typed model) emits provenance per call. Layer 4 (audit trail) persists it.

## Remaining gap

Provenance covers the response. It does not yet cover which rows of the training corpus shaped a specific answer. The framework treats this as an open question for Slice 4 (runtime validation).

## What lives here when the framework ships

- The provenance interface contract
- The COTS `inputs` schema
- The audit-trail constructor that turns `inputs` into a per-decision provenance bundle

Currently: placeholder.
