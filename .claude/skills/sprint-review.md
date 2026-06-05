# Sprint Review

Generate a sprint review readout and demo script for stakeholders.

## Steps

1. Read `config/team.json` to get the Jira project key, current sprint, and stakeholder Slack channel.
2. Query Jira for the completed sprint:
   - All stories marked Done
   - Stories that were not completed (carry-over)
   - Sprint velocity (planned vs actual story points)
3. Generate a sprint review readout using `templates/sprint-review-readout.md` including:
   - Sprint summary (goal, dates, team)
   - Completed work with brief descriptions
   - Incomplete work and reasons
   - Velocity: planned vs actual
   - Highlights and wins
   - What's coming next sprint (if known)
4. Generate a demo script with talking points for each completed story.
5. Show both artifacts to the user for review. Ask: "Would you like to post the summary to Slack?"
6. If approved, post the readout (not the demo script) to the stakeholder channel.

## Notes

- Never auto-post. Always get human approval.
- Demo script is for the presenter only — do not post it to Slack.
- Keep the stakeholder summary jargon-free and outcome-focused.
