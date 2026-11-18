# Math Research

Version: **0.3.0**

Use these instructions with Codex to run mathematical research rounds or prepare a paper from accumulated results.

| Language | Required project entry | Required research skill | Optional project rules template |
| --- | --- | --- | --- |
| English | [AGENTS.md](en/AGENTS.md) | [SKILL.md](en/SKILL.md) | [PROJECT_RULES.md](en/PROJECT_RULES.md) |
| 简体中文 | [AGENTS.md](zh-CN/AGENTS.md) | [SKILL.md](zh-CN/SKILL.md) | [PROJECT_RULES.md](zh-CN/PROJECT_RULES.md) |

## Set up or update a research project

1. Select one language and one release.
2. Copy its `AGENTS.md` to the root of the research project.
3. Use its `SKILL.md` in the research skill that Codex actually loads for that project.
4. If the project has lasting requirements, copy the optional template beside `AGENTS.md`. Fill in the sections that apply.

When you update the skill, update the project entry in each project that uses it.
The controller checks both files before a new round, same-round recovery, or paper integration.
If the check fails, use the reported paths to replace the affected files with copies from the same release.
Start the task again to repeat the check. Editing version numbers alone does not update the instructions.

## Write project rules

Maintain the root `PROJECT_RULES.md` independently of the release. Each rule needs a scope and a requirement.
Include exceptions and source references where applicable. The following examples illustrate two different restrictions.

- **Definition.** A ring in this project can lack a multiplicative identity. Before using a theorem for unital rings, check the identity hypothesis.
- **Proof restriction.** For target T, exclude the published proof of theorem A and arguments that depend on that proof. A new proof of A from the project hypotheses is permitted. Use it after mathematical admission.

For an exception limited to one task, give the exception in that task's request.
New rounds and new paper tasks use the current project rules. An interrupted round resumes with its recorded rules by default.
