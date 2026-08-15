# First Sunday, Design Decision Record

**Status:** LOCKED. Winner picked by Brian, 2026-08-15.
**Winning direction:** The Front Porch
**Reference mockup:** `first-sunday/design/mockups/front-porch-refined.html`

This file exists so a build session can load it cold and start building without
re-running the tournament. Open the reference mockup before writing code. It is a
single self-contained HTML file with every token and component already authored,
and the build should port from it rather than reinventing.

---

## 1. The thesis, in one paragraph

First Sunday is not an app about churches. It is an app about being invited over
on one particular morning. Warm paper, terracotta, and a light left on, so the
product feels less like a directory and more like walking up to a friend's door
on your first Sunday, already expected.

Every design decision gets tested against one question: **does this feel like a
person welcoming you, or like a listings site with nice paint?** If it is the
second, it is wrong regardless of how good it looks.

---

## 2. Palette

Copy these tokens verbatim into `:root`.

```css
--paper:#f4ead9;      /* app ground, the warm paper everything sits on */
--paper-deep:#ece0c9; /* headers and section bands, one step down from paper */
--card:#fbf4e6;       /* card and input surfaces, one step UP from paper */
--ink:#3a2c1f;        /* primary text */
--ink-soft:#6b5943;   /* secondary text, labels, meta */
--clay:#c1602f;       /* primary action, selection, warmth */
--clay-deep:#9c4620;  /* button gradient bottom, pressed states, emphasis text */
--clay-glow:#e8a86b;  /* the lit edge, quote rules, accents on dark */
--sage:#6f7d54;       /* SAFETY AND LOCATION ONLY, see rule below */
--gold:#d9a441;       /* top match, plan card, warm accents */
--oxblood:#8a2f1f;    /* SIGNAL ONLY, see rule below */
--line:#dcc9a6;       /* hairlines and borders */
--shadow:rgba(58,32,14,0.28);
--page-bg:#1c140d;    /* dark ground for mockup/marketing pages, not the app */
```

**Two color rules that are not decoration, do not break them:**

- **Sage is the safety and place color.** Use it for the "use my location"
  control and the public meeting spot box. Nothing else. It reads as "this is
  about where you physically are," which is exactly what needs to feel calm.
- **Oxblood is the signal color and is deliberately outside the warm family.**
  It exists so the "Demo persona" tag and the Report button read as real signals
  rather than blending into the cozy palette. Never use oxblood decoratively.
  If oxblood shows up anywhere that is not a warning or a report control, the
  warning loses its power.

---

## 3. Type

System fonts only. No CDN, no webfonts, no build step.

```css
/* headings, church names, question text */
font-family: ui-serif, Georgia, "Times New Roman", serif;

/* body, UI chrome, labels, buttons */
font-family: ui-sans-serif, -apple-system, BlinkMacSystemFont, "Segoe UI", system-ui, sans-serif;
```

The whole distinctive feel comes from the **serif-for-human-things, sans-for-
machine-things** split, not from a font purchase.

| Use | Font | Size | Weight |
|---|---|---|---|
| Intro headline | serif | 29px | 500 |
| Quiz question | serif | 25px | 500 |
| Church name in a card | sans | 16.5px | 600 |
| Church name expanded | serif | 20px | 500 |
| Answer row text | sans | 15.5px | 500 |
| Body and sub copy | sans | 13 to 15px | 400 |
| Meta and labels | sans | 10.5 to 12.5px | 600 to 800 |

Headings are weight 500, never 700. The warmth comes from generous size and
serif shape, not from bold. Uppercase is reserved for small labels with
`letter-spacing:0.03em` to `0.05em`.

---

## 4. Layout language

- **Rounded and soft.** Cards 20 to 22px radius, inputs and answer rows 16 to
  20px, buttons 14 to 18px. Nothing square.
- **Surfaces step upward.** Ground is `--paper`, cards are `--card` which is
  lighter, headers are `--paper-deep` which is darker. That three-step stack is
  what creates depth without heavy shadows.
- **Hairlines over heavy borders.** `1.5px solid var(--line)` is the default
  edge. Dashed `--line` separates a section within a card.
- **Shadows are warm and low.** `0 6px 16px -10px rgba(58,32,14,0.3)` for cards.
  Never a grey or black shadow, always brown-tinted.
- **Paper texture.** A 3px radial dot pattern at 0.035 alpha over the screen,
  0.5 opacity, pointer-events none. Subtle enough that you feel it rather than
  see it. Do not strengthen it.
- **44px minimum on every tap target.** Non negotiable, this is a phone product.

---

## 5. The signature: the sky strip

