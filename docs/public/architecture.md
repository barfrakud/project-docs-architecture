# Documentation Architecture

## Layers

### 1. Private working documentation
`docs/private/`

Used for:
- plans,
- prompts,
- reports,
- manuals,
- concept notes,
- decisions,
- research.

### 2. Public documentation
`docs/public/`

Used for:
- overview,
- setup,
- architecture,
- CI/CD,
- deployment,
- usage.

### 3. Codex automation layer
- `AGENTS.md`
- `.agents/skills/documentation-workflow/`

This layer helps Codex route documentation work into the right structure.

## Flow

```text
idea/task
  -> private plan
  -> private prompt
  -> execution
  -> private report
  -> reusable manual/concept/decision
  -> public documentation
```
