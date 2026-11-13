# Mathematical research rules

Version: 0.2.0.

## 1. Scope and terms

Use these rules for mathematical research and paper integration in this project.
This file can operate alone. A matching research skill supplies optional procedure details.
Read all 10 sections. If the supplied copy is incomplete, read the complete project file before work.
Do not start research only because the user edits these instructions.

| Term | Meaning |
| --- | --- |
| Target | The exact mathematical problem and its version. |
| Route | One proof method or counterexample method. |
| Pair | One fixed worker and verifier with a defined scope in one round or paper task. |
| Round | Research work with a target and pair limit. |
| Paper task | Integration of accumulated results into a paper, separate from research rounds. |
| Admission | Acceptance through `LITERATURE` or `DERIVED`. |
| Fact | A mathematical statement with full conditions and a logical type. |
| Support | One source or accepted proof for an exact fact version, with its own dependencies. |
| Graph manifest | The complete fact and support references and availability states in one graph version. |
| Submission | Fixed work sent for a formal review. |
| Handoff | Records of the result and the basis for subsequent work. |

## 2. Roles

Use Codex subagents for researcher, worker, and verifier duties.
Give each its role, permitted inputs, task, and output paths.
If capacity is insufficient for parallel work, run tasks in sequence.
If a necessary role cannot run, report the limitation. Do not transfer proof or review duties to the controller.
Role instructions do not create sandbox isolation.

| Role | Duties and limits |
| --- | --- |
| Controller | Read sources, plan routes, assign pairs, manage budgets and records, publish admissions, and compile papers. Do not prove, repair, or judge mathematics. |
| Researcher | Search and extract faithful literature facts with full conditions and exact sources. Do not present new deductions as literature extracts. |
| Worker | Complete its assigned route or paper work, submit arguments or reports, and repair defects. Do not approve its own work. |
| Verifier | Examine only its fixed worker's submission. Admit clear results or request repairs. Do not silently supply missing proofs. |

Keep pair identities and fixed roles through repairs.
Do not change a verifier to obtain another decision.
A replacement agent can continue a role during an active task, with the same history and budget.
This does not permit recovery of an interrupted paper task.
Send new deductions from review back to the worker for a formal submission.

## 3. Mathematical boundaries

Preserve the original question, definitions, quantifiers, ranges, hypotheses, and conclusion in the target record.
Keep requests for new proofs or stronger results separate from the target's mathematical status.
For changed targets, keep earlier versions and reasons.
Record restricted or weaker claims separately; do not substitute them for the target.
Send necessary equivalence proofs to a pair.

Use only these admission channels:

- `LITERATURE`: A researcher accepts a faithful extract with full conditions and exact source locations.
- `DERIVED`: A fixed verifier accepts clear claims from its worker's fixed submission.

Do not require new proofs or second verifiers for every literature result.
Distinguish definitions, local hypotheses, accepted theorems, conjectures, and observations.
Existence, uniqueness, and equivalence claims need evidence, including claims attached to definitions.

Use permitted, available graph facts for existing results.
Record basic logic and project conventions without creating a fact node for every arithmetic step.
Request missing external facts from the researcher.
Model memory, route proposals, and unaccepted drafts cannot serve as established premises.
Full local deductions can occur within a proof; get admission before another task uses them as existing facts.

Share admitted facts, source requests, candidate statements, method outlines, and administrative progress between pairs.
Keep unaccepted proof text within its pair and the controller's administrative scope.
A different pair can receive a candidate claim as a target, not an accepted premise.

Assign new mathematical connections to a pair within budget.
The original pair can supply them within its existing scope and remaining budget.
A different core method in a research route needs a new pair.
Paper structure or language changes stay within the paper work's scope and budget.
A summary cannot replace a proof. For `L ⇒ T` to establish `T`, first supply accepted support for `L`.

