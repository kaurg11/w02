# Design Introspection

Your own reflection on the design decisions you made this week. Written in your own words — this is
distinct from the LLM's assessment of your code, and distinct from your code-walk video.

Aim for a page. Cite your actual code: name the class and method you are talking about.

## 1. What you built

I worked on AgeMonths and Animal. AgeMonths stores an animal's age and checks that the age is valid. The Animal constructor stores the animal's name, species, age, and intake date.

## 2. Design decisions

- I chose to keep the age calculations in AgeMonths instead of Animal because they are about age. If I put them in Animal, the class would have too much work. The downside is that Animal depends on AgeMonths for age calculations.
- I chose to check the animal's information in the constructor instead of checking it later. This stops invalid animals from being created. The downside is that the constructor becomes a little longer.

## 3. Invariants

In AgeMonths, I make sure the age is not negative and does not go over 480 months. I check this in the AgeMonths.of() method.

In Animal, I make sure the name, species, age, and intake date are not missing. I check these in the Animal constructor. The values cannot be changed later because the fields are private final.

## 4. Testing

- I added tests for one month below the maximum age and for checking that the remaining months are 11 at that age. I added these tests to check that the code works correctly near the maximum age.
- The hardest test for me was the AgeMonths.toString() test because there are many different cases. Writing it taught me that small details like singular and plural words are important.
- Some unusual whitespace cases in an animal's name are still untested. If I had another hour, I would create an Animal with a tab or newline before and after the name and use assertEquals to check that the name is trimmed correctly.

## 5. What you would change

If I had another day, I would spend more time checking my code and testing different cases. I would also try to make my AgeMonths.toString() method simpler. I was focused on finishing the required work this week, so I did not have much time to improve the code after it was working.

## 6. What you found hard

The hardest part was understanding all the cases for AgeMonths.toString(). I had to pay attention to when to use "month" or "months" and "year" or "years". The examples and tests helped me understand it better.
