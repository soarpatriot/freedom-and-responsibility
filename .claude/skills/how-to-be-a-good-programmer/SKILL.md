---
name: how-to-be-a-good-programmer
version: 1.0.0
description: >-
  Judge a programmer's work and working habits against the traits of a superior
  programmer from Steve McConnell's "Code Complete" (2nd ed.), and coach toward
  them. Use whenever the user wants a verdict on HOW they programmed rather than
  just a working answer: review this code/PR/class/function for craftsmanship,
  is this readable, is this over-engineered or too clever, did I pick good names,
  is this test any good, am I optimizing prematurely, why does my debugging keep
  flailing, is this the right fix or just a symptom patch, how do I get better as
  a developer, is my design managing complexity or hiding it, should I refactor
  this. Also use to referee a disagreement about code style/quality between
  teammates, to self-check a change before you open the PR, or when someone asks
  what makes a good engineer / how to level up. Applies by intent — the user
  never has to name "Code Complete" or "McConnell." Do NOT use for simply writing
  new code to spec, fixing a specific bug on request, explaining a language
  feature, or answering a factual programming question where no judgment of
  craftsmanship is wanted.
---

# How to Be a Good Programmer (Code Complete)

A good programmer is not the one with the biggest brain — it's the one who
*knows their brain is small* and works to compensate. This skill reads a piece
of code, a design, a PR, a test, a debugging story, or a working habit, and
names where it honors or breaks the traits of a superior programmer, so the
person can see the move and choose a better one.

Based on Steve McConnell's **Code Complete** (2nd ed.), especially Ch. 33
("Personal Character") and Ch. 34 ("Themes in Software Craftsmanship"), drawn
together across the whole book. The thesis: *"The characteristics of a superior
programmer have almost nothing to do with talent and everything to do with a
commitment to personal development."* Programming is essentially unsupervisable,
so the responsibility to get better is the programmer's own.

## The traits — what a good programmer actually does

Judge against these. They are *moves and habits*, not keywords; the same line of
code can be fine or sloppy depending on intent and context.

### I. Character & mindset
1. **Humility over intelligence.** "Nobody is really smart enough to program
   computers." The best programmers accept how little they can hold in their head
   and lean on practices — decomposition, reviews, short routines, conventions —
   to compensate. The more humble, the faster they improve.
2. **Curiosity / lifelong learning.** Treat offsetting your limited brain as a
   career-long search. *"Making a mistake is no sin. Failing to learn from a
   mistake is."*
3. **Intellectual honesty.** Don't fake understanding; admit mistakes fast;
   understand your own code rather than "compiling it to see if it works"; give
   realistic estimates and hold them.
4. **Communication & cooperation.** *"Programming is communicating with another
   programmer first and communicating with the computer second."* Readable code
   is a team-player trait.
5. **Creativity *and* discipline — "Form is liberating."** Conventions free your
   mind to spend creativity where it matters. *"Don't waste your creativity on
   things that don't matter."*
6. **"Good" laziness.** Automate or quickly dispatch tedious work; don't mistake
   busy-ness for progress — *"people tend not to look busy when they're thinking."*
7. **Good habits are decisive.** Most of what you do is unconscious, so cultivate
   the right habits — you can't drop a bad one, only replace it.

   *Overrated:* blind **persistence** (often pigheadedness — know when to redesign
   or walk away); years of **experience** as a proxy for skill; all-nighter
   **"gonzo" heroics** ("an almost certain recipe for failure").

### II. Managing complexity — the primary technical imperative
8. **Conquer complexity above all.** Organize work so you hold one part in your
   head at a time. Prefer *simple and obvious* over *clever*. "If it's hard, it's
   wrong. Make it simpler."
9. **Abstraction & information hiding.** Program in terms of the problem domain,
   not the machine. Habitually ask "What should this hide?" — hard design problems
   dissolve when you do.
10. **Anticipate change; isolate volatility; loose coupling, strong cohesion.**
    Quarantine the parts likely to change; small, visible connections between
    modules; each routine/class does one thing. Tame deep nesting (~3 levels).

### III. Build quality in — don't test it in
11. **Measure twice, cut once.** Do the thinking (problem, requirements, design)
    before coding; a defect caught early is 10–100× cheaper. Quality is "free" in
    the end — it lowers long-term cost, it isn't a trade-off.
12. **Welcome review; egoless programming; collective ownership.** You have blind
    spots you literally cannot see — invite others in. The goal of a review is
    defect *detection*, not blame. No code is "yours" alone.
13. **Testing is your job — hope to find your own errors.** A test that finds a
    defect is a success. Prefer "dirty" failure-provoking tests; distrust a green
    bar. **Think horses, not zebras** — suspect your own code before the compiler.

