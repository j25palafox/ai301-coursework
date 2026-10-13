# Evidence guide: where evidence lives in a PR package

Use this guide with `rubric.md` and `procedure.md`. In eval mode, read only the frozen practice package; in live mode, inspect the working repository, branch, local PR artifacts, and applicable issue/repository instructions. This guide locates evidence; the procedure controls when to collect it, and the rubric controls each check's grade. Do not treat a PR description or a plan as proof that a change was made or a command was run.

## Plan fidelity (harness category: silent-drift)

**Rubric checks:** `plan-fidelity`, `claims-match-diff`.

**Where it lives — eval:** Read `plan_context_markdown` for the accepted approach, planned steps, named files or directories, in-scope/out-of-scope boundary, and any deviation notes supplied in the package. Compare these with `pr.diff` (the actual changed paths and hunks), then with `pr.title` and `pr.description` (what the contributor says the PR changes); use `issue.body_markdown` and `thread_highlights` for issue-specific expectations or maintainer direction. `pr.commits` can add context but cannot override what the full diff shows.

**Where it lives — live:** Read `plan.md`, especially implementation steps, file/scope boundaries, and `## Deviations`; inspect the entire branch diff with `git diff main...HEAD` (and the PR's Files changed view if available). Compare both against the title, Summary, Changes, and reviewer notes in `pr_draft.md`, plus the relevant issue thread. Assess committed changes actually proposed for the PR, not changes merely described as intended.

**What good looks like:** Every changed path and meaningful behavior change is covered by the plan or by a specific, disclosed deviation, and every planned step is visibly implemented or explicitly identified as incomplete. The title and description claim only changes supported by the diff; extra work without a deviation, omitted planned work without disclosure, or claims that exaggerate or understate the diff are silent drift.

## Test evidence (harness category: not-tested)

**Rubric checks:** `behavior-evidence`, `repository-checks`.

**Where it lives — eval:** Use the original failure and expected result from `issue.body_markdown` and the reproduction and test plan from `plan_context_markdown`. Inspect `pr.test_evidence` for the commands or procedures performed, observed before/after behavior, expected-after result, and results of applicable repository checks; consult `pr.diff` to see whether claimed test changes actually exist. Compare any testing statements in `pr.description` with the reported execution evidence, and use `repo_facts.raw_markdown` for explicitly required checks.

**Where it lives — live:** Compare the reproduction and test plan in `plan.md` (and the prior reproduction report, when available) with commands, output, and results recorded in `test_evidence.md`. Inspect test-related changes in `git diff main...HEAD`, the Testing section of `pr_draft.md`, and any applicable check or test instructions in the repository's documentation and contributing guide; use GitHub CI/check results if present. Distinguish an actual test run from a test file merely added to the diff.

**What good looks like:** The evidence identifies the original failing scenario, expected corrected behavior, verification commands or procedures, and actual observed results. Look for executed scripts, test output, or screenshots documenting the issue-related behavior, with before-and-after observations where available. Distinguish recorded execution from hypothetical output, test files that were only added, and unsupported statements such as "tests pass".

For repository-required checks, locate the applicable commands, their recorded execution results, and any reported failures, omissions, or inapplicability. Use these findings as evidence for `behavior-evidence` and `repository-checks`; apply the rubric to determine whether each check passes.

## Diff quality (harness category: unreviewable)

**Rubric check:** `diff-quality`.

**Where it lives — eval:** Inspect the complete `pr.diff` for all changed paths and hunks, additions and removals, test changes, and incidental modifications. Read `pr.commits` to understand how the work is grouped, using `plan_context_markdown` to separate the intended fix from unrelated edits. Do not infer an implementation from a commit message when it is absent from the diff.

**Where it lives — live:** Inspect `git diff main...HEAD` and the branch's commit list (`git log main..HEAD --oneline`), or the corresponding GitHub PR Files changed and Commits views. Compare the changes with `plan.md`; use `pr_draft.md` only to understand stated intent, not as a substitute for code review.

**What good looks like:** The changed hunks make the intended fix inspectable and keep supporting tests close to the behavior they verify, with no unrelated features, drive-by edits, debug leftovers, dead or commented-out code, or gratuitous formatting churn that obscures the change. Reviewability depends on the actual diff and whether each change has a reason, not on an invented limit for number of commits, lines, or files.

## Standards and comms (harness category: standards-wall)

**Rubric check:** `standards-comms`.

**Where it lives — eval:** Read `repo_facts.raw_markdown` for the stated PR-template requirements, contribution instructions, and AI-use policy; read `issue.body_markdown` and `thread_highlights` for explicit maintainer requests. Check `pr.title` and `pr.description` for the required issue reference, summary, change explanation, testing information, reviewer notes, and disclosures **when those are required**; use `pr.test_evidence` to cross-check how testing is described. A package that explicitly says there is no PR template or no stated AI policy does not create an imaginary template or disclosure requirement.

**Where it lives — live:** Inspect the repository's actual PR template (for example, `.github/PULL_REQUEST_TEMPLATE.md` or its configured equivalent), `docs/CONTRIBUTING.md` or the actual `CONTRIBUTING.md`, any stated AI policy, and the issue thread/maintainer comments. Compare those requirements with `pr_draft.md` and supporting `test_evidence.md` and `plan.md` deviation notes. For the PathReview PR template shown in class, check Summary, Issue, Changes, Testing, Screenshots / Demo (or a reasoned N/A), and Notes for Reviewers (including how AI was used and any deviation from the plan).

**What good looks like:** Every applicable repository or maintainer requirement is addressed with specific, non-placeholder PR content: the issue is identifiable, required template sections are meaningfully completed, testing is described accurately, and required AI-use and deviation disclosures are present. Missing mandated information, ignored explicit maintainer direction, or conflict with a stated contribution policy is a standards/comms problem; whether the description's **change claims** match the diff belongs under plan fidelity instead.
