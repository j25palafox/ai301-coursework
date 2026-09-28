# Evidence guide: where proof lives in a reproduction package

<!--
THIS IS THE PART YOU WRITE (new this week: Unit 1 handed you this file
finished; the scaffolding fades). The skill uses this guide as its map:
for every kind of proof a rubric check names, this file says WHERE to
find it in a package and WHAT GOOD LOOKS LIKE when you do.

Under each family heading below, write:

- Where it lives: the exact places to look. In an eval bundle (which
  section of the package: the issue context, the repo-facts block, the
  claim comment, the repro report and its parts). In live mode (where
  on GitHub or in the draft: the issue thread, the repo's docs, the
  student's draft comment).
- What good looks like: one or two sentences someone else could apply.
  Prefer observable conditions ("the versions named match what the
  issue targets, or the difference is called out") over adjectives
  ("environment is thorough").

A rubric check whose evidence this guide cannot locate is a check
nobody else can execute; the rubric swap showed you what that feels
like. Write the map you wish your grader had.
-->

## Environment

<!-- Where the environment record lives, and what a sufficient one
looks like against the issue's stated target. -->

**Where it lives**

Eval mode: the Environment line in the candidate repro report; compare
it with the issue's Environment line in the issue context and any
relevant version information in the repo-facts block.

Live mode: the Environment line in the student's repro-report draft;
compare it with the issue's stated environment/version and the repo's
relevant release or documentation when needed.

**What good looks like**

It records the version and OS or other environment details the repo
asks for, and matches the issue's target environment or explicitly
calls out any meaningful difference.


## Steps

<!-- Where the reproduction steps live, and what makes them followable
by a stranger, starting state to trigger. -->

**Where it lives**

Eval mode: the reproduction steps in the candidate repro report;
compare them with the setup, commands, inputs, or trigger described in
the issue context and any relevant setup information in the repo-facts
block.

Live mode: the reproduction steps in the student's repro-report draft;
compare them with the issue thread and the repo's setup or usage
documentation when those establish a required starting state or
command.

**What good looks like**

The steps take a stranger from a stated starting state through the
actions or commands that trigger the behavior, without requiring them
to guess a missing setup step, input, or action needed for the
reproduction.


## Behavior shown

<!-- Where the artifacts live (output excerpts, logs, screenshots),
and what it means for an artifact to show the issue's behavior rather
than an adjacent one. -->

**Where it lives**

Eval mode: the artifacts in the candidate repro report, such as output
excerpts, logs, error messages, or screenshots; compare what they show
with the behavior described in the issue context.

Live mode: the artifacts included or quoted in the student's
repro-report draft; compare them directly with the behavior described
in the issue thread.

**What good looks like**

The artifact shows the same behavior the issue describes, not merely a
related error or nearby behavior. The relevant part of the artifact is
specific enough that another reader can see what happened and connect
it to the issue.


## Honesty

<!-- Where claims and their backing meet: how to tell a report that
says exactly what happened (including an honest cannot-reproduce) from
one that claims more than its evidence shows. -->

**Where it lives**

Eval mode: the outcome stated in the candidate repro report and any
reproduction claim in the candidate claim comment; compare those words
with the report's steps and artifacts.

Live mode: the outcome and reproduction claims in the student's draft
comments; compare them with the steps and artifacts actually included
or quoted in the drafts.

**What good looks like**

The stated outcome does not claim more than the recorded evidence
shows. A reproduced result is backed by an artifact showing the
reported behavior, while a cannot-reproduce result says so directly
and records what was actually attempted and observed.


## Comms

<!-- Where the words meet the repo: the claim comment against the
issue, the comments against the repo's stated templates and
contribution policy (including AI-use disclosure requirements), and
what specific-and-honest looks like next to boilerplate. -->

**Where it lives**

Eval mode: the candidate claim comment and candidate repro report;
compare them with the issue context and any contribution, template, or
AI-use requirements recorded in the repo-facts block.

Live mode: the student's draft comments; compare them with the issue
thread, the repo's issue or bug-report templates, CONTRIBUTING or other
contribution-policy docs, and any stated AI-assisted contribution
policy.

**What good looks like**

The comments are specific about what was attempted and observed,
follow the repo's applicable posting and disclosure requirements, and
do not present unsupported claims or generic boilerplate as evidence.
Any required AI-use disclosure is present when the repo's policy
requires one.
