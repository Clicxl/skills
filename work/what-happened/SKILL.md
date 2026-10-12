---
name: what-happened
description: Summarise what happened in this session as a research-paper-style title, a short abstract, and a results list, for reporting work to a manager or in a meeting.
disable-model-invocation: true
---

# What Happened

Report this **session** like the opening of a research paper: a **title**, an **abstract** you could read aloud, then a **results** list for the facts behind it. The reader is a manager or CEO asking what work got done.

The report goes to chat. Write no files.

## Work item

A **work item** is the unit of work the session is about:

- **Issue**: a GitHub issue. A PR is how an Issue gets delivered, never a work item of its own. Returning to a PR to fix review changes, in this session or a fresh one, is still work on the same Issue.
- **Review**: an examination of a PR, or of another session's work, that produced findings.
- **Stray work**: any other work item with no GitHub Issue ID: a direct push to main, work on a local tracker ticket, a config or dependency chore.

A **blocker** is an obstacle that stalled progress: review findings that must be fixed before a PR can merge, or a decision or input (such as IDs, or a call from the whole team) that must come from someone else.

## Steps

1. Read the session for each work item: what changed, what failed, PRs opened or updated, blockers hit, decisions taken, tests written, changed or run.
2. When an Issue or PR number is known and `gh` is available, read its live state with read-only commands only (`gh issue view`, `gh pr view`, `gh pr checks`), and take each Issue and PR URL from them. Live state decides Status, Issue and PR state, and CI flags. The session decides what was done and why.
3. Branch on what step 1 found:
   - **One work item**: continue to step 4.
   - **Several related work items** (they share an Issue or PR, or one exists because of the other): continue to step 4 as one report.
   - **Several unrelated work items**: ask which to report, as a multi-select. Write a title, abstract and results for each pick.
   - **Stray work**: ask the user to choose "Report without an Issue" or "Leave it out", and suggest in one line that they can create an Issue with `/create-issue`. Create no Issue yourself; stay read-only.
   - **No meaningful changes** (discussion or exploration only): ask whether to write a short report anyway. If yes, lead with what was learned or decided.
4. Write the title, the abstract, then the results.

Done when every important change and blocker from step 1 appears in the abstract, and every PR, failure and flag appears in the results.

## Title

A paper-style noun phrase in Title Case, 3 to 4 words, in bold: "Login Timeout Window Extension". Plain English naming the behaviour, free of dates and issue numbers.

## Abstract

3 to 4 sentences, 25 to 30 words. The limit covers the abstract only, leaving out the title, the results and parenthetical explanations.

When the changes cannot fit in 3 to 4 sentences of about 30 words, write the abstract as a bullet list instead: one bullet per change, one sentence each, no cap on bullet count. A blocker goes in as the last bullet.

- Subject-less, past tense: start with the verb, "Fixed the login timeout…".
- Carry the changes and any blocker.
- A **resolved blocker** states the decision taken and why.
- An **unresolved blocker** states what is needed from the user to resolve it.
- Plain English. Name behaviour, not files.
- Explain an uncommon technical term in a short parenthetical. Common terms (CI failed, migration failed) get no explanation.
- Failures and "not yet tested" go in Flags. They enter the abstract only when a failure is the main story of the session.

## Results

A markdown bullet list under the abstract with bold labels, one bullet per label. Leave out any label with nothing to report. Separate multiple values on one line with ` | `.

```markdown
- **Status:** In progress
- **Issue:** #45
- **PRs:** #112 | #118
- **Flags:** CI failing (unrelated) | logout change untested
```

- Render each Issue and PR ID as a link to its GitHub page, `[#45](url)`. Use bare `#45` only when the URL is unknown.
- A local ticket's ID goes under **Issue** as plain text, unlinked.
- **Flags** names each test failure, CI failure and untested change in a few words. Give the details only when the user asks.
  - Passing runs stay out.
  - Code that changed with no tests run is flagged "not yet tested".

Status for an Issue or stray work:

- **Resolved**: the acceptance criteria are met.
- **In progress**: work started and continues.
- **Planned**: a plan exists, no code yet.
- **Blocked**: a blocker is unresolved.

Status for a Review: the verdict (**Approved**, **Changes requested** or **Commented**) plus the number of findings.

## Example

```markdown
**Login Timeout Window Extension**

Extended the mobile login timeout so sessions stop expiring early. Fixed a missing null check flagged in review. Both PRs are waiting on a second approval.

- **Status:** In progress
- **Issue:** [#45](https://github.com/acme/app/issues/45)
- **PRs:** [#112](https://github.com/acme/app/pull/112) | [#118](https://github.com/acme/app/pull/118)
- **Flags:** CI failing (unrelated) | logout change untested
```

Output the report as plain markdown in chat.
