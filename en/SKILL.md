---
name: math-research
description: Start a mathematical research round, redo a completed round, or resume an interrupted round. Integrate results into a paper or review other ways to prove or disprove the original claim. Update the register of contributed material. Use the project AGENTS.md from the same release.
metadata:
  version: "0.6.0"
---

# Mathematical research procedure

## 1. Entry and project layout

Before each task, read this skill and the research project's root `AGENTS.md`.
This applies to new rounds, same-round recovery, paper tasks, route reviews, and material updates.
Editing these files does not start a research task.

### Compare the release numbers

The controller performs this check once per task start or request to resume, whichever file the user invokes first.
Complete the check before you assign work, recover execution records, or write any task record.

1. Read the version declaration in the actual project root `AGENTS.md`.
2. Read `metadata.version` in the actual `SKILL.md` for the active research skill.
3. Compare all three parts of the release numbers, including the patch number.

If either file is missing or unreadable, stop. Also stop if either version is unknown or the versions differ.
Give the user both file paths and both versions where known. State the missing information and the reason for stopping.

Ask the user to use the files from one release. After the user synchronizes the files, repeat the check.
Leave both files intact during this check. A change to a version label alone does not synchronize their contents.
Use the actual files as evidence. Memory, skill listings, and the latest online release cannot establish a match.

After a match, apply the other entry conditions for the requested task.
Use section 2 for an ordinary new round or an explicit request to redo a completed research round.
Use section 9 to resume an interrupted round.
Use section 10 for paper integration or section 13 for a route review.
On a request to repeat a paper task or route review, start a new task under its usual rules.
Use section 14 for a request to update the register of contributed material.

If the user requests an update and a subsequent research round, review, or paper, complete the separate update first.
Then apply the entry checks for the requested task. An update alone ends with its change summary.

### When the user requests contributed material

The project register for ideas, proof drafts, and unpublished manuscripts is `human/STATUS.md`.
In rounds, route reviews, and papers, take items from `human/` as new input only on an explicit user request.
Section 10 also requires a source check for papers that use results from contributed material.

If the user requests `human/` or an item from it for one of these tasks, first look for `human/STATUS.md`.
For a new task, do this before you create task records, assign pairs, or start subagents.
If the register is missing, stop the entire task. Report the actual missing path and tell the user to request a separate material update.

If this happens during an active task, also send stop requests to its active subagents.
Keep completed work, fixed versions, and the budget already used.
For a research round, record `PAUSE` under section 9.
For a paper or review, mark the delivery or summary incomplete in its task record.

For a request to use all of `human/`, consider only entries with completed registration.
For a named item, title, or manuscript, read only the corresponding register section.
Read the fixed manuscript if you need its meaning, conditions, or proof details.
Without a specified version, use the latest fully registered version of that item.
Complete a separate update before you use a requested version with incomplete or missing registration.
Routine research, reviews, and paper tasks do not scan the manuscripts in `human/`.

### Apply project rules

For an ordinary new round, paper task, route review, or material update, first obtain any required confirmation.
Then look for `PROJECT_RULES.md` in the research project root.

If the file exists, read it before task setup.
If the file is absent, use the user's instructions and the usual defaults.
If it exists but you cannot read it, report its path. Wait for readable rules before you start the task.
Only the two required files take part in the release check.

For a redo, use the original round's fixed rules and exceptions under section 2, including a recorded absence.

For choices that this procedure permits, apply explicit instructions for the current task first.
For other permitted choices, use applicable project rules, then the defaults.
Distinguish requirements from preferences. Report the specific clauses that conflict.
Ask the user only if an unresolved conflict affects the task.
Keep the release check, fixed review, mathematical admission, and submission counting rules in force.

For a route review, give each researcher the applicable clauses and task exceptions.
For a new round or paper task, record the rules as follows.

1. If the selected rules file exists, save its exact text as `PROJECT_RULES_r01.md` in the task directory.
2. Set `project_rules_ref` to the project-relative path of that fixed copy, or to `null` for confirmed absence.
3. Record this reference and any task exceptions with their scope in `ROUND.yaml` or `PAPER.md`, as applicable.
4. Give the researcher, workers, and verifiers the applicable clauses, task exceptions, and fixed record reference.

Both members of a pair use the same rules and exceptions.
Keep a task exception in its task record. Change the root file only upon an explicit request for a lasting change.

For same-round recovery, first confirm both recovery conditions in section 9.
Use the round's fixed rules and exceptions, including a recorded `null`.
Report any addition, change, or removal of the root file since that record.
If an older round has no rules record, examine that round's recorded user requirements.
Ask the user if a condition essential to the task remains unknown.

If the user explicitly changes the rules for an active round or paper task, keep the previous references and exceptions.
Record the change, its scope, and the work from which it applies.

Save new text in the next fixed copy, such as `PROJECT_RULES_r02.md`. Update `project_rules_ref` in the task record.
If the user explicitly removes all project rules for the active task, set its new reference to `null`.
The responsible roles examine only affected targets, support, and submissions again. Keep all pair identities and used counts.

### Use project writing preferences

In each task, use the optional root `TASTE.md` before you first assign or start work on text for readers.
Reuse the current preferences in the same context. If a context lacks them, read the file.
Read it again if the user reports a change or you find that the file has changed.
Give the applicable preferences to the roles that write or review the text.

Apply the user's explicit writing instructions for this task before the project preferences.
Use preferences for the intended audience, choice of content, and steps that need explanation.
You can omit routine failed attempts from the text for readers.
Keep mathematical conditions and gaps that affect the result explicit. Preserve required reviews, handoff records, and deliverables.
Use the project rules and this procedure for mathematical definitions and restrictions on methods.

### Human notes for a round, route review, or paper

When the task ends normally, create `human.md` in its directory. Keep any existing file intact.
For a new file, write only these two headings. Delivery can proceed with both sections empty.

```markdown
## New ideas for future rounds

## Observations on this round
```

For a route review, use “Observations on this review” as the second heading.
For a paper, use “Observations on this paper”.
Use the first section for a possible proof route, counterexample strategy, construction, literature lead, or case to test.
The second gives the author's observations about a specific route, theorem, lemma, or proof step.
An observation can express doubt. Use statements here and leave questions for the conversation.

Only enter a note for the author on explicit request. Preserve the author's meaning.
Filling in this file does not start a task.

| Request | Notes to read |
| --- | --- |
| Ordinary new round without a reference to these notes | Skip task directories' `human.md` files. |
| New round that cites a task's `human.md` | Read the first section for candidate routes. |
| Redo of a completed research round | Read the second section of that round's file. |
| A specific note, section, or both sections | Read the requested material. |

If an old file is absent or the default section is empty, record that no such notes were available.
Proceed with the requested task. If a specific requested note is unavailable, report the omission and its effect on scope.
Do not supply a missing note yourself.

