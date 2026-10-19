---
name: distill
description: Turn the raw captures in a notes vault's inbox into organised atomic notes, updated skill hubs, tracker issues and a short digest.
disable-model-invocation: true
---

# Distill

Turn the **inbox** (raw, unformatted captures: dictation, pasted text, photos) into the vault's notes. The owner captured in flow; your job is that they never have to format, title, file or link anything.

The vault's **conventions file** (`CLAUDE.md`, or `AGENTS.md`, at the vault root) defines the layout, note types, templates, voice, triage, tracking and git rules. This skill is the procedure; the conventions file is the rulebook. Where they differ, the conventions file wins.

## Steps

1. **Load the map.** Read the conventions file if it is not already in context, then the root index it names. Read nothing else yet.
2. **Read the inbox.** Read the dump file and any other file in the inbox folder. Look at every embedded image: transcribe handwriting word for word, and describe a diagram in enough detail to rebuild it. If the inbox is empty, say so and stop.
3. **Split into pieces.** A **piece** is one idea, item, task or event; a thought tucked inside another piece ("…it made me think that time is the only real currency") is its own piece. Keep each piece's exact words, and its date: from a heading or timestamp in the dump, else today, shifted by any relative word in the piece ("last night", "yesterday").
4. **Route each piece** to exactly one of:
   - **learning**: something clicked, or a struggle (solved or not)
   - **media**: a book, movie, series, video, podcast, article or course consumed
   - **idea**: a project idea not yet started; append it to the end of the ideas note as `- YYYY-MM-DD — <idea>`
   - **project**: progress, a decision or a task on an existing project; or a new project being started
   - **goal**: a goal set, changed or reached
   - **experiment**: one started, updated or ended. Same hypothesis as an existing experiment → update that note; otherwise a new note that links the related one
   - **habit**: a habit started, changed or dropped
   - **thought**: a question or idea worth sparring about later; create its essay note now with `status: seed`, the piece quoted
   - **private**: a personal detail about another person (birthday, likes, health, relationships, anything the conventions file marks private)
   - **noise**
5. **Find each target before writing.** Navigate top-down as the conventions file says: root index → field index → hub. Before creating a concept note, `Glob` for an existing one by two or three keywords; extend it rather than duplicate it. Apply the triage rules to every learning piece.
6. **Write.** Create new notes from their templates with the frontmatter filled. In every touched skill hub: add the Log line, update Stuck on, list new concepts under Concepts, set `last_touched` to the piece's date and `status: active` (a hub is active once any piece lands in it). A project that gets a progress piece becomes `active` too. Add new hubs to their field index under the right discipline, and new fields, paths, projects and experiments to the root index. Update the status column of any Path that lists a touched hub, and set the Path's own `status: active` once any of its hubs is active. Follow the voice rules on every line you write.
7. **Track.** For project and goal pieces, use `gh` as the conventions file's tracking rules say: search open issues first, add a task checkbox to an existing issue when one fits, and create an issue only for a step big enough to earn one. Then refresh every active project note's tracker properties and the goals note's progress column from `gh`. If `gh` fails, list the intended tracker changes in the digest instead.
8. **Refresh the Now note** from what you touched plus its current content: active skills, projects, running experiments, what's being consumed, open questions (essay seeds), and current Stuck on items. Never scan the vault for this.
9. **Empty the inbox.** Append the raw dump, verbatim except for the private pieces, to the archive dump file for today (create it if missing). Private pieces never enter the archive, a note, or a commit. Then clear the dump file, keeping only a `## Left for you` section holding the private pieces, untouched.
10. **Commit** as the conventions file says.
11. **Report the digest** in chat, short enough to read on a phone, with these headings (skip empty ones):
    - **Created**: new notes, as links
    - **Updated**: touched notes with what changed, grouped where several share a change
    - **Tracker**: issues created, tasks added, milestones changed
    - **Dropped**: numbered, so the owner can reply "keep 2" to rescue one
    - **Left for you**: count of private pieces left in the inbox
    - **Questions**: only for a piece that could belong to two notes where a wrong guess would mislead. Otherwise choose and say what you chose under Updated.

Done when every piece from step 3 appears exactly once in the digest (as created, updated, tracked, dropped or left for you) and the dump file holds nothing but the "Left for you" section.
