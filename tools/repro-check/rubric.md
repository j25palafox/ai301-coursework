# Rubric: is this reproduction package ready to post?

<!--
THIS IS THE PART YOU WRITE. The skill in SKILL.md executes whatever
checks you define here. It ships empty on purpose: the judgment is your
work.

A filled rubric must contain:

1. At least one row in the checks table. Each row needs all four
   columns:
   - Check: a short name (used in the output JSON).
   - Evidence: exactly what to look at, and where in the package. Name
     the part (the claim comment, the repro report's environment
     record, the artifacts read against the issue's description, the
     repo-facts block) or a location from your
     references/evidence-guide.md. "The report" is not a source; "the
     output excerpt read against the error the issue describes" is.
   - Pass condition: a decision rule about the OUTCOME that someone
     else could apply and get your answer. Judge the thing itself (does
     the artifact show the issue's behavior?), never the write-up's
     shape (how many steps it has, how long it is, whether it uses a
     template's headings). Structure-shaped checks are what make
     graders disagree with themselves.
   - Weight: `required` (a fail here holds the package) or `preferred`
     (never changes the verdict).

2. A verdict rule below the table: how the check grades combine into
   accept (ready) or reject (hold), including how `unclear` is
   treated. The verdict space is binary. If you write no rule for
   `unclear`, the skill treats it as fail.

Cover what actually gets bad packages posted. The lecture named the
proof families: the environment is recorded, the steps are complete
and followable, the behavior shown matches the issue (not an adjacent
one), the outcome is stated honestly (an evidenced cannot-reproduce is
a pass, a confident wrong-target is not), and the words respect the
repo's conventions. A rubric that ignores a family will fail eval
packages designed around that family.
-->

## Checks

| Check | Evidence | Pass condition | Weight |
|---|---|---|---|
| env-recorded | The repro report's environment record. | Pass if the report identifies the environment in which the reproduction was attempted, including the operating system and the tested tool/build and version. The recorded information must be specific enough to identify what was actually tested. | required |
| steps-complete | The repro report's reproduction steps and recorded commands. | Pass if the steps are complete and followable enough for another person to rerun the same reproduction without guessing a necessary setup, build, or execution step. The steps must lead from the required starting state through execution to the recorded result. | required |
| behavior-shown | The reproduction artifact or recorded output, read against the issue's description of the reported behavior and the repro report's expected and actual behavior. | Pass if the reproduction exercises the same behavior or scenario described by the issue and records direct evidence of what occurred, whether the reported problem reproduces or does not reproduce. Fail if the evidence exercises a different or merely related behavior. Grade unclear if there is not enough evidence to determine whether the issue's described behavior was actually tested. | required |
| outcome-honest | The reproduction outcome stated in the repro report and claim comment, read against the reproduction evidence. | Pass if the stated outcome accurately reflects what the reproduction evidence establishes. A supported reproduction and a supported cannot-reproduce outcome may both pass. Fail if the package claims an outcome that the evidence does not support. Grade unclear if the evidence does not establish enough to determine whether the stated outcome is accurate. | required |
| comms-conform | The proposed claim comment, read against the repository facts and applicable contribution/reporting conventions. | Pass if the proposed comment follows the repository's applicable communication and contribution requirements. Repository silence on a convention is not itself a failure. | required |

## Verdict rule

<!-- State how the grades above combine into accept or reject, and how
unclear is treated. Example shape (write your own): "accept if every
required check passes; preferred checks never change the verdict;
unclear counts as fail." -->

Ready only if every required check is pass. Any fail or unclear on a required check means the package is not ready to post.