**This is the one element that makes it First Sunday and not a generic finder.
Build it.**

A 12px strip across the very top of every screen, above the status bar, that
progresses from pre dawn to full daylight as the user moves through the app.

```css
.sky-1{ background:linear-gradient(90deg,#20160e,#3a2416,#20160e); } /* intro */
.sky-2{ background:linear-gradient(90deg,#3a2416,#7a3c1e,#c1602f); } /* quiz */
.sky-3{ background:linear-gradient(90deg,#c1602f,#d9a441,#eccf94); } /* results */
.sky-4{ background:linear-gradient(90deg,#eccf94,#ffe9b8,#fff6e4); } /* expanded */
```

The interface enacts the morning instead of describing it. The sky strip still
carries that progression across screens.

**RETIRED 2026-08-15, the porch light.** An earlier version paired the sky with
a scripted clock (6:50 AM before you leave, through 9:15 AM doors open) and a
gold radial dot used at the intro, on the top match, on section headings, and as
a badge on greeter avatars. Both are gone.

The clock was removed first: the dusk-to-Sunday-morning story it told was not
legible to readers, and on a real phone it stacked a second clock under the
operating system's own.

The dot followed. Brian's call, and the reasoning is worth keeping: it read as
decorative rather than meaningful, and a motif that has to be explained is not
earning its place. Every trace went with it, the 64px glowing ball on the plan
screen, all five small dots, and the copy that referenced it. "The light's on.
You're expected." became "[Greeter] is expecting you.", which is warmer and more
specific because it names the actual person. "The light's still on" became "Your
Sunday plan".

Do not reintroduce a glowing dot as a section marker. If a marker is wanted
later, draw something that carries meaning on its own.

---

## 6. The greeter card, and the rules that cannot bend

This is the differentiator and the biggest risk. A greeter card must never read
like a dating profile. The structure below is what got this past the trust and
safety judge, so keep the structure.

Order within the card, top to bottom:

1. **Avatar** (authored gradient with initials, never a photo), with a small gold
   porch-light badge in the corner.
2. **Name and meta** on one line: `Maya R.` then
   `Lake Nona neighborhood, at Summit four years`. **Neighborhood only, never an
   address.**
3. **Report button**, top right of the card, oxblood outline, 44x44 minimum.
   It is visible on the card itself, never hidden in a menu.
4. **The demo tag**, full width, oxblood border and oxblood text:
   `Demo persona, not a real member`. This is a hard requirement and it must be
   unmissable. These greeters are invented. Nothing may ever imply a real person
   at a real church signed up.
5. **The quote**, italic, with a `--clay-glow` left rule, then **signed with
   their name right aligned** (`, Maya`). The signature is the single most
   important warmth device in the product. It was the best idea from the losing
   Handwritten Invitation direction and it is what turns a profile listing into a
   note from a person. Do not drop it.
6. **The meet box**, sage bordered, labeled, naming the actual public spot:
   `Foxtail Coffee, Lake Nona Town Center (public spot)`. **Public places only.**
7. **The action**, a clay button to ask them to meet you.

---

## 7. Voice

Warm, faith-forward, plain. Speak like a friend who already goes there.

Real copy anchors from the winning mockup, use these as the tuning fork:

> Let's plan your first Sunday.

> Five quick questions, about a minute, so when you walk in this Sunday morning,
> someone already knows to expect you.

> No wrong answer here, we just want you comfortable walking in.

> Nobody sees your answers but you. This just helps us find where you'll feel at
> home this Sunday.

> I came alone my first Sunday and nobody told me where anything was. I can fix
> that for you.

**Hard rules:**

- **No em dashes anywhere.** Use commas, or a period and a new sentence. This is
  Brian's standing copy rule and the winning mockup has zero. Grep for the
  character before every commit.
- Oxford comma. One space after periods.
- **Banned:** seamless, curated, journey, leverage, unlock, elevate, swipe,
  "discover your perfect match," and anything that sounds like a SaaS landing
  page or a dating product.
- **Never make a doctrinal judgment about any church.** Describe, do not rate.
  "Traditional" and "contemporary" are fine. "Biblical" or "sound teaching" as a
  rating is not.
- At most one Bible verse in the entire product, well placed, never decorative.
- "Church home" is good language, use it.

---

## 8. Technical constraints carried into the build

- ONE single-file HTML PWA. Vanilla JS. No build step, no framework, no backend,
  no accounts. Saved state in localStorage.
- No external fonts, images, scripts, or CDN links. Imagery is CSS gradients,
  authored inline SVG, or CSS shapes. Avatars are authored, never photo URLs.
- Mobile first. Must honor `prefers-reduced-motion` (the mockup kills all
  transitions and animations under that query).
