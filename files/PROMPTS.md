# Crestfield College OSA — Vibe-Engineering Prompt Log
**ENSG AI Class · Assignment 3 (full 5–10 page website)** · built for Cynthia Ojoma Abah

**Site:** Crestfield College Old Students' Association · 8 pages · HTML + Tailwind CSS + vanilla JS · built in VS Code.

**Where the prompts live (three places, so they can be graded):**
1. this file — full chain-of-thought prompts, per section
2. a condensed banner comment above every section in the page source
3. the on-site **Build & Prompt Log** page (`build-notes.html`, linked in the footer)

---

## Vibe coding vs. vibe engineering
Vibe coding accepts the first output. Vibe engineering runs the AI like a teammate under
review: **one scoped, chain-of-thought prompt per section** ("let's think step by step…"),
tested against acceptance criteria, then **refactored** before moving to the next. Nothing
was built in a single prompt; each page was reasoned through, then hardened.

## Why a generator (the core engineering move)
A static multi-page site has no server includes, so the nav, footer and crest would be
copied into all eight pages and drift the instant one changed. I moved them into shared
partials and **generate** the pages from one script (`build_site.py`). The *deliverable*
is plain HTML + Tailwind; the script is just the press that stamps it consistently.

## Design tokens (locked in P0)
| Role | Value |
|---|---|
| Forest (primary) | `#1F4D3A` / dark `#163A2B` / darker `#0F2A1F` |
| Heraldic gold | `#C9A227` / light `#E7CF7A` / pale `#F3E7C0` |
| Burgundy (accent) | `#7C2B2B` |
| Cream / paper / line | `#FBF8F1` / `#F4EFE3` / `#E4DBC7` |
| Display / body / mono | Fraunces · Libre Franklin · JetBrains Mono |
| Signature | the inline heraldic **crest** (book of knowledge + rising sun) on every page |

*Note on the palette:* green/gold/ivory + a serif is normally an "AI default" to avoid — but
here it's grounded in the subject (a real school crest), which the design brief says always
wins. Fraunces (a serif with character) and the hand-built crest keep it from reading generic.

## Sitemap & menu
- **Home** · **About** ▾ (Our Story / Executive Council / Constitution) · **Membership** ▾
  (Why Join / Register / Dues & Chapters) · **Community** ▾ (Events / News / Give-Back
  Projects) · **Contact** · CTA **Join / Donate**. Footer-only: **Build & Prompt Log**.

---

## The prompts, per section (chain-of-thought)

### P0 — Theme, name, crest & tokens
> "Let's think step by step before any code. (1) Theme = an Old Students' Association; give
> it a credible name, founding year and motto. (2) A crest is the identity anchor for a
> college body — design a heraldic shield (book of knowledge + rising sun) in the palette.
> (3) Palette + type: heritage green/gold on ivory is grounded in the subject, not the
> generic AI default — pick a display SERIF with character (Fraunces), a civic body face
> (Libre Franklin), and a mono for the log. (4) Decide the page set and menu structure.
> Only after this plan do we write markup."
**Accepted:** Crestfield College OSA · crest drawn · tokens above · 8 pages, 3 dropdowns.

### P1 — Information architecture
> "Think about the visitor before the pixels. Which pages does an alumnus actually need,
> and how do they group? Draft the sitemap and group the middle sections under dropdowns so
> the top bar stays calm."
**Accepted:** 8 pages, 3 dropdown groups, 1 CTA; Community groups events + news + projects.

### P2 — Sticky menu bar + dropdowns
> "Build only the header. Sticky, forest with a gold underline, crest + wordmark left,
> dropdown nav right linking to real pages/anchors. Must open on hover AND keyboard
> (focus-within), highlight the current page in gold, and provide a mobile hamburger that
> expands the SAME links — generate desktop + mobile from one model so they can't drift."
**Accepted:** sticky ✓ · keyboard-openable dropdowns ✓ · current page gold ✓ · one nav model ✓.

