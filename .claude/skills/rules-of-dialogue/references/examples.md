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

## Calibration — what NOT to flag

Firmness is not a violation. These are all *fine*:

- "I strongly disagree, and here's the data that changed my mind." — rule 4 ✅
- "You're right, I was wrong about the timeline." — rule 5 ✅ (credit it)
- "That's a fair point — let me make sure I understand it before I respond." —
  rule 8 ✅
- Passion, urgency, and bluntness aimed *at the problem* are healthy. Flag the
  move (attack, evasion, assertion), never the volume.