For each note you use, record its path and section in the existing route, review, or paper record.
Include the exact text or a fixed reference, the checks, and the outcome.
Continue with the recorded note after an edit unless the user explicitly changes the task.
Use the usual admission procedure before using a human judgment as a mathematical premise.
If you select material from the project `human/` directory through a note, apply its version, permission, and use rules.
Reading a task's notes alone does not require `human/STATUS.md`.

### Project layout

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
  PROJECT_RULES.md                 # Optional
  SUBAGENT_MODELS.json             # Optional
  TASTE.md                         # Optional writing preferences
  README.md
  CURRENT.yaml
  fact_graph/
    HEAD.yaml
    index.jsonl
    facts/F0042/r1.json
    supports/S0017/r1.json
    graphs/G0008.json
  additional_papers/
  human/                           # Optional contributed material
    notes.md                       # Contributor chooses the filename
    STATUS.md
    versions/H007/r1/notes.md      # Fixed source when a copy is necessary
  route_reviews/
    REVIEW001/
      REVIEW001.md
      human.md
      researchers/
        RESEARCHER01.md
        RESEARCHER02.md
        RESEARCHER03.md            # Only if the third researcher participates
  rounds/
    yyyy_mm_dd_roundNNN/
      PROBLEM.md
      ROUND.yaml
      PROJECT_RULES_r01.md          # Fixed copy if project rules exist
      ROUTES.md
      CHECKPOINT.yaml
      human.md
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
      human.md
      PROJECT_RULES_r01.md          # Fixed copy if project rules exist
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

Use stable identifiers for the objects in the table.

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
| Route review | `REVIEW001` |
| Material update | `U001` |
| Contributed item and revision | `H007@r1` |
| Literature source | `L001` |
| Computation run | `R003P01/E001` |

Each pair belongs to one research round or one paper task.
New rounds and paper tasks use new pair identifiers.
During recovery within the same round, keep its pair identifiers.
Inherited facts keep their original identifiers, revisions, and source references.

At each launch or replacement, specify the role's task, applicable rules, permitted inputs, and output paths.
Apply the input limits to inherited conversations, messages, and files that the role reads.
If your conversation contains excluded material, start the agent with `fork_turns: "none"` or its equivalent.
Give the agent only permitted inputs. This also applies when you have read another pair's pending proof.
Keep the fresh contexts required for independent route review drafts and independent work in a redo.

A replacement keeps the logical role, pair, and used budget. Supply only the permitted records and material it needs.
Keep the assigned verifier through repairs. Never replace a verifier to obtain a different decision.

Only one controller at a time may write shared records in a project.
Assign task and object identifiers, update shared control files, and publish graph versions in sequence.
Subagents can search, develop proofs, and review submissions in parallel. Copy admission decisions exactly.

An agent session identifier is only an additional reference.
It does not replace the logical role or pair identifier.
For historical evidence, refer to fixed records with their identifiers, versions, and actual paths.
`CURRENT.yaml`, `HEAD.yaml`, and `final/` are changeable entry points.
They are not sufficient identifiers for fixed historical evidence.

## 2. Start a new round — controller

An ordinary new round accepts only user requirements, `CURRENT.yaml`, the current fact graph, and the latest `final/` summary.
Use the entry check in section 1. User requirements include this round's project rules and subagent settings.
For ordinary startup, skip previous pair directories, submissions, verifier reviews, drafts, and checkpoints.
After a redo, use section 8 to select the next ordinary round's target and frontier.
For a redo, select historical inputs as specified below before you assign work.

Use section 9 to record a previous pause or resume an interrupted round.
A pause entry alone does not make execution recovery necessary.
Before new-round setup, complete any necessary confirmation from section 9.

1. Read the user's target, limits, changes, and interruption report.
2. If `CURRENT.yaml` is available, read it.
3. If an input handoff exists, read its `START_HERE.md`, `RESULT.yaml`, `PROBLEM.md`, and `FRONTIER.md` in that order.
4. From the selected graph, read the full records necessary for the task.
5. If the recovery conditions apply, use section 9 instead of the new-round steps below.
6. Record the new round, exact target, fixed handoff reference, rules reference, exceptions, policy, and new budgets.
7. If no graph exists, publish the initial project graph under section 6.
8. Record the fixed published input graph version. A new round needs only a reference to this version.
9. Apply the subagent model settings in `AGENTS.md`.
10. Assign the literature task to the researcher.

If there is no earlier state, initialize the project records.
An initial graph can contain no accepted results.
For an ordinary new round, read current facts through the root `fact_graph/HEAD.yaml`.
Do not replace a newer current graph with the graph in an older handoff.
A new conversation does not automatically create a new round budget.
Do not read `additional_papers/` during routine startup or recovery.

Create new pair identifiers, role assignments, and `TASK.md` records for this round.
Start each pair's submission sequence at `v01`.
Do not transfer previous pairs, pending reviews, or used submission counts into the new round.

Use the required contents for each record.

| Record | Required information |
| --- | --- |
| `README.md` | Project purpose, rule locations, date and path conventions, adopted policy location, reading order, supplementary-paper rule, deferred features. No separate progress ledger. |
| `CURRENT.yaml` | `project_id`, `current_round`, `current_fact_head`, `latest_handoff`. `current_fact_head` points to root `fact_graph/HEAD.yaml`. Fill paths only after targets exist. |
| `PROBLEM.md` | Original question, exact target, identifier and revision, objects, quantifiers, ranges, hypotheses, conclusion, definition references, additional requests, uncertainties, changes. |
| `ROUND.yaml` | Round identifier, creation time, preceding round in execution order, target revision and path. Fixed input and output graphs, budgets, started pairs, policy, and user instructions. Include `input_handoff_ref`, `project_rules_ref`, `subagent_models`, and task exceptions. |
| `ROUTES.md` | Route identifier, purpose, core method, sources, accepted inputs, distinguishing features, proof gaps, pair assignment, outcome, and stop reason. |
| `CHECKPOINT.yaml` | Last full graph, submissions, completed and pending reviews, accepted results awaiting entry, open requests, draft or code paths, next action. Use the formal records as the basis. |

Keep the exact question and its hypotheses in `PROBLEM.md`.
If the target changes, including through a new convention, save a new version such as `PROBLEM_r02.md`. Record the reason.
Point `ROUND.yaml` to the version in use. Identify a restricted or weaker claim separately.

Record explicit user assumptions with their scope. Other assertions need admission before use as established facts.
Give necessary proofs of equivalence to a pair.

For every new round, set `input_handoff_ref` to the exact handoff version you use.
Use `null` when no input handoff applies, including a redo from the first round's initial state.

