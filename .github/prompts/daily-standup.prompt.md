---
mode: agent
description: Generate a daily standup digest with completed work, in-progress status, and blockers.
---

# Daily Standup Prompt

Run the daily standup workflow for this repo.

## Inputs to read

- `config/team.json`
- `templates/standup-digest.md`

## Data to collect

- Stories moved to Done since yesterday.
- In-progress stories grouped by assignee.
- Stories not updated in the last 24h.
- Stories flagged or labeled as blocked.

## Required processing

- Classify stale items as "needs attention" unless clear blocker evidence exists.
- Assess burn-down status as on track, at risk, or behind.

## Output

- Produce draft content in the exact structure of `templates/standup-digest.md`.
- Use bullet points, not long paragraphs.

## Approval gate

- Ask: "Looks good to post to Slack?"
- Do not post without explicit approval.