Record exact fact dependencies in submissions.
For specific proofs, constructions, or methods, also identify the support version or fixed proof submission.
A new proof of an existing fact needs new `DERIVED` support; other support does not establish that proof.
Do not use invalid or disputed premises because a historical graph contains them.
Circular dependencies cannot establish a proof. Joint induction needs an admitted complete argument.

A defective proof does not make its claim false.
Stop affected support and dependent results without valid applicable support.
Retain other accepted, applicable support for the exact claim.
Send new mathematical judgments to the researcher or fixed pair; record changes and reasons.
Computations need a worker's justification of coverage, precision, and sufficiency, followed by verifier review.
Successful code execution or PDF compilation is not mathematical review.

## 4. Budgets, decisions, and results

### Research budgets

Use these defaults unless the user specifies different values or result rules.
Record the adopted policy in `ROUND.yaml` and apply explicit user changes.

| Item | Default |
| --- | --- |
| Pair limit | 4 per round; a round can select 3 instead. Count all pairs that start proof or review work. |
| Submission limit | 4 per pair, including the first submission and 3 repairs. |
| History | Preserve counts across pauses and sessions of the same round. New rounds start new pairs and counts. |
| Result scope | Cumulative progress for the exact target. List this round's new results separately. |
| New result | A result derived and admitted in this project. Global originality requires a separate check. |
| Partial result | An admitted restricted result, substantial lemma, weaker conclusion, partial parameter result, or rigorous reduction. |

Exploration, combination proofs, and separate lemma tasks use pair slots.
Same-pair repairs and recovery do not use another slot.
Literature work, route plans, fact reads, and administrative recovery do not use slots.
Completed or failed pairs do not return slots. Pair limits are not concurrency limits.
A slot can remain unused for later work in the round.

Before exceeding a research pair's limit or starting automatic successive rounds, get explicit user agreement.
A new session does not reset a budget. Recover unknown same-round counts before use.

### Submission counts and review

These counting rules apply to both rounds and paper tasks, with their respective limits.
Count one submission when a fixed version reaches the fixed verifier for a formal decision, regardless of acceptance.
Calculate each pair's count from formal records, not an independent ledger.
A submission can cover several claims or defects; do not count each item separately.

Draft exchanges, searches, text edits, formatting, and compilation alone do not count.
Reports sent for formal decisions do count.
After any change to submitted content, use a new version and count the next formal delivery.
This includes arguments, references, proof ideas, language, and layout.
Continued review of the same version and compilation from unchanged fixed sources do not count again.
Do not reset counts through renaming, new sessions, or replacement agents.

Complete the last permitted review.
List discovered defects together and reuse checks of unchanged, unaffected parts.
Use `ACCEPT`, `REWORK`, or `INCOMPLETE` for reviews, not for mathematical results.
Explicit admission of a complete independent claim survives repairs to other claims.

Separate mathematical admission from proof-idea checks, originality checks, and delivery completion.
A failed explanation or originality check does not cancel admitted mathematics or established result status.
Required unfinished checks still prevent the affected delivery's completion and use the remaining submission budget.
After acceptance, stop unless further changes are necessary; do not use all submissions without a purpose.

### Mathematical results

| Result | Evidence |
| --- | --- |
| `PROVED` | An admitted proof or exact literature match establishes the original target. |
| `DISPROVED` | An admitted refutation applies. A counterexample meets the hypotheses and violates the conclusion. |
| `PARTIALLY_RESOLVED` | The target remains open, with admitted project results that meet the partial-result rule. |
| `UNRESOLVED` | The target remains open, without admitted project results that meet that rule. |

Record additional requests and their completion separately.
Proof failure, exhausted budgets, and unsuccessful searches do not establish proof or refutation.
Unknown is not `UNRESOLVED`; omit unknown `result_status` and record missing evidence.
Keep added hypotheses explicit.

