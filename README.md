# Prompt Lib

A library of explicit-invocation Agent Skills for day-to-day engineering work: writing issues, resolving them, and reporting what got done. Each skill is a folder with a `SKILL.md`, invoked by name.

## Skills

The skills live in [`work/`](work/README.md):

- `create-issue`: draft or publish a tracker issue
- `resolve-issue`: diagnose, fix, verify, and optionally deliver an issue
- `what-happened`: summarise the current session as a short paragraph plus a status line, for reporting work in a meeting

## Install globally

Run:

```
npx skill add Clicxl/Prompt_Lib
```

## Invoke

Use the skill name shown by the client. Codex commonly uses `$skill-name`; clients that expose skills as slash commands commonly use `/skill-name`. Each skill is meant to be invoked explicitly.

## Repo layout

- `work/`: the skills and their README
- `CLAUDE.md` and `docs/agents/`: agent configuration for this repo (local-markdown issue tracker under `.scratch/`, default triage labels, domain-doc rules)
- `GLOSSARY.md`: terms used in this repo (Session, Work item, Issue, Review, Blocker, Proof)
