# Add hands-on mode toggle to feynman

Status: needs-triage

## What

Add a toggle to `thinking/feynman/SKILL.md` intake: "hands-on, or learn about it?" In hands-on mode a concept passes as `understood` only after the user has also *created* something with it: derived it, worked an example by hand, written a minimal implementation, or predicted an outcome and checked it.

## Why

"What I cannot create, I do not understand." A fluent explanation alone can still be knowing the name of a thing. Deferred from the first version to keep it small.

## Decided

- A toggle inside `feynman`, not a separate skill: the flow (intake, map, novice moves, hint ladder, ledger) is identical; only the pass criterion changes.
