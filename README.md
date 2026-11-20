# Math Research

Version: **0.5.0**

Use these instructions with Codex to run mathematical research rounds, review alternative routes, or prepare a paper from accumulated results.
You can also register ideas, proof drafts, and unpublished manuscripts for use in these tasks.

| Language | Required project entry | Required research skill | Optional project rules template |
| --- | --- | --- | --- |
| English | [AGENTS.md](en/AGENTS.md) | [SKILL.md](en/SKILL.md) | [PROJECT_RULES.md](en/PROJECT_RULES.md) |
| 简体中文 | [AGENTS.md](zh-CN/AGENTS.md) | [SKILL.md](zh-CN/SKILL.md) | [PROJECT_RULES.md](zh-CN/PROJECT_RULES.md) |

## Set up or update a research project

1. Select one language and one release.
2. Copy its `AGENTS.md` to the root of the research project.
3. Use its `SKILL.md` in the research skill that Codex actually loads for that project.
4. For lasting research requirements, copy the optional `PROJECT_RULES.md` template beside `AGENTS.md`. Fill in the sections that apply.
5. To create a project model file, copy the shared JSON template beside `AGENTS.md`. [SUBAGENT_MODELS.json](SUBAGENT_MODELS.json)

When you update the skill, update the project entry in each project that uses it.
The controller checks both files before each research round, recovery, paper task, route review, or material update.
If the check fails, use the reported paths to replace the affected files with copies from the same release.
Start the task again to repeat the check. Editing version numbers alone does not update the instructions.

## Set subagent models

Both languages use the same JSON template. Keep the roles and fields that you want to set.
Use the model ID in `model` and the reasoning level in `reasoning_effort`. The main agent uses its own session settings.
For a change to one subagent launch, identify the subagent and the requested settings in the task request.

New tasks use the current project settings. An interrupted round uses its recorded choices unless you explicitly request a change.
A native Codex agent file can override a launch setting. Keep its settings consistent with your project choices.

On a configuration error, the controller pauses the entire research round and reports the cause.
After correction, ask to resume that round with the corrected settings. For an incomplete paper task, request a new integration.
For a route review, the controller stops the review and its active researchers, keeps completed work, and reports the cause.

## Request a route review

Ask for alternative ways to prove or disprove the original claim. Two researchers first develop independent proposals.
The controller can assign a third researcher to search the literature or explore another approach.
Each review has its own directory. For example, `route_reviews/REVIEW001/REVIEW001.md` contains the summary and links to the researchers' records.
To use a proposal in a new round, cite the review and, if applicable, its route number.

## Use contributed material

1. Put your manuscript in the project's `human/` directory. Keep your own filename.
2. Ask, “Register `human/notes.md` for project research only.” The controller runs a separate material update and reports the item identifier.
3. Use that identifier in a later request, for example, “In the next round, try the induction in `H007`.”

`human/STATUS.md` gives the registered versions, use history, retry conditions, and permitted uses.
Use `H007@r1` to select a specific revision. A request for `H007` selects the latest fully registered revision.
You can also request the update and the next research task together. The controller completes the update first.
For an unpublished manuscript, specify any permission for public use and how to credit the author.

For lasting writing preferences, use the optional project file `TASTE.md`. For example, “In a paper, explain what the key substitution removes.”
The controller gives applicable preferences to writers and reviewers before they start this work.

## Write project rules

Maintain the root `PROJECT_RULES.md` independently of the release. Each rule needs a scope and a requirement.
Include exceptions and source references where applicable. The following examples illustrate two different restrictions.

- **Definition.** A ring in this project can lack a multiplicative identity. Before using a theorem for unital rings, check the identity hypothesis.
- **Proof restriction.** For target T, exclude the published proof of theorem A and arguments that depend on that proof. A new proof of A from the project hypotheses is permitted. Use it after mathematical admission.

For an exception limited to one task, give the exception in that task's request.
New rounds, paper tasks, route reviews, and material updates use the current project rules.
An interrupted round resumes with its recorded rules by default.
