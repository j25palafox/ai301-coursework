# Unit 4 — Test and Submit

Path: `beat-1-sandbox/unit-4/pull-request.md`

Record of the pull request you opened against the Path Review repo, and of the evaluation
runs that produced `eval-run.txt`. This file is graded at the path above; a copy kept
anywhere else in the repository is not read.

Complete every labelled field below. Each is graded on its own; content placed under the wrong
label is not graded.

---

## Your pull request

**Pull request**

[Link to the pull request you opened. It must be the pull request's own page on the Path
Review repo, not your fork's branch page.]

https://github.com/codepath/pathreview-ai301-fa26-s3/pull/187

**Branch**

[The name of the branch the pull request comes from, exactly as it appears in your fork.
The naming shape is a type prefix, then the issue number, then a short description. **The
issue number in the branch name must be the number of the issue the pull request fixes** —
a name carrying any other number does not satisfy this field.]

fix/56-structural-chunker-empty-no-headings

Fixes issue #56 by updating the structural chunker so non-empty documents without headings are not discarded and can produce chunks normally.

## Eval iterations

Answer all four sections. Quote source text directly; paraphrase does not satisfy these
fields.

**Run history**

[The agreement score of each run you did, in order. A single run is a complete answer if
only one run occurred. **The last score in your list must match the agreement line in the
`eval-run.txt` you committed** — that file is the record of your final run.]

agreement: 16/20
agreement: 18/20

**Package analysis**

[Pick one scored package (`pkg-01` through `pkg-20` — the four `calib-` packages are never
scored). Name it by id, say what your rubric decided and what the gold label said, and
explain why your rubric read it that way.]

`pkg-16`: Gold label **`accept`**; our skill's verdict **`reject`** in the 18/20 run. The reported failed checks included `claims-match-diff` and `plan-fidelity`. The skill was concerned that the PR description promised behavior not clearly established by the code change. In our targeted examination, the explanation cited a claim that "the start-time image loading path keeps its tolerant behavior," while the new `DoLoadImages` `len(succeeded)==0` return applied regardless of the caller, with no separate branch for that start-time path. The rubric therefore interpreted the description as making a claim the diff did not adequately support. This was a false rejection relative to the gold `accept` label.

**Check rationale**

[Quote one check from the `rubric.md` you uploaded to `tools/pr-precheck/`, exactly as it reads now.
Then say why it reads that way — what you revised to get there, or what you rejected in
favour of it.]

| `plan-fidelity` | Compare **every changed file and substantive hunk** in the diff against the plan's named files or folders, intended behavior, and `## Deviations`; compare additions, omissions, and departures against the PR description and issue. | Each changed file and substantive behavior change must fall within the plan's stated scope or a specific, justified, issue-related deviation documented in the plan and disclosed in the PR description. Every essential planned change must be implemented or replaced by a justified alternative that delivers the same required behavior. Missing essential implementation work, unexplained additions or omissions, unjustified deviations, and contradictions fail this check, even when disclosed. | required |

I refined this check to distinguish between justified deviations and changes that simply happen to be disclosed. During my own PR preparation, Black reformatted an unrelated section of a test file, which made me consider how formatting-only changes should be evaluated against the plan. I wanted the check to focus on substantive changes without overlooking unrelated work. I also made it explicit that disclosing a deviation is not enough to pass: the change must still be justified, related to the issue, and consistent with the intended behavior. This prevents a PR from passing just because it explains changes that should not have been included.

**Trade-offs**

[Every check gives something up. Any one of these is a complete answer: a package whose
result it changes, a canary you re-ran with `--only`, a case you accept it will miss, or a
stated reason nothing changed elsewhere. "Nothing changed, and here is how I know" earns
the point in full when the reason follows.]

Loosening the evidence and communication checks risks accepting shorter reports that omit detail useful for debugging. We chose to allow concise command-specific proof, while keeping the requirement that checks be evidenced, not merely asserted. In targeted rechecks, `pkg-13` and `pkg-19` moved to `accept`, while `pkg-16` still received a `reject` from a different check (`claims-match-diff`). The final 18/20 run still rejected `pkg-05` and `pkg-16` against gold `accept`; we retained the stricter claim-vs-diff rule rather than weaken it simply to gain agreements.

---

Related paths: `eval-run.txt` in this directory; your skill's files in
`tools/pr-precheck/`.
