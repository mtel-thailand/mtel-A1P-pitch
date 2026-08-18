# Deck Spec v2 — mtel A1P Pitch

Status: **specification only. Nothing has been implemented in `index.html`.**
Supersedes the flow described in `slide-structure.md` (v1, 16 slides). The layout, typography, and shared padding specs in v1 remain valid and are not repeated here.

---

## 1. Why v2

v1 opens by promising **three lines of work** (Software House, AI Workflow Operators, BytePlus Partner) and then proves only one of them.

Slide count by what each slide actually argues, in v1:

| Line of work | v1 slides | Proof |
| --- | --- | --- |
| Software House | mentioned in a bullet on 02 and 05 | none |
| AI Workflow Operators | 10, part of 12 | partial |
| BytePlus Partner | 03, 04, 05 (layer 03), 07, 08, 09 | strong |

The audience leaves believing mtel is a BytePlus reseller with an automation side business — the opposite of the "15+ years, one roof" positioning in the hero.

v2 fixes three things:

1. **Balance.** Each line of work gets its own chapter: claim → method → proof.
2. **Repetition.** 02/05 and 03/04 currently argue the same point twice. Merged.
3. **Orientation.** A persistent tag tells the audience which line of work is on screen at all times.

---

## 2. Decisions taken

| # | Decision | Chosen |
| --- | --- | --- |
| D1 | Slide 02 vs 05 overlap | **Option A** — 02 stays as the map (three names, one line each, no bullets). v1 slide 05 is dissolved; its three layers are split into the three chapters where each belongs. |
| D2 | Software House proof | 3 case studies, **one slide**, reusing the existing `.case-grid` / `.case-card` component. Content to be supplied later — build the slide with placeholders. |
| D3 | UX/UI content | 3 slides: the argument, the process, the proof. |
| D4 | Tags | Persistent three-segment indicator, not a single static label. See §3. |
| D5 | Slides 12–16 (v1) | Content approved as-is. Re-ordered and re-tagged only. |

---

## 3. Tag system

### Behaviour

Not a lone label. A **persistent three-segment indicator** in the top bar, next to the logo:

```
SOFTWARE HOUSE   ·   AI WORKFLOW   ·   BYTEPLUS
   (active)          (dimmed)         (dimmed)
```

- All three names are always visible. The active one is at full opacity in its chapter colour; the other two sit at ~30% opacity.
- On neutral slides (see below), all three are dimmed equally — that itself reads as "this applies to all three."
- The indicator repeats the three-capability message on every slide without spending a single extra slide on it.

### The neutral state

Slides that belong to all three lines of work must **not** be forced into one tag. Neutral slides: 01, 02, and the whole of Act 3 (outcomes, industries, partnership, ways to start, pricing, close).

### Colour

One colour per line of work, used consistently in:

- the tag indicator
- the chapter divider / eyebrow on the first slide of each chapter
- `.case-tag` and case-card accents inside that chapter
- the stack/layer numbering (01 / 02 / 03)

Colours to be assigned from the existing palette in `globals.css`. The current yellow accent stays reserved for headline emphasis and the closing CTA, so it should **not** double as a chapter colour.

### Also apply the tag to

- the slide overview overlay (`o` key) — currently titles only
- the presenter bar slide label
- `slideTitles` / `slideNotes` arrays should gain a parallel `slideTags` array

---

## 4. Slide map v2

21 slides. Growth is almost entirely the Software House chapter, which is the point of v2.

| # | Tag | Title | Status | Source |
| --- | --- | --- | --- | --- |
| **ACT 1 — WHO** | | | | |
| 01 | neutral | Cover | keep | v1 01 |
| 02 | neutral | Three capabilities. One operating partner. | **edit** | v1 02, reduced to the map |
| **CHAPTER A — SOFTWARE HOUSE** | | | | |
| 03 | Software House | What we build. | **new** | v1 05 layer 01 + hero logo wall |
| 04 | Software House | No UX without the U. | **new** | supplied material |
| 05 | Software House | Research. Diagnose. Design. Test. | **new** | supplied material |
| 06 | Software House | We test with real people. | **new** | supplied material + photos |
| 07 | Software House | Software house case studies | **new — placeholder** | to be supplied |
| **CHAPTER B — AI WORKFLOW OPERATORS** | | | | |
| 08 | AI Workflow | What we automate. | **new** | v1 05 layer 02 |
| 09 | AI Workflow | Audit. Automate. Operate. | keep | v1 10 |
| 10 | AI Workflow | Real deployments. Measured results. | keep, re-tag | v1 12 |
| **CHAPTER C — BYTEPLUS PARTNER** | | | | |
| 11 | BytePlus | The stack, and why you can't buy it elsewhere. | **merge** | v1 03 + v1 04 |
| 12 | BytePlus | Two things every business needs. | **edit** | v1 07 |
| 13 | BytePlus | Describe it. See it. (Create Faster demo) | keep | v1 08 |
| 14 | BytePlus | Ask anything. Get the answer. (Understand Deeper demo) | keep | v1 09 |
| 15 | BytePlus | The models you get access to. | **new** | v1 05 layer 03 |
| **ACT 3 — WORKING TOGETHER** | | | | |
| 16 | neutral | What changes when AI becomes operational. | **move** | v1 06, moved after the proof |
| 17 | neutral | Worked across sectors. | keep | v1 11 |
| 18 | neutral | Not a license. A partnership. | keep | v1 13 |
| 19 | neutral | Three ways to start. | keep | v1 14 |
| 20 | neutral | We don't quote. We scope. | keep | v1 15 |
| 21 | neutral | Ready to bring AI into your operations? | keep | v1 16 |

