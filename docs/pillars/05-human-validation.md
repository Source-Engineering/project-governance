# Pillar 5  -  Human Validation Points

> Interactive, evidence-aware feedback, surfaced to the user, closing the loop in the same session.

## 2025 claim

Design interactive, evidence-aware feedback mechanisms that are also exposed to the end-user for a prompt's output  -  enabling the user to probe the model's reasoning, highlight relevant data points, suggest alternative context, and flag potential inconsistencies.

## 2026 status

- **Shipped, thumbs-only.** Every chat surface exposes thumbs up/down with the user's prompt attached.
- **Shipped, advanced.** Evidence-aware feedback (probe specific data points, not just the overall response) is the differentiator in Anthropic Workspace, ChatGPT tasks/memory inspector, and NotebookLM source-grounded answers.

## Stack placement

Layer 3 (business guardrails) and Layer 4 (audit trail) consume human validation signals. Layer 2 surfaces the feedback controls.

## Remaining gap

Feedback is collected. It is not yet returned to the model as a runtime signal in the same session. The loop is broken at the latency layer.

## What lives here when the framework ships

- The evidence-aware feedback primitive
- The same-session feedback loop contract
- The validator / segment-author approval workflow

Currently: placeholder.
