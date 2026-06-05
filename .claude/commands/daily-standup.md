# Daily Standup

Generate a daily standup digest and surface blockers.

## Steps

1. Read `config/team.json` to get the Jira project key, active sprint ID, and Slack standup channel.
2. Query Jira for the active sprint:
   - All in-progress stories and their assignees
   - Stories moved to Done since yesterday
   - Stories not updated in the last 24 hours (potential blockers)
   - Any stories flagged or with blocker labels
3. Generate a standup digest using `templates/standup-digest.md` including:
   - What was completed yesterday
   - What is in progress today (by assignee)
   - Blockers / items not updated (flagged for attention)
   - Sprint burn-down status (on track / at risk / behind)
4. Show the digest to the user. Ask: "Looks good to post to Slack?"
5. If approved, post to the Slack standup channel.

## Notes

- Never auto-post to Slack. Always get human approval first.
- Flag stories idle for >24h as "needs attention", not as hard blockers.
- Keep the digest scannable — use bullet points, not paragraphs.