### Trim path to 17 slides

If the room only has time for ~17, cut in this order and no further:

1. **06 → merge into 05** as the visual for step 04. (Costs the chapter its only photographic proof — cut last if possible.)
2. **15 → merge into 11.** The model list becomes a strip at the bottom of the BytePlus slide.
3. **16 → cut.** With three chapters of cases carrying real numbers, the aggregate KPI slide is no longer load-bearing.
4. **18 → merge into 19.** Partnership phases become a footer strip on "Three ways to start."

---

## 5. Per-slide detail — changed and new slides

### 02 — Three capabilities. One operating partner. *(edit)*

**Change:** strip the three descriptive paragraphs. This slide is a 10-second map, not an explanation. Each capability gets a name, one line, and its chapter colour. The detail currently on this slide moves into the chapter opener for each line.

Keep the existing subline — "Most agencies do one of these things well. We do all three, and because they live under one roof, they reinforce each other on every engagement." — it is the thesis of the deck.

**Add:** first appearance of the three chapter colours, so the tag indicator that follows is already legible.

---

### 03 — What we build. *(new)*

**Tag:** Software House
**Headline:** `What we build.`
**Sub:** 15+ years building the platforms other people's AI has to run on.

**Content** — from v1 slide 05, layer 01:

- Custom Software Development
- System Integration
- Enterprise Platforms
- Cloud & Infrastructure
- Testing & QA
- UX/UI Design → flag this one forward: "and the layer that decides whether any of it gets used" → leads into 04

**Move the hero client-logo marquee here.** On the cover it reads as decoration; here it is evidence, and it should be labelled as such ("Platforms delivered for:" or similar). Decide whether it also stays on the cover — recommendation: keep a reduced version on the cover, full wall here.

**Framing note for the speaker:** the software house is not the legacy business. It is the reason the other two chapters work — the AI layer only produces value if someone can wire it into your systems and design the interface your team will actually use. This is the thing a pure BytePlus reseller cannot say.

---

### 04 — No UX without the U. *(new)*

**Tag:** Software House
**Headline:** `No UX without the U.`
**Sub:** Good design usually fails for one reason: the real user was never in the process. We build the process around them.

**Hero number:** `$1 → $100` — "Every dollar invested in UX returns up to $100." Source: Forrester Research, *The Six Steps For Justifying Better UX*.

**Closing line (set small, or spoken):** *Design is the cheapest place in a project to be wrong.*

**Rules:** one number only on this slide. It is a hook, not a stat wall — the other three statistics are distributed across slide 05. The number can reuse the existing `data-target` count-up animation used by the outcomes cards.

**Do not use the phrase "9,900% ROI."** Same fact, but stated that way it reads like a crypto ad and invites the room to disbelieve it. `$1 in, up to $100 back` is stronger and easier to defend.

---

### 05 — Research. Diagnose. Design. Test. *(new)*

**Tag:** Software House
**Eyebrow:** The UX scribble process
**Headline:** `Research. Diagnose. Design. Test.`

Four steps. Each carries its bullets **and one statistic set as a footnote under the step it justifies** — so each number is the reason that step exists, rather than a slide of loose statistics.

| Step | Bullets | Footnote stat |
| --- | --- | --- |
| **01 Research** — into the customer's and tenant's lived experience | One-on-one interviews with a representative of every user role · Observation: shadowing users in their workplace · Contextual inquiry on site, to capture the physical and environmental factors · Moderated stakeholder workshops to align the team and force decisions | 55% of all defects originate in the requirements phase. *Basili & Boehm, "Software Defect Reduction Top 10 List."* |
| **02 Diagnose** — identify the root cause, holistically | Analyse qualitative and quantitative data together · Look for patterns, common themes, and contradictions across user roles · Build user journey maps and workflow diagrams to make the pain visible | Up to 70% of software development effort is spent on rework, especially when requirements are unclear or change mid-project. *Boehm, Software Engineering Economics.* |
| **03 Design** — create the solution with multi-disciplinary teams | Multi-disciplinary team, not a lone designer · Several options, not one · Decided against evidence, not taste | *One option is a guess. Several options is a decision.* |
| **04 Test & Run** | Usability testing, in person and remote · Iterate before a line of production code is written | 100× more expensive to fix a defect after release than during design. *IBM Systems Science Institute — see §7 caution.* |