Use a reference that still identifies the handoff after replacement, such as its round and unique ending record.
Match this reference to the handoff or its archived copy in `audit/handoffs/HNNN/`.
The round number or the current `final/` path alone cannot identify a handoff version.

### Redo a completed research round

On an explicit request, assign the new round a number one greater than the highest project round number.
This applies to the latest completed round and to any earlier completed round.
For example, after `R010`, a redo of `R003` starts `R011`. Its preceding round in execution order is `R010`.
Keep all records of the original and later rounds intact.

If the round is interrupted and the user requests continuation, resume the same round under section 9.
For a redo, allocate new pairs and budgets under its requirements. Select models under the new-task rules in `AGENTS.md`.
Each pair starts at `v01`. Pending reviews and used counts stay with the original round.

1. Use the original `ROUND.yaml` to locate the fixed target, user requirements, project rules, exceptions, input graph, and input handoff.
2. Read the handoff version that the original round used. A redo of the first round uses its initial question and requirements.
3. Use the original fixed input graph by default, even if a paper task published a graph between rounds.
   For example, `R002` ended at `G0010`, but `R003` started at `G0011`. A redo of `R003` uses `G0011`.
   Use `G0010` only if the user explicitly selects that earlier state.
4. Apply the original fixed project rules and exceptions. Record the rules you use under section 1.
   Apply current material permissions and any other use restrictions that cover this task.
5. Read the original round's human notes under section 1. Treat any old conclusion in a note as a claim to check.
6. In the new `ROUND.yaml`, identify the original round in `redo_of`. Record the selected inputs and each explicit user adjustment.
   Identify any change to the historical inputs that current use restrictions require.

If fixed records cannot establish a necessary requirement, input graph, or handoff version, identify the missing record.
Ask the user to supply or confirm the historical inputs before you proceed.

Keep `CURRENT.yaml.current_fact_head` at the project graph entry. Leave `HEAD.yaml` at the current graph.
Set `CURRENT.yaml.current_round` to the new round. Update `latest_handoff` only after its handoff is complete.
If an external interruption stops the redo, use section 9 for that new round. Keep its used budget and input limits.

### Keep independent work within the selected inputs

Read only the necessary fields and exact fact and support versions in the historical manifest.
Follow dependencies within that same manifest. Check each selected fact and support for current availability and use restrictions.
Exclude withdrawn or invalid support. A later proof of the same fact cannot replace it in the starting material.

For a contributed item, supply its permitted fixed manuscript and current permissions.
Exclude attempt results that the original or later tasks added to `human/STATUS.md`.

At startup, skip the original round's own handoff, route outcomes, submissions, reviews, and paper.
Exclude facts, proofs, and deductions that the original round or subsequent rounds and paper tasks added.
Later handoffs, papers, and use records can disclose the same material. Keep it out of independent assignments.

Start each independent researcher, worker, and verifier with `fork_turns: "none"` or its equivalent.
Specify each role's reading limits in the task records. Supply only permitted historical inputs, applicable rules, and permitted human notes.
Researchers can search sources independently. Pairs can develop new proofs through the usual admission channels.
Record the actual source or deduction even if it gives the same result again.

If a note identifies an old proof step, assign the check to a fixed pair in the new round.
The worker reads only the necessary passage and context in the fixed original.
The worker records its location and submits a fixed report to the assigned verifier.
Charge the pair and its formal deliveries to the new round. The old decision cannot establish the step.

Keep the old text and comparison findings from pairs that still work independently.
This includes passages from human notes that disclose the excluded work.
Record the actual dependencies of each finding. Apply any change in support availability or permission to the affected work.
Compare each independent result only after its evidence and admission record are fixed.
Compare the round's overall results after the corresponding independent work is fixed.

### Record the use of contributed material

Treat items that the user names as part of the current request. Apply sections 1 and 14.

When you select an item, record its identifier, version, route, and intended use in this round's `ROUTES.md`.
After every change to that use record, immediately update the item's use history in `human/STATUS.md`.
Include the material version, round, route identifier, and evidence location.
Record an attempt only after it occurs. Then enter its result or obstacle in both files.

If an interruption separates the two writes, use this round's `ROUTES.md` to complete the existing register entry.
Count each attempt once. If a retry condition requires a search of earlier rounds, leave it for a material update.

### Use a route review that the user cites

During ordinary startup, skip `route_reviews/` unless the user cites material there.
If the user cites only a task's `human.md`, read only the requested notes under section 1.
If the user requests the review itself or one of its routes, read the summary.
For example, route 2 of `REVIEW001` refers to `route_reviews/REVIEW001/REVIEW001.md`.
Read the completion note and any corrections for the original route number.
Read an individual researcher record only if the user explicitly requests that record.

Select routes that fit the target, project restrictions, and permitted graph evidence for this round.
For each route you select, record the review identifier and route number in this round's `ROUTES.md`.
Treat proposed routes as leads. An unadmitted claim cannot serve as an established premise.

Use `LITERATURE` for eligible source extracts under section 3.
If an admitted extract settles the exact target, record how its statement and conditions match the target.
That result needs no separate proof pair.
Send new deductions to a fixed pair for `DERIVED` admission under section 5.

### Set the research budget

Apply the order in section 1 to permitted research limits and result policies.
Record the adopted limits and result scope in `ROUND.yaml`. Section 8 gives the default result policy.

| Field | Default for a new research round |
| --- | --- |
| `max_pairs` | 4 pairs. The round can use a limit of 3. A slot can remain available for later work. |
| `max_formal_submissions_per_pair` | 4 submissions per pair, including the first submission and up to 3 repairs. |
| `started_pair_ids` | Start with an empty list (`[]`). Add a pair when it starts proof or review work. |

Count exploration, combination proofs, and separate lemma tasks against the pair limit.
Completed and failed pairs use their slots even when work runs in sequence.
Same-pair repairs and same-round recovery keep the original slot.
Literature work, route planning, fact reads, and administrative recovery use no slots.

Use section 5 to count formal submissions. Preserve used counts across pauses and sessions of the same round.
If a count is unknown, determine it from formal records before using the remaining budget.
Get explicit user agreement before exceeding an adopted research limit or starting automatic successive rounds.

## 3. Literature research — researcher

For literature leads during a route review, use section 13. Use the procedure below for admission in rounds or paper tasks.

1. Search for previous results, limits, counterexamples, corrections, and open directions.
2. Read the source text and the context necessary for each result.
3. Record source metadata in `research_papers/SOURCES.yaml`.
4. Extract the full definitions, hypotheses, quantifiers, ranges, and conclusions.
5. Record the exact source location and the notation changes for each fact.
6. Accept faithful literature facts through `LITERATURE`.
7. Record the research boundary, target gaps, and search limits in `RESEARCH.md`. Add the admitted fact identifiers after publication.
8. Send full admission records and route material to the controller.

