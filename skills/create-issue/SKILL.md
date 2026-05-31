---
name: create-issue
description: >
  Use when you receive a task, assignment, or delegation that needs tracking —
  multiple steps, longer than one conversation, or handed off to another agent.
  Discover available agents dynamically before assigning. No explicit trigger
  from the user needed; you decide autonomously when a task warrants an issue.
---

# Create Issue

When you receive work that should be tracked, create a Paperclip issue at the
start of your response. Don't wait until the work is done.

## Step 1 — Decide if an issue is needed

Create an issue when:
- You receive a concrete task ("handle X", "build Y", "check Z")
- You delegate work to another agent
- The task spans more than this conversation or needs sign-off later
- Progress should be visible to the team

Skip it when:
- The request is a question requiring only an answer
- The task completes entirely within this response

## Step 2 — Discover available agents (dynamic)

Before assigning, query your team:

```
GET /api/companies/{companyId}/agents
Authorization: Bearer {agentToken}
```

From the response, pick the agent whose `role` or `name` best matches the task.
Don't hardcode agent IDs — always resolve from the live team list.

## Step 3 — Create the issue

```
POST /api/companies/{companyId}/issues
Authorization: Bearer {agentToken}
Content-Type: application/json

{
  "title": "Short, action-oriented title",
  "description": "Context and what done looks like (optional)",
  "assigneeAgentId": "{resolved agent ID or omit}",
  "priority": "critical | high | medium | low"
}
```

The response contains `identifier` (e.g. `ABC-42`) and `id`.

## Step 4 — Confirm and proceed

Always tell the user: `Issue created: ABC-42 — [title]`
If delegated: `Issue created: ABC-42 → [agent name] — [title]`
Then proceed with the work.

## Priority guide

| Priority | When |
|----------|------|
| `critical` | Production down, data loss, security incident |
| `high` | Blocking someone, deadline today or tomorrow |
| `medium` | Normal work, no urgent constraint (default) |
| `low` | Nice-to-have, background task, no deadline |