- Installable PWA.

---

## 9. What lost, and why it is recorded here

So a future session does not re-open a settled question.

| Direction | Warmth | Name fit + voice | Phone demo | Trust + safety | Total |
|---|---|---|---|---|---|
| **The Front Porch (WINNER)** | **9** | 7 | **8** | 7 | **31** |
| Sunday Morning Light | 7 | **9** | 7 | 6 | 29 |
| The Handwritten Invitation | 8 | 6 | 6 | **9** | 29 |

- **Sunday Morning Light** made the whole background progress from night to
  morning. Most ownable idea in the field, but it scored lowest on warmth and
  safety and the panel flagged a real risk of reading as a beautiful weather app
  rather than a warm human product. **Its core idea survives as the sky strip**
  in section 5, at a dose that does not cost legibility.
- **The Handwritten Invitation** won trust and safety outright by giving greeters
  no dating-style action button and boxing the meeting spot. **Its signed greeter
  note survives** in section 6 and is now the product's best warmth device.

**The known weakness of the winner, carried forward deliberately:** warm cream
and a soft serif are not inherently church-specific. The sky strip, the porch
light, and the greeter notes are what make it First Sunday rather than a bakery.
If a future change strips those three, the direction has lost the thing it won on.

---

## 10. The quiz, locked 2026-08-15

This list never actually lived in this file before, only in verbal
instructions to a research session, which is how it almost drifted
unrecorded. Recording it here now so a build session doesn't have to
reconstruct it.

