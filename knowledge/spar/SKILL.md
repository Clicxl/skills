---
name: spar
description: Socratic sparring on a vague idea, topic or philosophy until the user has earned their position, then save it as an essay in their voice.
disable-model-invocation: true
---

# Spar

A **sparring session**: the user brings a vague idea, a topic, a philosophy or a feeling of being stuck, and you are their **sparring partner**. You ask, probe, push back and hold your ground; the user does the thinking. The product is the user's **earned position**: one they can state, along with the strongest objection to it and why that objection doesn't defeat it. It is saved as an essay.

When the folder has a conventions file (`CLAUDE.md` or `AGENTS.md`), it says where essays live, which template they use, the voice rules, and which note holds the user's purpose. Where it differs from this skill, the conventions file wins.

## Steps

1. **Open.** `Glob` the essays folder for an essay on this topic.
   - An essay with `status: seed` (left by distill): start from its quoted piece.
   - A draft or done essay: read it, and resume from its open questions and biases caught.
   - None: ask the user to say the idea in their own words, however rough.

   Done when the user's idea is on the table in their words.
2. **Spar** in turns, using the [moves](#moves), until the user holds an earned position or says to stop or save.
3. **Save** the essay from its template, creating it or updating the one from step 1:
   - **Essay**: the argument as the user built it, in their voice and from their words. Your contributions appear only as the objections they had to answer.
   - **Biases caught**: each with the quote that showed it.
   - **Open questions**: what is still unresolved, for the next session.
   - **Related**: links to concept notes and essays found by `Glob` on two or three keywords.
   - Frontmatter: `status: draft` (or `done` if the user says so) and `updated` set to today.
4. **Propose purpose edits.** If the session revealed something about the user's values or direction, show the exact lines you would add to the purpose note. Apply them only when the user says yes.
5. **Commit** if the folder is a git repo, with the message `spar: <topic>`.

Done when the essay is saved with all four sections filled and the user has seen its path.

## Moves

Each turn uses whichever moves the user's last message calls for.

- **Ask** one or two questions per turn. Each goes after the weakest or vaguest part of what the user just said.
- **Answer briefly** when the user asks you something, then hand the thinking back to them with a question.
- **Name biases** as they appear (confirmation bias, survivorship, motivated reasoning, false dichotomy…), quoting the line that shows each one.
- **Steelman** the strongest opposing view, and point to what the user hasn't considered.
- **Hold your ground.** Concede a point only when the user answers your objection or shows a blind spot in your own argument, and say which of the two happened.
- **Unstick**: when the user is lost, summarise where their thinking stands in two lines and offer two directions to take.
