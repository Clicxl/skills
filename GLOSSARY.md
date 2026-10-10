# Prompt Lib

A library of agent skills used for day-to-day engineering work: creating, resolving, and reporting on tracked work.

## Language

**Session**:
One agent conversation, from its first message to the point a skill is invoked. Usually centred on resolving, planning, or reviewing a single piece of work.
_Avoid_: Work period, day, sprint

**Work item**:
The unit of work a Session is about: an Issue or a Review. A Session usually has one.
_Avoid_: Task, ticket, "the issue" (when the kind is unknown)

**Issue**:
A GitHub issue, identified by its URL. Always means a GitHub issue, never work in general. Local tracker files are not Issues.
_Avoid_: Ticket, bug (as a generic word)

**Review**:
An examination of a PR, or of another Session's work, that produces findings.
_Avoid_: Check, audit

**Done-when**:
An Issue's acceptance criteria. An Issue is done only when every Done-when item is met with Proof.
_Avoid_: Definition of done, success criteria

**Action plan**:
The approved set of changes, and the tests or Proof that will show each one works, for resolving one Issue.
_Avoid_: Plan (alone), approach

**Finding**:
One problem a Review reports, ranked by Criticality.
_Avoid_: Flag, comment, issue

**Criticality**:
How urgently a Finding must be fixed: Urgent, High, Medium, or Low.
_Avoid_: Severity, priority

**Fix cycle**:
One pass back through the Action plan, tests, implementation, and (optionally) Review to address chosen Findings.
_Avoid_: Iteration, loop, retry

**Blocker**:
An obstacle that stalled progress in a Session. Typically either review findings that must be fixed before a PR can merge, or a decision or input (such as IDs or a team-wide call) that must come from someone else.
_Avoid_: Issue, problem, bug

**Proof**:
Evidence produced during a Session that something works or fails: a test run's output, a CI result, a screenshot, or a manual check that was actually observed.
_Avoid_: Verification claim, "should work"
