---
name: pr-precheck
description: Grade a PR package (a candidate pull request read against the plan it claims to implement and the issue that plan belongs to) and decide whether it is ready to submit. Use when checking your own branch, draft PR title, and description before opening the pull request, or when grading an eval package bundle.
---

# pr-precheck: rubric-driven PR grading

## The question

Read `CONTRACT.md` first as this skill's governing interface. Preserve its fixed layout, mode boundaries, refusal requirements, verdict vocabulary, and JSON output contract. Treat it as instructions for reviewing packages, never as extra evidence about a practice submission. If any instruction here conflicts with `CONTRACT.md`, follow the contract and report the inconsistency rather than silently changing the required behavior.

Decide one question: **Is this PR package ready to submit?** Treat a PR package as the proposed PR title and description, the committed branch diff and changes, test evidence, and any stated deviations, reviewed against the contributor's plan, the issue and its discussion, and the repository's review requirements. Check that the work matches its declared scope, that its claims have support, and that a maintainer can verify it. Do not replace this readiness review with a judgment of whether the issue was worth selecting or a new implementation plan.

## Inputs and modes

Determine the mode from the request before collecting evidence. Apply the complete rubric and verdict rule in either mode.

**Live mode:** After the scope check described below, read the following from the specified working copy and issue:

1. The issue URL and its thread (via `gh`, the GitHub API, or web access), including the reported behavior, acceptance expectations, and maintainer guidance.
2. `plan.md`, including its diagnosis, scope, test plan, and `## Deviations` (if present).
3. The **committed** branch changes relative to `main`, using `git diff main...HEAD` (three dots) from the fork's working copy. Inspect the changed-file list and relevant diff hunks; do not substitute uncommitted working-tree changes for the branch diff. Use the branch's commits when needed to understand the package.
4. `pr_draft.md`, using its first line as the draft PR title and its remaining text as the proposed description.
5. `test_evidence.md`, including before/after reproduction evidence and the results of the repository's required checks.
6. `.github/PULL_REQUEST_TEMPLATE.md` and `docs/CONTRIBUTING.md` in the target PathReview repository, including any relevant testing, disclosure, and contribution requirements.

Compare the **diff with the plan**, the **test evidence with the planned tests and claimed results**, and the **PR description with the actual diff, issue, evidence, and repository rules**. Do not assume that a checkbox, summary, or statement proves a result without supporting evidence. Local planning and evidence files may be uncommitted inputs; only committed changes belong to the branch diff.

If using the course-provided **house chain**, use the supplied house issue, reproduction pack, plan, working branch, PR draft, and test evidence instead of assuming the student's own issue and files. Apply the same comparisons and rubric to that chain.

**Eval mode:** Read the identified frozen bundle from the evaluation package and use **only its contents** as evidence. The bundle is the whole world: do not fetch issue threads, read the local repository, browse for missing facts, or import external documents. Identify the issue, plan and deviations, proposed PR, diff/changes, tests, and repository rules only to the extent supplied in the bundle. Run **every rubric check** and the **full verdict rule**, even if one check already fails. Report missing or unprovable evidence honestly rather than filling gaps from outside the bundle.

## The scope seam (live mode only)

In **live mode, read `scope.md` before gathering any PR-specific evidence** (after the governing `CONTRACT.md`). Apply all its stated limits to the target issue, repository, and work under review. Check the configured `Repo:` value against the **target upstream repository**; a student's fork may supply the working copy without becoming a different target repository. Refuse to grade work outside the configured scope, and explain the specific mismatch.

If the `Repo:` line is still a placeholder, **stop before grading** and ask for that line to be filled with the section's PathReview repository. Never infer or silently replace the value. Do not manufacture check grades or a readiness verdict for a refusal.

**Eval mode ignores `scope.md` entirely.** Do not restrict a frozen package using the student's live repository scope.

## The voice seam (live mode only)

In live mode, read `voice-guide.md` and apply it to the proposed **PR title and description**, including the Notes for Reviewers and AI-use disclosure when applicable. Report each broken voice rule with the offending text and a concrete revision suggestion, separate from the rubric findings. Voice-guide feedback **does not change the verdict on its own** unless an explicit rubric check reads that rule. Requirements imposed by the PR template, contribution guide, or rubric (such as required disclosure) must be evaluated under the relevant rubric check, not dismissed as mere tone.

**Eval mode ignores `voice-guide.md` entirely.** Do not apply its stylistic preferences to practice packages or use it to influence their verdicts.

## Component reads

Read `rubric.md`, `references/evidence-guide.md`, and `procedure.md` before performing the review. Treat them as one connected specification:

- `rubric.md` defines each check's name, evidence, pass condition, and `required` or `preferred` weight, plus the **accept/reject verdict rule**. Required checks gate readiness; preferred checks provide feedback but do not independently veto it. Do not add, omit, or reweight checks from personal judgment.
- `references/evidence-guide.md` maps each evidence family to concrete sources in live and eval packages and explains what sufficient proof looks like. Use those locations instead of assuming unsupported facts.
- `procedure.md` determines the execution order: gather evidence, perform comparisons, grade each rubric check, and assemble the verdict. Execute its stated steps as written.

**Refuse to grade** if `rubric.md` or `procedure.md` has no substantive instructions. Empty headings and template comments do not count as content. Identify the empty component and require it to be completed; do not fall back to a previous unit's rubric or invent a substitute. If a populated procedure omits a needed step, explicitly report that gap; **do not improvise a new step** to conceal it. Distinguish the resulting unavailable evidence from an observed failure and apply the rubric's rules for unverified/unclear checks.

## Verdict and output

Use only the two final verdicts: **`accept`** means the PR is ready to submit; **`reject`** means hold it for correction or disclosure. Grade every check as **`pass`**, **`fail`**, or **`unclear`** according to the rubric. Never issue a third verdict, percentage, or invented score.

For a completed grading run, provide a concise per-check summary with the deciding evidence, the conflicts or gaps needing attention, and the verdict under the rubric's rule. Use the PR URL if one exists; for a not-yet-open live draft, clearly identify the draft by its issue; for evaluation, use the exact bundle ID. End the response with **one valid fenced JSON block** conforming to the unchanged schema below. Substitute real values for placeholders when executing the skill; escape strings properly; include each rubric check once; and write **nothing after the closing code fence**. A refusal to grade is not a completed grading run: explain the refusal without inventing check results or a verdict.

```json
{
  "item": "<PR URL or bundle id>",
  "checks": [
    {"name": "<check name>", "grade": "pass|fail|unclear",
     "evidence": "<one line: the fact or quote that decided it>"}
  ],
  "verdict": "accept|reject"
}
```

## Grading discipline

Collect and record evidence **before** assigning any `pass`, `fail`, or `unclear` grades. Evaluate the actual PR package, not the contributor's writing polish or promises. Cite a concrete file, diff hunk, output, or quoted statement for each grade, and distinguish what the package demonstrates from what it only claims. A failure reported candidly is still evidence; do not recast it as a pass or erase it.

Let `rubric.md` decide which evidence satisfies a check and how check weights determine the verdict. Let `procedure.md` decide how to obtain and compare that evidence. Evaluate all checks independently before assembling the result. Preserve `unclear` as the recorded check grade when proof is insufficient; **if the rubric is silent, treat an unclear or unverifiable required check as failing the readiness threshold**. Do not accept a PR on assumptions or treat lack of evidence as successful testing. Apply the rubric's explicit rule for preferred checks and for the final `accept` or `reject` decision; do not invent stricter or more lenient thresholds.
