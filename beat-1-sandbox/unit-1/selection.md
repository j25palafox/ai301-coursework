# Unit 1 — Issue Selection

Path: `beat-1-sandbox/unit-1/selection.md`

Record of the issue carried into Unit 2, and of the evaluation runs that produced
`eval-run.txt`. This file is graded at the path above; a copy kept anywhere else in
the repository is not read.

Complete every labelled field below. Each is graded on its own; content placed under the
wrong label is not graded.

---

## Selected issue

**Issue link**

https://github.com/codepath/pathreview-ai301-fa26-s3/issues/56


**Verdict output**

**#56 (Structural chunker) — ACCEPT** ✓
- AI-assisted work is silent/allowed (no explicit ban in contributing docs)
- Maintainer committed 2026-09-16 (within 60 days)
- Not archived; activity on 2026-09-16 (within 30 days)
- Bounded scope with explicit test case and clear success condition
- No assignee, no comments, no linked PRs
- **Fit: BEST MATCH** — explicit test failure provides a clear verification path, low difficulty with good learning value


```
[
  {
    "item": "https://github.com/codepath/pathreview-ai301-fa26-s3/issues/56",
    "checks": [
      {"name": "AI-assisted workflow permitted", "grade": "pass", "evidence": "CONTRIBUTING.md and README silent on AI restrictions; course is AI-focused (AI301)"},
      {"name": "Maintainer activity", "grade": "pass", "evidence": "Andrew Burke commits on 2026-09-16 (6 days ago, within 60-day window)"},
      {"name": "Repo activity", "grade": "pass", "evidence": "Not archived; push on 2026-09-16 (within 30-day window)"},
      {"name": "Newcomer-fit and bounded scope", "grade": "pass", "evidence": "Clear bounded task: fix chunker to handle documents without headings, with explicit failing test `test_document_with_no_headings`"},
      {"name": "Claim status", "grade": "pass", "evidence": "No assignees, no comments, no linked PRs; issue open since 2026-09-10"}
    ],
    "verdict": "accept"
  },
]

```

---

## Eval iterations

Quote source text directly in each field below. Paraphrase does not satisfy them.

**Run history**

agreement: 18/20

**Issue analysis**

issue-01  accept  reject   NO     failed: Newcomer-fit and bounded scope

**Check rationale**

```
| Newcomer-fit and bounded scope | Issue body; issue thread; maintainer comments; labels; linked or mentioned prior attempts | Pass if the issue asks for one bounded outcome with a clear success condition. Exact files, functions, tests, or implementation steps are not required. Multiple related files may be changed when they all support the same contained goal, and suspected causes, alternative approaches, or optional suggestions do not count as separate scope unless they are required deliverables. Fail if the issue is an umbrella/tracking issue, unresolved design debate, pure support request, highly open-ended core-internals change, requires coordinated implementation across multiple substantial product surfaces, leaves important product/specification decisions unresolved, or is a very old issue with repeated abandoned attempts that indicate substantial unresolved difficulty. | Required |
```

I wrote this check to favor issues that are bounded enough for an early-career engineer to understand, investigate, and verify without requiring broad system-wide changes. I wanted to allow work that may touch multiple related files when they all contribute to one contained outcome, while filtering out issues that span several distinct product areas, depend on unresolved design decisions, or are too open-ended to have a clear definition of done. I also included the age and abandoned-attempt criteria to avoid issues whose history suggests hidden complexity or unresolved difficulty.



**Trade-offs**

I repeatedly revised this check because `issue-01` was being rejected when I expected it to be accepted. After one revision, I re-ran `issue-01` with `--only` as a canary and it passed, but it was rejected again in the final full eval. This showed me that making the check flexible enough to allow bounded work across multiple related files also left some room for interpretation. I accepted that trade-off rather than making the rule so specific to `issue-01` that it would overfit one example.


---

## Selection rationale

Graded on whether all three are answered, in your own words. Not on how good the
reasoning is, and not on length — a short honest answer to each earns the full marks.
This is also the basis for the claim comment you write in Unit 2.

**Selection rationale**

This issue fits my interests because I enjoy debugging existing application logic, and its scope seems realistic for the time available in the course. The verdict correctly identified that the issue is bounded, has a clear outcome, and does not appear to already be claimed. Beyond the rubric, I also considered my familiarity with ingestion and chunking, which made me feel that the issue was manageable within the available time. I do not expect claiming it to be especially difficult because it is currently unassigned, although there is still a chance another contributor could claim it first.

---

Related paths: `eval-run.txt` in this directory; your skill's files in
`tools/issue-select/`.
