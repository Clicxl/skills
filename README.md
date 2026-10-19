# Prompt Lib

A library of explicit-invocation Agent Skills for day-to-day engineering work (writing issues, resolving them, reporting what got done) and for running a personal knowledge vault. Each skill is a folder with a `SKILL.md`, invoked by name.

## Skills

The skills live in [`work/`](work/README.md):

- `create-issue`: draft or publish a tracker issue
- `resolve-issue`: grill, plan, test first, implement, review, and optionally ship a GitHub Issue
- `what-happened`: summarise the current session as a short paragraph plus a status line, for reporting work in a meeting

The knowledge skills live in [`knowledge/`](knowledge/README.md):

- `distill`: turn raw inbox captures into organised atomic notes, hub updates and tracker issues
- `spar`: Socratic sparring on an idea until you've earned your position, saved as an essay
- `recall`: quiz yourself from your own notes
- `reflect`: evidence-based self-assessment of patterns, habits, goals and purpose

## Install globally

Run:

```
npx skills add Clicxl/skills
```

## Invoke

Use the skill name shown by the client. Codex commonly uses `$skill-name`; clients that expose skills as slash commands commonly use `/skill-name`. Each skill is meant to be invoked explicitly.

## Repo layout

- `work/`: the engineering skills and their README
- `knowledge/`: the knowledge-vault skills and their README
- `CLAUDE.md` and `docs/agents/`: agent configuration for this repo (local-markdown issue tracker under `.scratch/`, default triage labels, domain-doc rules)
- `GLOSSARY.md`: terms used in this repo (Session, Work item, Issue, Review, Blocker, Proof)
