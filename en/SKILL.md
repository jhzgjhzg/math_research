---
name: math-research
description: Run mathematical research or integrate accumulated results into a paper. Use fixed worker-verifier pairs, literature research, originality checks, versioned facts, and handoffs. Resume interrupted research rounds only.
metadata:
  version: "0.2.0"
---

# Mathematical research procedure

## 1. Entry and project layout

Before this procedure, read the instructions that apply to that project.
When the user requests research, research continuation, or paper integration, use this procedure.
Do not start research only because the user edits these instructions.
The project rules give roles, admission rules, budgets, and mathematical result meanings.

Use sections 10 and 11 for paper integration and its originality checks.
Use section 9 only for interrupted research rounds.
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
  AGENTS.md
  README.md
  CURRENT.yaml
  fact_graph/
    HEAD.yaml
    index.jsonl
    facts/F0042/r1.json
    supports/S0017/r1.json
    graphs/G0008.json
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
        submissions/v01/PROOF_IDEA.md
        reviews/v01/REVIEW.md
      final/
        START_HERE.md
        RESULT.yaml
        PROBLEM.md
        FACTS.ref.yaml
        FRONTIER.md
      temp/
  out_papers/
    PAPER001/
      PAPER.md
      INVENTORY.md
      pairs/
      src/
        main.tex
        references.bib
        CLAIMS.yaml
      out/
        paper.pdf
        BUILD.yaml
