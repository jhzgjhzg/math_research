# Mathematical research rules

## 1. Scope and terms

These rules apply to mathematical research in the project that uses this file.
A matching research skill is optional.
If present, use it for further procedure details.

| Term | Meaning |
| --- | --- |
| Target | The exact mathematical problem and its version. |
| Route | One proof method or one method to construct a counterexample. |
| Pair | One fixed worker and one fixed verifier for one route in one round. |
| Round | Research work with a stated target and pair limit. |
| Session | One Codex conversation or execution context. |
| Fact | A full mathematical record with its conditions and source. |
| Admission | Acceptance of a fact through one of the two permitted channels. |
| Fact graph | Facts, their versions, their dependencies, and their availability for use. |
| Submission | Fixed work that a worker formally sends for review. |
| Review | The decision of the fixed verifier about an exact submission. |
| Handoff | The records that give the round result and let subsequent work continue. |

Admission means that the responsible role accepted the fact through this workflow.

## 2. Roles

Use Codex subagents for researcher, worker, and verifier duties.
Keep the controller as the coordinator.
Give each subagent its role, permitted inputs, task, and output paths.

If agent capacity does not permit parallel work, do the tasks in sequence.
If a necessary role cannot run, report the limitation.
Do not merge proof or review duties into the controller role.
Role instructions do not create sandbox isolation.

| Role | Permitted work | Boundary |
| --- | --- | --- |
| Controller | Read source material. Plan different routes. Assign pairs. Manage budgets, files, information, and recovery. Record results from admission decisions. | Do not prove claims, decide mathematical correctness, repair proof gaps, or combine results through new deductions. |
| Researcher | Search previous work. Read sources. Extract full results. Accept faithful literature facts. Record notation changes and source limits. | Do not create new proofs or present a new deduction as a literature extract. |
| Worker | Develop one route. Write proofs or counterexamples. Do necessary computations. Submit work and repair reported defects. | Do not approve your own work or add candidate results to the accepted facts. |
| Verifier | Review only the fixed worker. Examine correctness and exact target coverage. Accept clear results or request repairs. | Do not review another worker or silently supply a missing proof in an unchanged submission. |

Within a round, keep each worker and verifier pair fixed through all repairs.
Do not change the verifier to get a different decision.
If an agent instance is lost, a replacement can continue the same role with its task and review history.
Keep the pair identity and budget unchanged.
If review work produces a new research result, send it to the worker for a clearly identified submission.

## 3. Mathematical boundaries

Keep the original question, definitions, quantifiers, parameter ranges, hypotheses, and requested conclusion in the target record.
Keep additional research requests, such as a new proof or a better bound, separate from the target status.
If the user changes the target, keep the previous version. Record the change.
If a route adds conditions or weakens the conclusion, record a separate claim.
Do not replace the original target with that claim.

If a proof is necessary for target equivalence, give that task to a pair.

Use only these admission channels:

- `LITERATURE`: The researcher accepts a faithful extract with full conditions and an exact source location.
- `DERIVED`: The fixed verifier accepts clear claims from a fixed submission of the worker.

Do not make a new proof or a second verifier necessary for each literature result.
Keep different logical types for definitions, local hypotheses, accepted theorems, conjectures, and experimental observations.
Claims about existence, uniqueness, or equivalence must have evidence, also when they accompany a definition.

Workers must use the permitted, available facts in the fact graph for existing mathematical results.
Record the rules of basic logic and the mathematical conventions for the project.
Do not make a fact node necessary for each arithmetic step.
Request missing external results from the researcher.
Do not use model memory, another worker's draft, or a route proposal as an accepted premise.

Full local deductions can occur in a proof during review.
Before another task uses a local result as an existing fact, get its admission.

Send accepted facts, source requests, route scopes, and administrative progress between pairs.
Keep unaccepted proofs in their pair and the controller's administrative scope.
For use by a different route, send a candidate claim as a target to prove.

