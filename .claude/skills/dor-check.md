# DoR Check (Definition of Ready)

Validate backlog stories against the team's Definition of Ready rules.

## Steps

1. Read `config/team.json` to get the Jira project key and backlog filter.
2. Read `config/dor-rules.json` to load the team's DoR rules.
3. Ask the user: "Check all backlog stories, or a specific list of issue keys?" and wait for response.
4. Query Jira for the target stories.
5. For each story, validate against every rule in `dor-rules.json`:
   - PASS: rule is satisfied
   - FAIL: rule is not satisfied (note what's missing)
   - WARN: partially satisfied or unclear
6. Generate a DoR report:
   - Stories that are READY (all rules pass)
   - Stories that NEED WORK (list failed rules per story with specific gaps)
   - Stories with WARNINGS
7. Show the report to the user. Ask: "Would you like to add DoR failure comments to the Jira issues?"
8. If approved, post a comment on each failing story listing what needs to be addressed.

## Notes

- Never update Jira without explicit approval.
- DoR rules are fully customizable in `config/dor-rules.json`.
- A story with 1 FAIL should not be pulled into sprint planning.
