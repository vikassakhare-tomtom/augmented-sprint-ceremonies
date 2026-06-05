# Augmented Sprint Ceremonies

AI-augmented toolkit for Scrum ceremonies. Uses Claude Code skills to generate sprint planning digests, standup summaries, review readouts, retro insights, and DoR checks — all human-approved before posting.

## Prerequisites

- [Claude Code](https://claude.ai/code) installed
- Jira API token ([generate here](https://id.atlassian.com/manage-profile/security/api-tokens))
- Slack bot token (ask your Slack admin or follow the setup guide below)

## Setup (5 minutes)

### 1. Clone the repo

```bash
git clone <repo-url>
cd augmented-sprint-ceremonies
```

### 2. Add your credentials

```bash
cp .env.example .env
```

Edit `.env` and fill in:

| Variable | Where to get it |
|----------|----------------|
| `JIRA_HOST` | Your org's Jira URL, e.g. `tomtom.atlassian.net` |
| `JIRA_USER` | Your Atlassian account email |
| `JIRA_TOKEN` | [Atlassian API tokens](https://id.atlassian.com/manage-profile/security/api-tokens) |
| `SLACK_BOT_TOKEN` | Slack app OAuth token (starts with `xoxb-`) |
| `SLACK_TEAM_ID` | Your Slack workspace ID |
| `ANTHROPIC_API_KEY` | [Anthropic Console](https://console.anthropic.com/) |

### 3. Configure your team

Edit `config/team.json`:

```json
{
  "jira": {
    "projectKey": "YOUR_PROJECT_KEY",
    "boardId": 123
  },
  "slack": {
    "standupChannel": "#team-standup",
    "sprintChannel": "#team-sprint",
    "stakeholderChannel": "#product-updates"
  }
}
```

### 4. Open in Claude Code

```bash
claude .
```

## Onboarding for New Teammates

Use this checklist when sharing the repo with colleagues.

### 1. Clone and open

```bash
git clone <repo-url>
cd augmented-sprint-ceremonies
code .
```

### 2. Create local credentials

```bash
cp .env.example .env
```

Fill `.env` with personal credentials (never share tokens).

### 3. Configure team values

Update these files for your team:

- `config/team.json` (Jira host/project/board, Slack channels, Confluence space/folder)
- `config/velocity.json` (set non-zero `averageVelocity`)
- `config/dor-rules.json` (optional: customize DoR rules)

### 4. Choose execution path

- **Copilot path**: use prompt files in `.github/prompts/`
- **Claude path**: use slash commands in `.claude/commands/`

### 5. MCP setup (recommended)

Each teammate must enable Jira/Slack MCP in their own local AI runtime settings.
Repo permissions only define what is allowed after MCP is connected.

### 6. First-run smoke test

Run one refinement pilot with epic `CET-2781` and verify:

- Draft output is generated
- Approval prompts appear before Slack/Jira/Confluence writes
- Output follows template structure

## Usage

Once open in Claude Code, run any ceremony skill:

| Ceremony | Command |
|----------|---------|
| Sprint Planning | `/sprint-planning` |
| Daily Standup | `/daily-standup` |
| Sprint Review | `/sprint-review` |
| Retrospective | `/retrospective` |
| DoR Check | `/dor-check` |

Each skill fetches live data from Jira, generates a draft, and asks for your approval before posting anything to Slack.

## Run with GitHub Copilot

This repo also includes Copilot-ready prompt files for each ceremony in `.github/prompts/`.

Quick Start (recommended):

1. Open Copilot Chat.
2. Type `/` and look for workspace prompts (for example, `sprint-refinement`).
3. Select the prompt, provide scope (for example, `CET-2781`), and run.

If prompts do not appear in `/`:

1. Open Command Palette.
2. Run `Chat: Run Prompt`.
3. Choose a file from `.github/prompts/`.
4. Provide scope and run.

Manual fallback (works in every setup):

1. Open a prompt file from `.github/prompts/`.
2. Copy the prompt text into Copilot Chat (Agent mode).
3. Review the generated draft.
4. Approve explicitly before any Slack or Jira write action.

Policy: Slack, Jira, and Confluence writes always require explicit user approval.

Available prompt files:

- `.github/prompts/sprint-planning.prompt.md`
- `.github/prompts/daily-standup.prompt.md`
- `.github/prompts/sprint-review.prompt.md`
- `.github/prompts/retrospective.prompt.md`
- `.github/prompts/dor-check.prompt.md`
- `.github/prompts/sprint-refinement.prompt.md`

Global Copilot behavior is defined in `.github/copilot-instructions.md`.

## Customization

- **DoR rules**: Edit `config/dor-rules.json` to match your team's Definition of Ready
- **Output format**: Edit templates in `templates/` to change the structure of any artifact
- **Velocity**: Set `averageVelocity` in `config/velocity.json` for sprint planning recommendations

## Security

- `.env` is gitignored — credentials never leave your machine
- All Jira/Slack writes require explicit human approval
- No story data is stored — everything is fetched live per session