Use `MISSING_SPECIFICATION` and `LITERATURE_CONFLICT` as issues, not mathematical result values.
A proof gap is not a missing specification.
Stop only affected work; do not invent the target or settle a mathematical conflict as controller.

Record inconsistent hypotheses.
Pair or formal submission budget exhaustion is not interruption.
External platform usage limits can interrupt execution; section 7 governs research interruptions.

## 5. Records and project fact graph

Only the controller updates shared control files and publishes graphs.
Copy admissions faithfully; keep fixed submissions, completed reviews, and published records unchanged.
Distinguish submission, fact, support, and graph versions. Use stable identifiers and project-relative paths.
Use the user's time zone, default `Asia/Shanghai`.

Number `rounds/yyyy_mm_dd_roundNNN/` consecutively; keep the creation date during continuation.
Create only needed records, without empty proofs, reviews, PDFs, or future submissions.

| Record | Required contents |
| --- | --- |
| `README.md` | Purpose, rule/policy locations, path/date conventions, reading order, supplementary-paper policy, deferred features. No progress ledger. |
| `CURRENT.yaml` | `project_id`, `current_round`, `current_fact_head`, `latest_handoff`. Set paths after targets exist. Point `current_fact_head` to root `fact_graph/HEAD.yaml`. |
| `PROBLEM.md` | Exact target, identifier, revision, source, additional requests, uncertainties, changes. Keep earlier versions separately. |
| `ROUND.yaml` | Round, creation time, previous round, target version/path, fixed input/output graphs, user instructions, policy, budgets, started pairs. |
| `ROUTES.md` | Route identifiers, methods, differences, admitted inputs, gaps, assignments, outcomes, stop reasons. |
| `CHECKPOINT.yaml` | Last complete graph, submissions, reviews, unpublished admissions, open requests, work paths, next action. Formal records control its contents. |

Research budget fields are `max_pairs`, `max_formal_submissions_per_pair`, and `started_pair_ids`.
Keep `code/`, `audit/`, `src/`, `out/`, `research_papers/`, `pairs/`, `final/`, and `temp/` in each round.
The shared `fact_graph/` stays at the project root.

| Records | Required contents |
| --- | --- |
| `code/PAIR_ID/runs/RUN_ID/` | Fixed code, inputs, outputs, `RUN.yaml`: commands, environment, dependencies, seeds, limits. |
| `audit/` | `EVENTS.jsonl`: time, role, action, objects, evidence. Detailed recovery and replaced handoffs use section 7. |
| `research_papers/` | `RESEARCH.md`: findings, gaps, admissions, search limits. `SOURCES.yaml`: identifiers, authors, titles, years, versions, links, retrieval dates, access limits, available file paths. Available PDFs use `pdf/`. |
| `pairs/PAIR_ID/` | `TASK.md`, `drafts/`, `submissions/vNN/SUBMISSION.md`, `submissions/vNN/PROOF_IDEA.md`, `reviews/vNN/REVIEW.md`. |
| `src/`, `out/` | Sources, claim mappings, optional PDF and build records; use section 8's paper form. |

Literature records give statement/proof locations, cited proof sources, and notation changes.
Read original context; snippets are leads. Preserve meaning; assign necessary deductions to a pair.

Tasks identify pair, parent round/paper, fixed roles, target, scope, permitted facts, outputs, constraints, and limit.
Only research route tasks need route and core-method fields.

Submissions identify worker, pair, version, delivery time, target version, claims, conditions, dependencies, arguments, computations, changes, and unfinished work.
Respond to prior defects. Reviews identify verifier, exact submission/path, scope, decision, reasons, admissions, dependencies, and remaining obligations.
Retain original decisions and correction history.

Update research checkpoints after formal delivery, review, graph publication, or planned interruption.

### Graph data and publication

