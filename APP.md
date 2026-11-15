# App: Concept Coach · Maths

**URL:** https://rajiqxf2.github.io/concept-coach/  *(update after deploying)*

A practice and progress app for a Class 6 student preparing for school exams and maths olympiads. The child practises short sets of questions; the parent sees which concepts are strong or weak and what to do next. All data is stored in the browser (localStorage), so a fresh browser starts empty.

## Logins
| Role | Username | Password | Lands on |
|---|---|---|---|
| Child | `child` | `Child@123` | Child home (`#/child`) |
| Parent | `parent` | `Parent@123` | Parent dashboard (`#/parent`) |

## Features
**Child**
- Home: greeting, day streak, topic status chips, last practice.
- **Daily practice:** N questions (default 10, parent can set 5–20), mostly from the weakest concepts and concepts due for revision, plus at least one Olympiad question.
- **Diagnostic test:** 16 questions, one Easy and one Medium from each of the 8 concepts.
- Each question: multiple choice or typed answer, Submit or Skip, then feedback with the correct answer. After a wrong answer the child picks a mistake type (careless, didn't understand, forgot the rule, ran out of time) before moving on.
- Results: score, skipped count, time taken, score by topic.

**Parent**
- **Dashboard:** questions practised, overall accuracy, day streak, last practised date, and a table of concept, attempts, mastery %, status and next revision date.
- **Weekly report:** Monday–Sunday, with previous/next week navigation; questions attempted, accuracy, days practised, top weak concepts, mistake-type breakdown, suggested action.
- **Add offline practice:** record paper/workbook practice (date, concept, difficulty, attempted, correct).
- **History:** all sessions and offline entries.
- **Settings:** child's nickname, questions per practice, reset all data.
- **How scoring works:** the rules below, shown in the app.

## Concepts (8)
Large numbers & place value · Factors, multiples, HCF & LCM · Fractions · Decimals · Integers · Ratio & proportion · Perimeter & area · Patterns & reasoning. Each has Easy, Medium and Olympiad questions (49 questions in total).

## Rules the app must follow (use as the oracle)
1. **Mastery %** = weighted accuracy over *all* attempts in the concept (online and offline). Weights: Easy 1, Medium 2, Olympiad 3. **Skipped questions count as wrong.** Rounded to the nearest whole number.
2. A concept needs **at least 5 attempts** for a mastery score; otherwise "Not enough data".
3. **Status:** Strong = 85% and above; Needs practice = 60–84%; Weak = below 60%.
4. **Next revision** is calculated from each day the concept was practised, in date order: Strong → +2 days, then +7, then +21 on later strong days; Needs practice → +2 days (and the 2/7/21 sequence restarts); Weak or not enough data → +1 day. Normal calendar arithmetic, across month and year ends.
5. **Day streak** = number of *consecutive calendar days* with at least one practice (online session or offline entry), counting back from today, or from yesterday if there's no practice today. Several practices on one day count as one day.
6. **Weekly report** covers Monday 00:00 to Sunday 23:59 inclusive.
7. **Top weak concepts** = up to 3 concepts with the lowest **mastery %** (rule 1), among concepts with at least 5 attempts.
8. **Answers:** typed fraction answers accept any equivalent fraction or decimal (3/4, 6/8, 0.75). Number answers ignore commas and spaces; "−5" and "-5" are the same.
9. **Offline practice validation:** date not in the future; attempted is a whole number 1–50; correct is a whole number from 0 up to attempted.
10. **Roles:** the child must never see parent pages (dashboard, report, offline entry, history, settings).
11. **Every question's stored answer must be mathematically correct.**
12. The timer counts while a practice is in progress and stops when it finishes; "Time taken" is fixed after that.

## Out of scope
Account creation, password reset, server sync, other subjects.
