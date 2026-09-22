# Scope: where to look, and who is looking

<!--
This file is the skill's field of view. The rubric (rubric.md) decides
whether an issue is GOOD; the scope decides which issues are candidates
at all, and whose hands the issue would land in. It applies in live mode
only: in eval mode the bundle is the whole world and this file is
ignored.

Two parts. Staff wrote the first; you write the second.
-->

## Where candidates come from

Only issues in the course's Path Review repository are candidates:

<!-- - Repo: `<ORG>/<PATH-REVIEW-REPO>` paste your section's repo from the Unit 1 Check-In page -->
- Repo: `codepath/pathreview-ai301-fa26-s3` <!-- paste your section's repo from the Unit 1 Check-In page -->

Do not search, fetch, or grade issues from any other repository, however
promising. The wider GitHub comes later in the course; for now the field
is Path Review.

**Path Review house rule.** Path Review is a classroom, and your
classmates are not strangers. Ignore the usual claim signals here: other
students' claim comments (and there may be several on one issue) do not
block an issue, and finding some on the issue you want is normal. Claim
anyway: course credit attaches to the pull request you open, not to
whether it merges, so a shared issue costs nobody anything. Everything
else in the rubric applies as written.

## Your fit profile

<!-- YOU write this part: a few sentences about you. What languages and
tools you have actually used, what you want to get better at, anything
you want to avoid. The skill uses this only to RANK the issues your
rubric accepts, never to change a verdict: fit cannot rescue an issue
your rubric rejects, and cannot sink one it accepts. -->

<!-- (Write a few sentences here.) -->

I am strongest in full-stack application work, including frontend with HTML/CSS, JavaScript, and React; backend with Express, FastAPI, PostgreSQL, and MySQL; mobile with Swift and Flutter; and applied AI work involving RAG, agents, safety/guardrails, evaluation, and debugging AI-assisted code.

For now, I prefer scoped issues where I can understand the expected behavior, trace the relevant code or documentation path, make a targeted change, and verify it with tests, docs builds, or manual checks. Good fits include application logic fixes, small frontend/backend changes, tests for existing behavior, and documentation updates that explain an existing feature or workflow.

Documentation issues are in scope when they have one clear documentation goal, concrete guidance in the issue body, and a bounded set of related pages to update. A docs issue should not be rejected only because it touches multiple documentation files, as long as all updates support the same named goal.

I am open to stretching beyond my current experience, but I would prefer small increases in difficulty rather than large leaps into infrastructure, deployment, Android-specific work, deep package-manager internals, compiler-level work, or domains far outside application development and documentation.

As a Mac user, I would also prefer issues that are reasonably workable on macOS.