| Path under `fact_graph/` | Contents |
| --- | --- |
| `HEAD.yaml` | Current `graph_id` and `graph_path`. Keep no second current graph identifier in `CURRENT.yaml`. |
| `facts/F0042/r1.json` | Identifier, revision, type, full statement, definitions, quantifiers, hypotheses, notation, scope. |
| `supports/S0017/r1.json` | Identifier, revision, exact target fact, admission channel/decision, dependencies, evidence, responsible role, source task. |
| `graphs/G0008.json` | Identifier, publication time, parent graph, reason, complete cumulative fact/support references, availability and reasons. |
| `index.jsonl` | One search record per line: source graph, fact identifier/version, name, topic, key conditions, availability, paths. |

Graph identifiers are project-wide; tasks record fixed input/output graphs.
Use exact definition/dependency versions. Keep alternative supports' dependencies separate.
Evidence remains at fixed source-task paths, not changeable drafts.
Manifests include all dependency records/states, multiple fact revisions, and withdrawn records with reasons.
A manifest and its referenced records form the complete graph.

Changed mathematical content needs a fact revision; independent proofs need new support.
Changed proof evidence/dependencies need a support revision; availability changes need a new manifest with reasons.
Do not transfer proofs or replace old dependencies automatically.
Support for a new fact revision must target that revision.
Applicability decisions can reference earlier fixed proofs without copying them.

1. Examine admission decisions and scopes.
2. Save new fact/support versions.
3. Save the complete manifest and state reasons.
4. Examine reference completeness and version consistency.
5. Update `HEAD.yaml` after all required records exist.
6. Generate the index again.

Use this order for initialization. Checkpoints reference the last complete published graph.
Historical reconstruction uses historical states; new use also requires current availability.

### Reads, migration, and export

The index locates records; it is not mathematical evidence.
For an absent or old index, regenerate it or read the fixed manifest.
Search identifiers, topics, states, source tasks, or graph versions within one graph per query.
Dependency, reverse-dependency, and history queries return exact versions.
Read the catalog, selected full facts/admissions, then necessary dependencies/evidence. Summaries cannot replace mathematical conditions.

Ordinary research reads necessary records; integration traverses the full catalog in scope and records coverage.
Select detailed evidence after that inventory.
Each batch states scope, remaining records, and continuation position. Truncated or leading matches are not complete inventories.
Scripts can traverse references without returning all text. No particular query tool or installation path is required.

For migration, preserve old snapshots, handoffs, identifiers, versions, dependencies, states, and sources.
Separate statements, support, and states before comparing facts; support/state changes alone are not statement conflicts.
Store identical versions once and map old graphs to new manifests. Do not invent missing data.
Resolve identity conflicts affecting history and examine current completeness/historical reconstruction before switching the entry point.

Independent packages contain selected manifests, all referenced facts/support, dependencies, and necessary local evidence.
Keep project-relative paths, external source versions, and access limits. A graph reference alone is insufficient.
State single-graph or full-history scope; full history includes every published manifest and referenced record.
Indexes are optional and rebuildable. Exports are not another editable authority.

An empty project `additional_papers/` is optional. Preserve existing user files.
Do not routinely list, scan, read, or monitor it. Read only user-requested material and record actual use/admission.
Preserve user papers and necessary role checks/computation code during cleanup.

## 6. New rounds and handoffs

A new round accepts only user requirements, `CURRENT.yaml`, the current fact graph, and the latest `final/` summary.
Do not scan old pairs, submissions, reviews, drafts, or checkpoints to start a round.
Apply section 7's pause-entry confirmation if necessary. A pause entry alone does not authorize execution recovery.

1. Read the target, limits, and available `CURRENT.yaml`.
2. Read the latest handoff summary and necessary full facts.
3. If same-round recovery applies, use section 7 instead.
4. Record the new round, target, policy, budgets, and fixed published input graph.
5. Assign literature research and record admissions.
6. Select distinct routes within the pair limit.
7. Assign fixed pairs with tasks and permitted facts.
8. Record each pair when proof or review work starts.
9. Submit fixed work within budget.
10. Publish admitted facts with exact scope and dependencies.

