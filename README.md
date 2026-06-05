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

## Customization

- **DoR rules**: Edit `config/dor-rules.json` to match your team's Definition of Ready
- **Output format**: Edit templates in `templates/` to change the structure of any artifact
- **Velocity**: Set `averageVelocity` in `config/velocity.json` for sprint planning recommendations

## Security

- `.env` is gitignored — credentials never leave your machine
- All Jira/Slack writes require explicit human approval
- No story data is stored — everything is fetched live per session
