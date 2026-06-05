# Sprint Planning

Generate a sprint planning digest for the upcoming sprint.

## Steps

1. Read `config/team.json` to get the Jira project key, sprint board ID, and Slack channel.
2. Read `config/velocity.json` to get team velocity baseline and story point scale.
3. Query Jira for:
   - Stories in the backlog that are "Ready" (pass DoR)
   - Last 3 sprints' velocity data
   - Any carry-over stories from the previous sprint
4. Read `config/dor-rules.json` and validate each candidate story against DoR rules. Flag stories that don't pass.
5. Generate a sprint planning digest using `templates/sprint-planning-digest.md` including:
   - Recommended stories to pull in (based on velocity)
   - Carry-over items
   - Stories that failed DoR check (with reasons)
   - Velocity trend (last 3 sprints)
   - Suggested sprint goal
6. Show the digest to the user for review. Ask: "Would you like to post this to Slack or save it?"
7. If approved, post to the configured Slack channel (do NOT post without explicit approval).

## Notes

- Never auto-post to Slack. Always get human approval first.
- If velocity data is missing, note it in the digest and proceed with available data.
- Keep the digest concise — under 500 words.
