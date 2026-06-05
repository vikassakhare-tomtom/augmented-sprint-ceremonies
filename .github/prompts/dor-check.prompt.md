---
mode: agent
description: Validate backlog stories against Definition of Ready rules.
---

# DoR Check Prompt

Run the Definition of Ready check for this repo.

## Inputs to read

- `config/team.json`
- `config/dor-rules.json`

## Scope prompt

Ask first: "Check all backlog stories, or a specific list of issue keys?"

## Data to collect

- Target stories from backlog filter or provided keys.

## Required processing

- Evaluate every story against every DoR rule.
- Use statuses: PASS, FAIL, WARN.
- A story with any FAIL is not ready.

## Output

- Produce a report with:
  - READY stories
  - NEEDS WORK stories and missing criteria
  - WARNINGS

## Approval gate

- Ask: "Would you like to add DoR failure comments to the Jira issues?"
- Do not update Jira without explicit approval.
