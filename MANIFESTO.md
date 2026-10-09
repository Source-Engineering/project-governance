# Source Engineering  -  Manifesto

> A discipline for grounding AI-based decisions with integrity.

## Why this exists

Large language models produce confident answers. Confidence is not the same as justification. In high-stakes domains  -  legal, medical, financial, regulatory  -  a structurally valid answer can be the wrong answer. The gap between "the model answered" and "I can act on the answer" is the hesitation factor.

Source Engineering is the discipline that closes the hesitation factor by treating model reasoning as **evidence-anchored**, not merely produced.

## The three principles

### 1. Provenance is a property of the response

Every input that shaped an output  -  prompt, retrieval chunk, system setting, prior turn, calibrated parameter  -  is logged at the time of the call and surfaces with the response. Not as an afterthought. Not in a separate dashboard. As part of the answer itself.

### 2. Context is a runtime signal

Context engineering  -  temperature, top-p, prompt cache state, tool budget, retrieval depth  -  is a public interface, not a hidden knob. The user sees what the model sees. The user can adjust it. The user can ask *why it was set this way*.

### 3. Judgment is separate from evidence

A model can return a decision that fits every declared option and still be the wrong decision for the situation. The evidence chain proves what the model considered; the judgment layer decides whether the decision holds for this user, this moment, this stake. The two must be separable surfaces.

## What this discipline is not

- It is not prompt engineering. Prompt engineering optimizes the question; Source Engineering optimizes the auditability of the answer.
- It is not chain-of-thought alone. CoT can produce plausible traces; Source Engineering requires the trace to be evidence-anchored.
- It is not model-side explainability. Model-side explainability explains weights and activations; Source Engineering explains the journey from input to decision in domain terms.
- It is not trust-by-policy. "Trust the provider" is not engineering. Source Engineering earns trust by surfacing enough for the user to verify, not by asking the user to assume.

## The chain of orchestrable and traceable sources (COTS)

A Source Engineering response carries a COTS  -  a structured, machine-readable bundle containing:

- **Inputs**: every data point that shaped the response, with provenance metadata
- **Context**: the runtime parameters set for this call, with their rationale
- **Decisions**: every decision point the workflow took, with the option set and the rationale
- **Evidence**: the chain linking each output to its supporting data and reasoning step
- **Validation**: the feedback surfaces exposed back to the user for this response

The COTS is the contract. If a response does not carry one, it is not a Source Engineering response.

## Working principles for contributors

- **No silent pillars.** Every claim in this discipline must trace to a working artifact or an explicitly labeled open question.
- **Reversible commitments.** Every interface proposal is a proposal until it ships. Once it ships, downgrades get a CR.
- **Domain first.** Architectures that work for one high-stakes domain do not assume others. Each domain writes its own COTS profile.
- **Human in the loop, but not in the way.** Feedback surfaces are designed to be evidence-aware and latency-tolerating, not to require a human at every step.

## Open questions

- Calibration drift across customer segments  -  how the runtime layer surfaces per-segment drift without leaking segment identity.
- Latency vs. auditability  -  the cost of carrying a full COTS at every call, and where amortization is possible.
- Legal-document summarization prototype  -  the in-progress validation domain; results feed back into the framework's evidence schemas.

The discipline grows where these questions get answered. The roadmap records which slice answers which question.