**Open item:** step 03 is thinner than the other three. If there is a real constraint applied there — how many options are produced, who is in the room (dev + PM + designer?), how the winner is chosen — one sentence of it should replace the placeholder line. Clients assume this step is just "the designer draws things"; a constraint is what disproves that.

**Layout note:** this slide rhymes with `Audit. Automate. Operate.` (slide 09). That is deliberate and good — one named method per line of work — but the two must be visually distinct. Recommendation: 05 as four columns, 09 stays as three stacked phases.

---

### 06 — We test with real people. *(new)*

**Tag:** Software House
**Headline:** `We test with real people. Before the build.`
**Visual:** the usability-testing images, in-person and remote, side by side.
**Content:** 2–3 numbers from an actual session.

This is the slide that makes the whole chapter worth adding. Any agency can draw a four-step diagram; almost none show a photograph of themselves running a test.

**Needed:** what testing actually changed on a real project. Candidates — task success rate before/after, features or screens cut before they were built, support tickets avoided, rounds of dev rework saved. One honest specific ("we killed 3 of 11 planned screens after testing") outperforms any generic claim.

---

### 07 — Software house case studies *(new — placeholder)*

**Tag:** Software House
**Headline:** to be written once the cases are chosen. Working title: `Built. Shipped. Still running.`
**Sub:** Three engagements. Different industries. Same process.

**Build this slide now with three empty cards**, reusing the existing `.case-grid` / `.case-card` component from v1 slide 12 with the Software House chapter colour on `.case-tag`.

Each card, per the existing component structure:

```
CASE 01 — [SECTOR]
  THE CHALLENGE      [1–2 sentences: what was broken, with a number if possible]
  WHAT WE BUILT      [1–2 sentences: the system, named plainly]
  RESULTS            [3 metrics: value + label]

CASE 02 — [SECTOR]
  ... same structure

CASE 03 — [SECTOR]
  ... same structure
```

**Metric guidance** — pick metrics that belong to *software delivery*, not to AI automation, so this slide does not duplicate slide 10: delivery time, systems integrated, users served, uptime, transactions handled, legacy platforms retired, release cadence.

**Naming:** confirm which clients can be named. If a client cannot be named, "a regional property group" is acceptable — v1 slide 12 already uses that convention.

---

### 08 — What we automate. *(new)*

**Tag:** AI Workflow
**Headline:** `What we automate.`
**Sub:** We don't sell tools. We hand back the hours your team spent on busywork.

**Content** — from v1 slide 05, layer 02: HR Workflow Automation · Finance Operations · Ops & Project Management · GEO Optimization · Custom AI Agents · Knowledge Retrieval (RAG).

---

### 10 — Real deployments. Measured results. *(keep, re-tag)*

Unchanged content. Re-tagged AI Workflow. Case tag colour switches to the AI Workflow chapter colour so it visibly pairs with slide 07 rather than competing with it.

---

### 11 — The stack, and why you can't buy it elsewhere. *(merge of v1 03 + 04)*

**Tag:** BytePlus

v1 splits one idea across two slides. Slide 03's subhead already says "exclusively," and then slide 04 spends a whole slide on exclusivity. Worse, slide 04's headline — "Doesn't sell to everyone." — has no subject on its own slide; it only parses if you have just read slide 03.

**Merged slide holds:**

- what BytePlus is: the enterprise AI division of ByteDance — TikTok, CapCut, Douyin
- the three proof stats: 2.2B global TikTok users · 50M+ in Thailand, 70%+ penetration · #1 in China's public cloud LLM market, H1 2025 (IDC)
- the exclusivity, as a single line, not a slide: *They choose their partners. In Thailand, that partner is mtel × BASICWARE. No reseller marketplace. No procurement portal.*
- the partner badge and the `slide-04-background.jpg` treatment, if it still fits the composition

---

### 12 — Two things every business needs. *(edit)*

**Tag:** BytePlus

**Two problems in v1:**

1. The two things *are* named — "Create faster and understand deeper" is in the accent line — but as one flowing sentence inside a two-line headline, so "two" never lands as two.
2. The slide sits mid-deck as if it frames the whole company, when it only frames the two slides after it, both of which are BytePlus demos.

**Fix:** split them visually and label them as the chapter's two halves.

```
Two things every business needs.

01  CREATE FASTER          02  UNDERSTAND DEEPER
    [5-word explanation]       [5-word explanation]
    → slide 13                 → slide 14
```