If a new deduction must combine accepted results, assign the deduction to a pair in the round budget.
Within the same round, the original pair can complete this work in its route and remaining submission budget.
For a new core method, use a new pair.
A summary cannot replace a combination proof.
To use `L ⇒ T` as a proof of `T`, first supply accepted support for `L`.

Record exact fact versions in each submission.
If fact inputs change, record the new dependencies clearly.
Do not use a known invalid or disputed premise because a previous snapshot contains it.
Do not use circular proof dependencies as evidence.
Mutual implications or joint induction must have a clear proof.

A defective proof does not establish that its claim is false.
Keep the claim separate from its individual sources of support.
Stop use of affected support. Stop use of dependent results that have no accepted, applicable support.

If existing records establish applicability, keep other accepted support for the exact claim.
Send new mathematical judgments to the responsible researcher or pair.
Keep the history and reason for each change.

Computations do not automatically prove general claims.
For a proof that depends on computation, the worker must justify its coverage, precision, and sufficiency.
The verifier must examine that justification.
A program run without errors or a PDF build is not a mathematical review.

## 4. Budgets and result policy

Use the defaults below unless the user specifies different values or result rules.
Record the adopted policy in `ROUND.yaml`.
Apply clear user changes to that policy.

| Item | Default |
| --- | --- |
| Pair limit | 4 in each round. A round can specify 3 as an alternative. |
| Pair count | All different pairs that do proof or review work in that round. |
| Submission limit | 1 first submission and 3 repairs. Maximum: 4 for each pair. |
| Submission history | The count continues across pauses and sessions within the same round. New rounds start with new pairs and counts. |
| Result scope | Cumulative progress for the exact target through this round. |
| New result | A related result derived and accepted in this project. Global novelty is a separate claim. |
| Partial result | An accepted restricted result, substantial lemma, weaker conclusion, partial parameter result, or rigorous reduction. |

New exploration, combination proofs, and separate lemma tasks use round slots.
Repairs and resumed work in the same pair do not use another slot.
Literature work, route plans, previous fact reads, and administrative recovery do not use pair slots.
Completed or failed pairs do not return slots.

The pair limit is not a limit on concurrent agents.
One slot can stay available for subsequent tasks. Its use is optional.

When the worker formally sends a fixed version for review, count one submission.
Draft edits, repeated delivery, continued review, and formatting alone do not increase the count.
After changes to claims, hypotheses, dependencies, or proof content, use a new version for the next formal submission.
Within a round, do not reset counts through a rename, a new session, or a replacement agent.

Before resumed work uses remaining budget, recover unknown counts.
Before you exceed a pair's submission limit, get a clear user agreement. Keep the pair's history.
A new session alone does not create a new round budget.
Before automatic work across rounds, get a user agreement.

Use only these mathematical result values:

| Value | Required evidence |
| --- | --- |
| `PROVED` | An accepted proof or an exact literature match establishes the original target. |
| `DISPROVED` | An accepted refutation applies to the original target. A counterexample satisfies its hypotheses and violates its conclusion. |
| `PARTIALLY_RESOLVED` | The original target stays open. Accepted project results meet the partial-result rule. |
| `UNRESOLVED` | The original target stays open. No accepted project result meets the partial-result rule. |

List results added in this round separately.
Report the completion of additional research requests separately.
Failure of a proof, exhausted budgets, and searches without counterexamples do not establish a refutation or a proof.

Keep added conditions clear.
Unknown results are not `UNRESOLVED`.
If the result is unknown, do not include `result_status`. Record the missing evidence.

Keep `MISSING_SPECIFICATION` and `LITERATURE_CONFLICT` in `issues`, separate from mathematical results.
Missing proof steps are not missing problem specifications.
Stop only tasks that depend on the missing information or disputed facts.
Do not invent the intended question or select a side in a mathematical conflict as controller.
Report inconsistent target hypotheses clearly.

## 5. Records

The controller alone updates shared control files and publishes fact graph snapshots.
Copy admission decisions without changes to their mathematical content.
Keep formal submissions, completed reviews, and published snapshots unchanged.
Use new versions or clear correction records for changes.

