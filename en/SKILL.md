---
name: math-research
description: Run or resume mathematical research with a controller, researcher, and fixed worker-verifier pairs. Use for literature research, proof routes, paired review, round records, and handoffs.
---

# Mathematical research procedure

## 1. Entry and project layout

Before this procedure, read the instructions that apply to that project.
When the user requests research or its continuation, use this procedure.
Do not start research only because the user edits these instructions.
The project rules give roles, admission rules, budgets, and result meanings.
Use the section for your assigned role and the necessary task records.

Use the project root as the base for all persistent paths.
Use the user's time zone for dates.
The project default is `Asia/Shanghai`.
Number rounds consecutively across the project.
When work continues on a different date, keep the creation date in the round name.

The tree shows permitted locations. Create files only at the necessary research stage.
`R003`, `R003P01`, `L001`, and the date are examples.

```text
project/
  README.md
  CURRENT.yaml
  additional_papers/
  rounds/
    yyyy_mm_dd_roundNNN/
      PROBLEM.md
      ROUND.yaml
      ROUTES.md
      CHECKPOINT.yaml
      code/R003P01/
        work/
        runs/E001/                  # RUN.yaml, fixed code, inputs, outputs
      audit/
        EVENTS.jsonl
        recovery/RECOVERY_001.md    # For a detailed recovery record
      fact_graph/
        HEAD.yaml
        snapshots/R003_G0000.json
      src/                         # main.tex, references.bib, CLAIMS.yaml
      out/                         # paper.pdf, BUILD.yaml
      research_papers/
        RESEARCH.md
        SOURCES.yaml
        pdf/L001__short-title.pdf
      pairs/R003P01__route-name/
        TASK.md
        drafts/
        submissions/v01/SUBMISSION.md
        reviews/v01/REVIEW.md
      final/
        START_HERE.md
        RESULT.yaml
        PROBLEM.md
        FACTS.json
        FRONTIER.md
      temp/
```

Keep these nine round-directory functions.
Empty directories are optional.
Do not create empty proofs, reviews, PDFs, or future submission versions.

Use stable identifiers such as these:

| Object | Example |
| --- | --- |
| Target and revision | `T001@r1` |
| Logical pair | `R003P01` |
| Route | `ROUTE00301` |
| Formal submission | `R003P01/v02` |
| Fact and revision | `F0042@r1` |
| Graph snapshot | `R003-G0007` |
| Literature source | `L001` |
| Computation run | `R003P01/E001` |

The pair identifier keeps its original round prefix across subsequent rounds.
An agent session identifier is only an additional reference.
It does not replace the logical role or pair identifier.
For historical evidence, refer to fixed records with their identifiers, versions, and actual paths.
`CURRENT.yaml`, `HEAD.yaml`, and `final/` are changeable entry points.
They are not sufficient identifiers for fixed historical evidence.

## 2. Start or resume a round — controller

1. Read the user's target, limits, changes, and interruption report.
2. For a pause entry or recovery of an earlier round, use section 9.
3. If `CURRENT.yaml` is available, read it.
4. Read the latest handoff in this order: `START_HERE.md`, `RESULT.yaml`, `PROBLEM.md`, then `FRONTIER.md`.
5. Read the full fact records necessary for the current task.
6. Use the user agreement to select the same round or a new round.
7. Record the exact target and the adopted policy in the control files.
8. Save a full initial fact snapshot with the applicable inherited facts.
9. After you save the full snapshot, update the graph entry points.
10. Assign the literature task to the researcher.

If there is no earlier state, initialize the project records.
An initial graph can contain no accepted results.
A new conversation does not automatically create a new round budget.
Do not read `additional_papers/` during routine startup or recovery.

Use these record contents:

