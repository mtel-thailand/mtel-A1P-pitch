# Deck Spec — mtel A1P Pitch, SHORT version

Status: **specification only. To be built as a new file `index-short.html`. Do not touch `index.html`.**

This is a 5-slide cut of the full deck for short meetings. It reuses the existing slide engine, styles, and components from `index.html` verbatim wherever possible. The layout, typography, shared padding, chapter colours, navigation pill, overview overlay, and presenter bar all already exist and work — this spec is about **which slides to keep, what to change on two of them, and one new component (slide 4).**

Read this together with `slide-structure.md` (layout/typography tokens) and `specs_v2.md` (the reasoning behind the long deck). Nothing here overrides those; it selects from them.

---

## 1. Goal

A 5-slide version for rooms with ~10 minutes. Same brand, same engine, same assets — fewer slides, one denser proof slide.

| # | Slide | Source in `index.html` | Work |
| --- | --- | --- | --- |
| 1 | Cover | `.slide.hero` (SLIDE 01) | **keep verbatim** |
| 2 | Who we are + exclusivity | `.slide.who` (SLIDE 02) | **edit** — fold the ByteDance/BytePlus exclusivity in with real weight |
| 3 | What AI does (split) | `.slide.automate` + the generative demo content | **new slide, two columns** |
| 4 | Cases (portfolio grid) | new component (see §5) | **new — ~20 cards + click-to-modal, scaffold with placeholders** |
| 5 | Contact | `.slide.ready-ops` (SLIDE 17) | **keep verbatim** |

The two "keep verbatim" slides carry over with zero content changes. The whole point is minimal new surface.

---

## 2. Build strategy

1. **Duplicate `index.html` → `index-short.html`.** Work only in the copy. `globals.css` is shared — do not fork it; if slide 4 needs new CSS, add it in a `<style>` block inside `index-short.html` (the deck keeps all its per-slide CSS inline in `index.html` already, so follow that convention).
2. **Delete the slides that aren't in the 5.** From the full deck, remove every `.slide` except hero, who, automate (repurposed), ready-ops. That means deleting: the software-house chapter opener, No-UX, Research/Diagnose/Design/Test, software-house cases, the merged stack+exclusivity slide, two-things, create-faster demo, understand-deeper demo, how-we-work, industries, get-started, pricing. Also delete the modals tied to deleted slides (`#processModalOverlay`, `#casesModalOverlay`) and their `openProcessModal`/`closeProcessModal`/`openCasesModal`/`closeCasesModal` functions and keydown guards.
3. **Renumber.** The engine sorts slides by `data-order` (see `index.html` ~line 3741) and reads parallel JS arrays. After trimming, set `data-order` to 1–5 in visual order and rewrite the arrays in §6.
4. **Keep the engine, nav pill, overview overlay, presenter bar, and progress rail as-is** — they're data-driven and will adapt to 5 slides automatically once the arrays match.

---

## 3. Chapter colours / tags

The full deck runs a per-chapter tag + colour system (`--ch-byteplus`, `--ch-workflow`, `--ch-house`, `--yellow`). The short version has no chapters — it's five standalone slides. Two options, pick one:

- **Recommended: all-neutral.** Set every entry in `slideTags` to `'neutral'`. The progress rail goes uniform yellow, the tag indicator stays quiet, and there are no chapter-intro title cards to fire. Simplest, and correct for a deck with no chapters.
- Alternative: tag slide 2 `byteplus`, slide 3 `workflow`, slide 4 `house` if you want the coloured progress segments as visual variety. Costs nothing but adds meaning the 5-slide flow doesn't really have. Neutral is cleaner.

If you go all-neutral, **remove the `chapterIntros` map** (`index.html` ~line 3763) or set it to `{}` so no title-card dissolve fires between slides.

---

## 4. Per-slide detail

### Slide 1 — Cover *(keep verbatim)*

`.slide.hero`, unchanged. Headline, sub, cursor glow, particle canvas, and the full client-logo marquee all stay. `data-order="1"`.

Note: the marquee already shows ~35 client logos here. That's fine — on the cover it reads as reassurance. Slide 4 will show the *same* clients as clickable cases, which is a deliberate escalation (logos → proof), not a duplication to worry about.

---

### Slide 2 — Who we are + exclusivity *(edit)*

