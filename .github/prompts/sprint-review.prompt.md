---
mode: agent
description: Generate a sprint review readout and presenter demo script.
---

# Sprint Review Prompt

Run the sprint review workflow for this repo.

## Inputs to read

- `config/team.json`
- `templates/sprint-review-readout.md`

## Data to collect

- Completed stories for the finished sprint.
- Incomplete carry-over stories and reasons.
- Planned vs completed story points.

## Required processing

- Create a stakeholder-friendly summary focused on outcomes.
- Create a separate demo script with talking points per completed story.

## Output

- Produce draft readout in the exact structure of `templates/sprint-review-readout.md`.
- Provide demo script as a separate section in chat.

## Approval gate

- Ask: "Would you like to post the summary to Slack?"
- Only post the summary, not the demo script.
- Do not post without explicit approval.