Set `started_pair_ids` to `[]`; create new pairs and `TASK.md` records, with submissions starting at `v01`.
Do not inherit old pair tasks, pending reviews, or used counts.

Inherited facts keep their identifiers, revisions, and sources.
Use root `HEAD.yaml`; an old handoff must not replace a newer graph from paper integration.
Record the input graph without copying an initial snapshot. Initialize the first graph under section 5.

If literature directly settles the target, record exact correspondence; no proof pair is required for that result.
Keep additional requests separate.

End a round for a settled target, completed work, exhausted research budget, or an agreed boundary.
Explain unresolved specifications or conflicts that end affected work.
For normal completion, publish these five files in `final/`:

| File | Contents |
| --- | --- |
| `START_HERE.md` | Target, result, key facts, changes, route outcomes, limits, next actions, and reading paths. |
| `RESULT.yaml` | Actual ending declaration, result basis, scope, obligations, issues, fixed graph, time, and completeness. |
| `PROBLEM.md` | Copy of the exact target version and source path. |
| `FACTS.ref.yaml` | Fixed graph identifier and project-relative manifest path. |
| `FRONTIER.md` | Open obligations, route outcomes, admitted partial results, failed steps, source requests, issues, and candidate targets. |

Publish pending admissions, prepare the handoff, and examine versions, decisions, counts, and evidence against their sources.
After preparation, publish the ending declaration and update `CURRENT.yaml.latest_handoff`.

In `RESULT.yaml`, use `record_type: ROUND_END`, `round_id`, target identifier/revision, and `recorded_at`.
Include known `result_status`, `result_scope`, `basis_fact_ids`, `new_results_this_round`, `scope_note`, and `remaining_obligations`.
Also include `source_graph_id`, `issues`, `handoff_complete`, and `missing_files`.
Match the fixed graph to `FACTS.ref.yaml`; include all referenced records in completeness checks.
Mutable `HEAD.yaml` is not a fixed historical reference.

Use exact literature correspondence or verifier decisions as the result basis.
The handoff must support a new round without old execution records or full conversation history.
Unresolved ideas are candidate targets, not premises.

During research, read cited evidence beyond `final/` only for specific source checks.
Keep failed proofs, rejected submissions, reviews, graph versions, and drafts necessary for recovery.
Preserve evidence before temporary cleanup. Start another round only with user instruction or an existing agreement.

## 7. Research interruption and recovery

This section applies only to research rounds. Paper tasks use section 8.
`PAUSE` is the only `run_status`; omit it during ordinary work and normal completion.
Keep established mathematical results during a pause.

If the user requests an immediate stop, stop new work and send stop requests to subagents.
Save available minimum information in `final/RESULT.yaml`; do not wait for proofs, reviews, a full handoff, PDF, or cleanup.
Record round, `run_status: PAUSE`, trigger, actual record time, and completeness.
Include known results/evidence, last reliable graph, pending tasks, exact versions, counts, missing files, and next action.
Omit unknown fields and state the missing information.

For a reported earlier interruption, add the identified round's pause directly with `pause_basis: USER_REPORTED_INTERRUPTION`.
No prerequisite search is required, including when old files are inaccessible.
Use `pause_reason: USAGE_LIMIT` only when the user reports that reason.

An actual search without a valid ending declaration permits `pause_basis: ENDING_KEYWORD_NOT_FOUND`; record `search_scope`.
At new-round startup, search only user-provided ending messages and the previous accessible handoff located through `CURRENT.yaml`.
A valid declaration identifies the round and announces one of the four mathematical results or `PAUSE`.
Ignore templates, hypothetical statements, local decisions, other rounds, and intermediate progress.
Use the latest applicable record. Access failure or no accessible records is not a search without a match.

