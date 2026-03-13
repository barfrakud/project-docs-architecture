# Setup

## Requirements
- Git
- Node.js and npm
- OpenAI Codex CLI account access

## Clone the repository

```bash
git clone <your-repo-url>
cd ai-project-documentation-playbook
```

## Install Codex CLI

```bash
npm i -g @openai/codex@latest
```

## Start Codex

```bash
codex
```

## Verify repository guidance

Inside Codex:
```text
/status
```

Confirm that Codex is running in the repository root so it can discover:
- `AGENTS.md`
- `.agents/skills/documentation-workflow/`
