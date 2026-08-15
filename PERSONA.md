# First Sunday, who this is for

**Status:** Written 2026-08-15, retroactively, after the design and initial
church research were already done without one. This should have come first.
Treat it as load-bearing going forward: any new quiz axis, ranking weight, or
copy decision should be checked against the primary persona's actual fear,
not against what happens to be easy to collect.

---

## Primary persona: "Nervous First Sunday"

**Who:** An adult (20s to 40s, skews slightly female per general
church-visit research, but not exclusively) who has a real, current reason to
walk into a church this specific Sunday, not someone idly browsing options.
Common triggers: just moved to Orlando/Lake Nona, a life event pushed them
toward faith (new baby, a loss, a recovery, a relationship), a friend or
coworker invited them, or they grew up in church, drifted, and are
considering going back after years away.

**What they're actually afraid of, in order:**
1. **Standing out as the new person.** Being noticed, greeted too hard,
   asked to stand up, put on a spot, or handed a microphone.
2. **Not knowing the unwritten rules.** What to wear, when to stand or sit,
   whether to sing along, what happens with communion if they're not a
   member, whether kids stay with them or go somewhere else.
3. **Wasting the trip.** Driving over and the vibe being wrong (too formal
   when they wanted casual, or the reverse), the sermon style clashing with
   what actually draws them, and leaving more discouraged than before.
4. **Logistics friction on the actual morning.** Not finding parking, not
   knowing where the entrance is, not knowing if the address they have is
   even the right building this week.

**What "success" looks like for this person:** they walk in already knowing
roughly what to expect, so the only new information that morning is the
people and the message, not the format. They leave able to say "that felt
like what I expected" whether or not they come back.

**How they use the app:** open it once, maybe twice (before leaving the
house and again in the car), never again after they've found their church.
This is a single-use-per-decision tool, not a habit-forming app. That
constrains everything: no feature earns its place if it doesn't reduce
first-visit anxiety directly.

---

## Secondary persona: "Invited by Someone"

**Who:** A friend, coworker, or family member of an existing church attendee
who is going because someone they trust asked them to, not from their own
search. They may never open the app's zip/quiz flow at all, they may
land directly on a specific church's page or greeter card that was shared
with them.

**What's different for them:** their fear is less "which church" (already
decided by the relationship) and more "will this be weird," "do I have to
sign anything," "is this going to be a hard sell." This is exactly what the
Demo persona greeter feature is trying to answer: a warm, named,
clearly-labeled point of contact instead of a cold building.

**Product implication already reflected in the locked design:** the greeter
card and its trust/safety guardrails (oxblood report button, "Demo persona"
label, public meeting spot only) exist for this persona specifically, so
they don't feel like they've been signed up for a program with strings
attached.

---

## Anti-persona: who this is explicitly NOT for

Naming these keeps future feature requests honest.

- **Deeply plugged-in existing churchgoers looking for their next home.**
  They already know the unwritten rules, already know what questions to
  ask, and are better served by word of mouth or a church's own site than a
  first-timer's discovery quiz. If the product starts optimizing for this
  user (deeper doctrinal filters, membership-transfer logistics), it has
  drifted from the actual challenge brief.
- **Theology comparison shoppers.** People trying to rank churches by
  doctrinal correctness. This is explicitly against the locked "describe,
  don't judge" rule, and the app should never grow a feature that invites
  this use.
- **Church staff or marketers evaluating competitors.** Not a target user
  for the visitor-facing app; the intake-form idea from the schema
  brainstorm is a separate, admin-facing surface, not this persona.
- **People who want a directory to browse for its own sake, no visit
  intent.** The single-use, gets-out-of-the-way design (no accounts, no
  feed, no browsing history) actively resists becoming this. If a future
  feature would make sense for a browsing-for-fun user but not for someone
  with a Sunday actually on the calendar, it's out of scope.

---

## What this resolves right now: the quiz axis swap

Checking both candidate replacements for "size" against the primary
persona's actual fear list above:

- **"Where you'll meet"** (dedicated sanctuary vs. a school, storefront, or
  borrowed building) maps directly onto fear #2 (not knowing the unwritten
  rules) and fear #4 (logistics friction). A visitor who expects a sanctuary
  and walks into a middle school cafeteria isn't in danger, but the mismatch
  between expectation and reality is exactly the kind of small friction this
  whole product exists to remove. **Keep this one, it's a strong axis.**
- **"Language of service"** maps onto a real but narrower slice of the
  persona, mainly relevant to Spanish-first or bilingual households in
  Central Florida, which is a meaningful population here but not universal
  to "Nervous First Sunday." It's a real, useful filter, just not as
  load-bearing as the meeting-space one. **Keep it, but as the lighter of
  the two, maybe folded into a secondary filter/badge rather than a full
  quiz question, if the five-question limit needs to stay tight.**

Both check out against the persona better than raw attendance size ever did,
size was never actually about the visitor's fear, it was a proxy for "will I
feel anonymous or exposed," which "where you'll meet" and existing axes
(music, dress) already cover more directly anyway.