### P3 — Home / hero
> "One job: make an alumnus feel belonging and click Join. Step through it — forest hero
> with the crest and a warm 'Welcome home, Crestfielder' headline + two CTAs; three
> credibility numbers; a 3-pillar 'what we do'; the featured reunion beside three news
> teasers; a closing membership band. Dignified, not corporate."
**Accepted:** hero + stats + pillars + event/news + CTA, warm specific copy.

### P4 — About (story · EXCO · constitution)
> "Trust before detail. Short history + mission/vision, then a real timeline (history is a
> genuine sequence, so ordered markers are earned), then the named Executive Council with
> SET years (a Crestfield signature), then a plain-language constitution summary with a
> placeholder PDF. Don't fabricate legal text."
**Accepted:** mission/vision · 4-milestone timeline · 6 EXCO cards · governance summary; `#exco`, `#constitution`.

### P5 — Membership (benefits · register · chapters)
> "Reduce friction. Benefits first, then registration as THREE steps not a wall, then one
> lightweight client-validated form that is honest about having no backend, then a dues +
> chapters list."
**Accepted:** 4 benefits · 3-step register · validated form · 6 chapters; backend flagged.

### P6 — Events, News & Projects
> "Three community pages, one pattern each. Events: a featured homecoming + upcoming list +
> past-reunion gallery. News: a category-tagged feed, newest first, obituaries handled with
> care. Projects: impact numbers BEFORE the ask, funding-progress bars, one donate CTA."
**Accepted:** featured+list+gallery · tagged news feed · impact+progress+donate; placeholders flagged.

### P7 — Contact
> "Effortless human contact: validated message form on one side, real secretariat details +
> map placeholder on the other; same kind, honest validation as membership."
**Accepted:** form + secretariat + map placeholder · client-validated · backend flagged.

### P8 — Sticky footer, JS & QA
> "A big footer can't sit at bottom:0 without covering content, so split it: rich columns in
> normal flow, THEN a slim sticky bar (copyright + build-log link + back-to-top) as the
> always-present footer. Add ~30 lines of vanilla JS (mobile toggle, footer year, form
> validation). QA: tag-balance every page, green/gold contrast, reduced-motion, mobile 360px."
**Accepted:** rich footer + slim sticky bar ✓ · JS minimal & commented ✓ · all 8 pages validated ✓.

---

## Engineering the vibe code — four edits I did NOT leave to the AI
1. **8 hand-copied pages → one generator.** Nav/footer/crest became shared partials.
2. **`<div onclick>` → semantic `<a href>`.** Keyboard-navigable, works without JS, dropdowns open on focus-within.
3. **Full sticky footer → slim sticky bar.** Requirement met without covering content on short screens.
4. **Silent placeholders → honest flags.** Every demo form / payment / PDF button is labelled as needing a backend or gateway.

## Appendix A — Photos & going live
Images ship as styled fallback tiles. Create `assets/img/` beside the pages and drop in
photos named as the tile labels suggest (e.g. `homecoming.jpg`, `hc25.jpg`) — each fades in
on load. Before publishing: connect the registration/contact forms to a backend (Formspree,
Google Forms or your own API), wire the donate button to Paystack/Flutterwave, replace the
constitution PDF and the `#` social links, and embed a real Google Map on Contact.

## Appendix B — Run it offline
Built with the Tailwind Play CDN (needs internet to paint). For a fully offline copy, run
the Tailwind CLI (as in the nexus-app project) to compile a local `styles.css` and swap the
CDN `<script>` for a `<link>`.

## Appendix C — Requirement traceability
| Brief item | Where |
|---|---|
| 5–10 pages | 8 pages |
| Name + logo | Crestfield College OSA + inline crest on every page |
| Menu with dropdowns to different pages | sticky header, 3 dropdown groups |
| Hero | home + section heros per page |
| Sticky menu AND footer | `sticky top-0` header · `sticky bottom-0` footer bar |
| Every prompt, per section | this file · per-section banners · build-notes.html |
| Chain-of-thought, not one prompt | P0–P8, each reasoned step by step |
| Worked on the vibe code + comments | refactor list + `[build-note]` comments throughout |
| Persona / style | warm association voice; engineer's `[build-note]` comments |
| HTML and/or Tailwind, in VS Code | HTML + Tailwind CSS |