Search snippets are leads, not sufficient evidence for a full theorem.
If the source is insufficient, keep the item as a lead.
Distinguish definitions, local hypotheses, admitted theorems, conjectures, and experimental observations.

For a proved claim, record its proof location or the proof source cited by the text.
Definitions alone need no proof location. Claims of existence, uniqueness, or equivalence attached to a definition need evidence.
Admission of a faithful extract requires neither a new proof nor a second verifier.

Each source record contains its identifier, title, authors, year, link or document identifier, version, retrieval time, and access limits.
If available, include the actual PDF path or a different location for source text.
Keep a different source record for each revision.
When subsequent rounds use the same source version, use the same source identifier and PDF.
Do not create placeholder PDFs.

Notation changes must keep the mathematical meaning unchanged.
Keep quantifier order, parameter ranges, norms, topology, regularity, uniformity, and constant dependencies unchanged.
If a source uses another definition under the same name, retain the source definition and hypotheses.
Before using the theorem, check that the current objects meet its hypotheses.
If a hypothesis fails, give any proposed generalization to a pair as a new claim.
If a change requires proof of equivalence or another condition, give the original fact and proof obligation to a pair.

If a literature result directly settles the target, give a clear target correspondence record.
The controller can then report the result without a proof pair.
Additional requests for a new proof or a stronger result stay separate tasks.
Report an unsuccessful search only in its actual search scope.
Do not claim global novelty from a search without a match alone.
For a paper's originality claims, use the complete checks in section 11.

List, scan, or read `additional_papers/` only for material the user requests. Do not monitor this optional directory.
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
If an active route changes its core method, count the new work as a new pair.
Repairs to the same method stay in the existing pair.

`TASK.md` identifies the pair, parent round or paper task, fixed roles, target, scope, and submission limit.
Include the input graph, permitted facts, expected output, constraints, and stop conditions.
For a redo, also identify the permitted support versions or fixed evidence for each assigned premise.
For research routes, add the route identifier, core method, distinguishing features, and proof gaps.
Do not invent proof routes for inventory, originality, manuscript, or presentation work.
Keep a record of material changes to the task.

Within their permitted inputs, pairs can share admitted facts, source requests, candidate claims, method outlines, and administrative progress.
Keep unaccepted proof text within its pair and the controller's administrative scope.
A different pair can take a candidate claim as a target. It needs admission before use as a premise.
Assign connecting arguments within the original scope and budget, or use an available pair.
Changes to paper structure or language stay within the assigned paper task.

## 5. Submit and review — worker and verifier

### Worker procedure

1. Read your `TASK.md`, the permitted facts, and your pair's previous review.
2. Complete your assigned route or paper work within its recorded scope and hypotheses.
3. Save useful drafts and specific failed steps in your own `drafts/` directory.
4. Request missing external facts from the researcher through the controller.
5. If a research route's core method must change, report the change to the controller.
6. Prepare the next formal submission in the remaining budget.
7. Save the submission in `submissions/vNN/`. Do not change this version.
8. Send this version to your assigned verifier for review.

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

For existing premises, use permitted, available graph facts with applicable support.
Record basic logic and project conventions without a separate fact for each arithmetic step.
Model memory, route plans, and unaccepted drafts cannot supply established premises.

A worker can prove a local claim inside its argument. Other tasks need its admission before use.
A summary cannot supply the proof.
To establish `T` from `L ⇒ T`, supply accepted support for `L`.

Identify the conclusion, proof, or method that each restriction covers.
Check whether the restriction includes indirect dependencies. Check whether it permits an independent proof.
If a restriction covers a proof, method, or indirect dependency, identify the exact support version you use.
If one proof is forbidden, use another admitted proof only if it meets the restrictions.
If the conclusion itself is forbidden, no proof of it permits its use within that scope.

### Verifier procedure

Examine only your fixed worker's submission. For paper reports, examine the assigned report and its evidence.

1. Read the fixed submission of your assigned worker and its exact dependencies.
2. Examine the claim against the target and all hypotheses.
3. Examine fact availability, versions, and applicability under the fixed rules and task exceptions.
4. Examine each necessary deduction for gaps and circular support.
5. Examine quantifiers, constant dependencies, uniformity, and applicable boundary cases.
6. If the argument uses computation, examine computational coverage and precision.
7. For a counterexample, examine the original hypotheses and the failure of the original conclusion.
8. Examine `PROOF_IDEA.md` against section 12.
9. Write `reviews/vNN/REVIEW.md` for that exact submission.

For restrictions on proofs, methods, or indirect dependencies, examine the selected support version and the dependency chain in scope.
For indirect dependencies in scope, check the selected support's fixed proof and its source when necessary.
If the fact graph has no record of a dependency, do not assume that the dependency is absent.
If you cannot verify a relevant dependency, do not treat this support as meeting the task restriction.

If the worker claims a permitted independent proof, examine the deductions that establish its independence.
Send a new deduction from review to the worker for formal submission.

The review records the verifier, pair, submission version, paths, scope, decision, and reasons.
Use the review decisions `ACCEPT`, `REWORK`, or `INCOMPLETE`.
These are review decisions, not mathematical results or paper completion states.
List exact accepted claims, their dependencies, target coverage, rejected steps, locations, reasons, and remaining obligations.

With a full basis and a clear scope, accept an independent local result.
A request for repairs to the whole proof does not cancel that local acceptance.
Record mathematical admission, proof-idea checks, and required paper checks separately.
Keep explicit mathematical admission and established result status when a required explanation or originality check is incomplete.
If a required check is incomplete, the affected delivery remains incomplete.

Use necessary recalculation or diagnostic counterexamples for review.
Do not silently complete the worker's proof.
For subsequent submissions, reuse checks of unchanged, unaffected parts.
Give a decision for the current version.

Complete the review of the last permitted submission before applying the limit.
At the limit, stop further submissions. Research pairs use their round policy. Paper pairs use section 10.
Keep accepted local results and the remaining obligations.

For correction of a completed review, keep the previous report. Add a clear correction.

### Count formal submissions

Use the same counting rules for rounds and paper tasks, with their respective limits.
Count one submission when a fixed version reaches the fixed verifier for a formal decision.
Count at delivery, regardless of the decision. Use each pair's formal records as its only count.
One delivery counts once even if it covers several claims or defects.

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

For a fact or proof from contributed material, keep its origin in the fixed source record or formal submission.
Include the item identifier, version, original author, and basis for its permitted uses.
The evidence references in the graph support record must lead back to that source.

Ordinary theorem use names the fact version.
Use or claims of a particular proof, construction, or method also identify its support or fixed proof version.

A new proof of an existing fact needs new support admitted through `DERIVED`.
Other valid support for the fact does not establish that proof.
Task restrictions govern use of evidence. Preserve the fact's admission and its historical support records.

