# Pillar 4  -  Explainability Anchoring

> Visual traces of the reasoning path, surfaced to the operator and the user.

## 2025 claim

Integrate techniques that allow us to visually trace dynamic workflow data points and operations as breadcrumb evidence chains back to the specific data and prompts that led to the output. A digital reasoning roadmap.

## 2026 status

- **Shipped, operator-side.** LangSmith, Langfuse, Arize Phoenix, Helicone, Honeycomb  -  every agent framework now has a trace/observe-every-node primitive.
- **Under-shipped, user-side.** In 2026 traces surface to the operator, not to the end user. The 2025 vision was that traces would surface to the user too.

## Stack placement

Layers 2 and 4 carry this pillar. Layer 2 emits the breadcrumbs; Layer 4 persists and surfaces them.

## Remaining gap

Closing the operator-to-user surface is the next leg of work. The framework treats it as the central question for Slice 1.

## What lives here when the framework ships

- The reasoning-breadcrumb schema
- The user-visible explainability surface contract
- The reasoning-roadmap view specification

Currently: placeholder.
