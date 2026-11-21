# Mathematical research rules

Version: 0.6.1

Use these rules to start a research round, redo a completed round, or resume an interrupted round.
They also apply to paper integration, route reviews, and updates to the register of contributed material.
Before work starts, read this file and the active research `SKILL.md` to confirm that their full versions match.
If you cannot confirm the match, stop. Report the paths, available versions, and reason to the user.

Use the entry procedure in the skill for the optional `PROJECT_RULES.md` in the project root.
For a redo, use the original round's fixed inputs and project rules as specified in section 2 of the skill.
Treat requests to edit these instructions as document work.

## Roles and mathematical admission

| Role | Authority |
| --- | --- |
| controller | Read sources, plan routes, assign pairs, and manage budgets. Maintain shared records, publish admitted facts, and compile papers. Do not prove, repair, or judge mathematical claims. |
| researcher | Find original sources. Admit faithful extracts through `LITERATURE` with their exact source locations and full conditions. Send new deductions to a pair. |
| worker | Develop the assigned proof, counterexample, or report. Submit fixed versions and repairs to the assigned verifier. Never approve your own work. |
| verifier | Examine only the fixed submission from the assigned worker. Admit supported claims through `DERIVED`. Return defects and new deductions to the worker. |

Use only these two admission channels. Each pair has one fixed worker and one fixed verifier.

During a route review, researchers propose routes and report literature leads. The controller compares their proposals and writes the summary.
Make no `LITERATURE` or `DERIVED` admissions during a route review.

For a material update, the controller works alone. Use section 14 of the skill to maintain `human/STATUS.md`.
During research, the controller also records each use of a registered item as specified in section 2.

Use Codex subagents for the researcher, worker, and verifier roles.
For each launch or replacement, specify the task, applicable rules, permitted inputs, and output paths.
Apply these limits to inherited conversations, messages, and file access.
If the parent conversation contains excluded material, start the role in a fresh context.
Use `fork_turns: "none"` or its equivalent. Give a replacement only the permitted records it needs.

Use fresh contexts for independent drafts in route reviews and for independent research and review in a redo.
Assign a check of an old proof step to a fixed pair in the new round.
If capacity limits parallel work, run the roles in sequence.
If a required role cannot run, report the limitation and keep its duties with that role.

Only one controller at a time may write shared project records.
Assign identifiers, change shared control files, and publish graph versions in sequence.
Subagents can search, develop proofs, and review submissions in parallel.

## Subagent model settings — controller

After the release check, use the skill to set up the new round, paper task, or route review.
Before the first subagent starts, look for `SUBAGENT_MODELS.json` in the research project root.
If the file exists, read the entire file once. Check its contents.
For same-round recovery, use section 9 of the skill.

The file is a JSON object. Its only role keys are `researcher`, `worker`, and `verifier`.
Each role entry is an object with optional `model` and `reasoning_effort` fields.
Each supplied value must be a nonempty string. Use the exact model ID and an effort level that it supports.

For each field, first use the user's explicit instruction within its stated scope. Otherwise, use the project value for that role.
If neither supplies a value, use the Codex default. An absent file or role supplies no values.

For a round or paper task, save the validated requests under `subagent_models` in `ROUND.yaml` or `PAPER.md`.
Use `{}` when all roles use Codex defaults.
For a single-launch exception in these tasks, record the role and the specific assignment or subagent ID.

For each task, pass the selected values as launch arguments. Apply a single-launch exception only to that launch.
If explicit settings require a fresh context, use one (`fork_turns: "none"`).
For rounds and paper tasks, record actual settings separately if the runtime reports them. Otherwise, leave the actual settings unknown.

Treat an unreadable file, invalid JSON, unknown keys, or invalid settings as a configuration error.
If Codex cannot apply a setting or reports a different value for it, treat this as a configuration error.
A known conflict with a native Codex agent setting is also an error.

If a configuration error occurs, follow the procedure for the current task.

- For a research round, pause the entire round. Follow section 9 of the skill to record the pause.
- For a paper task, stop the entire task. Follow section 10 of the skill to record that delivery is incomplete.
- For a route review, stop the task. Send stop requests to its active researchers. Keep completed work as specified in section 13 of the skill.

Do not automatically select a different model or effort level.
Report the task, configuration source, and cause to the user. Include the path, role, field, and requested value when known.