Base: `.slide.who` (SLIDE 02, ~line 2586). It already has the three pillars you want — Software House (apps/websites/platforms), AI Workflow Operators (AI solutions), BytePlus Partner (the exclusive tech). Keep the three-pillar structure. Two edits:

1. **Reframe the heading around the team, not the abstract "capabilities."** Current: *"Three capabilities. One operating partner."* For the short version, lead with the experienced-team framing the brief asked for, e.g. *"An experienced team building apps, websites, and AI."* Keep the existing `.lede` subline ("Most agencies do one of these things well. We do all three…") — it still works.

2. **Give the exclusivity real weight — this is the change that matters.** In the full deck, the ByteDance/BytePlus exclusivity gets its own slide. Here it's folded in, so it must not read as a footnote. Options, strongest first:
   - Add a full-width **exclusivity band** below the three pillars: a single strong line — *"And behind us, exclusive technology from the company that owns TikTok and CapCut."* — set large, with the BytePlus/ByteDance proof beneath it (TikTok · CapCut · Douyin logos, already in `assets/`: `tiktok.png`, `capcut.png`, `douyin.png`, `byteplus.png`). This makes the differentiator the visual peak of the slide, which is right.
   - Or promote the existing "BytePlus Partner" pillar to a wider, accented card so it visibly outweighs the other two.
   - Do **not** leave it as three equal pillars with the exclusivity buried in the BytePlus pillar's body text. The single most uncopyable claim in the pitch has to land.

**Rationale:** slide 2 is doing the work that four slides do in the long deck (who we are + what we do + the stack + exclusivity). The team/capabilities part is easy; the exclusivity is the part a competitor literally cannot say, so it gets the emphasis.

---

### Slide 3 — What AI does, split *(new slide, two columns)*

