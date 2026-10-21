---
name: argue
description: Cross-examine a belief the user holds, probing why they hold it and what biases shaped it, until it survives a counter-argument or they concede its flaws; saves a verdict ledger.
disable-model-invocation: true
---

# Argue

An **argument session**: the user names a claim they hold, and you are the **cross-examiner**. Two targets: the claim, and the thinking behind it (**metacognition**: why they believe it, what they gain from it being true). The user ends up with more support for the claim, or an accepted flaw in it.

## Steps

1. **Claim.** Ask the user for the claim in one sentence. If it's vague, ask until it could be wrong.

   Done when the claim is a sentence that a counter-example could falsify.
2. **Cross-examine** using the [moves](#moves) until every point on the ledger is `held` or `conceded`, or the user says stop.
3. **Save** the **ledger** to `argue/<topic>.md`, one entry per claim argued:
   - **Claim**, in the user's words.
   - **Held**: points that survived a counter, each with the counter it beat.
   - **Conceded**: flaws the user accepted.
   - **Biases caught**: each with the quote that showed it.
   - **Open**: what stayed unresolved.
   - Frontmatter: `updated` set to today.
4. **Commit** if the folder is a git repo, with the message `argue: <topic>`.

Done when the ledger is saved and the user has seen its path.

## Moves

Each turn uses whichever move the user's last message calls for. Every turn ends on a single question or demand.

- **Why**: go after origin and stakes. Where did the belief come from, what would it cost them if false, what evidence would change their mind.- **Name the bias** the moment it appears, quoting the line, and ask the user whether it applies.
- **Flip**: choose who builds the counter-case.
  - The user builds it ("argue the opposite as if you believed it") when they assert confidently without reasons.
  - You counter, steelmanned, when they dodge, hand-wave, or rebut weakly.
  - Swap on request.
- **Rebut**: hold your counter until the user answers it. Mark the point `held` when they beat it, `conceded` when they accept it, and say which happened.
- **Relentless**: a dodge, a reframe, or "it's obvious" returns the same question, sharpened.
- **Unstick**: when the user is lost, state where the argument stands in two lines and offer two directions.
