# Project Documentation Architecture

A public, reusable repository template for running **private-first documentation** in software engineering, DevOps, and Linux/sysadmin projects, with built-in support for **OpenAI Codex CLI** via `AGENTS.md` and a repo-local skill.

## Why this repository exists

Most project documentation is either too sparse to be useful during real work or too raw to publish publicly.

This repository uses a **private-first workflow**:

1. Work starts in `docs/private/`
2. Plans, prompts, reports, manuals, and concept notes are captured there
3. Stable knowledge is refined
4. Public-facing documentation is produced in `docs/public/` and `README.md`

That lets you:
- document work as you go,
- learn while building,
- keep rough learning notes private,
- publish only mature, portfolio-friendly documentation.

## Core principles

- **Private first**: draft, learn, and reason in `docs/private/`
- **Public second**: publish only distilled, professional content
- **Prompt aware**: treat AI prompts as project assets
- **Plan -> Execute -> Report**: capture decisions and results, not only final code
- **Reusable knowledge**: move durable know-how into manuals, concepts, and decisions

## Repository layout

```text
.
├── README.md
├── LICENSE
├── .gitignore
├── AGENTS.md
├── .agents/
│   └── skills/
│       └── documentation-workflow/
│           ├── SKILL.md
│           ├── agents/
│           │   └── openai.yaml
│           ├── assets/
│           │   ├── concept-note-template.md
│           │   ├── implementation-plan-template.md
│           │   ├── implementation-report-template.md
│           │   ├── manual-template.md
│           │   ├── prompt-template.md
│           │   └── public-doc-template.md
│           └── references/
│               ├── docs-policy.md
│               ├── naming-conventions.md
│               └── private-to-public.md
├── docs/
│   ├── index.md
│   ├── philosophy.md
│   ├── codex-cli-usage.md
│   ├── public/
│   │   ├── index.md
│   │   ├── overview.md
│   │   ├── architecture.md
│   │   ├── setup.md
│   │   ├── ci-cd.md
│   │   ├── deployment.md
│   │   └── usage.md
│   ├── private/
│   │   ├── index.md
│   │   ├── journal/
│   │   ├── prompts/
│   │   │   ├── index.md
│   │   │   ├── codex/
│   │   │   ├── chatgpt/
│   │   │   ├── claude/
│   │   │   └── generic/
│   │   ├── plans/
│   │   ├── reports/
│   │   ├── concepts/
│   │   ├── decisions/
│   │   ├── research/
│   │   └── manuals/
│   │       ├── installation/
│   │       ├── configuration/
│   │       ├── operations/
│   │       └── troubleshooting/
│   └── templates/
│       ├── concept-note-template.md
│       ├── implementation-plan-template.md
│       ├── implementation-report-template.md
│       ├── manual-template.md
│       ├── prompt-template.md
│       └── public-doc-template.md
└── examples/
    ├── example-task-lifecycle.md
    └── prompts/
        ├── bootstrap-project-documentation.md
        └── codex-private-plan-example.md
```

## What each area is for

### `docs/private/`
Working documentation for real execution:
- plans,
- prompts,
- implementation reports,
- training notes,
- concept explanations,
- research notes,
- architecture decisions,
- operating manuals.

### `docs/private/manuals/`
Step-by-step procedures with operational value, such as:
- installation,
- configuration,
- troubleshooting,
- deployment operations.

### `docs/public/`
Polished public documentation for GitHub readers:
- overview,
- setup,
- architecture,
- CI/CD,
- deployment,
- usage.

### `.agents/skills/documentation-workflow/`
A repo-local Codex skill that helps Codex classify documentation tasks and write into the correct destination using a private-first workflow.

### `AGENTS.md`
Persistent repository instructions for Codex. Keep this small, practical, and durable.

## Recommended workflow

### 1. Start with a plan
Create:

```text
docs/private/plans/YYYY-MM-DD-topic.md
```

Use this for:
- implementation plans,
- refactor plans,
- migration plans,
- investigation plans.

### 2. Save the prompt
If AI is used meaningfully, save the prompt in:

```text
docs/private/prompts/<tool>/YYYY-MM-DD-topic.md
```

### 3. Execute the task
Use Codex, another model, or manual work.

### 4. Write the report
Capture results in:

```text
docs/private/reports/YYYY-MM-DD-topic.md
```

### 5. Promote durable knowledge
If something becomes reusable:
- procedure -> `docs/private/manuals/`
- concept -> `docs/private/concepts/`
- decision -> `docs/private/decisions/`

### 6. Publish the public version
Once the work is mature, distill the private material into:
- `README.md`
- `docs/public/*.md`

## OpenAI Codex CLI support

This repository is designed for the current Codex CLI workflow:

- `AGENTS.md` is read automatically before work begins
- repo-local skills live in `.agents/skills`
- skills can be invoked explicitly or selected implicitly based on their description
- `/init` can scaffold `AGENTS.md`
- `/plan`, `/review`, `/diff`, `/status`, and `/permissions` fit this documentation workflow well