A single slide, two halves, showing the full AI range. Build it as a new `.slide.ai-split` (borrow the `.automate` slide's structure as the starting point — `.section-intro` / `.automate-grid` / `.automate-item` classes already exist and are styled).

**Heading:** something like *"Two sides of AI, both operated by us."* with `.accent` on part of it.

**Left column — Automate (back-office workflow).** Content from the existing `.automate` slide (SLIDE 07, ~line 2842). Reuse `.automate-item` cards:
- HR Workflow Automation
- Finance Operations
- Ops & Project Management
- GEO Optimization
- Custom AI Agents
- Knowledge Retrieval (RAG)

One-line framing: *"We hand back the hours your team spent on busywork."*

**Right column — Create (generative stack).** The BytePlus/ByteDance generative capabilities — the visually impressive half. Cards for:
- Video generation
- Image generation
- Websites / landing pages
- Digital humans

One-line framing: *"From a single brief to production-ready content, in minutes."* Assets available for illustration: the model logos `assets/model-seedance.svg`, `assets/model-seedream.svg`, `assets/model-omnihuman.svg`, and the video covers in `assets-video-cover/` (8 stills).

**Layout note:** two clearly separated columns with a divider or a numbered `01 AUTOMATE / 02 CREATE` header per side, so "two sides" reads as two. Keep it a static slide — do **not** try to port the full live `create-faster` / `understand-deeper` demo animations (SLIDE 12/13); they're heavy and belong in the long deck. If you later want one live demo here, the demo markup exists in `index.html` to lift, but that's out of scope for the scaffold.

---

### Slide 4 — Cases, portfolio grid *(new — scaffold with ~20 placeholder cards)*

The one dense slide. A grid of ~20 cards; each card shows a hero image, sector, and a short description; clicking a card opens a modal with the fuller story. See §5 for the full component spec. Build it now with **~20 placeholder cards** — real structure, dummy copy, logos as stand-in hero art — for Muri to fill later.

**Heading:** working title *"Selected work."* or *"Twenty ways we've delivered."* `data-order="4"`.

**Card mix matters:** slide 2 claims "apps, websites, AND AI." Slide 4 is the only proof of any of it, so the 20 cards should visibly span software builds *and* AI deployments, not lean all one way. Tag each card by sector using the existing industry buckets (Real Estate, Fintech, Entertainment, Electric/Mobility, Government, Services, Other) that the logo filenames already follow.

---

### Slide 5 — Contact *(keep verbatim)*

`.slide.ready-ops` (SLIDE 17, ~line 3655), unchanged. Contact block + BytePlus partnership block. `data-order="5"`. Confirm the contact details are current (`info@mtel.co.th`).

---

## 5. Slide 4 component spec — portfolio grid + modal

This is the only genuinely new component. Do not reuse the `.case-grid` / `.case-card` component from the long deck — that one shows 3 cards with all content visible. This needs ~20 compact cards that reveal detail on click. Build it fresh but **match the existing modal mechanics** (see the `.process-modal-overlay` / `.cases-modal-overlay` pattern in `index.html` — `.open` then `.visible` classes, `requestAnimationFrame` double-rAF to trigger the transition, Escape-to-close wired into the global keydown handler).

### 5.1 Data model

Drive the grid from a JS array so 20 cards aren't 20 hand-written blocks. One object per case:

```js
const portfolioCases = [
  {
    id: 'onebangkok',
    sector: 'Real Estate',
    title: 'One Bangkok',
    kind: 'software',                 // 'software' | 'ai'  — for the mix + optional filter
    short: '[One-line what we did.]',
    hero: 'logo/Logo-Realestate-Onebangkok.svg',  // placeholder: logo now, real image later
    // modal detail — any of these; scaffold with placeholders:
    challenge: '[What was broken.]',
    built: '[What we delivered.]',
    results: ['[Metric] [label]', '[Metric] [label]', '[Metric] [label]'],
    // OR, instead of challenge/built/results, a single paragraph:
    paragraph: null,
    bullets: null                     // OR an array of delivered-items
  },
  // …~20 total
];
```

Render both the grid cards and the modal body from this array. That way filling real content later = editing the array only, no markup surgery.

Seed the array with ~20 entries drawn from the client logos already in `logo/` (One Bangkok, Sansiri, Frasers, The Parq, PTT, EVme, Sharge, Major Cineplex, Ticketmelon, COOLISM, Cryptomind, Merkle, 100x, imBee, McDonald's, Anantara, AOT, CTF Life, Ministry of Industry, Police…). All copy fields as `[bracketed placeholders]`; `kind` guessed per client so the software/AI mix is visible.

### 5.2 Card markup (rendered per array item)

```html
<button class="pf-card reveal" data-id="onebangkok" onclick="openPortfolio('onebangkok')">
  <div class="pf-card-media"><img src="…" alt="…" loading="lazy"></div>
  <div class="pf-card-body">
    <div class="pf-card-sector">Real Estate</div>
    <h3 class="pf-card-title">One Bangkok</h3>
    <p class="pf-card-short">[One-line what we did.]</p>
  </div>
</button>
```

Use a `<button>` so it's keyboard-focusable and accessible. Grid: `.pf-grid` as CSS grid, `repeat(auto-fill, minmax(…))`, ~4 columns at desktop, 2 at tablet, 1 on mobile. 20 cards will scroll within the slide — that's expected; give the grid a max-height with internal scroll, or let the slide scroll, matching how the deck handles other tall slides.

### 5.3 Modal markup + behaviour

One reusable modal overlay (not 20). `openPortfolio(id)` looks the case up in `portfolioCases`, injects its detail into the modal body, then opens it with the existing `.open` → double-rAF → `.visible` pattern:

```html
<div class="pf-modal-overlay" id="pfModalOverlay">
  <div class="pf-modal-box">
    <button class="pf-modal-close" onclick="closePortfolio()" title="Close">✕</button>
    <div class="pf-modal-sector" id="pfModalSector"></div>
    <h3 class="pf-modal-title" id="pfModalTitle"></h3>
    <div class="pf-modal-body" id="pfModalBody"></div>
  </div>
</div>
```

`pfModalBody` renders whichever detail fields the case object has — the challenge/built/results triplet, or the single paragraph, or the bullet list. Wire `Escape` to `closePortfolio()` in the same keydown handler that already guards the other modals, and guard the slide-nav keys while the modal is open (copy the `if (processModalOpen) …` pattern).

### 5.4 Styling

Match the deck: `.reveal` for scroll-in, the deck's card radius/shadow language, chapter-neutral (yellow/ink) accents. Cards are quiet until hover (lift + accent border, same as `.pillar`/`.automate-item` hover). Keep the media box a fixed aspect ratio so mixed logos and real photos don't make the grid ragged; `object-fit: contain` for logos, and note in a comment that real hero photos should be `cover`.

---

## 6. JS engine updates

After trimming to 5 slides, rewrite the parallel arrays (in `index-short.html`, around where `slideTitles` etc. live, ~line 4008) so each has exactly 5 entries in visual order:

```js
const slideTitles = ['Cover', 'Who We Are', 'What AI Does', 'Selected Work', 'Contact'];
const slideTags   = ['neutral', 'neutral', 'neutral', 'neutral', 'neutral'];  // all-neutral (§3)
const slideGroups = ['about', 'about', 'about', 'about', 'getstarted'];        // or simplify labels
const slideNotes  = [
  '[Presenter note for cover.]',
  '[Note: lead with the team, land the TikTok/CapCut exclusivity hard.]',
  '[Note: left = automate the back office, right = generate content. Two sides.]',
  '[Note: portfolio. Flip through 3–4 live, mention the rest. Open one modal for depth.]',
  '[Note: close on a conversation, not a form.]'
];
```

- `totalSlides` derives from `slides.length` automatically — no manual count.
- The progress rail, overview overlay, and presenter bar all build from these arrays; once they're length-5 and consistent, those UIs are correct with no further edits.
- Delete `chapterIntros` entries (or set `{}`) so no chapter title-cards fire (§3).
- Delete the now-orphaned demo scripts: the create-faster typewriter/video-row (~line 4242) and the understand-deeper generate animation (~line 4502) belong to deleted slides — remove them so they don't error on missing DOM. Keep the hero particle/glow and the slide-02 orbital renderer only if those slides keep those elements (hero does; check slide 2 after editing).

**Watch for:** any `getElementById` / `querySelector` in the retained scripts that points at a deleted slide's element will throw on load. After trimming, open the console and clear every null-reference error before calling it done.

---

## 7. Assets inventory (already in the folder)

- **Client logos** — `logo/Logo-*.svg`, ~35, bucketed by sector in the filename. Primary source for slide 4 card art (placeholder) and slide 2's marquee.
- **Brand/tech** — `assets/tiktok.png`, `capcut.png`, `douyin.png`, `byteplus.png`, `byteplus-partner.png`, `byteplus-stack-3d.png` for the slide 2 exclusivity band.
- **AI model logos** — `assets/model-seedance.svg`, `model-seedream.svg`, `model-omnihuman.svg` for slide 3's generative column.
- **Capability art** — `assets/software-house.png`, `ai-workflow.png` (already used by the `.who` pillars).
- **Case imagery** — `assets/case_1.png`, `case_2.png`, `case_3.png` (3 real case images), plus `assets-industry/*` (7) and `assets-video-cover/*` (8). Enough for a handful of real hero images; the rest of the 20 stay logo-placeholder until supplied.

---

## 8. Open items — needed from Muri (none block the scaffold)

| # | Item | Blocks |
| --- | --- | --- |
| 1 | The ~20 cases: client/sector, one-line description, `kind` (software vs AI), and modal detail (challenge+result, or paragraph, or bullets) | slide 4 real content — scaffold builds now with placeholders |
| 2 | Which of the 20 have real hero images vs logo-only | slide 4 art |
| 3 | Client naming permissions — which can be named | slides 1, 2, 4 (marquee already names them; confirm) |
| 4 | Confirm the software-vs-AI balance across the 20 so slide 2's claim is backed | slide 4 mix |
| 5 | Final heading wording for slides 2, 3, 4 | copy polish |
| 6 | Confirm contact details on slide 5 (`info@mtel.co.th`) | slide 5 |

---

## 9. Verification checklist (before calling it done)

1. Exactly 5 `.slide` elements, `data-order` 1–5, no gaps.
2. `slideTitles`, `slideTags`, `slideGroups`, `slideNotes` each have 5 entries, aligned to order.
3. Nav pill reads `01 / 05`; arrows, `O` overview, and `P` presenter all work.
4. No console errors on load (orphaned element references from deleted slides = the main risk).
5. Slide 4: all ~20 cards render, click opens the modal with the right case, Escape and ✕ close it, background scroll is locked while open, arrow keys don't change slides while the modal is open.
6. Responsive: slide 3 columns stack and slide 4 grid reflows on mobile.
7. `index.html` untouched — diff shows only `index-short.html` (and any new asset) added.