Use stable identifiers and project-relative paths in persistent records.
Keep submission versions, fact versions, and graph versions separate.
Before a new use of historical facts, examine their current availability through `CURRENT.yaml`.
Keep checkpoints subordinate to actual formal records.

Use the project root as the base for persistent paths.
Use the user's time zone for dates. The default is `Asia/Shanghai`.
Name rounds `rounds/yyyy_mm_dd_roundNNN/` with consecutive project-wide numbers and the creation date.

At each research stage, create only the necessary files. Empty directories are optional.
Do not create empty proofs, reviews, PDFs, or future submission versions.

Keep these records at the project root or the round root:

| Location | Record | Required contents |
| --- | --- | --- |
| Project | `README.md` | Purpose, rule locations, date and path conventions, policy location, reading order, supplementary-paper rule, deferred features. No separate progress ledger. |
| Project | `CURRENT.yaml` | `project_id`, `current_round`, `current_fact_head`, `latest_handoff`. Set paths only after their targets are available. |
| Round | `PROBLEM.md` | Full target from section 3, identifier, revision, additional requests, uncertainties, and changes. Keep previous target versions at separate paths. |
| Round | `ROUND.yaml` | Round, creation time, previous round, target version and path, input graph, user instructions, policy, budgets, and started pairs. |
| Round | `ROUTES.md` | Route identifiers, core methods, differences, accepted inputs, proof gaps, pair assignments, results, and stop reasons. |
| Round | `CHECKPOINT.yaml` | Last full graph, formal submissions, completed and pending reviews, accepted facts awaiting entry, open requests, work paths, and next action. |

Use `max_pairs`, `max_formal_submissions_per_pair`, and `started_pair_ids` for budget fields.
Calculate counts from the current round's formal records. Do not maintain a second independent budget ledger.

Keep these nine directory functions in each round:

| Directory | Records and purpose |
| --- | --- |
| `code/` | Pair work and fixed computation evidence in `PAIR_ID/runs/RUN_ID/`. Use `RUN.yaml` for commands, environment, dependencies, inputs, outputs, seeds, and limits. |
| `audit/` | Important events in `EVENTS.jsonl`. Detailed recovery in `recovery/RECOVERY_NNN.md`. Replaced handoffs in `handoffs/HNNN/`. |
| `fact_graph/` | Full cumulative snapshots in `snapshots/`. `HEAD.yaml` contains `graph_id` and `snapshot_path`. |
| `src/` | Optional paper sources: `main.tex`, `references.bib`, and `CLAIMS.yaml`. Map claims to exact facts and proof locations. |
| `out/` | Optional `paper.pdf` and `BUILD.yaml`. Record fixed source paths, graph version, build time, command, and tools. |
| `research_papers/` | `RESEARCH.md` for findings, gaps, admitted facts, and search limits. `SOURCES.yaml` for source metadata. Available source PDFs in `pdf/`. |
| `pairs/` | One directory per pair: `TASK.md`, `drafts/`, `submissions/vNN/SUBMISSION.md`, and `reviews/vNN/REVIEW.md`. |
| `final/` | The five handoff files in section 6. |
| `temp/` | Temporary material. Move necessary evidence to stable paths before cleanup. |

In each source record, include its identifier, title, authors, year, version, link or document identifier, retrieval time, and access limits.
Include the available file path.
For literature facts, record exact statement locations and notation changes.
For proved claims, record proof locations or cited proof sources.

Read source text and context. Search snippets alone are insufficient.
Keep mathematical meaning unchanged during notation changes.
If a deduction is necessary for a change, give that task to a pair.

In `TASK.md`, record the pair, fixed roles, route, target, scope, permitted fact versions, method, expected outputs, constraints, and submission limit.

In each submission, record its pair, worker, version, delivery time, target version, numbered claims, hypotheses, dependencies, and full argument.
Include computations, changes, unfinished work, and responses to previous defects.

