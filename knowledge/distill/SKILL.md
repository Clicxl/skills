---
name: distill
description: Turn the raw captures in a notes vault's inbox into organised atomic notes, updated skill hubs, tracker issues and a short digest.
disable-model-invocation: true
---

# Distill

Turn the vault's **inbox** (raw captures: dictation, pasted text, photos, handwriting) into filed notes. The owner captured in flow; you do all the formatting, titling, filing and linking.

The vault's **conventions file** (`CLAUDE.md` or `AGENTS.md` at the vault root) is the rulebook: layout, note types, templates, voice, triage, tracker and git rules. This skill is the procedure. Where they differ, the conventions file wins.

## Steps

1. **Load the map.** Read the conventions file (if it is not already in context) and the root index it names. Done when you know where the inbox, archive, indexes and templates live.
2. **Read the inbox**: the dump file and every other file in the inbox folder. Transcribe handwriting verbatim, and describe each diagram in enough detail to rebuild it. If the inbox is empty, say so and stop.
3. **Build the ledger.** Split the inbox into **pieces**, one idea, item, task or event each. A thought tucked inside another piece ("…it made me think that time is the only real currency") is its own piece. Number each piece in the **ledger** with its exact words and its date: from a heading or timestamp in the dump, else today, shifted by any relative word in the piece ("last night", "yesterday"). Done when every line of the inbox belongs to a ledger entry.
4. **Route** each piece to exactly one of the [Routes](#routes), and record the route in its ledger entry.
5. **Find each target top-down**: root index → field index → hub, as the conventions file says. Before creating a concept note, `Glob` for it by two or three keywords and extend the existing note when one turns up. Apply the triage rules to every learning piece.
6. **Write** each piece as its route says. Create new notes from their templates with the frontmatter filled, and follow the voice rules on every line. Then do the [index upkeep](#index-upkeep).
7. **Track** project and goal pieces with `gh`, as the conventions file's tracking rules say: search open issues first, add a task checkbox to an issue that fits, and create an issue only for a step big enough to earn one. Then refresh every active project note's tracker properties and the goals note's progress column from `gh`. If `gh` fails, list the intended tracker changes in the digest.
8. **Refresh the Now note** from what you touched plus its current content: active skills, projects, running experiments, what's being consumed, open questions (essay seeds) and current Stuck on items.
9. **Empty the inbox.** Append the raw dump, verbatim minus the private pieces, to today's archive dump file (create it if missing). Then clear the dump file down to a `## Left for you` section holding the private pieces, untouched.
10. **Commit** as the conventions file says.
11. **Report the [digest](#digest)** in chat.

Done when every ledger entry appears exactly once in the digest and the dump file holds only the `## Left for you` section.

## Routes

The conventions file gives each route's note type and template; these are the rules on top of it.

- **learning**: something clicked, or a struggle (solved or not). In its skill hub: add the Log line, update Stuck on, list new concepts under Concepts, set `last_touched` to the piece's date and `status: active`.
- **media**: a book, movie, series, video, podcast, article or course consumed.
- **idea**: a project idea not yet started. Append `- YYYY-MM-DD — <idea>` to the end of the ideas note.
- **project**: progress, a decision or a task on an existing project, or a new project starting. A progress piece sets the project `status: active`. Tracked in step 7.
- **goal**: a goal set, changed or reached. Tracked in step 7.
- **experiment**: one started, updated or ended. Same hypothesis as an existing experiment → update that note; otherwise create a new note that links the related one.
- **habit**: a habit started, changed or dropped.
- **thought**: a question or idea worth sparring about later. Create its essay note now with `status: seed`, the piece quoted.
- **private**: a personal detail about another person (birthday, likes, health, relationships, anything the conventions file marks private). It lives only in the inbox's `## Left for you` section: keep it out of every note, the archive and every commit.
- **drop**: noise. It lands only in the digest's Dropped list.

## Index upkeep

- Add new hubs to their field index under the right discipline.
- Add new fields, paths, projects and experiments to the root index.
- In every Path that lists a touched hub, update the status column, and set the Path's own `status: active` once any of its hubs is active.

## Digest

Short enough to read on a phone, under these headings (skip empty ones):

- **Created**: new notes, as links
- **Updated**: touched notes with what changed, grouped where several share a change
- **Tracker**: issues created, tasks added, milestones changed
- **Dropped**: numbered, so the owner can reply "keep 2" to rescue one
- **Left for you**: the count of private pieces left in the inbox
- **Questions**: only for a piece that could belong to two notes where a wrong guess would mislead. For every other piece, choose and say what you chose under Updated.
