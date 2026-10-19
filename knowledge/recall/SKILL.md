---
name: recall
description: Quiz the user on a skill or topic using only their own notes, then log how it went.
disable-model-invocation: true
---

# Recall

**Retrieval practice** from the user's own notes: the questions come from what they wrote, so the quiz tests what they actually learned, not general knowledge.

If a conventions file (`CLAUDE.md` or `AGENTS.md`) is present, it says how to find a skill hub cheaply and how hub Log lines are written. Follow it.

## Steps

1. **Find the material.** Locate the skill hub for the topic the user named (index → field index → hub, or `Glob` by name). Read the hub and the concept notes listed under its Concepts, and nothing else. If no hub or notes exist, say so and stop.
2. **Ask five questions, one at a time**, waiting for each answer. Mix three kinds, easiest first:
   - **explain**: why something works
   - **apply**: use an idea on a new case
   - **connect**: link it to another skill or field the user has notes on
3. **Mark each answer** as right, partly right or wrong, citing the note it comes from, and give the missing piece in one or two lines.
4. **Close** with one line on what's strong and one line on what's weak.
5. **Log it** on the hub's Log: `- YYYY-MM-DD — recall: <score>/5, weak on <topic>`. Commit if the folder is a git repo.

Done when five questions are marked (or the user stopped early) and the Log line is written.