In each review, record its verifier, exact submission and path, scope, decision, reasons, admitted claims, dependencies, and remaining obligations.
Use `ACCEPT`, `REWORK`, or `INCOMPLETE` for review decisions.
These decisions are not round results.
Accept an independent local result only when its evidence is complete and its scope is clear.
Rework of other claims does not cancel that admission.

In each fact record, include its identifier, revision, logical type, full statement, definitions, conditions, scope, and exact dependencies.
Include its admission channel, source location or submission claim, admission decision, responsible role, availability, and correction history.
Keep separate records for different accepted support of the same claim.

After admission or a change to accepted facts, support, or availability, save a new full graph snapshot.
Then update `HEAD.yaml` and `CURRENT.yaml`.
Record important events with time, responsible role, object identifiers, and evidence paths.
After formal delivery, completed review, graph publication, or planned interruption, update the checkpoint.
Keep original decisions in their source records.

You can create an empty project-level `additional_papers/` directory.
Keep existing user files unchanged.
Do not list, scan, read, or monitor this directory as a routine action.
When the user mentions supplementary papers in a prompt, read only the material covered by that request.
The researcher records actual use and applies the admission rules.
Do not delete these papers during temporary file cleanup.

Keep necessary role checks and mathematical computation code.

## 6. Research sequence and handoff

A new round accepts only user requirements, `CURRENT.yaml`, the current fact graph, and the latest `final/` summary.
Do not read previous pair directories, submissions, reviews, drafts, or checkpoints to start a new round.
Use section 7 to record a previous pause or resume an interrupted round.
A pause entry alone does not make execution recovery necessary.
Before new-round setup, complete any necessary confirmation from section 7.

1. Read the target, user limits, and available `CURRENT.yaml`.
2. Read the latest handoff and full facts necessary for the task.
3. If the recovery conditions apply, use section 7 instead of the new-round steps below.
4. Record the new round, exact target, adopted policy, new budgets, and initial full fact snapshot.
5. Assign literature research and record its admissions.
6. Select different core routes within the pair limit.
7. Give each worker its task, permitted facts, and fixed verifier.
8. Record each pair when its proof or review work starts.
9. Submit fixed work for review within the submission limit.
10. Publish admitted facts with their exact scope and dependencies.

For each new round, set `started_pair_ids` to `[]`.
Create new pair identifiers, role assignments, and `TASK.md` records.
Start each pair's submission sequence at `v01`.
Do not transfer previous pairs, pending reviews, or used submission counts into the new round.
Keep inherited facts with their original identifiers, revisions, and source references.

If literature directly settles the target, record the exact target correspondence.
No proof pair is necessary for that result.
Keep additional research requests separate.

End the round for a settled target, completed tasks, exhausted budget, or an agreed boundary.
Unresolved specifications or conflicts can also end affected work with a clear explanation.
For completion without interruption, use these five files in `final/`:

| File | Required contents |
| --- | --- |
| `START_HERE.md` | Target, exact result, key facts, changes in this round, route results, limits, next actions, and reading paths. |
| `RESULT.yaml` | Ending declaration, result and evidence, scope, new results, remaining obligations, issues, source graph, record time, and handoff completeness. |
| `PROBLEM.md` | Copy of the target version in use, with its identifier, revision, and source path. |
| `FACTS.json` | Unchanged copy of the full source snapshot, with its graph identifier and fact availability. |
| `FRONTIER.md` | Open proof obligations, route outcomes, accepted partial results and conditions, failed steps, source requests, issues, and candidate targets. |

1. Collect formal results and unfinished tasks.
2. Publish accepted facts that still await graph entry.
3. Prepare the handoff from that full graph and the formal records.
4. Examine target versions, fact versions, decisions, counts, and evidence paths against their sources.
5. When the handoff is ready, publish the actual ending declaration in `final/RESULT.yaml`.
6. Update `CURRENT.yaml` with the latest handoff path.
7. Keep necessary evidence before temporary file cleanup.