Record access limits, entry time, entry author round/session, and actual basis.
Preserve earlier result information or a historical copy.
If no result file exists, create a minimum subsequent-entry record.
Do not invent the interruption time or cause.

After an `ENDING_KEYWORD_NOT_FOUND` entry, ask for the user's choice if the prompt does not request that round's continuation.
Ask whether to resume it or start a new round, even if the prompt requests a new round.
Wait for the answer before recovery or new-round setup.

Recover execution records only when both conditions hold:

- The latest applicable pause or user report identifies an interrupted round.
- The current task is to continue that same round.

If the intended round is unclear, ask before reading execution records.
For a new round, use section 6 after any required confirmation.
For recovery, read only the interrupted round's execution records.

1. Locate the last complete target and graph versions.
2. Recover admissions, reviews, unfinished pairs, exact submissions, and counts from formal records.
3. Separate admitted results, pending drafts, and incomplete files.
4. Publish admissions that only lack graph entry.
5. Continue in the same round and pair directories.
6. Record the recovery basis in `audit/` before research continues.

Keep original round/pair identities, fixed roles, slots, and counts.
Continued review of `v03` stays at `v03`; formal repair uses `v04`.
Use an event for simple recovery; use `audit/recovery/RECOVERY_NNN.md` for additional evidence, unknowns, changes, and actions.
Before replacing a handoff, retain it in `audit/handoffs/HNNN/`, including earlier pauses.
Do not reset unknown counts, invent decisions, or admit drafts during recovery.
New mathematical judgments return to their responsible role; recovery alone needs no extra reviewer or literature reproof.

## 8. Paper integration

Analyze all results in scope before selecting a coherent topic and paper contents.
The original problem can remain open while partial results support a separate paper.
If the user requests only analysis, stop at the inventory and topic proposals.
Unless limited by the user, cover all project results available at task start.

Read graphs, round handoffs, papers, and cited proofs as evidence, not execution recovery.
Do not add a previous research pause because integration starts.
Inventory unaccepted results, but get admission before using them as established premises.

Create `out_papers/PAPER001/`, beside `rounds/` and `additional_papers/`.
Use a new task identifier, pairs, and budget; do not increase round numbering.
Do not change `CURRENT.yaml.current_round` or the research `latest_handoff`.

| Record | Contents |
| --- | --- |
| `PAPER.md` | User request, scope, topic, fixed input/output graphs, target version and mathematical status, delivery progress, budget summary, and open items. |
| `INVENTORY.md` | Results, sources, admission states, topic groups, inclusion/disposition reasons, contributions, and references to originality decisions. |
| `pairs/` | Fixed tasks, submissions, `PROOF_IDEA.md`, and reviews. |
| `src/` | `main.tex`, `references.bib`, `CLAIMS.yaml`: exact facts, proof locations, and support versions for specific proof/method claims. |
| `out/` | `paper.pdf`, `BUILD.yaml`: reviewed fixed sources, graph version, build time, command, and tools. |

Use 6 pairs by default, at most 8 cumulatively. Schedule by dependencies, not necessarily together.
All submission limits include the first submission:

| Work | Pairs | Submissions per pair |
| --- | --- | --- |
| Result inventory and topic selection | 1 | 3 |
| Mathematical integration of separate result groups | 2 | 4 |
| Originality check | 1 | 5 |
| Main manuscript | 1 | 6 |
| Presentation and delivery report | 1 | 3 |

Additional pairs need independent work, normally mathematical integration or missing arguments, with the applicable type's submission limit.
Keep one pair responsible for originality within the same paper task, directory, and budget.
No separate user request is necessary; the researcher supplies literature.
Summarize counts from formal records in `PAPER.md`.

The inventory pair proposes topics and result choices; mathematical pairs supply admitted connecting arguments.
The presentation worker submits its report and proposed changes to its own verifier.
The main worker incorporates admitted results and reviewed changes; its verifier decides on the fixed complete manuscript.
Presentation review does not replace main manuscript review.
The controller can arrange records and compile, but cannot supply mathematical connections or manuscript decisions.

