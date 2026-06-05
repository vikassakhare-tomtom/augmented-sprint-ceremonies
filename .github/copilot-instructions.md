# Copilot Instructions for Augmented Sprint Ceremonies

You are assisting with Agile sprint ceremonies for this repository.

## Operating rules

- Always read these files first before generating ceremony output:
  - `config/team.json`
  - `config/dor-rules.json`
  - `config/velocity.json`
- Use the matching file under `templates/` as the output structure.
- Treat generated content as draft output only.
- Never post to Slack and never update Jira without explicit user approval.
- If required configuration values are missing or placeholders, stop and ask for the missing values.
- Keep output concise and scannable with headings and bullets.

## Ceremony command style

When a user asks for a ceremony output, execute this pattern:

1. Confirm which ceremony is requested.
2. Read config and template files.
3. Pull required Jira data (and Slack destination only if posting is requested).
4. Generate draft output in template shape.
5. Ask for approval before any external write.

## Quality bar

- Include assumptions when data is incomplete.
- Highlight blockers, risks, and missing DoR requirements.
- Use neutral, non-blaming language in retrospectives.
