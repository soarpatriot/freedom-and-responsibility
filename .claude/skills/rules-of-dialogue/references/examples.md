# Worked Examples

Each example shows a short exchange, the flags, and the summary — the shape the
skill should produce. Settings span enterprise, daily life, and negotiation.

---

## Example 1 — Review meeting (enterprise)

**Input:**

> **Lead:** This design is bad. You clearly didn't think about scale at all.
> **Dev:** I did think about it — we shard by tenant.
> **Lead:** Everyone knows sharding by tenant doesn't work. Just trust me, I've
> been doing this longer than you.
> **Dev:** What about when *your* service went down last quarter?

**Output:**

```
❌ Rule 2 — No personal attacks
   "you clearly didn't think about scale at all"  (Lead)
   Why: Attacks the dev's diligence instead of the design decision.
   Try: "I'm worried this doesn't hold at scale — walk me through the write path."

❌ Rule 4 — Base arguments on evidence
   "Everyone knows sharding by tenant doesn't work"  (Lead)
   Why: Asserts a conclusion with no evidence, leaning on "everyone knows".
   Try: "Tenant sharding struggled for us at >10k tenants — here's the latency graph."

❌ Rule 4 — Base arguments on evidence
   "Just trust me, I've been doing this longer than you"  (Lead)
   Why: Appeals to seniority instead of showing why the design fails.
   Try: "In a similar system I saw hot-tenant skew; can we check if that applies here?"

❌ Rule 3 — Stay on topic
   "What about when your service went down last quarter?"  (Dev)
   Why: Whataboutism — changes the subject to the Lead's past outage.
   Try: "Can you point to the specific failure mode you're worried about?"
```

**Summary:** The design question never actually got discussed — it turned into
seniority vs. counter-attack. The one change with the most leverage: the Lead
names a concrete failure mode with data, and the Dev answers *that*.

---

## Example 2 — Family talk (daily life)

**Input:**

> **A:** You never help around the house.
> **B:** That's not true, I —
> **A:** Let me finish. You're just lazy, like your father.
> **B:** Fine, whatever. You're always right.

**Output:**

```
❌ Rule 2 — No personal attacks
   "You're just lazy, like your father."  (A)
   Why: Labels B's character and drags in a relative instead of the actual issue.
   Try: "I feel like the chores land on me — can we split them?"

❌ Rule 6 — Dialogue, not a monologue
   "Let me finish."  (A)
   Why: Used to cut off B's reply, so only one side gets to speak.
   Try: "Let me say the whole thing, then I really want to hear your side."

❌ Rule 5 / Rule 1 — Clinging / seeking victory
   "Fine, whatever. You're always right."  (B)
   Why: Sarcastic surrender ends the dialogue without resolving anything — it
   concedes to end the fight, not to find the truth.
   Try: "I don't think that's fair. Here's what I did this week: ..."
```

**Summary:** This stopped being a dialogue at "let me finish" — after that only
one person was really speaking. Replace the character label with a specific
request ("chores land on me, can we split them") and the whole exchange has
somewhere to go.

---

## Example 3 — Negotiation

**Input:**

> **Buyer:** Your price is insulting. No serious company charges this.
> **Seller:** Our margins are thin; the quote reflects the custom tooling.
> **Buyer:** We agreed on $40k last call, you can't change it now.
> **Seller:** We never agreed to $40k.

**Output:**

```
❌ Rule 2 — No personal attacks
   "Your price is insulting. No serious company charges this."  (Buyer)
   Why: Attacks the seller's seriousness rather than the number.
   Try: "This is above our budget — can you show how the cost breaks down?"

❌ Rule 7 — Keep a record
   "We agreed on $40k last call" / "We never agreed to $40k"  (both)
   Why: The dispute is over what was agreed, with no record to settle it.
   Try: "Let's check the notes from last call. Going forward, we confirm numbers
         in writing after each meeting."

✅ Rule 4 — Evidence (good move)
   The Seller tied the quote to "custom tooling" — a concrete, checkable reason
   rather than just holding firm. Build on that.
```