Keeping it inside Chapter C resolves problem 2: it is a chapter opener for BytePlus, not a company thesis.

---

### 15 — The models you get access to. *(new)*

**Tag:** BytePlus
**Content** — from v1 slide 05, layer 03: Seedance 1.5 Pro · Seedream 5.0 Lite · OmniHuman 1.5 · Data Agent · VeCDP / DataFinder · Global Marketing Platform. With the line: available in Thailand exclusively through mtel × BASICWARE.

Placed *after* the two demos, so the audience has seen what the models do before reading their names.

---

### 16 — What changes when AI becomes operational. *(moved)*

**Tag:** neutral
Content unchanged from v1 slide 06.

**Why it moves:** in v1 these six large percentages appear three slides after the deck asks the room to accept an exclusivity claim, and before any case study has been shown. They read as assertions. Placed after all three chapters of proof, the same numbers read as a summary of what was just demonstrated.

**Trade-off, noted for the decision:** an executive audience sometimes wants the payoff number in the first three minutes. If the room is CFO-led, this slide can stay near the front — but then it should carry a "sources on request" line, because it is doing more persuasive work than its evidence supports at that position.

---

## 6. Repetition removed by v2

| v1 overlap | Resolution |
| --- | --- |
| 02 vs 05 — the same trio, twice | Option A. 02 is the map, 05 is dissolved into the three chapters. |
| 03 vs 04 — exclusivity stated twice | Merged into v2 slide 11. |
| 06 vs 12 — big percentages twice | 06 moves after the proof and becomes a summary. |
| 10 / 13 / 14 — three consecutive three-step models | Content approved, but they must not share a layout. Assign three distinct treatments: 09 stacked phases, 18 horizontal timeline, 19 three cards. |

**Triad watch.** v2 contains: 3 capabilities (02), 4 UX steps (05), 3 audit phases (09), 3 cases (07), 3 cases (10), 3 partnership phases (18), 3 entry points (19). The count itself is not the problem — the repeated *visual grammar* is. Requirement: no two consecutive slides use the same card-triplet layout.

---

## 7. Source caution

Three of the four statistics in the UX chapter need care before they go in front of a client CFO.

| Claim | Verdict | Action |
| --- | --- | --- |
| Forrester: $1 in → up to $100 back | Real, from the cited report | Keep. Drop the derived "9,900% ROI" phrasing. |
| Basili & Boehm: 55% of defects originate in requirements | Sound, from the defect-reduction literature | Keep. Match the slide wording to the source — defects *originating* in requirements, not "caused by design." |
| Boehm: up to 70% of effort spent on rework | Directionally supported by *Software Engineering Economics* | Keep, with the qualifier "when requirements are unclear or change mid-project" attached. Do not state it unqualified. |
| IBM Systems Science Institute: 100× after release | **Contested.** Researchers and journalists have repeatedly tried to locate the original study and failed. | Either keep it (nobody in the room will challenge it) or swap to the safer form: Boehm's cost-of-change curve, or simply "orders of magnitude more expensive after release." Decision required. |

References: The Register, *"Everyone cites that 'bugs are 100x more expensive to fix in production' research, but the study might not even exist"* (2021) · Laurent Bossavit's source hunt for the IBM SSI figure.

---

## 8. Open items — needed from Muri

| # | Item | Blocks |
| --- | --- | --- |
| 1 | Three software house case studies: sector, challenge, what was built, 3 metrics each | slide 07 content (slide can be built with placeholders now) |
| 2 | Client naming permissions — which can be named, which stay anonymous | slides 03, 07 |
| 3 | Usability testing photos, in-person and remote | slide 06 |
| 4 | What testing actually changed on a real project — 2–3 numbers | slide 06 |
| 5 | The real constraint in UX step 03 — how many options, who is in the room, how the winner is chosen | slide 05 |
| 6 | Chapter colours — three assignments from `globals.css`, avoiding the reserved yellow accent | tag system, all chapters |
| 7 | Decision on the IBM 100× stat: keep or swap | slide 05 |
| 8 | Decision on the trim path — build all 21, or target 17 | scope |
| 9 | Whether the client logo wall stays on the cover as well as slide 03 | slides 01, 03 |

---

## 9. Not carried forward

- v1 slide 05 as a standalone "The Stack" slide — dissolved into chapters A, B, and C.
- v1 slide 04 as a standalone exclusivity slide — merged into v2 slide 11.
- The "9,900% ROI" framing of the Forrester number.
- The legacy CSS sections listed in `slide-structure.md` (`LEGACY / UNUSED: PROBLEM`, `LOGO WALL`, `CTA`) — still unused; the logo-wall section may be worth reviving for slide 03 rather than writing a new component.
