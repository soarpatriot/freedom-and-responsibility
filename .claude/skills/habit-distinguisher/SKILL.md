---
name: habit-distinguisher
description: >-
  Classify everyday habits as Rich Habits (good) or Poor Habits (bad) using Thomas
  C. Corley's framework from the book *Rich Habits: The Daily Success Habits of
  Wealthy Individuals* (富有的习惯). Use this skill whenever the user gives you one
  habit or a list of habits — behaviors, routines, thinking patterns, or lifestyle
  choices — and wants to know whether each helps or hurts their path to success,
  wealth, health, or happiness. Trigger it on phrasings like "is this a good or bad
  habit", "分析我的习惯", "classify these habits", "which of my habits are holding me
  back", "好习惯还是坏习惯", "rate my daily routine", or whenever the user dumps a list
  of things they do each day and asks for judgment. Output is always a two-column
  table (Rich Habit vs Poor Habit) with a brief, book-grounded impact note for each
  habit. Prefer this skill over free-form advice whenever the task is to sort or
  judge habits.
---

# Habit Distinguisher

Classify habits as **Rich Habits (富有的习惯 / good)** or **Poor Habits (贫穷的习惯 / bad)** using the framework from Thomas C. Corley's *Rich Habits*. The book is built on a 5-year study of 233 millionaires (177 self-made) and 128 poor people, comparing their daily habits. Corley's central claim: **habits — not luck, IQ, or inheritance — determine wealth, health, and happiness.** Every habit produces a consequence; good habits compound toward success, bad habits compound toward failure.

Your job: take the habit(s) the user gives you and sort each one into the correct column, with a short explanation of *why* it helps or hurts, grounded in the book's reasoning.

## Core workflow

1. **Parse the input into individual habits.** The user may give one habit, a comma/line-separated list, or a loose paragraph ("I wake up at 6, scroll my phone for an hour, skip breakfast..."). Break it into discrete habits — one row per habit.
2. **Classify each habit** as a Rich Habit or a Poor Habit. Match against the book's framework in `references/habit-framework.md` — read that file to ground your judgment in Corley's actual categories and survey data. For habits the book names directly, use its reasoning. For habits the book doesn't name explicitly, reason *by analogy* to the book's principles (keystone habits, the habit seesaw, time as the most valuable investment, "pay yourself first", surrounding yourself with success-minded people, etc.) and say so.
3. **Write a brief impact note** for each — one or two sentences on the concrete consequence the book attributes to it. Where the book gives a survey statistic, weave it in (e.g., "88% of the wealthy read ≥30 min/day for self-education"). Keep it concrete, not generic cheerleading.
4. **Output the table** in the exact format below.

## Output format

ALWAYS produce a single table with exactly two columns. Put each habit in the column that matches its classification; leave the other column's cell for that row empty is NOT how this works — instead, list every habit as its own row, placing the habit text in the correct column and the impact note beside it. Use this structure:

```markdown
| Habit | Rich / Poor | Impact (why it helps or hurts) |
|-------|-------------|--------------------------------|
| Reading 30 min of industry material each morning | ✅ Rich Habit | Self-education is the #1 ranked Rich Habit — 88% of the wealthy read ≥30 min/day to stay current; it compounds into expertise and opportunity. |
| Buying lottery tickets every week | ❌ Poor Habit | Corley calls this "speculation" — chasing something for nothing. 77% of the poor play the lottery weekly vs. 94% of the wealthy who never do; it substitutes luck for the habit of pursuing goals. |
```

Rules for the table:
- **Two columns of meaning**: *what the habit is* and *which category it falls in*, plus the impact note. The "Rich / Poor" column is the heart of the request — mark it clearly with ✅ Rich Habit or ❌ Poor Habit.
- One row per habit. Never merge two habits into one row.
- Keep impact notes to 1-2 sentences. Lead with the consequence, not a lecture.
- Match the user's language. If they write in Chinese, answer in Chinese (Rich Habit = 富有的习惯, Poor Habit = 贫穷的习惯). If in English, answer in English. If mixed, follow their dominant language.

After the table, add a short (1-3 sentence) **summary** that applies the book's "habit seesaw" (习惯跷跷板) idea: to tilt toward wealth, more than 50% of daily habits must be Rich Habits — so note roughly where this set lands and which one or two swaps would move the needle most. Do not pad this; one tight paragraph.

## Classification principles (the quick version)

Read `references/habit-framework.md` for the full ranked lists and survey data. The short heuristics:

**Rich Habits** tend to involve: daily self-education/reading, regular aerobic exercise, pursuing *your own* goals (not others'), living with moderation/frugality, "do it now" (no procrastination), saving ≥10% ("pay yourself first"), positive/optimistic thinking, controlling emotions, building and maintaining relationships with success-minded people, finding mentors, multiple income streams, getting 7-8 hours sleep, rising early, calculated risk-taking, seeking feedback, making thinking a daily habit, and good manners.

**Poor Habits** tend to involve: speculation / get-rich-quick (gambling, lottery), excessive drinking, excessive TV/social-media/time-wasting, negative thinking and a victim mindset, not reading/learning, toxic relationships, a single income source, having no life plan or goals, spending more than you earn / debt, and unhealthy habits (junk food, no exercise, too little sleep).

**The deeper logic** (use this for habits the book doesn't name): habits are either *keystone* (核心习惯, they trigger chains of other habits — most powerful, hardest to change) or ordinary. Time is the one investment you can never recover, so time-wasting is always a Poor Habit. Beliefs and emotions trigger downstream habits, so a negative self-belief is a Poor Habit even though it's "just thinking." When classifying an unlisted habit, ask: *does this compound toward financial security, health, strong relationships, and goal-pursuit — or away from them?*

## Edge cases

- **Ambiguous or neutral habits** (e.g., "I drink coffee"): classify by effect in context. If it's genuinely neutral or depends entirely on degree, say so in the impact note and classify by the most likely effect, noting the condition (e.g., moderate = fine, excessive = Poor Habit per the moderation principle).
- **Habits the user frames positively but the book would flag** (e.g., "I work 14-hour days and skip vacations"): classify honestly per the book — Corley prizes *moderation* and balance; workaholism that wrecks health or relationships leans Poor Habit. Explain the tension rather than just rubber-stamping the user's framing.
- **A single habit**: still output the table (one row) plus the one-line summary. Don't skip the format just because there's only one item.
- **Something that isn't a habit at all** (a question, a goal, a feeling): gently note it's not a habit, and if you can infer an underlying habit, classify that instead.

Stay faithful to the book — don't invent statistics. If you cite a number, it must come from `references/habit-framework.md`. If you're reasoning by analogy beyond the book, make that explicit ("the book doesn't name this directly, but by its moderation principle...").
