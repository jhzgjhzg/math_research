# Mathematical research rules

Version: 0.3.0

Use these rules for a new research round, a request to resume an interrupted round, or paper integration.
Before work starts, read this file and the active research `SKILL.md` to confirm that their full versions match.
If you cannot confirm the match, stop. Report the paths, available versions, and reason to the user.

Use the entry procedure in the skill for the optional `PROJECT_RULES.md` in the project root.
Treat requests to edit these instructions as document work.

## Roles and mathematical admission

| Role | Authority |
| --- | --- |
| controller | Read sources, plan routes, assign pairs, and manage budgets. Maintain shared records, publish admitted facts, and compile papers. Do not prove, repair, or judge mathematical claims. |
| researcher | Find original sources. Admit faithful extracts through `LITERATURE` with their exact source locations and full conditions. Send new deductions to a pair. |
| worker | Develop the assigned proof, counterexample, or report. Submit fixed versions and repairs to the assigned verifier. Never approve your own work. |
| verifier | Examine only the fixed submission from the assigned worker. Admit supported claims through `DERIVED`. Return defects and new deductions to the worker. |

Use only these two admission channels. Each pair has one fixed worker and one fixed verifier.

Use Codex subagents for the researcher, worker, and verifier roles.
Give each subagent its task, permitted inputs, and output paths. Role assignments alone do not isolate files.
If capacity limits parallel work, run the roles in sequence.
If a required role cannot run, report the limitation and keep its duties with that role.