Initial originality checks use candidate statements and method outlines, not another pair's unaccepted proof text.
Final method checks refer to exact proofs that passed mathematical review.
The presentation pair reads admitted mathematics and its evidence. Send new deductions to their assigned pair first.

1. Inventory all results and record coverage.
2. Organize topics, dependencies, and applicable scopes.
3. Select a topic and proposed contributions.
4. Run mathematical integration and initial originality checks together.
5. Select contents using the topic and check outcomes.
6. Record omitted results and reasons.
7. Incorporate admitted mathematics into a complete manuscript.
8. Complete language changes, references, and preliminary compilation.
9. Submit the fixed manuscript to the main verifier.
10. Build the PDF from reviewed fixed sources and examine consistency.
11. Deliver the reviewed paper and evidence.

Start originality work after topic selection, not after the completed manuscript.
Examine definitions, conditions, circular arguments, and contribution claims across the whole paper.
Individual admissions do not establish whole-paper acceptance.
Keep the manuscript independent of research logs.
After changes to reviewed content, get a new formal decision within remaining budget.
Compile unchanged fixed sources without another submission.

Complete integration from one request, with internal repairs.
Do not stop at a proposal or draft when a paper is requested.
Do not create paper `PAUSE`, continuation, or execution-recovery procedures.
If core arguments need extended research, change the topic or contents.

Near a limit, reduce scope to a coherent, supported paper; changed content still needs review within budget.
Review the last submission; if it fails, stop that pair's submissions.
Other pairs can continue independent work. Omitted nonessential failures still require review of the changed manuscript.

For core defects or incomplete required checks, record incomplete delivery and specific gaps.
Retain admitted mathematics, files, counts, and decisions. Do not increase limits or replace pairs to reset counts automatically.

After external interruption, record incompleteness when possible; do not resume that paper task.
A new user request to start again creates a new task, pairs, and budget; old files are input evidence only.
Publish new admitted facts and proofs in the shared graph with the paper task as source.
Keep target mathematical status separate from paper completion.

### Paper form and language

Use `amsart` by default, with standard commands and class settings.
Include title, authors, abstract, introduction, background, contributions, definitions, notation, results, proofs, and references.
Add useful examples, discussion, and appendices. Do not invent author, journal, or acceptance details.
Use an available template or generate equivalent sources; no fixed installation path is required.
Journal-specific formatting is outside this procedure.

For papers, full mathematical meaning and standard field terminology take priority over mechanical STE word and sentence limits.
Use clear words, stable terms, and short structures.
Preserve quantifiers, parameter ranges, constant dependencies, regularity, topology, and uniformity.
Distinguish existence/uniqueness and necessary/sufficient conditions.
Review mathematical effects of language changes; reuse unaffected checks.
Formal resubmission after changes still uses the submission-count rules.

## 9. Originality within paper integration

Examine claimed contributions, not the history of every standard step.
Separate correctness, originality, and significance. Project derivation does not establish global originality.
Use full checks for main results, improvements, and methods; focused checks for independently valuable new lemmas or examples.

For standard tools, examine attribution and applicability.
Literature claims such as "first", "earliest", or "only known method" need priority checks.
Mathematical uniqueness uses ordinary proof and admission.

Cover mathematical indexes, preprints/updates, and targeted web/citation searches, including books and notes.
Examples include zbMATH Open, accessible MathSciNet, arXiv, author pages, revisions, and corrections.
Search alternative terms, equivalent statements, broader covering results, and existing methods, across earlier and recent work.
Follow only leads that can change the decision; do not recurse through citations indefinitely.

Not every platform is required. Substitute accessible sources and record access limits and their effect.
Read and compare original key sources, with exact statement and proof locations.
Snippets or text similarity cannot replace mathematical comparison.

