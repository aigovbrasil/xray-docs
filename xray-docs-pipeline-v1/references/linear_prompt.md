# Linear Integration Prompt

Template for generating a Linear-ready project setup prompt from an approved corpus.
Use during Phase 5 final output packaging.

---

## When to use

After all target documents are approved and the corpus is finalized.
Feed the approved backlog, roadmap, and user stories into this prompt to generate
a structured Linear import prompt.

---

## Prompt Template

Copy and use this prompt with the Linear MCP or Linear import tool:

```
You are setting up a Linear project from an approved product corpus.

PROJECT DETAILS:
- Project name: [PROJECT_NAME]
- Team: [TEAM_NAME]
- Workflow profile: [PROFILE]
- Target cycle: [CYCLE_DATES]

CONTEXT:
[Paste the approved PRD-lite summary here]

ROADMAP:
[Paste the approved roadmap Now/Next/Later sections here]

USER STORIES:
[Paste the approved user stories here]

BACKLOG:
[Paste the approved backlog table here]

INSTRUCTIONS:
1. Create a Linear project named "[PROJECT_NAME]"
2. Create cycles matching the roadmap phases
3. For each backlog item, create a Linear issue with:
   - Title: [item title]
   - Description: [use case + acceptance criteria from user story]
   - Priority: based on MoSCoW mapping:
     * Must → Urgent
     * Should → High
     * Could → Medium
     * Won't → No priority (create as backlog)
   - Estimate: map effort to points:
     * S → 1 point
     * M → 3 points
     * L → 8 points
   - Cycle: assign to correct roadmap cycle
   - Labels: use document type as label source
     * Feature → Feature
     * Bug → Bug
     * Chore → Chore / Tech Debt

4. Create Milestones matching roadmap phases
5. Link related issues (dependencies from backlog)
6. Create a project description using the PRD-lite purpose field

OUTPUT:
Confirm each issue created with: Issue ID | Title | Priority | Cycle
Report any items that could not be created and why.
```

---

## Mapping Table: Document to Linear

| Document field | Linear field |
|---------------|-------------|
| Backlog item title | Issue title |
| Story acceptance criteria | Issue description |
| MoSCoW priority | Issue priority (Urgent/High/Medium/None) |
| Effort S/M/L | Story points (1/3/8) |
| Roadmap phase | Cycle |
| Epic name | Project or Label |
| Definition of Done | Issue checklist |
| Depends on (backlog) | Blocked by (Linear relation) |

---

## Notes

- Linear cycles are time-boxed — map roadmap "Now" to current cycle dates
- If roadmap uses Q1/Q2/Q3 format, map to 3-month cycles
- Labels should be created in Linear before import if they don't exist
- For teams using sprints, map each sprint to a 2-week cycle
- ADR items that block development should be created as Chores in the current cycle
