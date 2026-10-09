# Source Engineering - Per-Channel Kanban Discipline

This file is the per-channel discipline rule for the Source Engineering discipline. It mirrors the pattern of the existing ECM rule for #enterprise-concepts-model and the nuel.otchere-com rule for the personal site channel.

## Rule

Every actionable item that arises on the Discord thread `CodingAgent / #source-engineering` (parent channel 1526858674822185010, this thread) **must produce a Kanboard card** on the Source Engineering Kanboard project, with column state matching the item's lifecycle. The rule runs autonomously without prompting.

## Channel binding

- **Guild:** 1496909480783249428
- **Parent channel:** 1526858674822185010
- **Discord source thread:** 1558168902519890112
- **GitHub repo:** https://github.com/emmanuel-a-otchere/source-engineering
- **GitHub Project:** https://github.com/users/emmanuel-a-otchere/projects/12

## Scope lock

The Source Engineering Kanboard project does **not** pull cards from channels outside its own scope. If a card emerges from a different channel (e.g. #enterprise-concepts-model, #world-semantic-foundation, #dea-catalog-*, #i-simulator, #astroforge, #systemone_stockapp, #github-technelabs), it routes to that channel's board instead.

Cross-cutting references (ECF framework, OpenDEAM vocabulary, ECM canon) remain admissible as inputs to Source Engineering cards; they do not transfer ownership of the card.

## Column states

| Column   | When an item lands here                                    |
|----------|------------------------------------------------------------|
| Backlog  | identified but not yet sized, no owner picked              |
| Ready    | sized and accepted, owner assigned, no in-flight work      |
| In Progress | an active worker is on it                                |
| In Review | a deliverable exists and is under review                   |
| Done     | the deliverable is shipped and accepted                    |
| Blocked  | the worker is stuck and waiting for human input             |

## GitHub mirror

In addition to Kanboard, each card is mirrored as a GitHub Project v2 item on `users/emmanuel-a-otchere/projects/12`. The card carries:

- the matching `Stage` field (Backlog / Ready / In Progress / In Review / Done / Blocked)
- a `Priority` field (P0 / P1 / P2 / P3)
- a backlink to the repo issue that originated it

## Recurring threads

When this Discord channel hosts recurring check-ins (e.g. weekly or daily standups for the discipline), each recurring thread produces one parent card and N sub-tasks on the Kanboard project, with `parents=[parent_id]` gating the sub-tasks.

## KB API credentials (record only - never commit live values)

The Kanboard REST API at `http://192.168.50.160:7000` requires either a session token or a personal API token. **Never commit the value to this file.** When the rule runs, the worker reads from the profile-level env (`~/.hermes/profiles/coder/.env`) under the names:

- `KB_URL` - base URL (default `http://192.168.50.160:7000`)
- `KB_USER` - either a username or a personal API token (preferred over basic auth)

If those env entries are absent, the worker stops and asks the operator rather than guessing.

## Audit + reflection

When a Source Engineering slice completes, the agent reflects in `MEMORY.md`:

- What shipped
- What fell short
- Which open question got answered
- Which new open question got opened

The discipline grows by closing questions, not by accumulating epics.

## Edit history

- 2026-10-10: Initial rule captured on discipline landing (Slice 0).
