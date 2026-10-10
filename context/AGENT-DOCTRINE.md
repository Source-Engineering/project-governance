# Agent Doctrine (Source Engineering)

This file binds the Source Engineering repo to the per-channel kanban discipline. It is the per-repo companion to `.github/discipline-rule.md`. Hermes profile root blocks writes to AGENTS.md (consent-prompt timeout), so this file lives at `context/AGENT-DOCTRINE.md` per the documented convention.

## Where work lives

- **Repo:** https://github.com/Source-Engineering/source-engineering
- **Local clone:** /home/hermes/Projects/source-engineering
- **Kanboard project:** http://192.168.50.160:7000/board/13 (id 13)
- **Snapshot doc:** /home/hermes/.hermes/profiles/coder/kanban/se-kanban-snapshot-2026-10-10.md
- **Skill:** source-engineering-kanban-discipline

## Channel binding

- **Discord guild:** 1496909480783249428
- **Parent channel:** 1526858674822185010
- **Source thread (this repo's bootstrap):** 1558169004336742480

## Cardinal rule

Every action, CR, ADR, test, task, activity, recon, decision on a Source Engineering Discord message produces a kanban card on project 13, with column state matching the lifecycle, autonomously. The next agent on this repo inherits this via the skill, not via chat memory.

## Lifecycle triggers

- Card created, not yet started: Backlog (52)
- First commit on the work: Work in progress (54)
- PR opened or staging push done: card stays in WIP, comment notes the PR
- Acceptance ritual complete: Done (55)
- User pauses to decide: keep in WIP, add `blocker` tag, do not auto-advance
- Cron or check-in finds the card stuck: add `blocker` tag, leave column unchanged

## Conventions (cardinal author rule)

- GitHub artefacts: no en-dashes (U+2013), no em-dashes (U+2014), no U+2E3B; use ASCII hyphens or sentence punctuation
- No triple-semicolons in prose; the divider is `;;` (two semicolons)
- Conventional commits: `feat:`, `fix:`, `refactor:`, `docs:`, `test:`, `chore:`
- License: Apache-2.0

## Snapshot doc discipline

After every card move, append a one-line dated note to the snapshot doc with: timestamp, old column, new column, triggering event (commit SHA, merge PR, accept, blocker reason). The diff between dated siblings is the agent's audit trail.

## Related

- `.github/discipline-rule.md` - per-channel rule (the doctrine this file points at)
- `.github/epics/*.md` - WBS epic specs (Pillars, Architecture, Reference Implementation, Validation Domains)
- `/home/hermes/.hermes/profiles/coder/kanban/se-kanban-snapshot-2026-10-10.md` - snapshot doc
- Skill `source-engineering-kanban-discipline` - runtime binding for the next agent
