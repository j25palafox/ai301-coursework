# Procedure: how this skill grades a plan package

<!--
THIS IS THE PART YOU WRITE, and it is a new kind of part. Weeks 1 and
2, SKILL.md carried a numbered workflow and you only wrote judgment
files. This week the workflow is gone from the frame: SKILL.md says
"execute procedure.md", and these are the operating steps you author.
The machinery is in your hands now.

Your operator swap is the design brief. When your executor stalled
because your rubric said WHAT to decide but not HOW to find the
evidence, that was a procedure gap. This file is where those gaps get
closed: a complete procedure lets someone who has never seen a plan
package before (a groupmate, or the skill itself) grade one exactly the
way you would.

Under each stage heading below, write the concrete steps for that
stage. The one-line note under each heading says what a complete
procedure must decide there. Write steps, not intentions: "read the
repro evidence before the plan, and note what behavior it pins down"
is a step; "understand the context" is a wish.
-->

## Read order

<!-- What gets read, in what order, before any check is graded, and
what to note down from each part while reading. A complete procedure
decides the order (issue first? repro evidence first?) and says why
the order matters for the checks that come later. -->

1) Read `references/evidence-guide.md` first to establish where each evidence family is located. Do not gather evidence or grade checks yet.

2) Read the issue and thread context to establish the reported behavior, expected outcome, and any maintainer decisions that define what the change should or should not accomplish.

3) Read the contributor's reproduction evidence next. Identify the behavior that was demonstrated and treat it as the behavioral baseline the plan is intended to address.

4) Read the repository evidence identified in `references/evidence-guide.md` to establish how the relevant code currently works, where the proposed change would occur, and any implementation or testing constraints the plan must account for.

5) Read the full proposed plan. Identify its diagnosis, proposed implementation approach, scope, validation strategy, and the claims it makes about the issue and repository.

6) Read the proposed plan comment last. Treat it as the public summary of the plan, not as a replacement for the full plan.

7) Do not begin grading individual rubric checks until all required inputs and available evidence have been read in this order.


## Evidence gathering

<!-- For each evidence family your rubric's checks name, the concrete
gathering move: which part of the package (or, live, which page or
thread location per your evidence guide) to pull the fact from, and
what to record. A complete procedure leaves no check whose evidence an
executor would have to hunt for. -->

1. Use `references/evidence-guide.md` to locate the source or sources for each evidence family. The evidence guide determines where to look; the steps below determine what to gather from those sources.

2. For diagnosis and grounding, gather:
   - the behavior reported in the issue,
   - the behavior demonstrated by the contributor's reproduction,
   - the cause or mechanism the plan claims is responsible, and
   - repository evidence that supports, contradicts, or limits that claimed cause.

3. For scope, gather:
   - the outcome requested by the issue,
   - any boundaries or constraints established by maintainers,
   - the behavior or components the plan proposes changing, and
   - enough repository evidence to determine whether those proposed changes remain within the problem established by the issue and reproduction.

4. For executability, gather:
   - the concrete implementation steps proposed by the plan,
   - the files, components, functions, or behaviors those steps depend on,
   - repository evidence confirming how those parts currently work, and
   - any dependencies, sequencing requirements, or implementation constraints necessary to carry out the proposed change.

5. For the test plan, gather:
   - the reproduced failing behavior that establishes the baseline,
   - the tests or verification steps the plan proposes,
   - the behavior each test is intended to exercise, and
   - the observable result that would demonstrate the planned change works and does not regress the reproduced case.

6. For honesty, gather:
   - factual and causal claims made by the plan,
   - the level of certainty with which those claims are stated, and
   - the available issue, reproduction, and repository evidence supporting or limiting those claims.
   Record unsupported assumptions or unresolved uncertainty rather than silently resolving them.

7. For communications, gather:
   - the full plan,
   - the plan comment,
   - relevant issue-thread context, and
   - any applicable repository or communication conventions identified by the evidence guide.
   Compare the plan comment with the full plan to determine whether it accurately communicates the proposed work without requiring the comment to reproduce every implementation detail.

8. When related evidence appears in multiple sources, preserve the chronology of the discussion. Later explicit maintainer corrections or decisions take precedence over earlier statements they supersede. Do not introduce claim-status, competing-work, or other requirements unless a rubric check explicitly requires them.

9. Record evidence that supports, contradicts, or fails to establish each required condition. Do not assign pass, fail, or unclear while gathering evidence; grading occurs during Check execution.

## Check execution

<!-- How one check runs against gathered evidence: in what order the
checks execute, what an executor does when evidence for a check is
genuinely absent, and when a check may be graded without re-reading
the whole package. A complete procedure makes two executors grade the
same package the same way. -->

1) Execute the rubric checks in the order they appear in `rubric.md`. Grade every required check independently; do not stop after an earlier check fails or is unclear.

2) For each check, use its stated pass condition and the evidence already gathered for that check during Evidence gathering.

3) Apply the rubric to the submitted plan as written. Do not fill in omitted steps, reinterpret incorrect implementation targets, or give credit for changes or tests that the plan does not actually propose.

4) When a check requires agreement with the issue or reproduction, compare the plan's proposed cause, change, scope, or test directly against the relevant source evidence.

5) When a check depends on repository grounding, distinguish repository-supported facts from assumptions stated only by the plan. A plan assertion is not repository evidence unless the gathered repository evidence supports it.

6) When a check contains multiple required parts, confirm that every required part is supported before assigning pass.

7) Assign fail when the available evidence contradicts a required condition, demonstrates a rubric-defined failure condition, or the submitted plan omits something that the check explicitly requires the plan to provide.

8) Assign unclear only when evidence needed to judge the condition is genuinely unavailable or insufficient and the absence is not itself a rubric-defined failure. Do not use unclear merely because the plan omitted a required detail.

9) If the gathered evidence for a check is sufficient and internally consistent, grade the check from that evidence without re-reading the full package. Re-open only the specific source identified by `references/evidence-guide.md` when the gathered evidence is incomplete, conflicting, or insufficient to distinguish pass, fail, and unclear.

10) Do not allow a strong result on one check to compensate for a failure or uncertainty on another required check.

11) For each check, record the grade and the single decisive fact or quote required by the output schema.


## Verdict assembly

<!-- How the per-check grades become the final accept or reject:
apply your rubric's verdict rule, state how unclear grades enter it,
and say what gets quoted in the output for the deciding check. A
complete procedure produces the same verdict from the same grades,
every time. -->

1) Review the completed check results and confirm that every required rubric check has exactly one result: pass, fail, or unclear.

2) Apply the verdict rule from rubric.md exactly as written. Do not create additional acceptance rules or exceptions in the procedure.

3) Populate the output schema required by SKILL.md using the completed check grades and decisive evidence.

4) If the verdict is not an acceptance, identify which failed or unclear checks prevent acceptance using the rubric's own terminology.

5) Keep the final assessment focused on whether the submitted plan is ready according to the rubric. Do not turn the verdict into a replacement implementation plan.

6) Emit no additional verdict logic or commentary beyond what the output contract requires.