| Record | Required information |
| --- | --- |
| `README.md` | Project purpose, rule locations, date and path conventions, adopted policy location, reading order, supplementary-paper rule, deferred features. No separate progress ledger. |
| `CURRENT.yaml` | `project_id`, `current_round`, `current_fact_head`, `latest_handoff`. Do not fill a path before its target is available. |
| `PROBLEM.md` | Original question, exact target, identifier and revision, objects, quantifiers, ranges, hypotheses, conclusion, definition references, additional requests, uncertainties, changes. |
| `ROUND.yaml` | Round identifier, creation time, previous round, target revision and path, input graph identifier and path, budgets, started pair identifiers, adopted policy, user-instruction references. |
| `ROUTES.md` | Route identifier, purpose, core method, source material, accepted inputs, differences from other routes, proof gaps, pair assignment, result or stop reason. |
| `CHECKPOINT.yaml` | Last full graph, submissions, completed reviews, pending reviews, accepted results awaiting entry, open requests, draft or code paths, next action. |

Use `max_pairs`, `max_formal_submissions_per_pair`, and `started_pair_ids` for the budget fields.
Record cumulative results, the approved partial-result scope, and project-level novelty in the policy.
Record pair counting and submission counting across rounds in the policy.
Calculate counts from the formal records.
Do not maintain a second independent budget ledger.

If the target changes, save a new problem version such as `PROBLEM_r02.md`.
Point `ROUND.yaml` to the version in use.
Do not make the controller prove equivalence between target versions.

## 3. Literature research — researcher

1. Search for previous results, limits, counterexamples, corrections, and open directions.
2. Read the source text and the context necessary for each result.
3. Record source metadata in `research_papers/SOURCES.yaml`.
4. Extract the full definitions, hypotheses, quantifiers, ranges, and conclusions.
5. Record the exact source location and the notation changes for each fact.
6. Accept faithful literature facts through `LITERATURE`.
7. Record the research boundary, target gaps, accepted fact identifiers, and search limits in `RESEARCH.md`.
8. Send full admission records and route material to the controller.

Search snippets are leads, not sufficient evidence for a full theorem.
If the source is insufficient, keep the item as a lead.
Do not accept conjectures or experimental observations as proved theorems.
For a proved claim, record its proof location or the proof source cited by the text.
Proof locations are not necessary for definitions alone.
This source check does not include a new proof of the result by the researcher.

Each source record contains its identifier, title, authors, year, link or document identifier, version, retrieval time, and access limits.
If available, include the actual PDF path or a different location for source text.
Keep a different source record for each revision.
When subsequent rounds use the same source version, use the same source identifier and PDF.
Do not create placeholder PDFs.

Notation changes must keep the mathematical meaning unchanged.
Keep quantifier order, parameter ranges, norms, topology, regularity, uniformity, and constant dependencies unchanged.
If a deduction is necessary for a change, submit the original fact with a request for a pair task.

If a literature result directly settles the target, give a clear target correspondence record.
The controller can then report the result without a proof pair.
Additional requests for a new proof or a stronger result stay separate tasks.
Report an unsuccessful search only in its actual search scope.
Do not claim global novelty from a search without a match.

When the user names supplementary papers, read only the requested material in `additional_papers/`.
Record actual use in `RESEARCH.md` and `SOURCES.yaml`.
Keep the original user paths and filenames.
The papers can stay at their original paths.
Subsequent use of accepted facts does not make another directory scan necessary.

## 4. Assign different routes — controller

1. Compare candidate routes by their primary construction, reduction, and proof method.
2. Before work starts on duplicate plans, remove those plans.
3. Select tasks in the unused round slots.
4. Create a `TASK.md` for each pair that will start.
5. Give the worker its task and permitted fact versions.
6. Bind a separate verifier to that worker.
7. When proof or review work starts, record the pair in `started_pair_ids`.

Shared background theorems do not make two routes identical.
Keep proposed bridges and expected lemmas as unproved targets.
For a different core method in an active route, count the new work as a new pair.
Repairs to the same method stay in the existing pair.

`TASK.md` contains the pair identifier, route identifier, creation round, fixed role identifiers, target, scope, and submission limit.
Include the initial graph version, input facts, core method, different features, proof gaps, expected output, constraints, and stop conditions.
Keep a record of material changes to the task.
Do not distribute another pair's unaccepted proof as an input.

