---
name: rules-of-dialogue
version: 1.0.0
description: >-
  Judge the health and fairness of a real back-and-forth between people — a
  conversation, transcript, thread, chat log, meeting notes, retro, one-on-one,
  Q&A, negotiation, or argument the user pastes or describes — against the 8
  "Rules of Dialogue" (对话守则, 1989), pointing out the exact words that break a
  rule. Use whenever the user wants a verdict on HOW people talked to each other
  rather than help producing new text: did I actually listen or just talk at
  them, did one person dominate or shut others down, was that criticism fair or
  empty hand-waving, who's genuinely making the case versus just scoring points,
  where did this go off the rails, was I being fair. Also use to referee a
  dispute between two sides, or to sanity-check the tone of a message the user is
  about to send to a boss, teammate, or family member. Applies by intent — the
  user never has to say "rules of dialogue." Do NOT use for drafting new content,
  transcribing, generating questions, or fact-checking a standalone claim.
---

# Rules of Dialogue (对话守则)

A dialogue is healthy when both sides are trying to find out what is true
together, not to defeat each other. This skill reads an exchange and names the
exact words that pull it away from that goal, so people can see the move and
choose a better one.

Based on the 1989 《对话守则》 ("Rules of Dialogue: A Rarity of Its Time").

## The 8 rules

1. **Seek truth, not victory.** The goal is to find out what is true together,
   not to win. (目的在于寻求真理，而非竞争。)
2. **No personal attacks.** Argue against the position, never against the person.
   (绝不进行人身攻击。)
3. **Stay on topic.** Keep closely to the question being discussed. (紧扣主题。)
4. **Base arguments on evidence.** Claims must rest on evidence, not assertion.
   (辩论必须基于证据。)
5. **Don't cling to an error.** When shown to be wrong, correct it rather than
   defend it. (不要坚持错误不改。)
6. **Dialogue, not a monologue.** Distinguish real dialogue from "only I get to
   speak" — let the other side finish and be heard. (分清"对话"与"只许自己讲话"。)
7. **Keep a record.** The dialogue must be recorded, so claims and commitments
   can be checked later. (对话必须有记录。)
8. **Try hard to understand the other side.** Make a genuine effort to grasp
   what they actually mean. (尽量理解对方。)

## What breaks each rule — watch for these moves

Rules are broken by *moves*, not keywords. The same word can be fine or hostile
depending on intent. Judge the function of the words in context.

- **Rule 1 (truth over victory):** scoring points, gloating, "admit I'm right",
  reframing a shared problem as a contest to be won, caring more about the
  record of who-was-right than about getting it right.
- **Rule 2 (no personal attacks):** attacking the person instead of the claim —
  "you always...", "you're being emotional/naive/stupid", questioning their
  competence, motives, or character in place of their argument (ad hominem).
- **Rule 3 (on topic):** changing the subject, whataboutism ("what about when
  *you*..."), dragging in old grievances, strawmanning so the reply answers a
  different point than the one made.
- **Rule 4 (evidence):** assertion with no support, "everyone knows",
  "obviously", appeals to authority or feeling in place of evidence,
  made-up or unverifiable numbers.
- **Rule 5 (don't cling to error):** doubling down after being shown wrong,
  moving the goalposts, "that's not what I meant" used to escape a conceded
  point, refusing to say "you're right about that".
- **Rule 6 (dialogue, not monologue):** interrupting, "let me finish" used to
  block the other side, dismissing a reply before it's heard, decisions
  announced as if discussed, filibustering.
- **Rule 7 (record):** denying or rewriting what was agreed, "I never said
  that" against the record, resisting writing decisions down, no notes/owners
  for commitments.
- **Rule 8 (understand the other side):** not listening, assuming bad intent,
  "you just don't get it", answering a caricature instead of asking what they
  mean, refusing to restate their point fairly.

## Modes

Figure out which mode fits from how the user asks; when unclear, default to
**Analyze a transcript**.

- **Analyze a transcript** — user pastes a conversation, meeting notes, or
  thread and wants it reviewed. Flag violations across all speakers.
- **Live co-pilot** — flag violations turn by turn as the conversation unfolds,
  *including the user's own words*. Be concise so you don't interrupt the flow.
- **Self-check before sending** — user drafts a message/reply and wants it
  checked before sending. Review only their draft; be a candid friend, not a
  censor.
- **Coach / rewrite** — go beyond flagging and rewrite the user's side to be
  truth-seeking and non-combative while keeping their actual point and voice.

## Output format

For every flagged violation, use this block:

```
❌ Rule <N> — <rule name>
   "<exact words quoted from the dialogue>"  (<speaker, if known>)
   Why: <one sentence — what the words do that breaks the rule>
   Try: "<a rephrasing that keeps the point but obeys the rule>"
```

Then close with a short **Summary**: which rules held up, which were strained,
and the one change that would most improve the exchange.

Guidance that keeps the output useful:

- **Quote exactly.** Point to the real words, not a paraphrase — the person has
  to recognize their own sentence to learn from it. If a violation spans a few
  lines, quote the pivot phrase.
- **One block per distinct move.** If one sentence breaks two rules, show both,
  but don't pad the list with near-duplicates.
- **The "Try:" line must preserve the point.** The aim is not to soften people
  into saying nothing — a good rewrite still disagrees, still pushes, still
  states the hard thing. It just does it against the argument and with evidence.
  If the original point was itself empty (pure attack, pure noise), say so and
  offer the honest version of what they might actually be trying to say.
- **Credit good moves too**, briefly, when someone concedes a point, asks for
  evidence, or restates the other side fairly — rules 5, 4, and 8 in action.
  People repeat what gets noticed.
- **Don't over-flag.** Strong feeling, bluntness, and firm disagreement are not
  violations. A heated "I think that's completely wrong, and here's why: ..."
  obeys the rules. Flag the *move*, not the volume.
- **Note silent violations.** Rules 6 and 7 are often broken by what's *missing*
  — a decision with no discussion, commitments with no record. Call these out
  even though there are no "words" to quote; quote the surrounding line instead.

See `references/examples.md` for worked before/after examples across enterprise,
daily-life, and negotiation settings.

## A note on the spirit

These rules are easy to weaponize — turning "no personal attacks" into a way to
dismiss anyone who gets passionate, or "stay on topic" into a way to duck an
inconvenient point. Don't. Apply them to protect the *conversation*, not to
win it. If pointing out a violation would itself break rule 1 (scoring a point)
or rule 8 (missing what they meant), reconsider.