```

Keep the eight round-directory functions and the shared project fact graph.
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
| Support and revision | `S0017@r1` |
| Project graph | `G0008` |
| Paper task and pair | `PAPER001`, `PAPER001P01` |
| Literature source | `L001` |
| Computation run | `R003P01/E001` |

Each pair belongs to one research round or one paper task.
New rounds and paper tasks use new pair identifiers.
During recovery within the same round, keep its pair identifiers.
Inherited facts keep their original identifiers, revisions, and source references.

An agent session identifier is only an additional reference.
It does not replace the logical role or pair identifier.
For historical evidence, refer to fixed records with their identifiers, versions, and actual paths.
`CURRENT.yaml`, `HEAD.yaml`, and `final/` are changeable entry points.
They are not sufficient identifiers for fixed historical evidence.

## 2. Start a new round — controller

A new round accepts only user requirements, `CURRENT.yaml`, the current fact graph, and the latest `final/` summary.
Do not read previous pair directories, submissions, reviews, drafts, or checkpoints to start a new round.
Use section 9 to record a previous pause or resume an interrupted round.
A pause entry alone does not make execution recovery necessary.
Before new-round setup, complete any necessary confirmation from section 9.

1. Read the user's target, limits, changes, and interruption report.
2. If `CURRENT.yaml` is available, read it.
3. Read the latest handoff in this order: `START_HERE.md`, `RESULT.yaml`, `PROBLEM.md`, then `FRONTIER.md`.
4. Read the full fact records necessary for the current task.
5. If the recovery conditions apply, use section 9 instead of the new-round steps below.
6. Record the new round, exact target, adopted policy, and new budgets in the control files.
7. Set `started_pair_ids` to `[]`.
8. Record the fixed published input graph version. Do not copy a snapshot for each new round.
9. If no graph exists, publish the initial project graph under section 6.
10. Assign the literature task to the researcher.

If there is no earlier state, initialize the project records.
An initial graph can contain no accepted results.
Read current facts through the root `fact_graph/HEAD.yaml`.
Do not replace a newer current graph with the graph in an older handoff.
A new conversation does not automatically create a new round budget.
Do not read `additional_papers/` during routine startup or recovery.

Create new pair identifiers, role assignments, and `TASK.md` records for this round.
Start each pair's submission sequence at `v01`.
Do not transfer previous pairs, pending reviews, or used submission counts into the new round.

Use these record contents:

| Record | Required information |
| --- | --- |
| `README.md` | Project purpose, rule locations, date and path conventions, adopted policy location, reading order, supplementary-paper rule, deferred features. No separate progress ledger. |
| `CURRENT.yaml` | `project_id`, `current_round`, `current_fact_head`, `latest_handoff`. `current_fact_head` points to root `fact_graph/HEAD.yaml`. Fill paths only after targets exist. |
| `PROBLEM.md` | Original question, exact target, identifier and revision, objects, quantifiers, ranges, hypotheses, conclusion, definition references, additional requests, uncertainties, changes. |
| `ROUND.yaml` | Round identifier, creation time, previous round, target revision and path. Fixed input and output graphs, budgets, started pairs, policy, and user-instruction references. |
| `ROUTES.md` | Route identifier, purpose, core method, sources, accepted inputs, distinguishing features, proof gaps, pair assignment, outcome, and stop reason. |
| `CHECKPOINT.yaml` | Last full graph, submissions, completed reviews, pending reviews, accepted results awaiting entry, open requests, draft or code paths, next action. |

Use `max_pairs`, `max_formal_submissions_per_pair`, and `started_pair_ids` for the budget fields.
Record cumulative results, the approved partial-result scope, and project-level novelty in the policy.
Count pairs and submissions within each round. Keep used counts through pauses and sessions in that round.
Calculate counts from the current round's formal records.
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
Do not claim global novelty from a search without a match alone.
For a paper's originality claims, use the complete checks in section 11.

When the user names supplementary papers, read only the requested material in `additional_papers/`.
Record actual use in `RESEARCH.md` and `SOURCES.yaml`.
Keep the original user paths and filenames.
The papers can stay at their original paths.
Subsequent use of accepted facts does not make another directory scan necessary.

## 4. Assign different routes — controller

This route procedure applies to research rounds. For paper work, use the scopes and limits in section 10.

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

`TASK.md` identifies the pair, parent round or paper task, fixed roles, target, scope, and submission limit.
Include the input graph, permitted facts, expected output, constraints, and stop conditions.
For research routes, add the route identifier, core method, distinguishing features, and proof gaps.
Do not invent proof routes for inventory, originality, manuscript, or presentation work.
Keep a record of material changes to the task.
Do not distribute another pair's unaccepted proof as an input.

## 5. Submit and review — worker and verifier

### Worker procedure

1. Read your `TASK.md`, the permitted facts, and your pair's previous review.
2. Complete your assigned route or paper work within its recorded scope and hypotheses.
3. Save useful drafts and specific failed steps in your own `drafts/` directory.
4. Request missing external facts from the researcher through the controller.
5. If a research route's core method must change, report the change to the controller.
6. Prepare the next formal submission in the remaining budget.
7. Fix the submission content in `submissions/vNN/`.
8. Send the exact version to the fixed verifier.

Use `v01` for the first submission. Increase the version for each formal repair within the task's actual limit.
Put the proof in `SUBMISSION.md` or in a clearly identified `proof.tex`.
Keep one authoritative proof body for each submission.
For non-proof work, submit the assigned report.
Include a separate `PROOF_IDEA.md` under section 12, fixed to the same submission version.

Record the formal delivery time, pair, worker, version, target revision, and numbered claims.
Include full statements, hypotheses, fact versions, the full argument, computations, changes, and unfinished work.
For a specific proof or method, identify the exact support version or fixed proof submission.
For repairs, record the response to each review defect and the effect of the change.
Do not edit a fixed submission during review.

### Verifier procedure

Examine only your fixed worker's submission. For paper reports, examine the assigned report and its evidence.

1. Read the fixed submission of your assigned worker and its exact dependencies.
2. Examine the claim against the target and all hypotheses.
3. Examine fact availability, versions, and applicability.
4. Examine each necessary deduction for gaps and circular support.
5. Examine quantifiers, constant dependencies, uniformity, and applicable boundary cases.
6. If the argument uses computation, examine computational coverage and precision.
7. For a counterexample, examine the original hypotheses and the failure of the original conclusion.
8. Examine `PROOF_IDEA.md` against section 12.
9. Write `reviews/vNN/REVIEW.md` for that exact submission.

The review records the verifier, pair, submission version, paths, scope, decision, and reasons.
Use the review decisions `ACCEPT`, `REWORK`, or `INCOMPLETE`.
These are review decisions, not mathematical results or paper completion states.
List exact accepted claims, their dependencies, target coverage, rejected steps, locations, reasons, and remaining obligations.

With a full basis and a clear scope, accept an independent local result.
A request for repairs to the whole proof does not cancel that local acceptance.
Record mathematical admission, proof-idea checks, and required paper checks separately.
An unfinished explanation or originality check does not cancel explicit mathematical admission.
If a required check is incomplete, the affected delivery remains incomplete.

Use necessary recalculation or diagnostic counterexamples for review.
Do not silently complete the worker's proof.
For subsequent submissions, reuse checks of unchanged, unaffected parts.
Give a decision for the current version.

Complete the review of the last permitted submission before applying the limit.
At the limit, stop further submissions. Research pairs use their round policy; paper pairs use section 10.
Keep accepted local results and the remaining obligations.
For correction of a completed review, keep the previous report. Add a clear correction.

### Count formal submissions

Use the same counting rules for rounds and paper tasks, with their respective limits.
Count one submission when a fixed version reaches the fixed verifier for a formal decision.
Count at delivery, not acceptance. Count each pair separately from its formal records.
One delivery can cover several claims and defects; do not count them separately.

Draft exchanges, source searches, language edits, formatting, and compilation alone do not increase counts.
A report sent for a formal decision does count.
After any change to submitted content, use a new version and count the next request for a formal decision.
This includes arguments, references, explanations, language, and layout.
Continued review of the same version and compilation of unchanged fixed sources do not increase counts.

Keep all earlier submissions and reviews unchanged.
Do not reset counts through renaming, new sessions, or replacement agents.

List the current version's discovered defects in one review.
Reuse checks of unchanged, unaffected material.
After acceptance, stop unless further changes are necessary. Do not use the budget without a purpose.

## 6. Publish and read the project fact graph — controller

Only the controller publishes the shared project graph.
Research rounds and paper tasks use the same root `fact_graph/` directory.
Use graph identifiers unique across the project, not round-based graph numbers.
Keep submission, fact, support, and graph versions distinct.

| Record | Required contents |
| --- | --- |
| `HEAD.yaml` | Current `graph_id` and `graph_path` to its manifest. |
| `facts/F0042/r1.json` | Stable identifier, revision, logical type, full statement, definitions, quantifiers, hypotheses, notation, parameter ranges, and scope. |
| `supports/S0017/r1.json` | Identifier, revision, exact target fact, admission channel and decision, exact dependencies, evidence paths, responsible role, and source task. |
| `graphs/G0008.json` | Graph identifier, publication time, parent graph, and reason. Complete cumulative fact and support references, their availability, and reasons. |
| `index.jsonl` | One search record per line. Source graph, fact identifier and revision, name, topic, key conditions, availability, and paths. |

Keep definition and dependency references exact, such as `F0042@r1`.
Each support has its own dependencies. Do not merge alternatives into one set of joint prerequisites.
Keep original evidence in its source task. Cite fixed source or submission and review versions.
A changeable draft or latest manuscript cannot serve as fixed evidence.

Ordinary theorem use names the fact version.
Use or claims of a particular proof, construction, or method also identify its support or fixed proof version.

A new proof of an existing fact needs new support admitted through `DERIVED`.
Other valid support for the fact does not establish that proof.

If one support fails, retain another accepted, applicable support for the exact statement.
Stop affected support and dependent results without valid applicable support.
Send new mathematical judgments to the researcher or fixed pair. Do not decide them as controller.
Circular dependencies cannot establish a proof; joint induction needs an admitted complete argument.

1. Examine the identity and exact scope of admission decisions.
2. Save new fact and support versions.
3. Save the new manifest with availability states and their reasons.
4. Examine all references and exact version correspondence.
5. After all required records exist, update `HEAD.yaml`.
6. Generate the search index for that graph again.
7. Record the publication event in its source task.
8. For a research round, update its checkpoint.

`CURRENT.yaml.current_fact_head` points to the root `HEAD.yaml`.
Do not keep another current graph identifier in `CURRENT.yaml`.
`ROUND.yaml` and `PAPER.md` refer to fixed input and output graph versions.
For the first graph, save the records and manifest before setting the entry point.
An interruption record refers to the last complete published graph.

Keep published fact, support, and manifest files unchanged.
For changed statements, hypotheses, or definitions, create a fact revision.
For an independent proof, add support without changing the fact statement.
For changed proof evidence or dependencies, create a support revision.

For availability changes or withdrawals, create a graph manifest with reasons.
Support for a new fact revision must name that revision as its target.
An applicability decision can refer to an old fixed proof without copying it.
Do not transfer proofs or replace dependencies automatically.

A manifest can contain several revisions of the same fact.
Include all exact dependency records and their states.
Retain withdrawn or invalid records with their identifiers, states, and reasons.

The full manifest and referenced records form the full graph without repeated copies of mathematical text.
Historical reconstruction uses the states in that graph.
New use of a historical fact also requires examination of its current availability.
Draft edits and rejected candidate claims do not require a graph publication.
You can publish several admission records together.

### Read only necessary records

Use the index for discovery, not as mathematical evidence.
If it is absent or old, generate it again or read the fixed manifest directly.
Queries can select identifiers, topics, availability, source tasks, or graph versions.
Keep one graph version per query. Return exact dependency, reverse-dependency, and history references.

1. Search the catalog for candidate facts.
2. Read selected full statements and admission bases.
3. Read necessary dependencies, support, and source evidence.

Do not replace definitions, hypotheses, quantifiers, or ranges with summaries.
For ordinary research, read records necessary for the current task.
For paper integration, traverse all catalog entries in scope and record coverage before selecting detailed evidence.

Each batch must state its scope, remaining records, and continuation position.
Truncated results and leading search matches cannot establish a complete inventory.
Scripts can traverse all references without returning all text to the model.
No specific query tool or installation path is required.

### Migrate and export

Retain old snapshots and handoffs as fixed evidence.
Separate mathematical statements, support, and graph states before examining version conflicts.
Support or availability changes alone are not conflicts in a fact statement.

Preserve identifiers, revisions, dependencies, states, and sources. Map each old graph to a new manifest.
Store identical versions once. Record conflicting mathematical content explicitly.

Resolve identity conflicts that affect historical reads before changing the entry point.
Do not invent missing admissions or dependencies.
Examine current completeness and historical reconstruction before switching to the project graph.

For an independent package, include the selected manifest and all referenced facts and support.
Include dependency records and necessary local evidence. A `FACTS.ref.yaml` alone is insufficient.

Keep project-relative paths and exact external source versions and access limits.
State whether the package covers one graph or the full history.
Full history includes all published graph versions and their referenced records.
The index is optional and can be generated again.
Exports do not create another editable source of authority.

### Events

Record important events in `audit/EVENTS.jsonl`.
Each event contains its identifier, time, responsible role, action, object identifiers, evidence paths, and necessary explanation.
Refer to the original review. Do not copy a second decision into the event record.
For a research round, update its checkpoint after formal delivery, completed review, graph publication, or planned interruption.
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
For new proof or method claims, also identify the actual support or fixed proof version.
Keep open claims clearly identified as open.

The controller can arrange existing text and compile the paper.
Give new mathematical connections to a pair.
For integration across rounds, use the complete procedure in section 10.
Use the default `amsart` form and mathematical language rules in that section for papers.

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
Pair or formal submission budget exhaustion is not an interruption.
An external platform usage limit can interrupt execution; use section 9 in that case.
Unresolved specifications or conflicts can also end the affected work with a clear explanation.
For completion without interruption, use only necessary pair slots and actual outputs. A paper or PDF is optional.

1. Record the actual reason for completion.
2. Collect formal outcomes and unfinished tasks.
3. Add accepted facts that await graph entry.
4. Publish graph changes under section 6, if changes are necessary.
5. Identify the complete published graph for the handoff.
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
| `FACTS.ref.yaml` | Fixed source graph identifier and project-relative manifest path. |
| `FRONTIER.md` | Open proof obligations, route outcomes, accepted partial results and conditions, failed steps, source requests, issues, and candidate targets. |

For known information in `RESULT.yaml`, use these fields:

- `record_type: ROUND_END`, `round_id`, target identifier and revision, and `recorded_at`.
- `result_status`, `result_scope`, `basis_fact_ids`, and evidence locations.
- `new_results_this_round`, `scope_note`, and `remaining_obligations`.
- `source_graph_id`, `issues`, `handoff_complete`, and `missing_files`.
- Pause and recovery fields from section 9 when applicable.

Use a clear literature correspondence or verifier decision as the result basis.
Keep changes in `START_HERE.md` and evidence paths in the existing records.
Match `RESULT.yaml.source_graph_id` to `FACTS.ref.yaml`.
Examine the manifest and referenced records as part of handoff completeness.
Use `handoff_complete` and `missing_files` for actual gaps.
Mutable `HEAD.yaml` is not a fixed historical reference.

The handoff must support a new round without previous execution records or the full conversation history.
Keep unresolved ideas as candidate targets. Only admitted facts can serve as existing premises.

During research, read cited evidence beyond `final/` only for a specific source check.
Before future use of a historical fact, examine its current availability through `CURRENT.yaml`.

Keep failed proofs, rejected submissions, reviews, graph versions, and drafts necessary for recovery.
Do not delete user papers as temporary material.
Do not start a new round without the user's instruction or an existing agreement.

## 9. Pause and recover — controller

This section applies only to research rounds. Paper integration has no execution-recovery procedure.
`PAUSE` is the only `run_status` value. Omit `run_status` during ordinary work and completion without interruption.
Keep established mathematical results when a pause occurs.

### Immediate stop

1. When the user tells you to stop immediately, stop new research work.
2. Send stop requests to active subagents.
3. Save the available minimum pause information in `final/RESULT.yaml`.

Record the round, `run_status: PAUSE`, trigger, actual record time, and handoff completeness.
Include known results, their evidence, the last reliable graph, pending work, exact versions, used submissions, missing files, and next action.
If a value is unknown, do not include its field. Record the missing information.
Do not wait for unfinished work or a full five-file handoff.

### Add an earlier pause entry

If the user reports an earlier interruption, add `PAUSE` to the identified round directly.
Use `pause_basis: USER_REPORTED_INTERRUPTION`.
If the user reports a usage limit, record `pause_reason: USAGE_LIMIT`.
Do not make a search necessary for this entry.
The user's interruption report permits a pause entry when previous files are inaccessible.

An actual search without an ending declaration also permits a subsequent pause entry.
Use `pause_basis: ENDING_KEYWORD_NOT_FOUND` and record `search_scope`.
At new-round startup, search only user-provided ending messages and the previous round's accessible handoff records.
Use `CURRENT.yaml` to locate that handoff.
An actual ending declaration must identify the round and announce its result or pause.
Accept the four mathematical result keywords or an actual `PAUSE` declaration in that context.

Ignore templates, rule definitions, hypothetical statements, local lemma decisions, other rounds, and intermediate progress.
Use the latest applicable record to determine whether that round remains interrupted.
An access failure is not a search without a match.
If no records are accessible, do not claim a search without a match.

Record `pause_basis`, the known `pause_reason`, `recorded_at`, and the round or session that makes the entry.
Record access limits.
Before the administrative addition, keep earlier result information or a clear historical copy.

If there is no previous result file, create a minimum record. Identify it as an entry made after the interruption.
Do not invent an interruption time or infer a usage limit from a missing declaration.
Use an event for a simple recovery.
For recovery details beyond an event, use `audit/recovery/RECOVERY_NNN.md`. Record evidence, unknowns, changes, and next actions.

After you add `PAUSE` with `pause_basis: ENDING_KEYWORD_NOT_FOUND`, apply this confirmation rule.
If the current prompt does not request that round's continuation, ask whether to resume it or start a new round.
This confirmation also applies when the current prompt requests a new round.
After you ask, wait for the user's choice before execution recovery or new-round startup.

### Resume the interrupted round

Recover execution records only when both conditions hold:

- The latest applicable pause record or the user's report identifies the previous round as interrupted.
- The current task is to continue that same round.

After any necessary confirmation, use section 2 for a requested new round with new pairs and budgets.
If the intended round is unclear, ask the user before you read execution records.
During recovery, read only the interrupted round's execution records.

1. Locate the last full, identifiable target and graph versions.
2. Recover literature admissions and completed verifier decisions from formal records.
3. Locate unfinished pairs, exact submissions, review progress, and submission history.
4. Separate accepted facts, pending drafts, and incomplete files.
5. Restore accepted results that only lack mechanical graph entry.
6. Continue in the existing round and pair directories.
7. Before research continues, save the recovery basis.

Keep the original round identifier, pair identities, fixed roles, used pair slots, and submission counts.
Continued review of `v03` is review of `v03`.
A formal repair after that review uses `v04`.

If a new handoff replaces an earlier handoff, keep the earlier one in `audit/handoffs/HNNN/`.
When a replacement occurs, create that history directory.
Keep previous pause records in history.
Do not add a new run-status value for recovery or completion without interruption.

Do not reset unknown counts, invent missing decisions, or accept drafts during recovery.
New mathematical judgments return to the responsible role.
Recovery alone does not make another independent reviewer or new proofs of literature results necessary.

## 10. Integrate a paper — controller and fixed pairs

Start this task when the user requests a paper from accumulated results.
If the user requests only analysis, stop after the inventory and topic proposals.
Examine all results in scope before selecting a coherent paper topic and its contents.

The original problem can remain open. Substantial partial results can support a separate paper.
Do not put every result in the paper. Record the disposition of omitted results.

Create `out_papers/PAPER001/` at the project root, beside `rounds/` and `additional_papers/`.
Use a new paper task identifier, pairs, and budget. Do not increase the round number.
Do not change `CURRENT.yaml.current_round` or the research `latest_handoff`.
Unless the user limits the scope, examine all results available when the task starts.

Read graph records, round handoffs, papers, and cited proofs as evidence, not as execution recovery.
Do not add a previous research pause because paper integration starts.
Unaccepted results can enter the inventory, but cannot serve as accepted premises.
Get admission for omitted mathematical results before use as established facts.

| Record | Contents |
| --- | --- |
| `PAPER.md` | User request, scope, topic, fixed input and output graphs. Original target version and mathematical result. Delivery progress, budget summary, and open items. |
| `INVENTORY.md` | Result identifiers, sources, admission states, topic groups, inclusion decisions, and reasons. Contribution claims and references to originality decisions. |
| `pairs/` | Tasks, drafts, fixed submissions with `PROOF_IDEA.md`, and fixed reviews. |
| `src/` | `main.tex`, `references.bib`, and `CLAIMS.yaml`. Exact facts, proof locations, and support versions for proof or method claims. |
| `out/` | `paper.pdf` and `BUILD.yaml`, with fixed sources, graph version, command, build time, and tools. |

Use 6 pairs by default, with a cumulative maximum of 8 for the task.
Schedule pairs by their work dependencies; they need not run together.
These limits include the first formal submission:

| Work | Pairs | Submissions per pair |
| --- | --- | --- |
| Result inventory and topic selection | 1 | 3 |
| Mathematical integration of separate result groups | 2 | 4 |
| Originality check | 1 | 5 |
| Main manuscript | 1 | 6 |
| Presentation and delivery report | 1 | 3 |

Additional pairs must have independent work, normally mathematical integration or a missing argument.
Use the submission limit for that work type. Keep one pair responsible for originality.
Do not transfer failed work to a new pair to reset its count.
Summarize counts in `PAPER.md` from formal records, not from an independent ledger.

The inventory pair identifies connections and proposes topics and result choices.
Mathematical pairs supply accepted arguments between results.
The originality pair works within this paper task, with the same task identifier, directory, and budget.
The researcher supplies literature. No separate user request for originality work is necessary.

The presentation worker submits a report and proposed changes to its own verifier.
The main worker incorporates accepted results and reviewed presentation changes into its manuscript.
The main verifier decides on that worker's exact complete manuscript.
The presentation decision does not replace the main manuscript decision.
The controller can arrange records and compile sources. It cannot supply mathematical connections or manuscript decisions.

Use candidate statements and method outlines for simultaneous initial originality work.
Do not send another pair's unaccepted proof text between pairs.
Final method-originality checks must refer to exact proofs that passed mathematical review.
The presentation pair reads admitted mathematics and its evidence. Send new deductions to their own pair first.

1. Complete the result inventory and coverage record.
2. Organize results by topic, dependencies, and scope.
3. Select a topic supported by existing results.
4. List the proposed contributions.
5. Run mathematical integration and initial originality checks together.
6. Select results using the topic and check outcomes.
7. Record omitted results and their disposition.
8. Incorporate admitted mathematical work.
9. Complete language changes, references, and preliminary compilation.
10. Send the fixed complete manuscript to the main verifier.
11. Build the delivery PDF from the reviewed fixed sources.
12. Examine source and PDF consistency before delivery.

Start originality work after topic and contribution selection, not after the whole manuscript is complete.
Use the outcomes to revise content and contribution claims.
Keep the paper independent of research logs.
Examine conflicting definitions, missing conditions, circular arguments, and contribution claims in the whole manuscript.
Acceptance of individual results does not establish acceptance of the whole manuscript.

After changes to reviewed content, request a new formal decision within the remaining budget.
Compilation of unchanged fixed sources does not use another submission.

Complete the task from one user request, with internal repairs as necessary.
Do not end at a topic proposal or draft when the request is for a paper.
Do not create a paper `PAUSE`, continuation entry point, or execution-recovery procedure.
If a core argument needs extended research, change the topic or selected results.

Near a submission limit, reduce the scope to a coherent paper with sufficient evidence.
Review changed content within the remaining budget. Scope reduction does not remove review requirements.

Review the last permitted submission. If it fails, stop further submissions from that pair.
Other pairs can continue work that does not depend on the failed item.
You can omit a nonessential failed result; the changed manuscript still needs review within budget.

If a core defect or required check remains open, record delivery as incomplete with the specific reason.
Retain admitted mathematics, existing files, used counts, and review outcomes.
Do not increase submission limits automatically.

After an external interruption, record incompleteness when possible. Do not resume the paper task.
For a new user request to start integration again, create a new task, pairs, and budget.
Previous files can serve as input material, not restored execution state.

Publish new admitted facts and new accepted proofs in the shared graph.
Record the paper task as the support source. No research round is necessary for these results.
Keep the original target's mathematical result separate from paper delivery completion.

### Paper form and language

Use `amsart` as the default document class.
Include title, authors, abstract, introduction, background, contributions, definitions, notation, main results, proofs, and references.
Add examples, discussion, and appendices when they serve the paper.
Use standard section, equation, theorem, proof, and citation commands with the class defaults.

Use an available template or generate equivalent sources. No fixed template installation path is required.
Do not invent author details, a target journal, or acceptance information.
Journal-specific formatting is outside this procedure.

For papers, preserve full mathematical meaning and standard field terminology first.
Use clear words, stable terms, and short sentence structures.
Do not force paper language into the ASD-STE100 dictionary or sentence limits.
Preserve quantifier order, parameter ranges, constant dependencies, regularity, topology, and uniformity.
Keep existence, uniqueness, necessity, and sufficiency distinct.

If a language change affects mathematics, review the affected statements and arguments again.
Pure language or layout changes do not require repeated checks of unaffected proofs.
Formal delivery after content changes still follows the submission-count rules.

## 11. Originality checks within paper integration

Examine claimed contributions, not the history of every standard proof step.
Keep correctness, originality, and significance separate.
Independent derivation in this project does not establish global originality.
Use full checks for main results, improvements, and new methods.
Use focused checks for new lemmas or examples with claimed independent value.

For standard tools, examine attribution and applicability.
Claims such as "first", "earliest", or "only known method" need a separate priority check.
Mathematical uniqueness uses ordinary proof and admission, not a literature priority check.

Cover these source types for main contributions:

- Mathematical indexes, such as zbMATH Open or accessible MathSciNet.
- Preprints and updates, such as arXiv, author pages, revisions, and corrections.
- Targeted web searches and directly relevant citation paths, including books and notes.

Search alternative terms, equivalent statements, more general covering results, and existing proof methods.
Include earlier and recent work. Follow only leads that can change the contribution decision.
Do not continue citation searches without a stopping condition.

Not every platform is required. Use other sources when access fails and record the effect of access limits.
If a critical source cannot be examined, keep only the affected originality claim open.

Read original key sources and compare exact statements and proof locations.
Search snippets and text-similarity checks cannot replace mathematical comparison.

An objection must identify a source, a possible equivalence or derivation, or a specific consequential search gap.
A concrete lead can trigger a focused check before a full overlap proof exists.
To confirm overlap, give exact source locations and mathematical coverage evidence.

The originality worker supplies necessary new arguments; its fixed verifier reviews them.
The verifier can suggest a lead, but cannot admit its own unreviewed deduction.
New usable equivalence results or reductions still need `DERIVED` admission; originality is not a third channel.

An implication `A ⇒ B` establishes a mathematical relation, not the absence of all contribution.
Examine what the new argument, method, or connection adds.
Simple renaming or routine substitution normally gives a restatement or corollary.
For a known result with a different proof, examine the claimed proof or method contribution.
Examine actual changes to hypotheses, ranges, bounds, and conclusions.
Failure to prove overlap does not itself prove originality.

For each contribution, complete these checks:

1. State the exact claim and proposed originality type.
2. Cover applicable source types and principal statement variants.
3. Read and compare key sources that could cover the result.
4. Resolve concrete overlap doubts and record the basis.

Resolution can confirm overlap and change the contribution claim.
Start with an initial search; use focused follow-up for specific gaps.
When these checks are complete and no new leads remain, stop general searches.
Time, search counts, and exhausted budgets cannot replace completion of the checks.

| Finding | Action |
| --- | --- |
| Earlier work covers the result | Cite it and revise the contribution claim. |
| Checks complete; no coverage found; concrete doubts resolved | Permit a normal originality claim for the examined contribution. |
| A consequential doubt remains | Identify missing evidence. Keep that originality claim open; do not call it confirmed new work. |

A search with no match alone does not establish originality.
After complete checks, unknown literature in the abstract must not prevent a decision or cause endless searches.
Do not require proof that no existing theory can imply the result.
You can describe an examined contribution as a new theorem, proof, or method within the accepted scope.
Do not require "new only in this project" or "to our knowledge" before every contribution.
Use a qualifier when the particular priority claim needs it.

Record contribution and proof versions, search dates, scope, queries, source locations, comparisons, access limits, doubts, and decisions.
Keep these records in the same paper task's pair submissions and reviews.
Let `INVENTORY.md` refer to those decisions without creating another decision record.

For a new specific source or a material contribution change, reopen only the affected check.
Pure grammar and layout changes do not reopen originality checks.
If earlier work is later found, correct attribution and retain any separately supported new contribution.
Unresolved originality does not cancel mathematical admission, but can prevent completion of a paper's required core contribution.

## 12. Proof ideas for human readers

Each research or paper pair must include `PROOF_IDEA.md` with every formal submission.
The worker writes it; the fixed verifier examines it.
Use the same `submissions/vNN/` directory as the submitted argument or report.
Keep the file fixed with that version. For changes sent for another decision, use a new version and count.

Explain how features of the problem suggest the chosen method.
Usually use 1 to 3 paragraphs, with a simple example or special case if useful.
Describe concrete clues, the reason for the route, the intended obstacle, and the least obvious construction or transformation.
Identify documented sources of ideas and what the proof retains or changes.
If a source cannot be confirmed, say so.

You can reconstruct an explanation for teaching. Do not present it as the actual discovery history.
Statements about attempts or sources of inspiration need records.
Do not invent sudden insights or failed attempts.
Distinguish earlier clues from explanations made after a proof was found.

If no natural prior motivation is known, explain why the construction works.
An intuitive reason is not a prerequisite for exploration.

For an unfinished route, state its purpose, progress, and remaining obstacle.
For inventory or comparison work, explain the method without inventing a proof.
Keep intuition, analogy, and proved steps distinct.
Refer to proof locations without copying the full proof. This explanation is not a separate admission basis.

In `REVIEW.md`, examine the problem clues, agreement with the proof, necessary conditions, open gaps, and source evidence.
Examine the distinction between explanation, documented discovery, and later reconstruction.
Record this check separately from the mathematical decision.
Request repairs for missing, unclear, or false explanations.

Keep explicit mathematical admission when only this explanation needs repair.
Required explanation work still controls delivery completion and uses the task's remaining submission budget.
If the budget is exhausted, retain the admitted result and record the unfinished explanation without adding submissions automatically.
Readability cannot replace a full proof.
The verifier need not establish that humans would choose this route or that every other route fails.
