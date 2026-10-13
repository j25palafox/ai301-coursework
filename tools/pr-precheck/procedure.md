# Procedure: how this skill grades a PR package

## Read order

1. After `SKILL.md` selects the mode and applies its input and scope gates, read `references/evidence-guide.md` first. Use it to identify where each evidence family lives; do not gather findings or grade checks yet. In live mode, use only the authorized repository and inputs; in eval mode, use only the frozen package.

2. Read the issue and relevant thread context to establish the reported problem, intended outcome, and any maintainer requirements or decisions. In eval mode, use the issue context supplied by the package rather than fetching the live thread.

3. In live mode, read the full plan.md, including its scope, implementation approach, test plan, and deviation notes. In eval mode, read plan_context_markdown and any deviation notes supplied in the frozen package. Record the planned behavior, files or components, verification steps, and explicitly disclosed changes to the plan. Do not assume the PR implements the plan merely because its description says so.

4. Read the applicable repository requirements: the PR template, `docs/CONTRIBUTING.md`, and any other policy or convention actually supplied or identified by the evidence guide. In eval mode, use the frozen repository-facts or standards evidence. Distinguish mandatory requirements from recommendations.

5. Read the complete proposed change: in live mode, identify the PR's feature branch and target base branch, then inspect the committed changes using git diff <base-branch>...HEAD (three dots), including the changed-file list and relevant hunks. In eval mode, inspect the supplied diff. Read commit information when available to clarify what is being proposed, but assess the final diff rather than the number or appearance of commits.

6. Read the test and verification evidence alongside the plan's test plan. Identify recorded commands, their printed output, observed outcomes, failures, skipped checks, and stated limits. Treat an assertion that a test passed as a claim, not as its own proof.

7. Read the draft PR title and description last, including summary, issue reference, changes, testing, screenshots/demo or N/A explanation, and reviewer notes where the repository template calls for them. Identify what the author claims was changed, tested, not changed, or left incomplete.

8. Do not grade individual checks until all available required inputs have been read in this order. If an input triggers a refusal under `SKILL.md`, follow that refusal rule rather than inventing substitute evidence.

## Evidence gathering

1. For every check in `rubric.md`, use `references/evidence-guide.md` to locate its named sources. Record the specific file, diff hunk, plan passage, command/output, PR field, or repository rule that supports, contradicts, or fails to establish each condition. Keep source facts separate from contributor claims.

2. For `plan-fidelity`, gather:
   - the issue's intended outcome and the plan's stated scope, steps, and deviation notes;
   - every file and substantive behavior changed in the diff;
   - planned changes that are absent, additional changes that were introduced, and any explanation recorded in the deviation notes; and
   - evidence showing whether the final change remains aligned with the issue and the plan as amended.
   Compare the diff against the plan in both directions: extra work and missing planned work can both matter. A claim of fidelity does not excuse a contradiction in the diff.

3. For `claims-match-diff`, gather:
   - the PR title and the description's purpose, change summary, and material limitations;
   - concrete assertions about files, behavior, scope, or unchanged areas; and
   - the relevant diff hunks or complete changed-file list that confirm or contradict those assertions.
   Check negative claims against the full diff rather than treating absence from an excerpt as proof. Do not require particular wording or description length unless the repository actually requires it.

4. For `behavior-evidence`, gather:
   - the reproduced or reported behavior and the expected outcome identified by the issue and plan;
   - the specific behavior the plan's test steps were intended to exercise;
   - the tests and verification artifacts supplied, including commands and their output, executed scripts, screenshots, or demonstrations showing observable behavior;
   - the observed results and any disclosed failure, limitation, or untested behavior.
   Compare what the evidence visibly demonstrates with what the PR says it demonstrates. A disclosed failure is evidence of the actual outcome, not proof of success and not automatically grounds for rejection by itself.

5. For `repository-checks`, gather:
   - the applicable test, lint, build, or other verification commands actually required by the repository;
   - the commands the contributor attempted or ran, including printed output and recorded results; and
   - any omitted, blocked, or failing checks and the contributor's explanation.
   Distinguish an attempted check with an observable failure from a bare claim that checks ran. Do not invent required commands or treat a failure as a pass; apply the rubric's rule to the disclosed outcome and available proof.

