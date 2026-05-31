# paperclip-skills

A collection of reusable [Paperclip](https://paperclip.ai) agent skills by [maxone.one](https://maxone.one).

## Available skills

### create-issue

Teaches any Paperclip agent to autonomously create issues when receiving tasks, assignments, or delegations. The agent discovers available team members dynamically via the Paperclip API — no hardcoded IDs.

**Install:**
```bash
POST /api/companies/{companyId}/skills/import
{ "source": "https://github.com/maxone-one/paperclip-skills" }
```

**What it does:**

The agent decides on its own when a task warrants an issue. When writing to any agent in free text — "handle the onboarding", "check the server logs", "delegate this to the designer" — the agent creates a Paperclip issue immediately, assigns the right team member based on a live API lookup, and confirms with the issue identifier before proceeding.

No slash command needed. The agent reads context and acts.

## Usage

Import individual skills by subfolder path, or import the full collection from the repo root. Skills follow the [Paperclip SKILL.md format](https://paperclip.ai/docs/skills).

## License

MIT