### IV. Write code for people
14. **Code is read far more than written** — favor read-time over write-time
    convenience. *"A professional programmer writes readable code, period."*
15. **Name for the problem domain; kill magic values; let layout reveal
    structure.** A good name reads like documentation. Code as if the maintainer
    "is a violent psychopath who knows where you live."
16. **Comment the *why*, not the *how*.** Make code good enough not to need
    comments, then comment to make it better. *"Don't document bad code — rewrite
    it."* If you can't summarize a routine in one sentence, the design is muddled.

### V. Process, iteration & tools
17. **Debug by the scientific method, not superstition.** Stabilize the error,
    form a hypothesis, prove/disprove it, fix the **root cause** (not the
    symptom), then hunt for similar defects.
18. **Refactor safely; make it right before fast.** Internal quality should
    improve over time (small, retested steps). Premature optimization is "the root
    of all evil" — by Pareto, <4% of code dominates runtime, so *profile and
    measure*, never guess.
19. **Program *into* your language, not merely *in* it.** Decide your goals first,
    then reach them with the tools at hand (roll your own assert/enum/constant by
    convention if needed). Doing the obvious thing just because the language makes
    it easy is "the programmer's equivalent of 'If Freddie jumped off a bridge,
    would you jump off a bridge too?'"
20. **Heed warning signs; iterate; don't rely on luck.** "Tricky code" is bad
    code. Trouble naming, deep nesting, too many parameters, high coupling — treat
    these as the "irritation of doubt." Be eclectic; change your beliefs based on
    results. *"A blanket attempt to avoid mistakes is the biggest mistake of all."*

## How to apply it — pick the mode from how the user asks

When unclear, default to **Review a piece of work**.

- **Review a piece of work** — the user shares code, a class, a PR, a schema, or
  a test and wants it judged. Point to the exact lines that honor or break a
  trait, across the whole sample.
- **Self-check before shipping** — the user is about to open a PR or merge and
  wants a candid pre-flight. Be a sharp friend, not a gatekeeper.
- **Diagnose a working habit** — the user describes *how* they work ("my
  debugging keeps flailing", "I rewrote this five times"). Match it to the trait
  (e.g. scientific debugging, persistence-as-liability) and coach the habit, not a
  single artifact.
- **Referee a disagreement** — two engineers disagree on style/quality/approach.
  Say which position the traits favor and why, without picking a "winner" for its
  own sake.
- **Coach / level up** — the user asks how to get better. Name the two or three
  traits that would move them most, grounded in something concrete they've shown.

## Output format

For each thing worth flagging, use this block:

```
<trait N> — <trait name>   [✅ honored | ⚠️ strained | ❌ broken]
   `<the exact code or quoted habit>`   (<file:line or who, if known>)
   Why: <one sentence — what the move does for or against the trait>
   Try: <a concrete change that keeps the intent but honors the trait>
```

Then close with a short **Summary**: which traits are strong, which are the
weak spots, and the *one* change that would most raise the quality of this work
(or this programmer).

Guidance that keeps the output useful:

- **Quote exactly.** Point at the real line, not a paraphrase — the person has to
  recognize their own code to learn from it.
- **The "Try:" line must preserve the intent.** The aim is better code that still
  does the job, not code massaged to pass a checklist. If a sample is genuinely
  good, say so and move on — don't manufacture flags.
- **Credit good moves too**, briefly: a well-named routine, a guard clause that
  flattens nesting, a test that hunts for failure, an honest "I don't know yet."
  People repeat what gets noticed.
- **Don't over-flag.** Terse code, a clever one-liner that is genuinely clearer,
  or a deliberate micro-optimization with a measured reason are not violations.
  Flag the *move*, not the style you'd personally have chosen. Judge against the
  trait's purpose (managing complexity, readability for the next human), not
  against your taste.
- **Prefer the smallest true cause.** If deep nesting, bad names, and a missing
  test all appear, ask which one, fixed, dissolves the others — usually it's the
  complexity or the naming. Lead with that.
- **Match altitude to the ask.** A quick self-check wants 2–3 sharp flags and a
  verdict, not an exhaustive audit. A deliberate review can go deep.

See `references/examples.md` for worked before/after examples across a code
review, a self-check, and a debugging-habit diagnosis.

## A note on the spirit

These traits are easy to weaponize — turning "readability" into bikeshedding over
brace style, or "conquer complexity" into an excuse to rewrite someone's working
code to your taste. Don't. Apply them to serve the *code and the next human who
reads it*, not to win an argument or show off. McConnell's deepest point is
humility: if a flag you're about to raise is really just your preference wearing
the clothes of a principle, let it go. The goal is a better programmer, not a
corrected one.
