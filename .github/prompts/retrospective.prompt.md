---
mode: agent
description: Generate a retrospective starter summary with patterns and action items.
---

# Retrospective Prompt

Run the retrospective workflow for this repo.

## Inputs to read

- `config/team.json`
- `templates/retro-summary.md`

## Data to collect

- Mid-sprint additions (scope creep).
- Incomplete stories.
- Stories that exceeded estimates.
- Bugs/defects logged during sprint.
- Blocked stories and blocked duration.

## Required processing

- Infer what went well from completion and flow data.
- Identify improvement themes from blockers and misses.
- Propose measurable action items with blank owners.
- Use constructive language; avoid blame.

## Output

- Produce draft content in the exact structure of `templates/retro-summary.md`.

## Approval gate

- Ask: "Would you like to use this as a starting point for the retro?"
- Do not post to Slack automatically.