**Five questions, in this order:** music, dress, meeting space, kids during
service, denomination. **Size was cut.** A research pass across all 20
churches in the real dataset found only 1 of 20 states a real Sunday
attendance number on its own site, so there was nothing honest to rank
against. It was checked against the persona in `PERSONA.md` and replaced
with meeting space (dedicated building vs. a shared or rented space like a
school or another church's building), which maps directly onto the primary
persona's actual fear of not knowing the unwritten rules, and had real data
for 12 of 20 churches after the same rigor of research.

**Language is a filter or badge, not a sixth quiz question.** It has real
data for 10 of 20 churches (mostly English plus Spanish, a few with
Portuguese, ASL, or Arabic), useful and worth surfacing, but keeping it out
of the quiz preserves the locked voice anchor in section 7, "Five quick
questions, about a minute." If a future session wants a true six-question
quiz instead, that line needs to change too, don't let one drift without the
other.

**Answer vocabulary**, matching what `data/churches.json`'s `vocabulary`
block uses for ranking:
- **Dress** (locked): "Jeans and t-shirts," "Business casual," "Sunday
  best," "Really varies," "No preference"
- **Music** (provisional): "Full band, modern worship," "Blended, some
  hymns some contemporary," "Traditional hymns, organ or piano," "Choir led,
  traditional," "Chant and liturgical music," "Varies by service"
- **Meeting space** (provisional): "Dedicated church building," "Shared or
  rented space"
- **Kids during service** (provisional): "Own class during service," "Kids
  classes sorted by age," "Stay in the main service," "Cry room or nursery
  available, no separate class"
- **Denomination**: whatever denomination string is on the church record,
  not a fixed list, this one is closer to a filter than a matched vibe axis

**Language, locked as a filter chip, not a quiz question (2026-08-15).**
`languageOptions` shows as a filter chip before or alongside the quiz
(exact placement is a build-time UI call, not a design decision), never as
one of the five questions. This keeps the "five quick questions, about a
minute" voice line true.

## 11. Formerly "not yet decided," now built (2026-08-15)

Everything this section used to list open is now decided and shipped in
`index.html`:

- **Fit score math:** weighted axis match. Music 25, kids 25, dress 20,
  meeting space 20, denomination 10 as a bonus. Exact match earns full
  weight, a neutral answer ("No preference," "Not bringing kids," "Still
  deciding") earns full weight, church data missing earns 60% of weight
  (never punish a church for a sparse website), a mismatch earns 20%.
- **Out of area screen:** built ("First Sunday is starting in Orlando"),
  dim sky strip, keeps the zip visible in a pill, offers the Orlando list
  or a retry.
- **Safety page:** built, reachable from the greeter section and the plan
  screen. Sage blocks for place rules, oxblood blocks for report and demo
  disclosure, and the closing rule: a good greeter never rushes you,
  pressures you, or asks for money.
- **Confirmation screen:** built as the "plan" screen. "[Greeter] is expecting you."
  You're expected." with a gold plan card (real date of the next service
  day, greeter and public spot, service times, address, parking, dress),
  an unmissable oxblood demo disclosure, and a persistent resume card on
  the intro screen ("Your Sunday plan") so the plan is one tap away
  when the app reopens in the car.
- **Greeters:** live, two fictional demo personas per church (40 total) in
  the locked card structure from section 6, mirrored to
  `data/greeters.json`. Report hides the profile immediately and cancels
  any plan that named that greeter.

---

## 12. The ink glyph system, added 2026-08-15

Five hand-drawn SVG marks, one per screen on the main path, telling the same
arrival story the app itself walks the reader through:

| Beat | Screen | Mark |
|---|---|---|
| 1 | Intro | A figure walking, satchel over the shoulder |
| 2 | Quiz | Five footprints walking away, one per question |
| 3 | Results | The double door, closed |
| 4 | Expanded | One leaf swung open, light reaching the step |
| 5 | Plan | Inside: the window, the light on the floor, two rows of pews |

**They are drawn by hand as path data, never generated.** A second AI
illustration would drift in line weight and palette from the intro hero, and
that inconsistency is the exact tell the art system exists to avoid. If a sixth
mark is ever wanted, draw it, do not prompt for it.

**The ink line never changes. The wash does.** Every mark strokes at 1.4px in
`--ink-soft` with `vector-effect:non-scaling-stroke`. What moves across the five
is the wash behind the line, from a dim night brown to full gold:

```css
.glyph-1{ --wash:rgba(58,36,22,0.12); }
.glyph-2{ --wash:rgba(122,60,30,0.16); }
.glyph-3{ --wash:rgba(193,96,47,0.18); }
.glyph-4{ --wash:rgba(217,164,65,0.30); }
.glyph-5{ --wash:rgba(217,164,65,0.42); }
```

That is the same night-to-morning progression the sky strip runs (section 5), so
the glyph and the sky read as one story rather than two decorations. Change one
and change the other.

Two presentations, both the same component. `.glyph` is a block mark above a
heading, used where the screen has no label of its own. `.chapter` puts it on a
row beside a small uppercase label, used on the quiz and results where a label
already exists, so the mark costs no vertical room on a short phone.

Each mark carries its own tight `viewBox` in `GLYPH_BOX`. Without that, the wide
flat marks (the footprints) render as a smudge at the same CSS height as the
tall ones.

**Off-path screens carry no glyph on purpose.** Out of area, safety, and report
are detours, not steps in the arrival. Adding a mark there would break the count.

### Reusing the hero, never re-generating it

The intro illustration is embedded once as `HERO_IMG`. The results header and the
plan screen show the SAME constant at different crops via `object-position`, not
a second embedded image. Style consistency is then guaranteed and the page does
not grow.

- `.band-results` at `56% 18%`, the arch and the lit opening. Suits "a few places."
- `.band-plan` at `74% 38%`, the greeter with her hand raised. Suits "[Greeter] is expecting you."

Both bands are 86px tall and masked to fade into the paper, the same treatment
the intro hero uses, so no text ever sits on the artwork.

---

## 13. The shortlist and compare, added 2026-08-15

Twenty ranked churches is a list, not a decision. The shortlist is what turns
one into the other.

- **Save lives on the card, not behind it.** Each result card is a container
  with two buttons: `.pc-body` opens the church, `.save-btn` in a `.pc-foot`
  saves it. The card used to be a single button, and a save control nested
  inside a button is invalid markup that does not reliably fire. Do not put it
  back.
- **The count is in the results header, always.** It reads "Compare 3 saved"
  once anything is saved and "Save a few to compare them" (disabled) before
  that, so the feature explains itself instead of hiding until it is used.
- **Compare is a real table, not cards in a row.** One column per saved church,
  one row per field, with the field names sticky on the left so they stay put
  while the churches scroll past. Horizontal scroll is contained to
  `.cmp-scroll`, never the page body.
- **Every row reads a field that already exists on a church object.** Fit,
  denomination, music, dress, meeting space, kids, services, language, greeter
  count, address. Nothing is inferred, so the comparison cannot claim more than
  the church's own site said. Missing data reads "Not listed yet" in italic,
  never as a blank or a zero.

`state.shortlist` is an array of church ids in save order, persisted by the
existing `saveState()`. It did NOT need a `STORAGE_KEY` bump: a v2 state saved
before the shortlist existed is still fully readable, it simply has no
`shortlist` key, and a defensive default covers it the same way `hiddenGreeters`
is covered. Bump the key only when the shape of an existing answer changes.

**The glyph follows the sky, not the screen.** Compare shares results' sky
(`sky-results`), so it carries results' mark, the closed door. That is right on
its own terms: on the compare screen you are still outside, weighing which door.
A sixth mark would have broken the five-beat count in section 12.
