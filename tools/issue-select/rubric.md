# Rubric: is this a good first issue?

<!--
THIS IS THE PART YOU WRITE. The skill in SKILL.md executes whatever checks
you define here. It ships empty on purpose: the judgment is your work.

A filled rubric must contain:

1. At least one row in the checks table. Each row needs all four columns:
   - Check: a short name (used in the output JSON).
   - Evidence: exactly what to look at, and where. Name the source
     (repo-facts block, issue body, comment thread, or the locations in
     references/evidence-guide.md). "The repo" is not a source; "the last
     5 default-branch commit dates" is.
   - Pass condition: a condition someone else could apply and get your
     answer. Prefer thresholds with numbers ("a maintainer commented
     within 30 days") over adjectives ("maintainer is responsive").
   - Weight: `required` (a fail here rejects the issue) or `preferred`
     (never changes the verdict; a nice-to-have that helps rank the
     issues you accept).

2. A verdict rule below the table: how the check grades combine into
   accept or reject, including how `unclear` is treated. The verdict
   space is binary. If you write no rule for `unclear`, the skill treats
   it as fail.

Cover what actually kills first contributions. The lecture named four
families: the maintainer is alive, the repo is in use, the scope fits a
newcomer, and nobody else is already on it. A rubric that ignores a family
will fail eval issues designed around that family.
-->

## Checks

| Check | Evidence | Pass condition | Weight |
|---|---|---|---|
| AI-assisted workflow permitted  | Repo facts `contribution policy` line; `CONTRIBUTING.md`; `.github/` contributor docs; `AI_POLICY.md`; `AI_USAGE_POLICY.md`; `AGENTS.md`; issue/PR templates | Pass if the repo is silent about AI use or allows AI-assisted work with followable conditions such as disclosure, personal understanding, testing, or human review. Fail if the repo explicitly bans AI-generated or AI-assisted contributions. | required |
| Maintainer activity | Recent default-branch commits; commit authors; maintainer first-response sample; Owner/Member/Collaborator activity in the issue thread | Pass if there is at least one clear sign of human maintainer activity within the previous 60 days, measured against the repo-facts capture date in eval mode or today in live mode. Valid signs include a human-authored default-branch commit, an Owner/Member/Collaborator issue response, or a maintainer first-response sample within that window. Bot-only activity does not count unless the bot is clearly merging a human-reviewed PR. | required |
| Repo activity | Archived flag; last push to any branch; latest release; recent default-branch activity | Pass if the repo is not archived and has at least one repo activity signal within the previous 30 days, measured against the repo-facts capture date in eval mode or today in live mode. Valid signs include a push, default-branch commit, or release. Fail if the repo is archived or has no activity within the threshold. | required |
| Newcomer-fit and bounded scope | Issue body; issue thread; maintainer comments; labels; linked or mentioned prior attempts | Pass if the issue has one coherent primary outcome, a reasonably clear success condition, and appears bounded enough for a first contribution. Use the following as strong fail signals rather than absolute rules: the issue explicitly acts as a tracking/umbrella/meta issue; it contains several independently completable required deliverables; it spans multiple substantial product surfaces that require coordination; it leaves major product or design decisions unresolved; it is primarily investigation/discussion/support rather than an implementable change; or it has multiple abandoned prior attempts suggesting hidden complexity. Do not fail based on file count alone. Related changes across several files may still be bounded when they support one contained outcome. Treat an issue as likely umbrella scope when it groups multiple independent outcomes, tracks sub-issues, or could be meaningfully split into separate contributions without breaking the intended result. | required |
| Claim status | Assignees; linked PRs; claim comments; maintainer replies to claims; label history/freshness; issue open date versus capture date | Pass if the issue has no assignee, no open linked PR, and no credible unresolved claim from the previous 14 days. A claim is credible only when a maintainer acknowledges or approves it. Unacknowledged comments such as “I’ll take this,” “working on this,” or “can I work on this?” do not count as active claims. Closed or abandoned PRs count as history/risk, not active claims. When sidebar data and comments disagree, trust the thread. | required |


## Verdict rule

<!-- State how the grades above combine into accept or reject, and how
unclear is treated. Example shape (write your own): "accept if every
required check passes; preferred checks never change the verdict, they
rank accepted issues; unclear counts as fail." -->

Explicit AI-assisted contribution bans are immediate rejects. Otherwise, all required checks must be pass to accept; any fail or unclear rejects.
