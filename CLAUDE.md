# Augmented Sprint Ceremonies

AI-augmented Scrum ceremony toolkit. Each skill automates one ceremony using Jira and Slack data.

## Jira Epic

CET-2781 — AI Augmentations: Augmented Sprint Ceremonies

## Available Skills

| Skill | Command | What it does |
|-------|---------|-------------|
| Sprint Planning | `/sprint-planning` | Velocity digest, story recommendations, DoR check |
| Daily Standup | `/daily-standup` | In-progress summary, blockers, burn-down status |
| Sprint Review | `/sprint-review` | Readout + demo script for stakeholders |
| Retrospective | `/retrospective` | Pattern detection, action item suggestions |
| DoR Check | `/dor-check` | Validate stories against Definition of Ready rules |

## Key Principles

- **Human-in-the-loop always**: Never post to Slack or update Jira without explicit user approval.
- **Editable outputs**: All generated content is a draft — users can modify before publishing.
- **Config-driven**: Team settings, DoR rules, and velocity live in `config/`. Skills read from there.

## Config Files

- `config/team.json` — Jira project key, Slack channels, ceremony schedule
- `config/dor-rules.json` — Customizable DoR rules for story validation
- `config/velocity.json` — Velocity baseline and sprint history

## Output Templates

Templates in `templates/` define the structure of each ceremony artifact. Edit them to match your team's preferred format.

## MCPs Required

- **Jira MCP** — reads sprint data, stories, velocity
- **Slack MCP** — posts approved digests to channels

Credentials are loaded from `.env` (see `.env.example`).