**Summary:** The missing record (rule 7) is doing real damage — neither side can
prove the $40k claim, so the talk stalls on memory. Agreeing to confirm numbers
in writing removes that whole category of fight. Keep the seller's evidence-based
framing; drop the "insulting" opener.

---

## Example 4 — Self-check before sending, with OFNR rewrite (daily life)

Shows the construction recipe (Observation → Feeling → Need → Request) turning a
blaming draft into an honest one, step by step.

**Input:**

> Draft I'm about to send my teammate: "You make me feel like an idiot every
> time you rewrite my code without telling me. You're so controlling."

**Output:**

```
❌ Rule 2 — No personal attacks
   "You're so controlling."  (draft)
   Why: Labels the person's character instead of naming the action and its effect.

❌ Rule 1 — Seek truth, not victory
   "You make me feel like an idiot"  (draft)
   Why: Hands the feeling to them as blame ("you make me") instead of owning it,
   which invites a fight rather than a change.
```

Building the Try: line with OFNR:

- **Observation:** "the last two PRs, my code was rewritten before we talked" —
  filmable, no verdict.
- **Feeling:** not "like an idiot" (a thought about yourself) — the real feeling
  is *discouraged* and *frustrated*.
- **Need:** to be consulted; to feel my work is trusted.
- **Request:** doable, positive, declinable.

```
Try: "On the last two PRs, my code got rewritten before we talked about it (observation).
      I felt discouraged (feeling), because I want to be looped in on changes to my work
      (need). Could we talk before reworking each other's PRs from now on? (request)"
```

**Summary:** The draft would have landed as an attack and provoked defensiveness.
Same point, rebuilt through OFNR, it stays honest — it still says "this isn't
working for me" — but gives the teammate something to say yes to.

---

## Example 5 — Referee a dispute: needs vs. strategies (negotiation)

When refereeing, the job is to surface each side's *need* underneath the
*strategy* they're fighting over — two strategies can clash while the needs
behind them don't.

**Input:**

> **Farmer:** These workers just ignore the rules. I need them gone.
> **Worker:** He's a racist. We need him to stop watching our every move.

**Output:**

```
❌ Rule 2 — No personal attacks
   "He's a racist." / "These workers just ignore the rules."  (both)
   Why: Each side diagnoses the other's character instead of naming what happened.

❌ Rule 4 — Base arguments on evidence
   Both claims are verdicts with no specific incident attached.
   Try (farmer): "Twice this week the safety checklist wasn't signed before the
         shift started."
   Try (worker): "You came to our station six times yesterday to check on us."
```

Refereeing move — separate need from strategy:

- "I need them gone" is a *strategy*, not a need. The need underneath is likely
  *reliability / safety*. Ask: "what would being gone give you that you're not
  getting now?"
- "Stop watching our every move" is a strategy too; the need is likely *trust /
  dignity*. Ask: "what do you need to feel trusted on the job?"

Once it's "I need the safety steps followed" vs. "I need to be trusted to do my
job," the two needs aren't actually opposed — and a shared solution (a signed
checklist the workers own themselves) can satisfy both.

**Summary:** The fight was strategy-vs-strategy ("gone" vs. "stop watching"),
which has no overlap. Moving each side to the need underneath — reliability and
dignity — opens a solution neither opening position allowed. Note the goal is
*both needs met*, not a compromise where each gives something up.

---

## Calibration — what NOT to flag

Firmness is not a violation. These are all *fine*:

- "I strongly disagree, and here's the data that changed my mind." — rule 4 ✅
- "You're right, I was wrong about the timeline." — rule 5 ✅ (credit it)
- "That's a fair point — let me make sure I understand it before I respond." —
  rule 8 ✅
- Passion, urgency, and bluntness aimed *at the problem* are healthy. Flag the
  move (attack, evasion, assertion), never the volume.
