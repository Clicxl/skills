---
name: reflect
description: Review what a notes vault shows about its owner (patterns, habits, goals, skill status) and propose edits to their purpose note.
disable-model-invocation: true
---

# Reflect

A periodic **self-assessment** drawn from evidence: what the owner keeps learning, consuming, thinking about and dropping. Run it monthly, or whenever the owner feels lost.

The vault's **conventions file** (`CLAUDE.md` or `AGENTS.md`) names the self notes (patterns, habits, goals, purpose, now), the index and the tracker. Follow it.

## Steps

1. **Gather evidence since the last reflect** (the patterns note's `updated` date; everything, if it has none):
   - the root index, Now, Patterns, Habits, Goals and Purpose notes
   - skill-hub frontmatter only, via `Grep` for `status:` and `last_touched:`
   - essay and media frontmatter dated after the cutoff
   - the archived dump files dated after the cutoff (this is the one skill that reads them)
2. **Update Patterns.** For each recurring theme (a subject, a way of working, a question that keeps returning, something started and dropped), write one line with two or more evidence links. Strengthen themes that recur and mark fading ones `(fading since YYYY-MM-DD)` rather than deleting them.
3. **Age skill hubs.** Unless the conventions file says otherwise: set `active` to `paused` after 30 days untouched, and `paused` to `dormant` after 90. Mirror the changes in Path tables and the root index.
4. **Update Habits** from habit mentions in the evidence: new, changed, or dropped (keep dropped rows, with the date and reason).
5. **Refresh Goals** progress from the tracker (`gh api repos/<repo>/milestones`). Flag goals with no progress since the cutoff.
6. **Propose Purpose edits.** Show the owner the exact lines you would add or change in the purpose note, each tied to a pattern. Apply them only when the owner says yes.
7. **Set `updated`** on every self note you changed, commit as the conventions file says, and report in chat: the top three patterns, the changes made, and the proposed purpose edits.

Done when every theme in Patterns has evidence links dated within or before the cutoff, every hub's status matches its `last_touched`, and the purpose proposal has been shown.