## 5. Submit and review — worker and verifier

### Worker procedure

1. Read your `TASK.md`, the permitted facts, and your pair's previous review.
2. Develop the assigned route with the recorded hypotheses.
3. Save useful drafts and specific failed steps in your own `drafts/` directory.
4. Request missing external facts from the researcher through the controller.
5. If the core method must change, report the proposed change to the controller.
6. Prepare the next formal submission in the remaining budget.
7. Fix the submission content in `submissions/vNN/`.
8. Send the exact version to the fixed verifier.

Use `v01` for the first submission and `v02` through `v04` for repairs.
Put the proof in `SUBMISSION.md` or in a clearly identified `proof.tex`.
Keep one authoritative proof body for each submission.

Record the formal delivery time, pair, worker, version, target revision, and numbered claims.
Include full statements, hypotheses, fact versions, the full argument, computations, changes, and unfinished work.
For repairs, record the response to each review defect and the effect of the change.
Do not edit a fixed submission during review.

### Verifier procedure

1. Read the fixed submission of your assigned worker and its exact dependencies.
2. Examine the claim against the target and all hypotheses.
3. Examine fact availability, versions, and applicability.
4. Examine each necessary deduction for gaps and circular support.
5. Examine quantifiers, constant dependencies, uniformity, and applicable boundary cases.
6. If the argument uses computation, examine computational coverage and precision.
7. For a counterexample, examine the original hypotheses and the failure of the original conclusion.
8. Write `reviews/vNN/REVIEW.md` for that exact submission.

The review records the verifier, pair, submission version, paths, scope, decision, and reasons.
Use the review decisions `ACCEPT`, `REWORK`, or `INCOMPLETE`.
These are review decisions, not round states.
List exact accepted claims, their dependencies, target coverage, rejected steps, locations, reasons, and remaining obligations.
With a full basis and a clear scope, accept an independent local result.
A request for repairs to the whole proof does not cancel that local acceptance.

Use necessary recalculation or diagnostic counterexamples for review.
Do not silently complete the worker's proof.
For subsequent submissions, reuse checks of unchanged, unaffected parts.
Give a decision for the current version.

After four formal submissions, stop more submissions unless the user clearly adds a budget.
Keep accepted local results and the remaining obligations.
For correction of a completed review, keep the previous report. Add a clear correction.

## 6. Publish accepted facts — controller

1. Examine the identity and exact scope of each researcher or verifier admission decision.
2. Copy only the accepted content into the next full graph snapshot.
3. When applicable, record corrections, support changes, and affected dependencies.
4. Save the snapshot with a new graph identifier.
5. Point `fact_graph/HEAD.yaml` to the full snapshot.
6. Point `CURRENT.yaml` to the current graph entry point.
7. Record the event.
8. Update the checkpoint.

Each snapshot contains its graph identifier and full cumulative fact records.
Each fact record contains:

- Stable identifier, revision, and object type.
- Full statement, quantifiers, conditions, parameter ranges, definitions, notation, and scope.
- Direct dependency identifiers and revisions.
- Source type: `LITERATURE` or `DERIVED`.
- Exact source, or submission claim and review location.
- The responsible researcher or fixed verifier.
- Current availability, reasons for restrictions, and correction or replacement relations.
- Separate support records when the claim has more than one accepted basis.

`HEAD.yaml` contains `graph_id` and `snapshot_path`.
After admission or changes to accepted statements, support, or availability, publish a new graph snapshot.
Draft edits and rejection of an unaccepted claim do not make a new snapshot necessary.
You can publish a small group of admission records together.
Keep previous snapshots unchanged.
New fact versions do not automatically invalidate previous versions or transfer previous proofs to new statements.

Record important events in `audit/EVENTS.jsonl`.
Each event contains its identifier, time, responsible role, action, object identifiers, evidence paths, and necessary explanation.
Refer to the original review. Do not copy a second decision into the event record.
After formal delivery, completed review, graph publication, or planned interruption, update the checkpoint.
Do not save every edit, tool log, or conversation step.

