---
mode: agent
description: Generate a sprint planning digest using Jira data, DoR checks, and velocity.
---

# Sprint Planning Prompt

Run the sprint planning workflow for this repo.

## Inputs to read

- `config/team.json`
- `config/velocity.json`
- `config/dor-rules.json`
- `templates/sprint-planning-digest.md`

## Data to collect

- Backlog stories that are candidates for next sprint.
- Last 3 sprints velocity (planned and completed points).
- Carry-over stories from previous sprint.

## Required processing

- Validate each candidate story against all DoR rules.
- Mark each story as READY, NEEDS WORK, or WARN.
- Recommend a set of stories based on velocity and `capacityBuffer`.

## Output

- Produce draft content in the exact structure of `templates/sprint-planning-digest.md`.
- Include failed DoR stories with specific reasons.
- Keep it under 500 words when possible.

## Approval gate

- Ask: "Would you like to post this to Slack or save it?"
- Do not post without explicit approval.