Read [`docs/codex-cli-usage.md`](docs/codex-cli-usage.md) for setup and usage examples.
See [`examples/prompts/bootstrap-project-documentation.md`](examples/prompts/bootstrap-project-documentation.md) for a reusable prompt that can be executed with `Zrealizuj bootstrap-project-documentation` to bootstrap this workflow in an already existing repository.
In a real adopted project, copy that prompt into `docs/private/prompts/codex/bootstrap-project-documentation.md` rather than leaving it under `examples/`.

## Fast start

### Install Codex CLI

```bash
npm i -g @openai/codex@latest
```

### Start Codex in this repository

```bash
codex
```

### Initialize or refresh repo guidance

```text
/init
```

### Ask Codex to use the repo-local documentation skill

In the Codex composer:
```text
$documentation-workflow
Create a private implementation plan for adding CI/CD to this repository.
```

Or let Codex choose the skill implicitly:
```text
Create a private implementation plan and a matching implementation report template for adding CI/CD to this repository.
```

### Execute a saved prompt by name

If the repository contains prompt assets and `AGENTS.md` defines the convention, you can invoke them directly:

```text
Zrealizuj bootstrap-project-documentation
```

## Suggested Git usage model

Use **one of these two patterns**:

### Pattern A: private repo -> public repo
Keep all materials, including `docs/private/`, in a private repository.
When the project is ready, publish only selected files in a separate public repository.

### Pattern B: one repo with filtered publication
Keep `docs/private/` local or private and publish only public content.
If needed, exclude private working docs from publication.

If the repository itself is public and you do not want `docs/private/` to be pushed to that remote, add it to `.gitignore`, for example:

```gitignore
docs/private/
```

## Adapting this to an existing repository

If your repository already exists and was not documented with this standard, do not rewrite everything at once. Adopt the structure incrementally.

### 1. Copy the documentation scaffold
Add these elements to the existing repository:

```text
AGENTS.md
.agents/skills/documentation-workflow/
docs/private/
docs/public/
docs/templates/
```

If you only want the minimum viable setup, start with:

```text
AGENTS.md
.agents/skills/documentation-workflow/
docs/private/
docs/public/
```

### 2. Decide where private documentation will live
Before migrating content, choose your publication model:
- private repo with separate public output, or
- one repo where `docs/private/` stays unpublished or filtered out.

This avoids mixing internal working notes with public-facing documentation by accident.

### 3. Classify what you already have
Review the current documentation and sort it into three groups:
- stable reader-facing docs -> keep in `README.md` or move to `docs/public/`
- operational know-how -> move to `docs/private/manuals/`
- rough notes, investigations, migration plans, and AI prompts -> move to `docs/private/`

Do not force old material into polished public docs if it is still incomplete or exploratory.

### 4. Start with a migration plan, not a full rewrite
Create your first migration plan in:

```text
docs/private/plans/YYYY-MM-DD-docs-migration.md
```

Use it to define:
- which existing files will stay public,
- which notes should become manuals, reports, or concepts,
- which outdated documents should be archived, rewritten, or deleted later.

### 5. Migrate only active work first
Apply the workflow first to current or upcoming tasks:
- create plans in `docs/private/plans/`
- save meaningful prompts in `docs/private/prompts/`
- write implementation results in `docs/private/reports/`

Older documentation can be reorganized gradually as you touch related parts of the project.

### 6. Refine public documentation after the private layer exists
Once private documentation starts capturing real work, update:
- `README.md`
- `docs/public/overview.md`
- `docs/public/setup.md`
- other public docs that matter for readers

The public layer should be a distilled version of what has already been validated privately.

### Recommended migration strategy

For an existing project, this usually works best:

1. add the scaffold and `AGENTS.md`
2. create one migration plan
3. use the private-first workflow for all new work
4. gradually sort old docs into manuals, concepts, decisions, or public docs
5. rewrite `README.md` only after the structure starts reflecting real usage

For a reusable Codex command, keep a short prompt asset name such as:

```text
docs/private/prompts/codex/bootstrap-project-documentation.md
```

Then invoke it in Codex with:

```text
Zrealizuj bootstrap-project-documentation
```

Use `examples/prompts/` only in the template repository or for demonstrative sample prompts.
In an actual working project, keep reusable executable prompts in `docs/private/prompts/`.

## Naming conventions

- Use `kebab-case`
- Use `YYYY-MM-DD-topic.md` for plans, prompts, and reports
- Use action-oriented names for manuals, such as:
  - `install-docker-on-ubuntu.md`
  - `configure-nginx-reverse-proxy.md`

## Who this is for

This template is useful for:
- software engineering projects,
- DevOps labs,
- Linux administration labs,
- cloud experiments,
- CI/CD playgrounds,
- portfolio repositories,
- AI-assisted learning projects.

## License

MIT