## 7. Computations, papers, and unresolved issues

For a computation used as evidence, keep fixed code, inputs, and outputs in `code/PAIR_ID/runs/RUN_ID/`.
In `RUN.yaml`, record the run, pair, submission, purpose, command, environment, dependency versions, input method, output paths, and limitations.
When applicable, record random seeds.
Keep exploratory observations separate from proof claims.
The worker supplies the mathematical justification for exhaustive search, exact arithmetic, or rigorous numerical bounds.
The verifier reviews that justification.

For a requested paper, use `src/main.tex`, `references.bib`, and `CLAIMS.yaml`.
Map paper labels to exact fact versions and proof locations in `CLAIMS.yaml`.
Keep open claims clearly identified as open.
The controller can arrange existing text and compile the paper.
Give new mathematical connections to a pair.

For a published PDF, save `out/paper.pdf` and `BUILD.yaml`.
Record the build time, fixed source location, graph version, command, and necessary tools.
Keep separate source records for separate published versions.

Record issues with stable identifiers in `FRONTIER.md` and references in `RESULT.yaml`.

| Issue type | Required record and action |
| --- | --- |
| `MISSING_SPECIFICATION` | Missing target information, its effect, searched sources, reason the researcher cannot supply it, affected tasks, and the necessary user input. |
| `LITERATURE_CONFLICT` | Exact conflicting claims and source locations, hypotheses, quantifiers, notation, versions, affected dependencies, checks completed, and questions open. |

If definitions or versions can differ, tell the researcher to examine the source context and corrections.
If accepted sources conflict with the same conditions, stop use of the disputed support and affected dependencies.
Keep unaffected facts available.
If a new mathematical judgment is necessary, assign it to a pair in budget.
If an accepted literature counterexample directly refutes the target, record `DISPROVED` instead of an unresolved conflict.

## 8. Complete a round — controller

Complete the round for one of these reasons: a settled target, completed tasks, exhausted budget, or an agreed boundary.
Unresolved specifications or conflicts can also end the affected work with a clear explanation.
For completion without interruption, use only necessary pair slots and actual outputs. A paper or PDF is optional.

1. Record the actual reason for completion.
2. Collect formal outcomes and unfinished tasks.
3. Add accepted facts that await graph entry.
4. Save the full graph snapshot.
5. Update the graph entry points.
6. Prepare the five handoff files in the table below.
7. Examine target versions, fact versions, decisions, counts, and evidence paths against their source records.
8. After the handoff files are ready, publish the actual ending declaration in `final/RESULT.yaml`.
9. Update `CURRENT.yaml` with the latest handoff location.
10. Keep the actual paper and computation outputs with their source records.
11. Before cleanup, move necessary evidence from `temp/` to stable locations.
12. Delete only temporary material that is safe to remove.

| Handoff file | Contents |
| --- | --- |
| `START_HERE.md` | Target, exact result from `RESULT.yaml`, key facts, this round's changes, route outcomes, limits, next actions, and reading paths. |
| `RESULT.yaml` | Actual ending declaration, result evidence, scope, remaining obligations, issues, and handoff completeness. |
| `PROBLEM.md` | Copy of the target version in use, with its identifier, revision, and source path. |
| `FACTS.json` | Unchanged copy of the full source snapshot, including its graph identifier and fact availability. |
| `FRONTIER.md` | Open proof obligations, route positions, accepted local results and conditions, failed steps, source requests, issues, exact continuation paths, and remaining submission budgets. |

For known information in `RESULT.yaml`, use these fields:

- `record_type: ROUND_END`, `round_id`, target identifier and revision, and `recorded_at`.
- `result_status`, `result_scope`, `basis_fact_ids`, and evidence locations.
- `new_results_this_round`, `scope_note`, and `remaining_obligations`.
- `source_graph_id`, `issues`, `handoff_complete`, and `missing_files`.
- Pause and recovery fields from section 9 when applicable.