Send a suspected proof gap or a conflict between accepted sources under the same conditions for formal examination.
If the examination confirms a defect or conflict, stop using the affected support.
Follow reverse dependencies to check all affected results. Keep other valid support for the exact statement available.
Stop using a result if it loses all applicable valid support.
A defective proof does not by itself refute the claim.

Send new mathematical judgments to the researcher or fixed pair. Do not decide them as controller.
Circular dependencies cannot establish a proof. Joint induction needs an admitted complete argument.

### Compare admitted results before publication

Apply this procedure to each result or batch from any research round or paper task.
Comparison and publication can start while other work continues.

1. Fix each exact statement and its admission evidence.
   For `LITERATURE`, use the researcher's fixed source and admission record.
   For `DERIVED`, use the worker's fixed submission and its assigned verifier's decision.
   In a redo, complete this step before you read excluded results for comparison.
2. Read the manifest that `fact_graph/HEAD.yaml` identifies at publication. Use `index.jsonl` to find candidate matches.
   If the index is missing or old, rebuild it or read the manifest directly.
3. Compare the full statements, definitions, hypotheses, quantifiers, ranges, and conclusions. Compare entries within the batch as well.
4. Check the fixed proof or source, actual dependencies, and review records before you reuse support.
   A similar name, wording, or method can suggest a candidate. It cannot establish a match.

The controller can check identity, versions, and the admitted scope.
If equivalence, implication, proof relationships, or support applicability need a new argument, assign it to a fixed pair under `DERIVED`.
Use the remaining pair slots and submissions of the round or paper task that needs the comparison.

If the budget is insufficient or the relationship remains open, retain the precise admitted statements and evidence.
Record the open relationship. Keep the records separate until evidence permits a merge or reuse of support.
Do not increase the task budget automatically.

| Finding | Publication decision |
| --- | --- |
| Same statement and same usable fixed evidence | Reuse the fact and support versions. Keep the task's own source or submission and review records. |
| Same statement with different admitted support | Keep the fact version. Add support with its evidence and actual dependencies. A change of wording or submission number alone does not establish a new proof. |
| Correction to the same proof | Create a support revision for the corrected evidence or dependencies. |
| Correction to the same statement | Create a fact revision. Keep the old version. Each support must name the exact version it establishes. |
| Distinct statements with uses of their own | Register them separately. For example, a stronger result and a weaker result can both have entries. |
| Admitted statement absent from the current graph | Create one fact for all matching records in the batch. Register each distinct admitted support once with its source and dependencies. |

Record each task's own result and fixed evidence separately from its mapping to reused or new graph records.
A proof cites only evidence it actually used. A later match cannot supply an earlier premise.

On a repeated publication request, check the existing mapping. Register each fixed version once.
If all entries reuse existing records and no state changes, keep the current graph. Record the reproduction in the task.
In the publication or handoff record, identify the comparison graph and final output graph, even when they match.

### Publish changes and assign admitted results

1. Before publication, check whether the current graph has changed since the comparison.
   If it has changed, check the affected entries against the new manifest.
2. Save new or revised fact and support records.
3. Use the current graph at publication as the parent of the new manifest. Keep all other facts, supports, and dependencies.
4. Record availability states and reasons. Check all references and versions.
5. After all required records exist, update `HEAD.yaml`.
6. Generate the search index for that graph again.
7. Record the publication event in its source task. For a research round, update its checkpoint.

After admission, comparison, and publication, another pair can use the result during the same task.
Specify the exact fact version and its permitted support or fixed evidence in the task record.
In a redo, give independent pairs only usable premises from the selected historical inputs.
You can also give them this round's results if independent work established them from permitted inputs through mathematical admission.
For example, a second pair can use the first pair's admitted proof of a lemma.
Exclude earlier proofs outside that pair's scope, even if both proofs share a fact identifier.

Record actual dependencies for findings from a comparison or a check of old text.
Use such findings to match records, update support states, and publish changes.
Keep findings that rely on excluded material out of independent work. Preserve the evidence each pair actually used.
A worker can still prove and use a local lemma within one complete submission.

`CURRENT.yaml.current_fact_head` points to the root `HEAD.yaml`.
Do not keep another current graph identifier in `CURRENT.yaml`.
`ROUND.yaml` and `PAPER.md` refer to fixed input and output graph versions.
For the first graph, save the records and manifest before setting the entry point.
An interruption record refers to the last complete published graph.

Keep published fact, support, and manifest files unchanged.
Changes to hypotheses or definitions also require a fact revision.

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
Successful execution or PDF compilation alone cannot establish a mathematical claim.

For a requested paper, use `src/main.tex`, `references.bib`, and `CLAIMS.yaml`.
Map paper labels to exact fact versions and proof locations in `CLAIMS.yaml`.
For new proof or method claims, also identify the actual support or fixed proof version.
Keep open claims clearly identified as open.

### Review the complete manuscript

For delivery as a completed paper, assign the complete manuscript to a fixed worker and verifier.
This applies to papers from one round and papers from several rounds.
The controller can arrange existing text and compile the paper. Give new mathematical arguments to a pair for admission.
For integration across rounds, use the complete procedure in section 10.
Use the default `amsart` form and mathematical language rules in that section for papers.

1. Have the responsible worker submit the exact, fixed, complete manuscript to its verifier.
2. Have that verifier check the definitions, notation, hypotheses, cross-references, links between arguments, and contribution claims throughout the manuscript.
   Complete the other checks that apply to this paper. Record the decision for this exact manuscript.
3. After acceptance, build the final PDF from the reviewed fixed sources. Check that the PDF matches those sources.

Within a research round, use a suitable existing pair or an available pair slot.
Charge the manuscript and formal repairs to that pair's remaining submissions in its own task.
An existing `PAPER` task uses its own pairs and budget. Keep round and paper budgets separate.
If the budget is insufficient or a required review remains open, record incomplete paper delivery. Keep admitted mathematical results.

A research round can retain a partial manuscript or PDF. Record the completed work, actual review scope, and outstanding checks.
Record paper delivery separately from the mathematical result. A partial manuscript alone does not start a `PAPER` task.

For a published PDF, save `out/paper.pdf` and `BUILD.yaml`.
Record the build time, fixed source location, graph version, command, and necessary tools.
Keep separate source records for separate published versions.

### Record unresolved issues

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

Keep issue types separate from mathematical results. Record inconsistent hypotheses.
A proof gap alone does not show a missing specification.
Stop only the affected work. Keep unresolved target information explicit.

## 8. Complete a round — controller

### Determine the mathematical result

For an ordinary round, assess cumulative progress for the exact target version by default.
List this round's new results separately. Count a project deduction as a new statement only after admission and comparison under section 6.
For claims of originality in a paper, use section 11.

