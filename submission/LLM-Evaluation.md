
# LLM Evaluation

Produced with an LLM using the prompt in `LLM-Evaluation-prompt.md`, then reviewed and answered by
you. **Both halves are required** — an unread LLM assessment pasted in whole is worth nothing.

---

## Assessment

Paste the LLM's assessment here, in full and unedited.

1. Immutability and encapsulation — 25/25
   All four Animal fields are private final (Animal.java:28-31), and AgeMonths.months is private final behind a private constructor (AgeMonths.java:19,30). No setters anywhere, no method reassigns a field after construction. Every accessor returns an already-immutable type (String, Species enum, AgeMonths, LocalDate), so none leak a mutable reference. AgeMonths.MAX_MONTHS is the only public field, and it's a constant the tests themselves require (AgeMonths.MAX_MONTHS at AgeMonthsTest.java:32). No deductions.
2. Constructor validation — 25/25
   All five required checks are present and distinguishable (Animal.java:56-70): null name, blank/whitespace-only name, null species, null age, null intake date — each with its own message ("name must not be null", "name must not be blank", etc.). Validation fully precedes assignment: the five checks come before any of the four field assignments on lines 71-74. The name is stored trimmed only after the blank check, so "   " is correctly rejected rather than silently trimmed to empty first.
3. Correctness — 15/15
   Traced AgeMonths.toString() (AgeMonths.java:115-146) through all seven specified inputs (0, 1, 11, 12, 23, 24, 25 months) — every one matches the spec exactly, including singular/plural agreement and the omission of the months clause on whole years. Animal.toString() (line 135) produces exactly "Luna (Cat, 1 year, 11 months, intake 2026-09-21)" for the Luna case.
4. Testing and coverage — 10/15
   Boundaries for AgeMonths are genuinely covered: 0 (AgeMonthsTest.java:26), 11/12 (lines 47-51), the maximum (line 31), one past the maximum (line 41), and a student-added one-below-the-maximum case (lines 99-107). All assertThrows calls target IntakeException.class specifically, and message-content assertions (AgeMonthsTest.java:92-98, AnimalTest.java:109-117) would fail against a wrong-message implementation.

Three specific gaps:

toString() at the maximum is untested. theMaximumIsAllowed() checks only .months(), not that AgeMonths.of(480).toString() renders "40 years".
Non-space whitespace in a blank name is untested — aNameOfOnlyWhitespaceIsRefused only tries " ". The student names this exact gap themselves in introspection.md ("a tab or newline before and after the name"), so it's a known, unaddressed hole.
No student-authored AnimalTest cases exist at all. AnimalTest.java content here is identical to the shipped spec — every Animal-level edge case (e.g., an animal at the age maximum, with Species.BIRD) was left untested by choice.
5. Code quality and style — 8/10
Animal.toString() correctly delegates — no "year"/"month" literal anywhere in it, relying entirely on this.age's own toString(). Every public member carries documentation beyond its name (though much of this prose, e.g. the Animal class/constructor Javadoc, reads like supplied assignment text rather than student-authored — worth confirming in the code walk).

Deductions: AgeMonths.toString() has four near-duplicate singular/plural branches (lines 119-145) that a small pluralize() helper would collapse. Brace spacing is inconsistent — if (...){ at Animal.java:59 and AgeMonths.java:126, }else { at AgeMonths.java:129, and a stray space in IntakeException ( at Animal.java:69.

6. Scope discipline and code walk — 5/10
   No equals/hashCode, no added inheritance, no collections anywhere — clean on scope. But introspection.md never mentions Species, enum, or label() at all — it covers only AgeMonths and Animal. The rubric specifically requires evidence the student can explain why Species is an enum with a field and method rather than three constants, and that evidence is simply absent from the one document meant to carry it.

Total: 88/100

Most important thing to do differently next time: be ready to explain Species concretely — why an enum with a label() method beats three separate constants — since the introspection currently shows zero engagement with the one piece of shipped code the rubric explicitly asks about.

One thing done genuinely well: AgeMonths.toString() is fully correct across all seven specified cases, and the student went past the minimum by adding their own boundary test one month below the maximum (AgeMonthsTest.java:99-107) — real engagement with edge cases despite calling it the hardest part.

Its scoring categories are the ones in `LLM-Evaluation-prompt.md`, which are the same categories and
the same weights as the rubric in `how-to-submit.md`. If the LLM invents different categories or
weights, say so below rather than silently accepting them.

**Coverage reported:**  100% 

---

## Your response

The part that is actually marked. For each point below, a few sentences.

### Where it is right

I agree that I could add more tests. In particular, I would test the maximum age's toString() output and more unusual whitespace, such as tabs and newlines. I also agree that I could review my code formatting more carefully for consistent spacing.

### Where it is wrong

I disagree with the deduction in Section 6 about `Species`. `Species` was provided as completed code, so I did not write it. The explanation of `Species` is part of my code-walk video, where I will explain why it is an enum and how its `label` field and `label()` method work.

### What it missed

I think my test names could have been clearer. Some of my test names are a little long or have spelling mistakes, so I could improve them to make the tests easier to understand.

### What you changed

I did not make any changes to my code after the LLM evaluation. I only reviewed the feedback and understood which parts of my tests could be improved.

---

## Declaration

- Which LLM and version you used: Claude Sonnet 5 High
- Confirm you understand every line you submitted, regardless of who or what wrote it: yes