6. For `diff-quality`, gather:
   - the complete changed-file list and substantive diff hunks;
   - unrelated edits, debug artifacts, accidental files, generated debris, or changes that obscure the issue-related work; and
   - repository evidence showing whether an unusual change is necessary or expected.
   Judge whether the final diff is reviewable, not whether its commit count, line count, or formatting matches an arbitrary preference.

7. For `standards-comms`, gather:
   - the repository's actual PR template and contributor or AI-use requirements;
   - the PR description fields and reviewer notes addressing those requirements;
   - any required disclosure of AI use, deviations, known limits, or missing evidence; and
   - the issue reference and any relevant maintainer directions.
   Compare each applicable requirement with the supplied PR material. Accept a justified N/A only where the requirement permits it. In live mode, keep separate any `voice-guide.md` feedback that `SKILL.md` says does not independently change the verdict; eval mode does not use that guide.

8. Preserve source attribution and chronology when evidence conflicts. Later explicit maintainer decisions can supersede earlier guidance. Do not turn optional practices into required checks or use the PR description as independent proof of the diff or test results.

9. Record the evidence for every rubric check without assigning `pass`, `fail`, or `unclear` yet. Grading belongs to Check execution.

## Check execution

1. Execute all checks in the order listed in `rubric.md`, including any preferred checks. Grade each independently and do not stop after an earlier failure or uncertainty.

2. For each check, apply its exact pass condition to the evidence gathered for that check. Grade the proposed PR package as submitted, not a hypothetical PR the contributor could improve later.

3. For comparisons to the plan, use the actual diff and any documented deviations; do not silently excuse extra changes or assume omitted planned changes were implemented.

4. For description and test claims, distinguish a statement made by the contributor from independent evidence in the diff or recorded command output. Do not grant credit for an asserted passing test with no observable support.

5. Apply the rubric to the demonstrated outcome, including failed or incomplete verification. A disclosed failure is evidence of what happened, not evidence of a successful fix. A failed test directly relevant to the issue must satisfy the rubric's failure condition regardless of how accurately the contributor disclosed it. Evaluate unrelated failures separately under applicable repository requirements.

6. Apply only repository standards supported by the actual template, contributor guidance, policy, or maintainer instruction. Do not add requirements for commit count, PR length, or stylistic polish that are absent from the rubric and repository rules.

7. When a check has multiple required parts, assign `pass` only if every part is supported. Assign `fail` when evidence contradicts a required condition, shows a defined failure, or the submission omits something the check explicitly requires. Under the contract default, an affirmative PR claim with no verifiable support fails unless the rubric explicitly provides a different rule.

8. Assign `unclear` only when the evidence needed to judge a condition is genuinely unavailable or insufficient and the gap is not itself a rubric-defined failure or a refusal condition. Do not use `unclear` to excuse an omitted required item or to guess the result of an unshown test.

9. When gathered evidence is sufficient and consistent, grade from the recorded evidence without rereading the whole package. If something conflicts or is incomplete, revisit only the relevant source indicated by `references/evidence-guide.md`.

10. Never allow a passing check, a preferred check, or a polished description to compensate for a failed or unclear required check. Keep live-only voice feedback separate unless a rubric check independently requires the same underlying repository convention.

11. For each check, record its exact rubric name, grade (`pass`, `fail`, or `unclear`), and one decisive source-backed fact or quote suitable for the final output schema.

## Verdict assembly

1. Confirm that every check in `rubric.md` has exactly one grade and one decisive evidence line. Revisit any grade that rests on an assumption or on a PR claim treated as independent proof.

2. Apply `rubric.md`'s verdict rule exactly: `accept` only when every required check passes; `reject` if any required check fails or is unclear. Preferred checks can inform feedback but never change the verdict. Do not invent extra gates or exceptions.

3. Populate the unchanged JSON structure required by `SKILL.md` with the PR URL or eval package ID, the named check results and decisive evidence, and the single `accept` or `reject` verdict.

4. For a `reject` verdict, identify the failed or unclear required checks using their rubric names and the evidence that held the PR. Keep any accompanying explanation focused on PR readiness rather than writing a replacement plan or proposing unverified fixes.

5. Follow `SKILL.md`'s output contract exactly, including ending the completed response with its fenced JSON block and nothing after it. Do not introduce alternative verdict logic or additional output fields.