| Result | Required evidence |
| --- | --- |
| `PROVED` | An admitted proof or an exact literature result establishes the original target. |
| `DISPROVED` | An admitted refutation applies. A counterexample must satisfy the original hypotheses and violate the conclusion. |
| `PARTIALLY_RESOLVED` | The target remains open. At least one admitted project result satisfies the partial-result policy. |
| `UNRESOLVED` | The target remains open. No admitted project result satisfies the partial-result policy. |

Partial results include a restricted result, a substantial lemma, a weaker conclusion, or a result for some parameter values.
A rigorous reduction can also qualify. State any extra hypotheses.

If the result status is unknown, omit `result_status`. Record the missing evidence.
Proof failure, budget exhaustion, and an unsuccessful search do not establish proof or refutation.
Report progress on extra requests separately, including a new proof under method restrictions or a stronger result.

For a redo, apply the same four criteria within the scope of independent work.
Use only permitted historical evidence and evidence independently admitted from permitted inputs in this round.
In `RESULT.yaml`, record the following information.

- In `result_scope`, identify the original round, actual historical inputs, and applicable restrictions.
- In `basis_fact_ids` and the evidence locations, identify the facts and exact support or fixed evidence used within this scope.
- In `scope_note` and the handoff, distinguish the independent result from findings of directed checks or comparisons.
  Give the current status of the original decision separately.
- In `new_results_this_round`, use the publication decisions from section 6. Record a reproduction separately and a new proof as new support.

For example, a redo can end as `UNRESOLVED` even if the original round ended as `PROVED`.
Failure to reproduce the result leaves the original decision in force unless formal examination changes its basis.
Report findings from checks of excluded evidence with their actual scope and dependencies. They cannot establish independent reproduction.

### Prepare the handoff

Complete the round when you settle the target, finish the tasks, exhaust the budget, or reach an agreed boundary.
Pair or formal submission budget exhaustion is not an interruption.
If an external platform usage limit interrupts execution, use section 9.
Unresolved specifications or conflicts can also end the affected work with a clear explanation.
For completion without interruption, use only necessary pair slots and actual outputs. A paper or PDF is optional.

1. Record the actual reason for completion.
2. Collect formal outcomes and unfinished tasks.
3. Check any remaining admitted results against the project graph under section 6.
4. Publish any changes from that comparison.
5. Identify the complete current project graph for the handoff, including results outside a redo's evidence scope.
6. Prepare the five handoff files in the table below.
7. Examine target versions, fact versions, decisions, counts, and evidence paths against their source records.
8. After the handoff files are ready, publish the actual ending declaration in `final/RESULT.yaml`.
9. Update `CURRENT.yaml` with the latest handoff location. Create or preserve the round's `human.md` beside `final/` under section 1.
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

Use the following fields for known information in `RESULT.yaml`.

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

After a redo, the next ordinary round follows the target and frontier in the latest handoff by default.
Use the full current graph and ordinary rules for project requirements, models, budgets, and result scope.
If the user selects an earlier target, read only that target and its necessary frontier from the earlier records.
Use the current graph unless the user explicitly limits the inputs.

During research, read cited evidence beyond `final/` only for a specific source check.
Before future use of a historical fact, examine its current availability through `CURRENT.yaml`.

Keep failed proofs, rejected submissions, reviews, graph versions, and drafts necessary for recovery.
Preserve code necessary for review or computation.
Do not delete user papers as temporary material.
Do not start a new round without the user's instruction or an existing agreement.

## 9. Pause and recover — controller

This section applies only to research rounds. Paper integration has no execution-recovery procedure.
For a request to resume research, first complete the entry check in section 1.
`PAUSE` is the only `run_status` value. Omit `run_status` during ordinary work and completion without interruption.
Keep established mathematical results when a pause occurs.

### Immediate stop

Use these steps for an immediate stop request or a subagent model configuration error.
Also use them if a request to use contributed material stops an active round under section 1.

1. Stop new work in the entire round.
2. Send stop requests to active subagents.
3. Save the available minimum pause information in `final/RESULT.yaml`.

Record the round, `run_status: PAUSE`, trigger, actual record time, and handoff completeness.
Include known results, their evidence, the last reliable graph, pending work, exact versions, used submissions, missing files, and next action.
If a value is unknown, do not include its field. Record the missing information.
Do not wait for unfinished proofs, reviews, a full handoff, a PDF, or cleanup.

For a subagent model configuration error, set `pause_reason: SUBAGENT_MODEL_CONFIG_ERROR`. Include the error in the pause record.
If Codex rejects a launch, the request itself uses no pair slot or formal submission.
After reporting the error, wait for the user to request continuation of this round before resuming it.

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

Recover execution records only when both conditions hold.

- The latest applicable pause record or the user's report identifies the previous round as interrupted.
- The current task is to continue that same round.

After any necessary confirmation, use section 2 for a requested new round with new pairs and budgets.
If the intended round is unclear, ask the user before you read execution records.
During recovery, read only the interrupted round's execution records.
Apply the fixed rules and any explicit changes under section 1 before resuming the work.

Use the round's saved `subagent_models` for new launches. Keep each single-launch exception within its recorded scope.
If a configuration error prevented the first valid settings record, read the corrected settings under `AGENTS.md`.
For an older round without a settings record, use its recorded model instructions or the Codex defaults.

Change a saved setting only at the user's explicit request. If the user selects a corrected file, read it again.
Record the old and new values and the first affected launch.
After a configuration error, check the settings before work resumes. If the error persists, keep the round paused.

1. Locate the last full, identifiable target and graph versions.
2. Recover literature admissions and completed verifier decisions from formal records.
3. Locate unfinished pairs, exact submissions, review progress, and submission history.
4. Separate accepted facts, pending drafts, and incomplete files.
5. Use section 6 for admitted results still awaiting publication.
6. Continue in the existing round and pair directories.
7. Before research continues, record the recovery basis in `audit/`.

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

When the user requests a paper from accumulated results, start with the entry check in section 1.
If the user requests only an analysis of accumulated results, stop after the inventory and topic proposals.
Examine all results in scope before selecting a coherent paper topic and its contents.

The original problem can remain open. Substantial partial results can support a separate paper.
Do not put every result in the paper. Record the disposition of omitted results.

Create `out_papers/PAPER001/` at the project root, beside `rounds/` and `additional_papers/`.
Use a new paper task identifier, pairs, and budget. Do not increase the round number.
Do not change `CURRENT.yaml.current_round` or the research `latest_handoff`.
Before the first subagent starts, apply the model settings in `AGENTS.md`.
For a new integration that cites notes from an earlier task, use the requested notes under section 1.

Unless the user limits the scope, examine all results available when the task starts.
Use the current project rules for each new paper task, including a new request after an interruption.
Identify restricted results or proofs in the inventory. Cover all results in the requested scope.

