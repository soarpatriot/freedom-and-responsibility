# Worked Examples

Each example shows a short input, the flags, and the summary — the shape the
skill should produce. They span a code review, a self-check before shipping, and
a working-habit diagnosis.

---

## Example 1 — Review a function (code review)

**Input:**

> Review this for craftsmanship:
> ```python
> def p(d, f):
>     r = []
>     for i in range(len(d)):
>         if d[i] != None:
>             if d[i]["status"] == 1:
>                 if d[i]["amt"] > 1000:
>                     r.append(d[i]["amt"] * 0.9)  # 0.9 = discount
>     return r
> ```

**Output:**

```
❌ Trait 15 — Name for the problem domain
   `def p(d, f):` and `r`, `d`, `i`
   Why: Single-letter names force the reader to decode what the code does; `f` is
        a parameter that's never even used.
   Try: `def discounted_large_amounts(records):` returning `discounted`; drop `f`.

❌ Trait 13/15 — Kill magic values
   `d[i]["status"] == 1` and `d[i]["amt"] > 1000` and `* 0.9`
   Why: 1, 1000, and 0.9 are magic numbers; the `# 0.9 = discount` comment is
        patching a naming problem instead of fixing it.
   Try: named constants — `STATUS_ACTIVE`, `LARGE_ORDER_THRESHOLD`,
        `VOLUME_DISCOUNT` — so the condition reads in problem terms.

❌ Trait 10 — Tame deep nesting
   three stacked `if`s
   Why: Nesting hides the single real intent and makes each branch harder to hold
        in your head (Trait 8, conquer complexity).
   Try: iterate directly and use a guard/`continue`, or a comprehension filtered
        on `is_active` and `is_large` — one level, reads top-to-bottom.

⚠️ Trait 16 — Comment the why, not the how
   `# 0.9 = discount`
   Why: Explains a value the code should name itself; says nothing about *why* the
        discount is 10%.
   Try: let `VOLUME_DISCOUNT = 0.10` carry the "what", and comment only if there's
        a business reason worth recording.
```

**Summary:** The logic is probably correct, but it's written for the computer, not
the next human. The strained traits are all one root cause — **managing
complexity through naming** (Traits 8, 15). Fix the names and the magic values
first; the nesting and the comment largely dissolve once the intent is visible.
One change with the most leverage: rename everything to the problem domain.

---

## Example 2 — Self-check before shipping (self-check)

**Input:**

> About to open this PR. I added a cache to speed up the dashboard. Quick gut
> check before I hit submit? I didn't add tests because it's "just a cache" and I
> eyeballed that it's faster.

**Output:**

```
❌ Trait 18 — Make it right before fast; measure, never guess
   "eyeballed that it's faster"
   Why: Optimizing without a profile is guessing; you can't tell a real win from a
        placebo, and a cache adds a whole class of staleness bugs for the win.
   Try: measure the dashboard load before/after with real data; keep the cache
        only if the numbers justify the added complexity.

❌ Trait 13 — Testing is your job
   "didn't add tests because it's just a cache"
   Why: Caches are exactly where subtle defects live — stale reads, invalidation,
        concurrent writes. "Just a cache" is where you most want a dirty test.
   Try: add tests that provoke failure — a stale-after-write case and a
        cold-vs-warm case — not just a happy-path hit.

✅ Trait 1 — Humility
   "quick gut check before I hit submit"
   Why: Inviting review before merging is the move — welcoming a second pair of
        eyes on your blind spots (Trait 12).
```

**Summary:** The instinct to self-check is good (Traits 1, 12). The two weak
spots are **unmeasured optimization** and **skipped tests on the riskiest code**.
The one change before you ship: profile it — if the speedup isn't real and large,
the simplest, most honest PR is no cache at all.

---

## Example 3 — Diagnose a working habit (habit coaching)

**Input:**

> My debugging keeps flailing. A test fails, I start changing things — flip a
> condition, add a sleep, tweak a config — rerun, repeat for an hour until it goes
> green. Sometimes it works and I don't even know why. How do I get better?

**Output:**

```
❌ Trait 17 — Debug by the scientific method, not superstition
   "flip a condition, add a sleep, tweak a config — rerun, repeat"
   Why: Changing things at random is "debugging by superstition" — a green bar you
        can't explain means the bug is probably still there, just hidden.
   Try: stabilize the failure (make it reproduce reliably), form ONE hypothesis
        about the cause, change ONE thing to prove or disprove it, then decide.

❌ Trait 3 — Intellectual honesty
   "sometimes it works and I don't even know why"
   Why: Shipping a fix you don't understand is the hobbyist/professional line;
        you've patched a symptom, not found the cause (Trait 17, root cause).
   Try: don't close it until you can say *why* the change fixed it — if you can't,
        you haven't finished.

⚠️ Trait 7 (overrated: persistence) — know when to step back
   "repeat for an hour"
   Why: Grinding the same loop for an hour is persistence turning into
        pigheadedness; the method, not the stamina, is what's missing.
   Try: after ~15 minutes of no progress, stop and switch to the hypothesis loop
        above, or step away and come back fresh.
```

**Summary:** This isn't a knowledge gap — it's a **process** gap. The one habit to
build: replace guess-and-rerun with *stabilize → hypothesize → test one thing →
understand the fix*. You can't drop the old habit directly (Trait 7); you replace
it by running the scientific loop deliberately until it becomes the reflex. Once
you can always say *why* a fix worked, the flailing is gone.
