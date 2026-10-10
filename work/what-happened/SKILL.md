---
name: what-happened
description: Summarise what happened in this session as a short spoken-style paragraph plus a status line, for reporting work to a manager or in a meeting.
disable-model-invocation: true
---

# What Happened

Report this **session** as a **paragraph** you could read aloud, then a **status line** for the facts behind it. The reader is a manager or CEO asking what work got done.

Output goes to chat only. Write no files.

## Work item

A **work item** is the unit of work the session is about:

- **Issue**: a GitHub issue. A PR is how an Issue gets delivered, never a work item of its own. Returning to a PR to fix review changes, in this session or a fresh one, is still work on the same Issue.
- **Review**: an examination of a PR, or of another session's work, that produced findings.

A **blocker** is an obstacle that stalled progress: review findings that must be fixed before a PR can merge, or a decision or input (such as IDs, or a call from the whole team) that must come from someone else.

## Steps

1. Read the session for each work item: what changed, what failed, PRs opened or updated, blockers hit, decisions taken, tests written, changed or run.
2. When an Issue or PR number is known and `gh` is available, check its live state with read-only commands only (`gh issue view`, `gh pr view`, `gh pr checks`). Label anything fetched live as "as of now". The session is the source of truth for what you did; `gh` only confirms current state.
3. Branch on what step 1 found:
   - **One work item**: continue to step 4.
   - **Several related work items** (they share an Issue or PR, or one exists because of the other): continue to step 4 as one report.
   - **Several unrelated work items**: ask which to report, as a multi-select. Write one paragraph per pick.
   - **No meaningful changes** (discussion or exploration only): ask whether to write a short report anyway. If yes, lead with what was learned or decided.
4. Write the paragraph, then the status line.

Done when every important change, failure, PR and blocker from step 1 appears in the paragraph or the status line.

## Paragraph

4 to 5 sentences, close to 50 words. The limit is soft: stretch it when an important item would otherwise drop out.

- Subject-less, past tense: "Fixed the login timeout…", never "I fixed…" and never "The session fixed…".
- Plain English. Name behaviour, not files.
- Explain an uncommon technical term in a short parenthetical. Explanations do not count toward the word limit. Common terms (CI failed, migration failed) get no explanation.
- A **resolved blocker** states the decision taken and why.
- An **unresolved blocker** states what is needed from the user to resolve it.
- Tests and proof: mention only failures and flags, with what failed and why. A run where everything passed gets no mention.
- Flag code that changed with no tests run: "not yet tested".

## Status line

Under the paragraph. Does not count toward the word limit.

`Status: <status> · Issue #<n> · PR #<n> · Flags: <flags>`

Include only the parts that exist.

Status for an Issue:

- **Resolved**: the acceptance criteria are met.
- **In progress**: work started and continues.
- **Planned**: a plan exists, no code yet.
- **Blocked**: a blocker is unresolved.

Status for a Review: **Approved**, **Changes requested** or **Commented**, plus the number of findings.

## Example
```
Fixed the mobile login timeout by extending the token refresh window (the time before a login expires). Opened a PR; review flagged a missing null check, which was fixed. CI failed on an unrelated payment test. The logout change has no tests yet. Merge is waiting on a second approval.

Status: In progress · Issue #45 · PR #112 · Flags: CI failing (unrelated), logout change untested
```