Use a clear literature correspondence or verifier decision as the result basis.
Keep changes in `START_HERE.md` and evidence paths in the existing records.
Do not make separate delta or automatic index files necessary.
The handoff must give sufficient information about the round without the full conversation history.
For detailed source checks, use references to evidence beyond `final/`.
Before future use of a historical fact, examine its current availability through `CURRENT.yaml`.

Keep failed proofs, rejected submissions, reviews, snapshots, and drafts necessary for recovery.
Do not delete user papers as temporary material.
Do not start a new round without the user's instruction or an existing agreement.

## 9. Pause and recover — controller

### Immediate stop

1. When the user tells you to stop immediately, stop new research work.
2. Send stop requests to active subagents.
3. Save the available minimum pause information in `final/RESULT.yaml`.

Record the round, `run_status: PAUSE`, trigger, actual record time, and handoff completeness.
Include known results, their evidence, the last reliable graph, pending work, exact versions, used submissions, missing files, and next action.
If a value is unknown, do not include its field. Record the missing information.
Do not wait for unfinished work or a full five-file handoff.

### Add an earlier pause entry

The two bases below are independent.

| Basis | Procedure |
| --- | --- |
| `USER_REPORTED_INTERRUPTION` | Record the user's report for the identified previous round directly. If the user reports a usage limit, record `USAGE_LIMIT`. |
| `ENDING_KEYWORD_NOT_FOUND` | Record the actual accessible search scope and the absence of an actual ending declaration. Keep access failures separate. |

For the search basis, examine available ending records, handoff entries, recovery records, and ending messages for the previous round.
If the previous round used a different layout, use its ending locations.
An actual ending declaration must identify the round and announce its result or pause.
Accept the four mathematical result keywords or an actual `PAUSE` declaration in that context.

Ignore templates, rule definitions, hypothetical statements, local lemma decisions, other rounds, and intermediate progress.
If there is more than one declaration, use the applicable record version.
If no material is accessible, do not claim a search without a match.
The user's interruption report permits a pause entry when previous files are inaccessible.

Record `pause_basis`, the known `pause_reason`, `recorded_at`, and the round or session that makes the entry.
For a search, record `search_scope` and access limits.
Before the administrative addition, keep earlier result information or a clear historical copy.

If there is no previous result file, create a minimum record. Identify it as an entry made after the interruption.
Do not invent an interruption time or infer a usage limit from a missing declaration.
Use an event for a simple recovery.
For recovery details beyond an event, use `audit/recovery/RECOVERY_NNN.md`. Record evidence, unknowns, changes, and next actions.

### Continue work

1. Locate the last full, identifiable target and graph versions.
2. Recover literature admissions and completed verifier decisions from formal records.
3. Locate unfinished pairs, exact submissions, review progress, and submission history.
4. Separate accepted facts, pending drafts, and incomplete files.
5. Restore accepted results that only lack mechanical graph entry.
6. Record the selected round for continuation, in accordance with the user agreement.
7. Before research continues, save the recovery basis.

For the same round, keep all used pair slots and submission counts.
For a new round, count each pair that continues proof or review work in that round.
Keep the original pair identity, fixed roles, and cumulative submission count.
In the new pair directory, create `CONTINUE.yaml` instead of a second independent original task.

`CONTINUE.yaml` refers to the original `TASK.md`, pair, fixed roles, continued submission, last completed review, and all formal submissions.
Also record the current graph, input changes, continued scope, and counting policy.
Keep previous evidence in the previous round.
Save only new work in the new round.
Continued review of `v03` is review of `v03`.
A formal repair after that review uses `v04`.

If a new handoff replaces an earlier handoff, keep the earlier one in `audit/handoffs/HNNN/`.
When a replacement occurs, create that history directory.
Keep previous pause records in history.
Do not add a new run-status value for recovery or completion without interruption.

Do not reset unknown counts, invent missing decisions, or accept drafts during recovery.
New mathematical judgments return to the responsible role.
Recovery alone does not make another independent reviewer or new proofs of literature results necessary.
