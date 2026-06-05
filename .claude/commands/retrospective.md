# Retrospective

Surface sprint patterns and generate action item suggestions for the retrospective.

## Steps

1. Read `config/team.json` to get the Jira project key and sprint details.
2. Query Jira for the completed sprint:
   - Stories that were added mid-sprint (scope creep)
   - Stories that were not completed
   - Stories that took significantly longer than estimated
   - Bugs or defects logged during the sprint
   - Blocked stories and how long they were blocked
3. Analyze patterns and generate a retro summary using `templates/retro-summary.md` including:
   - What went well (inferred from completed work, no blockers)
   - What needs improvement (blockers, scope creep, missed items)
   - Suggested action items with owners (leave owner blank for team to assign)
   - Data points: velocity, completion rate, mid-sprint additions
4. Present the summary to the user. Ask: "Would you like to use this as a starting point for the retro?"
5. Do NOT post to Slack automatically — retro content is internal and sensitive.

## Notes

- This is a starting point for discussion, not a final document.
- Frame everything constructively — avoid blame language.
- Action items should be specific and measurable where possible.