If selected evidence comes from contributed material, follow its source references even if the user did not name `human/`.
Read the specific register entry and fixed manuscript as necessary to confirm the author and current permission for public use.
Record the item version, mathematical basis, author, and permitted public use in `INVENTORY.md`.

Select unpublished proofs within the recorded permission. Follow the recorded requirements for credit.
Apply the restrictions in section 14 to each support.
If a restriction takes effect during the paper task, revise the affected selection and keep its earlier source records.

Read graph records, round handoffs, papers, and cited proofs as evidence, not as execution recovery.
Do not add a previous research pause because paper integration starts.
Unaccepted results can enter the inventory, but cannot serve as accepted premises.
Get admission for omitted mathematical results before use as established facts.

| Record | Contents |
| --- | --- |
| `PAPER.md` | User request, scope, topic, fixed input and output graphs. Original target version and mathematical result. Record `project_rules_ref`, `subagent_models`, task exceptions, delivery progress, budget summary, and open items. |
| `INVENTORY.md` | Result identifiers, sources, admission states, topic groups, inclusion decisions, and reasons. Contribution claims and references to originality decisions. |
| `pairs/` | Tasks, drafts, fixed submissions with `PROOF_IDEA.md`, and fixed reviews. |
| `src/` | `main.tex`, `references.bib`, and `CLAIMS.yaml`. Exact facts, proof locations, and support versions for proof or method claims. |
| `out/` | `paper.pdf` and `BUILD.yaml`, with fixed sources, graph version, command, build time, and tools. |

Use 6 pairs by default, with a cumulative maximum of 8 for the task.
Schedule pairs according to their work dependencies. They can run at different times.
Each limit in the table includes the first formal submission.

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
The report must include checks of mathematical language, proof ideas, citations, and consistency between source files and the PDF.

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
13. Deliver the reviewed paper and its supporting records.

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

On a subagent model configuration error, stop the entire paper task. Send stop requests to its active subagents.
Record incomplete delivery and the cause in `PAPER.md`. Report the error as specified in `AGENTS.md`.

Near a submission limit, reduce the scope to a coherent paper with sufficient evidence.
Review changed content within the remaining budget. Scope reduction does not remove review requirements.

Review the last permitted submission. If it fails, stop further submissions from that pair.
Other pairs can continue work that does not depend on the failed item.
If you omit a nonessential failed result, the changed manuscript still needs review within budget.

If a core defect or required check remains open, record delivery as incomplete with the specific reason.
Retain admitted mathematics, existing files, used counts, and review outcomes.
Do not increase submission limits automatically.

After an external interruption, record incompleteness when possible. Do not resume the paper task.
For a new user request to start integration again, create a new task, pairs, and budget.
Previous files can serve as input material, not restored execution state.

Use section 6 to compare and publish admitted results during the paper task.
Identify the paper task as the source of its new or revised support. Preserve the source of any support you reuse.
No research round is necessary for these results.

Keep the original target's mathematical result separate from paper delivery completion.
Use section 7 for complete manuscript review. When the task ends normally, create or preserve its `human.md` under section 1.

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
For results from other fields, explain how their notation and terms correspond to those in the paper.
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

For main contributions, include the following source types in the search.

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

The originality worker supplies necessary new arguments. Its fixed verifier reviews them.
The verifier can suggest a lead, but cannot admit its own unreviewed deduction.
New equivalence results or reductions need `DERIVED` admission before use.

An implication `A ⇒ B` establishes a mathematical relation, not the absence of all contribution.
Examine what the new argument, method, or connection adds.
Simple renaming or routine substitution normally gives a restatement or corollary.
For a known result with a different proof, examine the claimed proof or method contribution.
Examine actual changes to hypotheses, ranges, bounds, and conclusions.
Failure to prove overlap does not itself prove originality.

Complete the following checks for each contribution.

1. State the exact claim and proposed originality type.
2. Cover applicable source types and principal statement variants.
3. Read and compare key sources that could cover the result.
4. Resolve concrete overlap doubts and record the basis.

Resolution can confirm overlap and change the contribution claim.
After the initial search, search again for specific gaps.
When these checks are complete and no new leads remain, stop general searches.
Time, search counts, and exhausted budgets cannot replace completion of the checks.

| Finding | Action |
| --- | --- |
| Earlier work covers the result | Cite it and revise the contribution claim. |
| All checks are complete. No source examined covers the claimed contribution. All concrete doubts have an answer. | Permit a normal originality claim for the examined contribution. |
| A consequential doubt remains | Identify the missing evidence. Keep that originality claim open. |

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
The worker writes the explanation. Its fixed verifier examines it.
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

## 13. Review possible research routes — controller and researchers

When the user requests alternative ways to prove or disprove the original claim, start a separate route review.
Use the entry check and the current project rules in section 1.
Propose routes only. Leave proofs, counterexample verification, and mathematical admission to formal research.
A route review uses no research round number, pair slot, or formal submission.

### Set up the review — controller

Use the next review number in the project, even if two reviews follow the same round.
Write the review files in their own directory, such as `route_reviews/REVIEW001/`.
You can read `CURRENT.yaml`, earlier route records, `final/` handoffs, and the project fact graph to organize the review.
Treat all these inputs as read-only.

Start the summary in a file with the review identifier as its name, such as `REVIEW001.md`.
Record the review date, original claim and version, applicable restrictions, and the version of any fact graph you use.
Before the first researcher starts, read and validate the project root `SUBAGENT_MODELS.json` if present.
Use the field priorities and launch rules in `AGENTS.md` for the `researcher` role.

In the summary, identify each participant record as received, unfinished, or missing. State whether the summary is complete.
If work stops or a participant cannot finish, keep the available material. Record what is missing and why, where known.
Complete the summary only after you receive the finished records from all participants.

### Assign the researchers — controller

Assign two researchers by default. Use at most three.
Start the first two in fresh contexts with `fork_turns: "none"`. Neither researcher inherits your conversation.
Give both the same starting material. Specify what they may read for the first draft.

- Include the original claim and its version, the definitions, the user's instructions, and the applicable project restrictions and exceptions.
- Include the necessary admitted facts with their versions.
- Exclude earlier routes, assessments of those routes, and other participants' views from the material you supply.

Each researcher uses only this material to propose routes and save an independent draft in its own record.
Wait until both save their drafts before sharing the designated historical material and participant records for comparison.
Share the user's selected contributed routes and notes from earlier tasks only during comparison.
Use section 1 to record the notes you use.
In the review summary, record the item, version, and comparison. If the review only discussed the route, say so.

If you identify a separate search question or another approach, you can assign a third researcher.
The third researcher can start with the others or after the first drafts.
This researcher can search the literature, propose routes, or do both.
A search can cover recent papers, results under other terms, or known counterexamples.

