# Assignment 01 — TA feedback: Gurpreet (Gurpreet Kaur)

- **Evaluated by:** Yilin Pan (TA)
- **Date:** 2026-10-05

## Scores

| Category | Pts | Student's LLM eval | TA verified | Notes |
|---|---|---|---|---|
| Immutability & encapsulation | 25 | 25 | 25 | |
| Constructor validation | 25 | 25 | 25 | |
| Correctness | 15 | 15 | 15 | |
| Testing | 15 | 10 | 10 | Kept, but see feedback |
| Code quality & style | 10 | 8 | 8 | 4 Checkstyle warnings |
| Introspection, LLM eval & code walk | 10 | 5 | 10 | `Species` is graded from the code walk |
| **Total** | **100** | **88** | **93** | |

## Checks

- [x] All tests pass (31/31)
- [x] No `UnsupportedOperationException` stubs left
- [ ] Checkstyle warnings: 4 (brace spacing at AgeMonths.java:126, 129 and Animal.java:59)
- [x] Coverage (lines / branches): 98% / 97% (AgeMonths.java:143 never runs)
- [x] Nothing out of scope (inheritance, collections, `equals`/`hashCode`)
- [x] `submission/LLM-Evaluation.md` present
- [x] `submission/introspection.md` present

## Where the TA disagrees with the student's LLM evaluation

- Categories 1–5: I agree with your LLM's scores.
- Cat 6 +5: you were right. `Species` is covered in the code walk, not the introspection, and your code walk covered it, so full credit.

## Feedback

The constructor is clean: every check runs before any assignment, and each has a clear message.
Testing is the weak spot. You added two tests, both at 479, and neither checks an exception message,
which is the first thing how-to-submit asks for. Coverage also shows AgeMonths.java:143 never runs.
A test for `AgeMonths.of(26).toString()` would cover it. Also clear the 4 Checkstyle warnings. A
small pluralize helper could replace the four branches in `AgeMonths.toString()`.

## Grade

**Final grade:** 93 / 100
