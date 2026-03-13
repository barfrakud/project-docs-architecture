# AGENTS.md

## Purpose

This repository defines a **private-first documentation workflow** for software engineering, DevOps, and sysadmin projects.

Codex should help maintain the structure and discipline of that workflow.

## Documentation model

There are 3 layers of documentation:

1. `docs/private/`
   - working notes
   - implementation plans
   - AI prompts
   - implementation reports
   - manuals
   - concept notes
   - decisions
   - research notes

2. `docs/private/manuals/`
   - installation
   - configuration
   - operations
   - troubleshooting

3. `docs/public/`
   - concise public documentation for repository readers
   - professional, portfolio-friendly
   - no raw learning notes or scratch thinking

## Default behavior

- Default destination is `docs/private/` unless the task explicitly requests public documentation.
- Do not write directly to `docs/public/` when the task is still exploratory, educational, or incomplete.
- Do not move private notes into public docs without summarizing and simplifying them.
- Treat prompts as reusable project assets and store them in `docs/private/prompts/` when AI usage is meaningful.

## Required outputs for meaningful implementation work

When work is substantial, create or update:

- a plan in `docs/private/plans/`
- a prompt in `docs/private/prompts/` if AI was used significantly
- a report in `docs/private/reports/`

If durable knowledge appears:

- procedures go to `docs/private/manuals/`
- concepts go to `docs/private/concepts/`
- architecture or technology choices go to `docs/private/decisions/`

## Naming conventions

- Use `kebab-case` for file names.
- Use `YYYY-MM-DD-topic.md` for plans, prompts, and reports.
- Use task-oriented names for manuals, such as `install-docker-on-ubuntu.md`.

## Public documentation rules

Public documentation must:
- be concise,
- avoid beginner scratch notes,
- avoid internal uncertainty unless it materially matters,
- focus on architecture, setup, CI/CD, deployment, usage, and decisions.

Public documentation must not expose:
- raw learning notes,
- discarded experiments,
- private operational details,
- security-sensitive details,
- unfiltered prompt transcripts.

## Working style

When asked to create documentation:
1. classify the task,
2. select the correct destination file,
3. use the matching template if available,
4. write complete Markdown content,
5. cross-link related files when useful.

## Skill routing

Prefer the repo-local skill:

- `.agents/skills/documentation-workflow/`

Use it when the task is about:
- planning documentation,
- creating prompts,
- creating implementation reports,
- creating manuals,
- promoting private docs into public docs,
- maintaining this repository's documentation structure.
