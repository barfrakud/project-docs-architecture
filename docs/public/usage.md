# Usage

## Use this repository as a starter template

1. Copy the repository
2. Keep the structure
3. Replace example files with project-specific content
4. Preserve the private-first workflow

## Typical task lifecycle

1. Create a plan in `docs/private/plans/`
2. Save the AI prompt in `docs/private/prompts/`
3. Execute the task
4. Write the implementation report in `docs/private/reports/`
5. Promote stable knowledge into manuals, concepts, or decisions
6. Publish concise public docs

## Typical Codex usage

```text
$documentation-workflow
Create a private implementation plan and implementation report template for documenting a Docker-based deployment.
```

## Existing repository migration

If the repository already exists and has scattered or missing documentation, start from the example prompt:

`examples/prompts/bootstrap-project-documentation.md`

In a Codex session, invoke it as:

`Zrealizuj bootstrap-project-documentation`

The prompt tells Codex to inspect the whole project, classify existing documentation, create the private planning/reporting layer, and then refine the public documentation while staying consistent with any existing `AGENTS.md` and repo-local skills.