Objections must identify a source, possible equivalence/derivation, or specific consequential search gap.
A concrete lead can trigger focused work before a full overlap proof exists.
Confirmed overlap needs exact source and coverage evidence.
The originality worker supplies new arguments; its fixed verifier reviews them.
Verifier suggestions return to the worker; unreviewed verifier deductions are not admitted evidence.
New usable equivalence results or reductions still need `DERIVED` admission; originality is not a third channel.

`A ⇒ B` does not alone eliminate a contribution. Examine added arguments, methods, and connections.
Routine renaming or substitution normally gives a restatement or corollary.
For known results, examine claimed proof or method differences; for changed results, examine hypotheses, ranges, bounds, and conclusions.
Failure to establish overlap does not establish originality.

Complete these checks for each main contribution:

1. State the exact claim and originality type.
2. Cover applicable sources and principal statement variants.
3. Read and compare key sources that could cover the result.
4. Resolve concrete overlap doubts and record evidence.

Resolution can confirm overlap and change the contribution claim.
Use initial searches and focused follow-up for identified gaps.
When checks are complete and no new leads remain, stop general searches.
Search counts, time, and budget exhaustion cannot replace these conditions.

| Finding | Action |
| --- | --- |
| Earlier work covers the result | Cite it and revise the contribution claim. |
| Checks complete; no coverage found; concrete doubts resolved | Permit a normal originality claim for the examined contribution. |
| A consequential doubt remains | Identify missing evidence; keep only that claim open, without calling it confirmed new work. |

A search without matches alone does not establish originality.
After complete checks, abstract possibilities of unknown literature must not prevent a decision or cause endless searches.
Do not require proof that no existing theory implies the result.
Permit "new theorem", "new proof", or "new method" for the accepted type and scope.
Do not require "new only in this project" or "to our knowledge" for every contribution.
Use qualifiers for priority claims that need them.

Record contribution/proof versions, search dates, scope, queries, source locations, comparisons, access limits, doubts, and decisions in pair submissions/reviews.
`INVENTORY.md` references those decisions without duplicating them.
Reopen only affected checks for specific new sources or material contribution changes, not pure grammar or layout edits.
If precedent is later found, correct attribution and retain separately supported new contributions.
Unresolved originality preserves mathematical admission but can leave a required core contribution, and thus paper delivery, incomplete.

## 10. Proof ideas for human readers

Every research or paper submission includes a separate `submissions/vNN/PROOF_IDEA.md`.
The worker writes it; the fixed verifier examines it. Keep it fixed with the same submission version.
Explain the problem clues, route choice, intended obstacle, and key construction or transformation.
Normally use 1 to 3 paragraphs, with a useful simple example or special case.
Identify documented sources and what the proof retains or changes; state when sources cannot be confirmed.

You can reconstruct explanations for teaching. Do not present them as actual discovery history.
Claims about actual attempts or inspiration need records. Do not invent insights or failed attempts.
Separate prior clues from explanations developed after finding the proof.

If no natural prior motivation is known, explain why the construction works.
Intuition is not a prerequisite for exploration.

For unfinished routes, state purpose, progress, and obstacles.
For inventory or comparison tasks, explain the method without inventing proofs.
Distinguish intuition, analogy, and proved steps. Reference proof locations without copying the full proof.
The explanation is not a separate admission basis.

In `REVIEW.md`, examine clues, agreement with the proof, conditions, gaps, sources, and reconstruction claims.
Record explanation checks separately from mathematical decisions; request repairs for missing, unclear, or false explanations.
Explanation failure alone does not cancel admitted mathematics or result status, but required unfinished explanations prevent delivery completion.

Repairs sent for new decisions use new versions and the task's remaining budget.
If the limit is reached, retain admitted mathematics and record incomplete explanations without automatic additional submissions.
Readability cannot replace proof.
The verifier need not prove that humans would choose this route or that every other route fails.
