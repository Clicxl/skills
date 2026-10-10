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
A GitHub issue. Always means a GitHub issue, never work in general.
_Avoid_: Ticket, bug (as a generic word)

**Review**:
An examination of a PR, or of another Session's work, that produces findings.
_Avoid_: Check, audit

**Blocker**:
An obstacle that stalled progress in a Session. Typically either review findings that must be fixed before a PR can merge, or a decision or input (such as IDs or a team-wide call) that must come from someone else.
_Avoid_: Issue, problem, bug

**Proof**:
Evidence produced during a Session that something works or fails: a test run's output, a CI result, a screenshot, or a manual check that was actually observed.
_Avoid_: Verification claim, "should work"
