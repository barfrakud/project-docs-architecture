# Using this repository with OpenAI Codex CLI

This repository is designed to work with the current Codex CLI model of:
- `AGENTS.md` for durable repo guidance,
- repo-local skills in `.agents/skills/`,
- explicit and implicit skill invocation,
- interactive slash commands for planning and review.

## 1. Install Codex CLI

```bash
npm i -g @openai/codex@latest
```

## 2. Start Codex in the repository root

```bash
codex
```

This lets Codex discover:
- `AGENTS.md`
- `.agents/skills/documentation-workflow/`

## 3. Generate or refresh `AGENTS.md`

Inside Codex:

```text
/init
```

Review the generated scaffold and keep only durable repository guidance.

## 4. Check session state

Inside Codex:

```text
/status
```

Useful to confirm:
- active model,
- approval policy,
- writable roots,
- context status.

## 5. Plan before implementing

Inside Codex:

```text
/plan Create a private implementation plan for adding CI/CD documentation to this project.
```

This is especially useful before:
- large changes,
- documentation migrations,
- refactors,
- public-doc promotion.

## 6. Invoke the documentation skill explicitly

Open the skill picker with `/skills` or type `$` in the composer, then select:

```text
$documentation-workflow
```

Example prompt:

```text
$documentation-workflow
Create a private implementation plan in docs/private/plans/ for adding a Jenkins-based CI/CD example to this repository. Also create a matching implementation report template.
```

## 7. Let Codex invoke the skill implicitly

Because the skill description is written narrowly, Codex can often select it automatically.

Example:

```text
Create a private implementation plan, prompt, and implementation report for adding Docker deployment documentation to this repository. Use the private-first workflow.
```

## 8. Execute a saved prompt by name

If the repository `AGENTS.md` defines a prompt-execution convention, you can invoke a stored prompt asset directly by its file stem.

Example:

```text
Zrealizuj bootstrap-project-documentation
```

Recommended setup:
- keep executable prompt assets in `docs/private/prompts/` or `examples/prompts/`
- use short, unambiguous kebab-case file names
- let `AGENTS.md` define how Codex should resolve the prompt and execute it

In this repository, `Zrealizuj bootstrap-project-documentation` should resolve to:

`examples/prompts/bootstrap-project-documentation.md`

## 9. Review local changes

After Codex edits files:

```text
/diff
/review
```

Recommended order:
1. `/diff` to inspect file changes
2. `/review` to ask Codex for a second-pass review

## 10. Manage permissions

If you want tighter control:

```text
/permissions
```

Choose:
- `Read Only` for consultative mode
- `Auto` for normal work
- stronger access only when you trust the repository and task

## 11. Compact long sessions

After long documentation sessions:

```text
/compact
```

This helps preserve the important context while reducing transcript bloat.

## Suggested daily workflow

1. Open repository in terminal
2. Run `codex`
3. Run `/status`
4. Use `/plan` for substantial work
5. Use `$documentation-workflow` for documentation tasks
6. Review with `/diff` and `/review`
7. Commit when satisfied

## Prompt patterns that work well

### Plan only
```text
$documentation-workflow
Create a private implementation plan for migrating all Docker notes into the private/public documentation structure used by this repository.
```

### Execute a reusable prompt asset
```text
Zrealizuj bootstrap-project-documentation
```

### Plan + prompt + report
```text
$documentation-workflow
For the task of documenting a new monitoring stack, create:
1. a plan,
2. a Codex prompt,
3. an implementation report template.
Use the correct file locations and naming conventions.
```

### Promote private docs into public docs
```text
$documentation-workflow
Based on the existing private manuals and reports, produce a concise public docs/public/deployment.md suitable for a GitHub portfolio repository.
```
