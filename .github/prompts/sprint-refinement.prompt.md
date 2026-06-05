---
mode: agent
description: Run sprint refinement readiness and story-quality review using DoR and INVEST.
---

# Sprint Refinement Prompt

Run the sprint refinement workflow for this repo.

## Inputs to read

- `config/team.json`
- `config/dor-rules.json`
- `config/velocity.json`
- `templates/sprint-refinement-report.md`

## Intake behavior

- If user gives an Epic key: fetch all open child stories.
- If user gives a Story/Task key: review that issue.
- If user gives project key or sprint name: fetch open sprint stories.
- If unclear: ask once for epic or story key.

## Required processing

- Action 1: Score DoR readiness for each story (PASS/WARN/FAIL).
- Action 2: Run INVEST review for each story.
- For detected gaps, propose concrete fixes:
  - Gherkin acceptance criteria
  - Story decomposition
  - User-value rewrite
  - Dependency link suggestions

## Output

- Produce refinement report using `templates/sprint-refinement-report.md`.
- Include a concise Slack-ready summary block.
- Include a Jira change checklist with per-story checkboxes.

## Approval gates

- Ask before posting summary to Slack.
- Ask before creating or updating Confluence content.
- Ask before any Jira writes.
