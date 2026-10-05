# Evidence guide: where evidence lives in a plan package

<!--
THIS IS THE PART YOU WRITE (second week running: the judgment files
stay in your hands). The skill uses this guide as its map: for every
kind of evidence a rubric check names, this file says WHERE to find it
in a plan package and WHAT GOOD LOOKS LIKE when you do.

Under each family heading below, write:

- Where it lives: the exact places to look. In an eval bundle (which
  section of the package: the issue context, the repro-evidence block,
  the candidate plan's scope statement or test plan, the plan comment,
  the repo-facts block). In live mode (where on GitHub or in the
  draft: the issue thread, the student's posted repro comment, the
  repo's docs, the draft plan and comment).
- What good looks like: one or two sentences someone else could apply.
  Prefer observable conditions ("the stated cause cites behavior the
  repro evidence actually shows") over adjectives ("diagnosis is
  solid").

A rubric check whose evidence this guide cannot locate is a check
nobody else can execute, and this week that cuts twice: your
procedure.md tells the skill WHEN to gather each family, and this
guide tells it WHERE. Write the map you wish your executor had.
-->

## Diagnosis and grounding

<!-- Where the plan states its cause, and where the repro evidence
pins down the behavior that cause must explain. What it means for a
diagnosis to follow from the evidence rather than contradict or
ignore it. -->

**Where it lives**

- Eval mode: read the proposed cause in `plan_markdown` and compare it with the behavior demonstrated in `repro_evidence_markdown`.
- Live mode: read the diagnosis in `plan.md` and compare it with the contributor's posted reproduction evidence.

**What good looks like**

The stated cause explains the behavior the reproduction actually shows. It does not contradict, ignore, or invent behavior beyond that evidence.


## Scope

<!-- Where the plan bounds itself: the in-scope statement, the
not-in-scope line, the files or areas named. What one bounded change
looks like next to a drive-by rewrite. -->

**Where it lives**

- Eval mode: read the in-scope and out-of-scope statements and the files or areas named in `plan_markdown`.
- Live mode: read the scope, exclusions, and files or areas named in `plan.md`.

**What good looks like**

The plan describes one bounded change aimed at the reproduced problem. The named work stays within that change rather than expanding into unrelated cleanup, rewrites, or drive-by changes.


## Executability

<!-- Where the plan says what will actually be done: files or areas,
approach, order of work. What it means for a stranger to be able to
start executing without asking the author anything. -->

**Where it lives**

- Eval mode: read the files or areas, implementation approach, and order of work in `plan_markdown`.
- Live mode: read those same parts of `plan.md`.

**What good looks like**

The plan identifies where the work will happen, what will be changed, and the order or approach clearly enough that another contributor could begin implementing it without asking the author to fill in missing steps.


## Test plan

<!-- Where the plan says how success will be observed, and how that
maps onto the repro evidence's steps and artifacts. What a decisive
test plan names that a vague one does not. -->

**Where it lives**

- Eval mode: read the test plan in `plan_markdown` against the steps, controls, expected behavior, and observed artifacts in `repro_evidence_markdown`, plus any testing requirements stated in the issue or `thread_highlights`.
- Live mode: read the test plan in `plan.md` against the contributor's reproduction comment, the issue thread, and relevant repository test conventions.

**What good looks like**

The test plan exercises the behavior demonstrated by the reproduction and states an observable corrected result. It preserves useful controls or regression coverage where relevant so that passing the test would demonstrate the reported problem was fixed rather than merely exercising nearby code.


## Honesty

<!-- Where claims meet uncertainty: risks, unknowns, and deviations.
How to tell stated unknowns from false confidence, and where an
honest mid-build deviation gets recorded. -->

**Where it lives**

- Eval mode: read risks, unknowns, assumptions, and qualifications in `plan_markdown`; compare them with unresolved questions or conflicting evidence in the issue, `thread_highlights`, and `repro_evidence_markdown`.
- Live mode: read risks and unknowns in `plan.md` before the build. After implementation, also read `## Deviations` for differences between the planned and actual work and why they occurred.

**What good looks like**

The plan distinguishes established facts from unresolved questions and does not claim certainty that the available evidence does not support. Material risks or unknowns are stated when they could affect the proposed change, and post-build deviations truthfully describe meaningful differences from the original plan.


## Comms

<!-- Where the words meet the thread and the repo: the plan comment
read against the issue's maintainer signals (thread highlights, or
the live thread) and against the repo-facts block's stated templates,
contributing asks, and contribution policy (including AI-use
disclosure requirements). What thread-aware looks like next to
boilerplate. -->

**Where it lives**

- Eval mode: read `plan_comment_markdown` against relevant `thread_highlights` and the contribution, template, and AI-use requirements in `repo_facts.raw_markdown`. Use `plan_markdown` when needed to confirm that the comment accurately represents the full plan.

- Live mode: read the draft `comment.md` against the GitHub issue thread and the repository's contribution documentation, issue or PR templates, and any AI-use policy. Use `plan.md` when needed to confirm that the comment accurately summarizes the proposed work.

**What good looks like**

The comment reflects relevant maintainer direction, follows applicable repository communication and disclosure requirements, and accurately represents the plan. It does not ignore known constraints, contradict the plan, or read like generic boilerplate that could have been posted without reading the issue.