For an independent opinion, use the same fresh context setting, starting material, and reading limits.
That researcher must also save its own draft before it sees comparison material.
For a proposal about a known obstacle, give the researcher the specific obstacle.

### Write your record — researcher

Write your own file in `researchers/`, as shown in section 1. Create the third record only if the third researcher participates.
Start with your assignment and the material you received. Identify the claim and restrictions for independent work.
For work on a known obstacle, state the question the controller gave you.

- Give each proposed route a title that identifies its method. State what you hope to prove or where to look for a counterexample.
- Describe the construction, reduction, or special case you would try. Give a concrete mathematical observation or source that suggests it.
- State the necessary conditions. Give versions for admitted facts and identify steps that still need proof.
  Name the main obstacle and the first check that could show whether the route is worth further work.
- For a literature search, state the question. Give the authors, title, and a specific location such as a theorem number, page, or link.
  Explain which result or method could apply and how its conditions compare with the claim's conditions.
  A researcher assigned only a search can report just these findings after the opening.

Keep new source results as literature leads and new deductions as proposals for verification.
If you find no useful new lead, record the directions you examined and the obstacle you found.
After comparison, append any change of opinion. Identify the affected route and the material that changed your assessment.
Keep the independent draft intact.

### Complete the summary — controller

Write a summary that readers can use without opening the individual records. Keep the completion note and list the rounds compared.
Briefly describe earlier methods and their main obstacles.
Compare proposals with the relevant rounds' `ROUTES.md`, `final/FRONTIER.md`, and admitted facts.
Use the core method and key obstacle to identify overlap.

Give each candidate route a stable number within the summary and a short title. For each route, include the following information.

- State what the route could prove or disprove. Give the proposed method and the reason to try it.
- Identify the related earlier route and the key difference. You can combine proposals with the same method and obstacle.
  Link to the relevant section in each contributor's record.
- Give the relevant fact versions or source locations in the summary. Distinguish admitted facts, literature leads, and unverified proposals.
- Identify the open step and the first useful check. If researchers disagree, give the reasons for each view.
  When available, describe a check that could distinguish those views.

If a comparison requires an unadmitted equivalence, implication, or impossibility claim, leave that judgment open.
Do not prove or decide a new claim to combine routes or settle a disagreement.
If all proposals repeat earlier routes, report the overlap and the remaining obstacle.

After delivery, append corrections to the summary. Give the date, reason, and affected route numbers for each correction.
Preserve the original text and route numbers. For use in a new round, follow section 2.
When the review ends normally, create or preserve its `human.md` under section 1.

## 14. Update the register of contributed material — controller

Start a separate material update when the user asks you to organize new or revised material in `human/`.
The user can also request an update to add a missing attempt or to close or reopen an item.

Use the entry checks in section 1. Do the work without subagents. Give each update its own identifier, such as `U001`.
A material update uses no research round number, pair slot, or formal submission.
Use the fact graph, `CURRENT.yaml`, and existing task directories as read-only sources.

### Register each source version

1. For the first update, examine the manuscripts the user specifies.
   For later updates, compare the material with the previous update. Identify additions, revisions, and explicit withdrawals within scope.
2. Assign a stable identifier such as `H007` to each idea or result that a task can cite separately.
   Keep the identifier across revisions, such as `H007@r2`.
3. Cite a traceable fixed original if one exists. Otherwise, save a copy under `human/versions/` for that version.
4. For each item, find use records after the last task and location examined.
   Read only route, review, or paper records that cite the item. Read their fixed evidence when necessary to verify an outcome.
5. Create `human/STATUS.md` on the first update. Give each item a section under its identifier.
   Update only entries that have changed.
6. Record the update identifier, date, tasks examined, and registration status of each version.
   Report changes and outstanding checks to the user.

Mark each version complete only when its fixed manuscript and its register entry are both complete.
If the update stops, completed versions remain available. An incomplete revision cannot become the default version.
Keep earlier versions, past attempts, reasons for closure, and use records already entered by research rounds.
On a repeated update, record each version and each attempt only once.

### Contents of an item entry

- **Proposal and source.** Summarize the problem, method, conditions, and main gap.
  Give the version, registration status, original path, and fixed source location, including the page or section.
  Name the original author and, if different, the contributor.
- **Use history.** Give the last task and location examined. Distinguish no recorded attempt, discussion only, and an actual attempt.
  For an attempt, record the method and outcome or obstacle. Cite the task record.
  Cite the fixed fact or review version for an existing decision. Verify the entries from research rounds.
- **Future work.** Mark the item open, open under a stated retry condition, or closed.
  Give the reason for a priority retry. For closure, record the user's instruction, its scope, and any reason the user gave.
- **Permitted use.** Record permission for project research and for public papers separately.
  State the credit and citation requirements. Give the basis for the permissions and requirements.
  If permission for public use of unpublished material is unknown, use it only within the project.

Route reviews and paper tasks record use in their own task records. Add that use to the register during a material update.

### Apply changes and restrictions

If an item has a retry condition, make sure it holds before another attempt.
Finding a way to meet that condition can be a new research target.

Close or reopen an item only on the user's explicit instruction in a material update.
For a request to retry a closed item, report the scope and reason for closure.
An attempt within that scope requires explicit reopening, even if the user names another version.
Register a substantially different variant outside that scope separately. State the difference.
For a project-wide restriction that also covers independently proposed methods, use `PROJECT_RULES.md`.

An active task keeps its selected version when the author revises the manuscript. A change to permitted use can affect that task.
For a withdrawal, closure, or change of permission, record the user's scope and when the change takes effect.
Apply it to all tasks in that scope, including active tasks.
For a withdrawal, identify the items or versions, uses, and affected tasks.
Record the withdrawal under future work or permitted use, as the user intended.

Apply each restriction to the stated result, proof, method, and indirect dependencies within its scope.
Assess each independent support against its own source and restrictions.
Record the obstacle a failed attempt encountered. A claim that the entire route is impossible needs mathematical evidence.
For an admitted counterexample or impossibility proof, give the exact claim and conditions it rules out.
If the user asks for a proof under the same conditions, cite the counterexample or impossibility proof.

### Separate the proposal from its mathematical evidence

Registration records what the author proposed. The controller can report existing decisions. Leave new proofs and counterexample checks to formal research.
Use an idea as a possible route. An explicit user assumption supports only a conditional conclusion.

For an eligible literature source, the researcher admits a faithful extract through `LITERATURE`.
For an original proof or counterexample that needs verification, the worker prepares a fixed submission.
The assigned verifier examines it under `DERIVED`. Record who wrote the original and who verified the work.

Use admitted results under the fact graph rules. Permission for public use still applies.
A change in use or closure leaves mathematical decisions intact. Send doubts about correctness through the existing review and graph procedures.
