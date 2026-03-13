# Example Task Lifecycle

This example shows how a single engineering task should flow through the documentation system.

## Example task
Add Docker-based deployment documentation for a small Python service.

## Expected private artifacts

### 1. Plan
`docs/private/plans/2026-03-13-docker-deployment-docs.md`

### 2. Prompt
`docs/private/prompts/codex/2026-03-13-docker-deployment-docs.md`

### 3. Report
`docs/private/reports/2026-03-13-docker-deployment-docs.md`

### 4. Durable manual
`docs/private/manuals/operations/deploy-python-service-with-docker.md`

### 5. Public output
`docs/public/deployment.md`

## Why this matters

Instead of jumping directly to a polished public document, you:
- preserve reasoning,
- preserve prompts,
- preserve outcome tracking,
- convert the final result into a cleaner public form later.
