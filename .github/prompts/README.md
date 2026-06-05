# Copilot Ceremony Prompts

This folder contains reusable prompt files for running ceremony workflows from GitHub Copilot Chat.

## Available prompts

- `sprint-planning.prompt.md`
- `daily-standup.prompt.md`
- `sprint-review.prompt.md`
- `retrospective.prompt.md`
- `dor-check.prompt.md`
- `sprint-refinement.prompt.md`

## Recommended usage

1. Open one prompt file.
2. Copy the content into Copilot Chat (Agent mode).
3. Provide optional scope input (for example epic key or sprint name).
4. Review draft output.
5. Approve before any Slack/Jira/Confluence write.

## Notes

- Prompt files assume team configuration exists in `config/`.
- Output shape is controlled by files in `templates/`.
- These prompts are policy-aligned for approval-first external writes.
