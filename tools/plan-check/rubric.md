# Rubric: is this plan ready to post and build from?

<!--
THIS IS THE PART YOU WRITE. The skill in SKILL.md executes whatever
checks you define here (via your procedure.md). It ships empty on
purpose: the judgment is your work.

A filled rubric must contain:

1. At least one row in the checks table. Each row needs all four
   columns:
   - Check: a short name (used in the output JSON).
   - Evidence: exactly what to look at, and where in the package. Name
     the part (the plan's scope statement, the test plan read against
     the repro evidence's steps, the plan comment read against the
     thread highlights, the repo-facts block) or a location from your
     references/evidence-guide.md. "The plan" is not a source; "the
     plan's stated cause read against what the repro evidence shows"
     is.
   - Pass condition: a decision rule about the OUTCOME that someone
     else could apply and get your answer. Judge the thing itself (is
     this one bounded change? could a stranger start executing it?),
     never the write-up's shape (how many sections it has, how long it
     is, whether it uses headings). Structure-shaped checks are what
     make graders disagree with themselves.
   - Weight: `required` (a fail here holds the package) or `preferred`
     (never changes the verdict).

2. A verdict rule below the table: how the check grades combine into
   accept (ready) or reject (hold), including how `unclear` is
   treated. The verdict space is binary. If you write no rule for
   `unclear`, the skill treats it as fail.

Cover what actually gets bad plans posted. The lecture named the
failure families: the diagnosis ignores or contradicts the reproduced
evidence, the change is unbounded (scope creep), the plan targets the
symptom while the evidence points at the cause, a stranger could not
start executing it, the test plan proves nothing observable, the
unknowns are dressed up as certainty, and the comment ignores what the
thread or the repo's stated conventions ask. A rubric that ignores a
family will fail eval packages designed around that family.
-->

## Checks

| Check | Evidence | Pass condition | Weight |
|---|---|---|---|
| diagnosis | The contributor's claim comment, reproduction comment, and candidate plan for the same issue. | Pass if the plan identifies a cause for the reproduced behavior that is consistent with the contributor's prior claim and reproduction evidence. Fail if the diagnosis addresses a different issue or contradicts the previously established behavior. | Required |
| scope | The contributor's reproduction evidence and candidate plan. | Pass if the plan identifies the files or components it intends to change and explains how those changes address the diagnosis and previously reproduced behavior. The planned implementation may involve files or components not named in the reproduction evidence, but it must remain directed at resolving the same established issue and behavior. Fail if the proposed changes address a different behavior, include unrelated work, or are not justified by the diagnosis and reproduction evidence. | Required |
| test | The contributor's reproduction evidence and candidate plan. | Pass if the plan includes a test or verification step that exercises the previously reproduced behavior and states the expected corrected result. Existing reproduction tests or reproduction steps may be reused or updated when appropriate. Fail if the planned test or verification does not cover the reproduced behavior or would not demonstrate that the fix works. | Required |
| comms | Repo facts `contribution policy` line; `CONTRIBUTING.md`; `.github/` contributor docs; `AI_POLICY.md`; `AI_USAGE_POLICY.md`; `AGENTS.md`; issue/PR templates; issue and thread context; candidate plan comment. | Pass if the public plan comment is consistent with the candidate plan and follows all applicable repository and thread communication requirements. If AI-assisted work is permitted only with conditions such as disclosure, personal understanding, testing, or human review, the comment must satisfy any condition that applies to the public communication. Fail if the comment contradicts the plan or thread, omits an explicit required communication element, or violates an applicable repository policy. | required |

## Verdict rule

<!-- State how the grades above combine into accept or reject, and how
unclear is treated. Example shape (write your own): "accept if every
required check passes; preferred checks never change the verdict;
unclear counts as fail." -->

The plan is ready only when every required check passes. Any failed required check makes the plan not ready. Any unclear required check requires manual inspection before a final verdict.