In `RESULT.yaml`, use `record_type: ROUND_END`, `round_id`, the target identifier and revision, and `recorded_at`.
Include known `result_status`, `result_scope`, `basis_fact_ids`, `new_results_this_round`, `scope_note`, `remaining_obligations`, `source_graph_id`, `issues`, `handoff_complete`, and `missing_files`.

Use explicit literature correspondence or verifier decisions as evidence.
The handoff must support a new round without previous execution records or the full conversation history.
Keep unresolved ideas as candidate targets. Only admitted facts can serve as existing premises.

Evidence can remain at its actual paths outside `final/`.
During research, read cited evidence only for a specific source check.
Keep failed proofs, rejected submissions, reviews, snapshots, and drafts necessary for recovery.
Do not start another round without the user's instruction or an existing agreement.

## 7. Interruption and recovery

`PAUSE` is the only value of `run_status`.
For work and completion without interruption, do not include `run_status`.
Budget exhaustion alone does not mean interruption.
When a pause occurs, keep an established mathematical result.

If the user tells you to stop immediately, stop new work. Send stop requests to active subagents.
Save only the available minimum pause record in `final/RESULT.yaml`.
Do not wait for proofs, reviews, a full handoff, a PDF, or cleanup.

Record the round, `run_status: PAUSE`, trigger, actual record time, and handoff completeness.
Include known results, evidence, last reliable graph, pending tasks, exact versions, used submissions, missing files, and next action.
For unknown values, omit the fields and record the missing information.

If the user reports an earlier interruption, add `PAUSE` to the identified round directly.
Do not add a prerequisite investigation or keyword search.
Use `pause_basis: USER_REPORTED_INTERRUPTION`.
If the user reports a usage limit, record `pause_reason: USAGE_LIMIT`.

An actual search without an ending declaration also permits a subsequent pause entry.
Use `pause_basis: ENDING_KEYWORD_NOT_FOUND` and record `search_scope`.
At new-round startup, search only user-provided ending messages and the previous round's accessible handoff records.
Use `CURRENT.yaml` to locate that handoff.
An actual ending declaration identifies the round and announces its mathematical result or `PAUSE`.

Ignore templates, rule definitions, hypothetical statements, local lemma decisions, other rounds, and intermediate progress.
Use the latest applicable record to determine whether that round remains interrupted.
An access failure is not a search without a match.
If no records are accessible, do not claim a search without a match.

Record access limits and the actual basis and time of a subsequent entry.
Keep earlier result information or a historical copy before this addition.
If the result file is absent, create a minimum record identified as a subsequent entry.
Do not invent the cause or time of interruption.

After you add `PAUSE` with `pause_basis: ENDING_KEYWORD_NOT_FOUND`, apply this confirmation rule.
If the current prompt does not request that round's continuation, ask whether to resume it or start a new round.
This confirmation also applies when the current prompt requests a new round.
After you ask, wait for the user's choice before execution recovery or new-round startup.

Recover execution records only when both conditions hold:

- The latest applicable pause record or the user's report identifies the previous round as interrupted.
- The current task is to continue that same round.

After any necessary confirmation, use section 6 for a requested new round with new pairs and budgets.
If the intended round is unclear, ask the user before you read execution records.
During recovery, read only the interrupted round's execution records.

1. Locate the last full target and graph versions.
2. Recover admissions, completed reviews, unfinished pairs, exact submissions, and counts from formal records.
3. Separate accepted facts, pending drafts, and incomplete files.
4. Publish accepted results that only lack mechanical graph entry.
5. Continue in the existing round and pair directories.
6. Before research continues, record recovery evidence, unknowns, changes, and next actions in `audit/`.

Keep the original round identifier, pair identities, fixed roles, used pair slots, and submission counts.
Continued review of `v03` stays at `v03`. A formal repair uses `v04`.

Before a new handoff replaces an earlier one, save the earlier handoff in `audit/handoffs/HNNN/`.
Keep previous pause records in that history.
Do not reset unknown counts, invent missing decisions, or accept drafts during recovery.
Send new mathematical judgments to the responsible role.
