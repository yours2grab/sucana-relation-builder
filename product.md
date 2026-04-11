# dm — Product Status

## What Is It

Claude Code skill that runs Virgil's LinkedIn DM workflow via Kondo. Pulls unread + reminder threads, scores CHARM stage, generates 3 reply options per person, sets drafts and reminders in Kondo, logs CRM notes. Runs as `/dm` in the harness.

**Location:** `~/.claude/skills/dm/`

## Active Spec — v3.1 Conversion-Gap Model (2026-04-11)

**Current version:** v3.1
**Previous pivot:** 2026-04-10 — Sucana Tool → AI Sales Systems for Founders (now superseded by v3.1)
**v3.1 plan file:** `~/.claude/plans/floating-hopping-koala.md`
**Prior plan file:** `~/.claude/plans/moonlit-prancing-pumpkin.md`

### Why v3.1 exists

The 2026-04-10 pivot introduced a sales-team requirement as an ICP gate ("non-negotiable, if you don't have a sales team"). v3.1 corrects that bug. Virgil's lived data — **every past win was a solo operator or founder without a dedicated closer team** — contradicts a hard sales-team gate. Tina (1M YouTube, premium offer, no sales team, small team of editor + VA, built the system → started selling) is the canonical archetype, not an exception. The old v3 filter would have killed her.

v3.1 keeps everything from the 2026-04-10 pivot **except** the sales-team gate. It replaces it with:
- **Conversion gap** as the universal ICP gate ("leads come in, sales don't come out")
- **Small team** as a minimum qualifier — the founder is not doing everything alone; **any helper counts** (VA, ops, assistant, editor, contractor, freelancer, agency, part-time)
- **Sales team** demoted to a context variable — Branch B pain questions instead of Branch A
- **$1K offer floor** (dropped from $2K) because $1K implies ~$20–30K+ monthly turnover, making the $2K/mo retainer math work
- **Stage D (Diagnose)** as a mandatory new stage between A and R — name the leak before asking for anything
- **Surgeon's Pivot rule** — if pain hasn't landed by Message 4 of a prospect thread, force the System Reset

## Active Pivot — Sucana Tool → AI Sales Systems for Founders

**Started:** 2026-04-10
**Plan file:** `~/.claude/plans/moonlit-prancing-pumpkin.md`

### Why this rewrite is happening

The old skill was 100% pitched at PPC agencies with **Sucana the SaaS tool** as the offer. 6-month data: ~99 openers → ~34 replies (34%) → ~12 past small talk (12%) → 3 pitched → **0 calls booked via DM**. The motion didn't convert. Sucana the tool is dead as of 2026-04-10.

The new motion (decided 2026-04-06 + 2026-04-09 with Victor, confirmed by Virgil 2026-04-10):

> **"We sell AI sales systems for founders who sell premium offers."**

- **Service, not SaaS.** Done-for-you AI automation built by Virgil + Victor + Vinod.
- **Lead magnet:** free automation build, no strings.
- **Pricing:** $500 setup → $2K/month retainer.
- **ICP:** founders/CEOs of service-based digital businesses, selling $2K+ offers, with an existing sales team (setter + closer).
- **Trust:** $70M+ in client funnel sales (Victor's agency) + Sukana Labs build experience (the SaaS work proves automation chops).
- **Channel:** LinkedIn DM is still the main channel. Vinod's action item from 2026-04-09 confirms it.

### Source transcripts

| Date | ID | Participants | Why it matters |
|---|---|---|---|
| 2026-04-09 | `01KNR2E57BYV1CRP26Q43PSNET` | Virgil + Victor (solo) | ICP refinement, $500/$2K offer structure, "high ticket" word ban |
| 2026-04-06 | `01KNH4GR39KKTRGQ5M00CQ3KT5` | Virgil + Victor + Vinod | Pivot decision, $70M trust signal, "free funnel automations" lead magnet, Vinod's "we handle" reframe |

## What's Dying in SKILL.md

| Section | Why it dies |
|---|---|
| IDENTITY RULE — "Sucana = AI analytics platform for PPC agencies" | Sucana the tool is dead |
| CHARM Stage R — "Want to give Sucana a spin? Read-only access" | No more SaaS beta. Replaced by free automation build offer |
| CHARM Stage H bridge — "How many clients?" / "What's your reporting setup?" | Wrong qualifying questions for new ICP |
| CHARM Stage A ladder — service → clients → reporting → time sink → tools | Replaced by premium-offer → sales-team → lead-drop → automation-tried |
| ICP FILTER — skip consultants, coaches, mindset, SEO-only | Inverts. Coaches/consultants/services with sales teams selling $2K+ are now **inside** ICP |
| Top 3 objections (data security in particular) | Sucana-tool specific, no longer relevant |
| White-label angle (floated for Klaas earlier today) | Killed by Virgil decision 2026-04-10 |

## What's Being Added

| New element | Source |
|---|---|
| New IDENTITY: 3-founder team selling AI sales systems for founders with premium offers | Virgil 2026-04-10 + Apr 6/9 transcripts |
| ICP filter — 3 non-negotiables: premium offer ($2K+) + sales team + service-based | Virgil Apr 9 transcript |
| New Stage A ladder: premium offer? → sales team? → lead drop point? → automation tried? | Distilled from pain triggers |
| New Stage R offer: free automation build (no strings) | Virgil Apr 6 transcript |
| Vinod's voice reframe: "we **handle** the automation" not "we **automate**" | Vinod Apr 6 |
| Trust signal: $70M+ funnel sales (Victor) + Sukana Labs build chops | Victor Apr 6 |
| Word ban: "high ticket" → use "premium offer" / "$2K+ offer" | Virgil Apr 9 |

## Architecture

```
dm/
├── SKILL.md          (the entire skill — single file, no progressive disclosure split)
└── product.md        (this file — pivot context, phase changelog, decisions)
```

Note: unlike `linkedin-writer`, the dm skill is currently a single-file skill. Progressive disclosure split is **not** part of this pivot — the pivot is content-only. A future restructure may split SKILL.md into config/charm/voice files, but that's a separate piece of work and not in scope today.

## Phase Status (2026-04-10 pivot)

| Phase | Description | Status |
|---|---|---|
| 0 | Plan written + approved | Done |
| 1 | Create product.md baseline | Done |
| 2 | Replace IDENTITY RULE block | Done |
| 3 | Replace ICP FILTER block | Done |
| 4 | Replace CHARM Stage A ladder + Stage H bridge | Done |
| 5 | Replace CHARM Stage R offer | Done |
| 6 | Update VOICE RULES (ban "high ticket", add Vinod reframe) | Done |
| 7 | Re-label PIPELINE TREND DATA as pre-pivot baseline | Done |
| 8 | Update QUICK START intro block | Done |
| Kakiyo | Prospect score + objection map + angle tracking | Done |
| Verify | 4-agent Ralph test (20+10+16+10 checks) | Done — 3 minor fixes applied |
| 9 | Wipe + redo 3 live Kondo drafts (Benton, Jennifer, Klaas) | Pending |
| 10 | Decide on 14 stale Kondo reminders | Pending |

## Pre-Pivot Baseline (captured 2026-04-10 before any edits)

| Metric | Value |
|---|---|
| `SKILL.md` line count | **346** |
| `SKILL.md` byte count | **15868** |
| `product.md` exists | No (created in this Phase 1) |
| Hard guardrail block in SKILL.md | Yes (added earlier today after the 14-draft incident) |
| Auto-advance rule (presentation only) | Yes |
| `IDENTITY RULE` block | Sucana-tool era, lines ~182–186 |
| `ICP FILTER` block | PPC-only, lines ~227–235 |
| `CHARM Stage R` block | Sucana beta + read-only, lines ~211–219 |
| Pipeline data block | 34/12/0% Sucana funnel, lines ~237–257 |

## Decisions Locked Before Phase 1

| Date | Decision | Why |
|---|---|---|
| 2026-04-10 | Keep pre-pivot pipeline data as historical baseline | Useful as benchmark to measure post-pivot performance against; doesn't influence new openers |
| 2026-04-10 | Use both $70M and Sukana Labs as trust signals in Stage R | Two angles of authority; Sukana Labs proves build chops, $70M proves funnel chops |
| 2026-04-10 | Kill the white-label angle entirely | Pre-pivot idea, doesn't fit founder/premium-offer ICP |
| 2026-04-10 | Wipe + redo the 3 live Kondo drafts in Phase 9 | Cleanest way to avoid sending pre-pivot pitches |

## Changelog

### Phase 1 — 2026-04-10 — Create product.md baseline

- Created `~/.claude/skills/dm/product.md` (this file).
- Captured pre-pivot baseline of `SKILL.md`: **346 lines, 15868 bytes**.
- Locked 4 scope decisions (above).
- No edits to `SKILL.md` yet.

**Status:** Phase 1 complete.

### Phase 2 — 2026-04-10 — Replace IDENTITY RULE block

**File:** `~/.claude/skills/dm/SKILL.md`
**Location:** `## IDENTITY RULE` block (was lines 199–203 post-guardrail edit, pre-pivot line range ~182–186 in plan)

**Removed (old, pre-pivot):**
```
Virgil is the founder of Sucana — an AI analytics platform for lead gen PPC agencies.
He is NOT the ads expert. Victor (co-founder) runs the actual agency. Virgil speaks
as a founder building for the space.

Never position Virgil as a PPC specialist or ads guru.
```

**Added (new, post-pivot):** Full rewrite centered on:
- **Lead positioning sentence:** "We sell AI sales systems for founders who sell premium offers." (Virgil 2026-04-10)
- **3-founder team introduction:** Virgil (marketing/positioning/DM), Victor (ads + funnel, owns $70M+ track record), Vinod (builder)
- **What we sell:** Free automation build (entry) → $500 setup → $2K/month retainer. (Virgil 2026-04-09 transcript)
- **Who we sell to:** Founders/CEOs of service-based digital businesses selling $2K+ offers with existing sales team. (Virgil + Victor 2026-04-09)
- **Trust signals:** Victor's $70M+ in client funnel sales (Victor 2026-04-06) + Sukana Labs build experience as proof of automation chops (per locked decision 2026-04-10)
- **Explicit bans:** No "Sucana the tool" positioning, no "PPC specialist" framing, no "SaaS beta" language

**Transcript citations:**
- Virgil 2026-04-09 (`01KNR2E57BYV1CRP26Q43PSNET`): "I'm trying to refine the positioning to what we discussed on Monday" / "one education or service based digital businesses" / "you need to have a high ticket offer" / "$500 bucks setup calls" / "2K monthly retainers"
- Virgil + Vinod + Victor 2026-04-06 (`01KNH4GR39KKTRGQ5M00CQ3KT5`): "We are not building Sukana the tool for PPC agencies only" / "we have generated over 70 million for our clients with funnels" / "our value proposition starts at 2,000 a month"
- Virgil 2026-04-10 session: "We sell AI sales systems for founders who sell premium offers"

**Status:** Phase 2 complete. SKILL.md edited once, surgically. No other sections touched.

### Phase 3 — 2026-04-10 — Replace ICP FILTER block

**File:** `~/.claude/skills/dm/SKILL.md`
**Location:** `## ICP FILTER (Apply BEFORE Stage C)` block

**Removed (old, pre-pivot — PPC-operator filter):**
```
Before sending ANY opener, verify the person actually manages ad accounts or
runs a PPC/lead gen agency. Skip if they are:
- Consultants (messaging, positioning, branding) who don't run ads themselves
- Coaches, mindset people, non-PPC founders
- Engagement pod people just swapping likes
- Amazon-only, SEO-only, or non-paid-media operators
```

**Added (new, post-pivot — founder-with-premium-offer-and-sales-team filter):**
- **3 non-negotiables** (all must be true): premium offer $2K+ / has sales team (setter + closer) / service-based digital business
- **Who's IN** list — coaches, consultants, agencies, course creators, mastermind operators — explicitly inverted from the old filter
- **Who's OUT** list — solo operators without sales team, under-$2K, physical product, pod people
- **Why this inverted** note — explicit explanation that the old filter was Sucana-tool specific; the new service targets the exact crowd the old filter skipped
- **Pain signals to listen for** — sales team language, cohort/retainer/CRM chaos language, scaling-stuck complaints
- **Historical note** — 40% non-ICP rate from old era, expect pipeline churn during pivot

**Transcript citations:**
- Virgil 2026-04-09 (`01KNR2E57BYV1CRP26Q43PSNET`):
  - "service based digital businesses"
  - "CEOs or C levels in companies who run the whole thing"
  - "you need to have a high ticket offer"
  - "non negotiable, if you don't have a sales team"
  - "75% are done-for-you digital services, 30 to 45% have a setter and closer"
- Victor 2026-04-09 (`01KNR2E57BYV1CRP26Q43PSNET`):
  - "you hire the closer or the sales team and you don't know what's happening"
  - "they throw ropes to each other, but you don't, you're not selling"

**Status:** Phase 3 complete. SKILL.md edited once, surgically. No other sections touched.

### Phase 4 — 2026-04-10 — Replace CHARM Stage A ladder + Stage H bridge questions

**File:** `~/.claude/skills/dm/SKILL.md`
**Location:** `### Stage H — Humanize` + `### Stage A — Analyze` blocks (single contiguous edit)

**Removed (old, Sucana-tool qualifying):**
- Stage H bridge questions: "How many clients are you managing right now?" / "What's your reporting setup look like?"
- Stage A ladder: "service/who they help → how many clients → how they handle reporting → biggest time sink → tools or manual?"
- Stage A rule: "No pitch unless they ask about Sucana first"

**Added (new, founder/sales-team qualifying):**

**New Stage H bridge questions** (3 options, all map to the 3 ICP non-negotiables):
1. "Are you selling a premium offer right now, or mostly low-ticket stuff?" → price point
2. "Do you run your own sales team, or are you still closing deals yourself?" → sales team
3. "What's the main thing you're selling these days — a service, a program, a cohort?" → service-based

**New Stage A ladder** (5-step, ask ONE at a time):
1. **Offer price point** — confirm $2K+
2. **Sales team structure** — confirm setter + closer, not solo founder
3. **Where leads drop** — find the specific broken handoff (booking / show-up / call / follow-up)
4. **Automation history** — have they tried to automate, how did it go? Listen for "Zapier duct tape" or "manual"
5. **Volume confirmation** (optional) — enough volume that $2K/month retainer makes ROI sense

**New Stage A rules:**
- Frame as curiosity, never interrogation
- Never pitch until prospect describes a broken handoff in their own words
- Never mention Sucana / SaaS / "a tool" — we sell a service
- If asked what Virgil does, short answer: "Victor and I build AI automation for founders with sales teams — the stuff that glues the funnel together so leads don't drop between setters and closers"
- The "description of broken handoff in their own words" IS the gate to Stage R

**Transcript citations:**
- Virgil 2026-04-09: the 3 non-negotiables (price point + sales team + service)
- Victor 2026-04-09: "you hire the closer or the sales team and you don't know what's happening" / "they throw ropes to each other, but you don't, you're not selling"
- Vinod/Virgil/Victor 2026-04-06: "once we have fixed their sales cycle, their Leads all by getting insights what's happening, making sure that the leads land in the agendas of the closers, all these simple automations"

**Status:** Phase 4 complete. SKILL.md edited once, surgically. No other sections touched.

### Phase 5 — 2026-04-10 — Replace CHARM Stage R offer

**File:** `~/.claude/skills/dm/SKILL.md`
**Location:** `### Stage R — Request` block

**Removed (old, Sucana beta pitch):**
- Goal: "Get them using Sucana. Offer the tool first, call second."
- Primary ask: "Want to give Sucana a spin? No strings attached."
- Secondary ask: "15 minutes, quick call, would love your take"
- Pre-empt block: "read-only access, we only look at data, never make changes" (Sucana-tool specific, killed)

**Added (new, free automation build):**
- New goal: Get them to accept a **free automation build**, not a call/demo/login
- Offer script: "Pick the one thing in your sales flow that's bleeding the most. Victor and I will build that automation for you. Free. No strings. You keep the build either way."
- 6-move Stage R structure:
  1. Summarize the broken handoff in their own words (gate: no Stage A pain = go back to A)
  2. Bridge with ONE trust angle (either $70M Victor OR Sukana Labs build chops — per locked decision, both are available, pick one per message)
  3. Make the free automation build offer
  4. Path to yes: 15-min intake (framed as build intake, NOT a sales call)
  5. Easy out
  6. Pre-empt objections — kill "data security" (Sucana tool era), add "too busy" counter using Vinod's "we handle it" reframe
- Explicit "what NEVER to do" list: no Sucana references, no pricing in DM, no naked "quick call" ask, no "high ticket"

**Locked decisions reflected in this phase:**
- Decision (2026-04-10): Use both $70M and Sukana Labs as trust signals → both present in Stage R, with instruction to pick one per message
- Decision (2026-04-10): Kill white-label angle → not referenced anywhere in new Stage R

**Transcript citations:**
- Virgil 2026-04-06 (`01KNH4GR39KKTRGQ5M00CQ3KT5`):
  - "We're building a free funnel automations a few farms to stress that what we do... one free build no catch one in so he goes in a stage of selling"
  - "our value proposition starts at 2,000 a month because that's the surface"
  - "30 clients on a 2K retainer" → $60K MRR target
- Victor 2026-04-06:
  - "we have generated over 70 million for our clients with funnels"
- Vinod 2026-04-06:
  - "instead of saying we will automate something for you, say we will handle the automation for you. We will do the job."
- Virgil 2026-04-09 (`01KNR2E57BYV1CRP26Q43PSNET`):
  - "$500 bucks setup calls to set up that automation for you"
  - "We are going to build one simple automation with what we decide upon. 2K"
  - "this is literally what the AI automation guys are doing"

**Status:** Phase 5 complete. SKILL.md edited once, surgically. No other sections touched.

### Phase 6 — 2026-04-10 — Update VOICE RULES

**File:** `~/.claude/skills/dm/SKILL.md`
**Location:** `## VOICE RULES (Always Active)` block

**Added (new banned phrases, pivot-specific):**
- "High ticket" → use "premium offer" / "$2K+ offer". Virgil Apr 9: "The word high ticket is often associated with guys who have no clue what they're doing."
- "Sucana" as product/tool name → dead brand in sales context
- "SaaS / platform / tool / beta / trial" → we sell a service. Use "we build", "we handle", "we set up"
- "We automate X for you" → Vinod's reframe: "we **handle** the automation"

**Modified:** "Don't sound like" extended with: "a SaaS salesman, a high ticket closer bro, or someone pitching a tool demo"

**Unchanged:** Original banned words, banned patterns, "Sound like" calibration, format rule.

**Status:** Phase 6 complete.

### Phase 7 — 2026-04-10 — Re-label PIPELINE TREND DATA

**File:** `~/.claude/skills/dm/SKILL.md`

**Changed:** Split into two subsections:
1. **PRE-PIVOT BASELINE** — old funnel (99/34/12/3/0), with explicit "kept as benchmark, not active guidance" disclaimer. Sorted into "still carries forward" (Dutch priority, Bali, Victor trust, no naked call asks, no generic openers) vs "dead" (read-only, PPC filter, data security)
2. **POST-PIVOT TARGETS** — $60K MRR target (30 × $2K), pricing ladder, 3 expected objection placeholders, empty metric tracker to fill as data arrives. No fake numbers.

**Status:** Phase 7 complete.

### Phase 8 — 2026-04-10 — Update QUICK START intro block

**File:** `~/.claude/skills/dm/SKILL.md`
**Location:** The ``` DM SESSION READY ``` code block shown on every /dm run

**Replaced entirely.** New block includes:
- Header: "AI SALES SYSTEMS FOR FOUNDERS" + one-liner + pricing ladder + MRR target
- CHARM stages rewritten: H bridges to "premium offer? / sales team?", A ladder to new qualifying, R = free automation build (not Sucana spin)
- ICP summary: 3 non-negotiables inline
- Rules: $70M trust signal, Bali lean-in, never "quick call" / "high ticket" / "Sucana" / "SaaS" / "we automate" — "we handle" instead
- Also fixed comment flow reference: "no Sucana" → "no product names"

**Status:** Phase 8 complete. All 7 content phases of SKILL.md done.

### Post-Phase — 2026-04-10 — Kakiyo-inspired features + breakup flow + scoring upgrade

**Additions to SKILL.md (3 batches):**

**Batch 1 — Kakiyo features (from competitive research):**
- Prospect scoring system (initially 1-5, later upgraded to 0-100)
- Objection → Response map (5 placeholder entries, marked untested)
- Angle tracking on every option (10 example angle tags, logged to CRM on pick)

**Batch 2 — Breakup flow (from Kristof Bardos incident):**
- Added breakup flow to content type rules: NO → breakup message → archive → 90-day reminder
- Breakup message = short, clean, no pitch, no angle. "Door is open."
- 90-day reminder: check organic re-engagement only. If no re-engagement → dead forever.
- Rule added to both SKILL.md and CLAUDE.md
- Memory saved: `feedback_no_means_no.md`
- Incident: I generated 3 reply options for Kristof who explicitly said "not ready to buy or check." Virgil caught it. Root cause: I read the data but ignored the clear "no." Fix: rule now requires reading last message BEFORE generating any options.

**Batch 3 — Scoring upgrade (matching Kakiyo's 0-100 dynamic system):**
- Replaced 1-5 static score with 0-100 dynamic score
- Score updates after every message, not just at first presentation
- Data sources expanded: profile + posts + every reply + CRM notes + full thread (LLM analysis, not checkbox)
- Scoring rubric: ICP signals (+20 each for offer/team, +10 service-based), pain signals (+15/+5), engagement signals (+5 each), trust shortcuts (+5), negative signals (-100 no, -30 missing ICP, -50 vendors)
- Thresholds: 70+ priority, 40-69 warm, 20-39 cold, <20 park, 0 dead
- Dynamic re-scoring logged in CRM notes: `Score: XX → YY (reason)`
- Drop-below-20 flag added: "Score dropped — continue or park?"
- All inbox table and reply presentation formats updated from `Score [X/5]` to `Score [XX/100]`

**Bridge question refinement (earlier, pre-Kakiyo):**
- Stage H bridge questions rewritten to pain-first: no mention of sales team, closers, setters, AI
- Rule: that language only comes up AFTER they mention it or it's in their bio
- Quick Start CHARM summary updated to match

**Status:** All post-phase additions complete. SKILL.md fully pivoted + enhanced.

---

## v3.1 — 2026-04-11 — Conversion-Gap Rewrite

**Plan file:** `~/.claude/plans/floating-hopping-koala.md`
**Canonical ICP doc:** `/Users/virgilbrewster/My Drive/Virgil Brain/Projects/sucana/Brand/icp.md`
**Service model doc:** `/Users/virgilbrewster/My Drive/Virgil Brain/Projects/sucana/Products/service-model.md`

### The bug v3.1 fixes

The 2026-04-10 pivot (Phases 0–8 above) introduced **sales team** as a hard ICP non-negotiable. This was wrong:

- **None of Virgil's past wins had a dedicated sales team.** Tina (1M YouTube, premium offer, no sales team, small team of helpers, no conversion system → built the system → started selling) is the canonical ICP, not an edge case.
- **Virgil's LinkedIn positioning explicitly says the pain is the conversion gap, not the team gap:** *"Leads come in, but where are your sales? Somewhere between the click and the sale, everything falls apart."*
- **Sucana hasn't solved the closer / sales-team domain yet.** That's future work. The current lane is founders with premium offers and leaky conversion. If a team'd lead shows up, we fix around the team (pre-call and post-call layers), not the internal setter↔closer workflow.

### Deltas vs the 2026-04-10 pivot

| Area | v3 (pre-v3.1) | v3.1 |
|---|---|---|
| ICP gate | Sales team required | Conversion gap + small team (1–2 helpers, any type) |
| Offer floor | $2K+ | $1K+ |
| Solo scoring | Solo founder = −30 auto-dead | Pure lone wolf (zero helpers) = −40 hard disqualifier; small-team solos = +20 |
| Pain questions | Team-centric (setter/closer/handoff) | Branch A (small team) + Branch B (team'd) |
| Stage R offer | Free automation build | Free diagnostic (format TBD in live test) |
| Stage count | C H A R M | C H A **D** R M (Diagnose = new mandatory stage) |
| Pain-by-Message-4 | Soft "bridge faster" guidance | Hard Surgeon's Pivot rule with System Reset message |
| Rules | Scattered across sections | 11 Non-Negotiables consolidated into one block |
| Pre-send | No explicit gate | Context Amnesia Check + Status Audit + Surgeon's Pivot Check + Stage-D Gate Check |
| Context Amnesia | Implicit | Explicit — blocks the "Darren mistake" of resetting rich threads |
| Price dodge | "Let's start with the build first, no commitment" | Direct answer (Rule 6): "$500 setup + $2K/mo, first diagnostic free, custom scope on top" |
| "No sales team" objection | Not addressed | Explicit counter: "Doesn't matter. The system works at any point in the sales cycle." |

### Files touched in v3.1

**Created:**
- `/Users/virgilbrewster/My Drive/Virgil Brain/Projects/sucana/Brand/icp.md` — canonical v3.1 ICP (replaces stale icp.md)
- `/Users/virgilbrewster/My Drive/Virgil Brain/Projects/sucana/Products/service-model.md` — offer ladder, direct price language, diagnostic format as open test, closer-workflow scoped out

**Archived:**
- `/Users/virgilbrewster/My Drive/Virgil Brain/Projects/sucana/Brand/icp-archived-sucana-tool-era.md` — old v3 ICP

**Updated in `~/.claude/skills/dm/SKILL.md` (surgical edits, no full rewrite):**
- QUICK START — CHADRM stages, 4 non-negotiables, lone-wolf disqualifier
- IDENTITY RULE — "Who we sell to" paragraph rewritten for conversion-gap ICP
- Stage A — team classifier (infer from profile first), branched Branch A / Branch B pain questions, $1K offer floor
- **Stage D (Diagnose) — NEW** — mandatory one-sentence leak naming between A and R
- Stage R — free diagnostic + permission-first + direct price language + "no sales team" objection counter
- **Surgeon's Pivot hard rule — NEW** — forces System Reset if pain hasn't landed by Message 4
- ICP FILTER — 4 non-negotiables (offer / attention / conversion gap / small team), Tina rule, lone-wolf hard disqualifier
- PROSPECT SCORE rubric — all v3.1 fit / pain / negative signals updated
- **11 NON-NEGOTIABLE RULES — NEW** — consolidated block
- **PRE-SEND CHECKS — NEW** — Context Amnesia + Status Audit + Surgeon's Pivot + Stage-D Gate
- Stage detection rules — added D, added Stage-D gate language
- REMINDER DEFAULTS — added D (7 days)
- POST-PIVOT TARGETS — fixed stale "Free build (entry)" language
- OBJECTION → RESPONSE MAP — fixed price-dodge counter, added "no sales team" row

### Ralph test results (spec validation)

Ran 9 scripted tests against updated SKILL.md. 3 latent failures found and patched during the run:

| # | Test | Result |
|---|---|---|
| 1 | Tina (golden archetype) | PASS |
| 1b | Lone wolf | PASS |
| 2 | Marina (partner lane) | PASS |
| 3 | Darren (context amnesia) | PASS (after Context Amnesia Check added) |
| 4 | George (disqualifier respect) | PASS |
| 5 | High-ticket physical (luxury cars) | PASS |
| 6 | Low-ticket ecom | PASS |
| 7 | Pain-by-Message-4 | PASS (after Surgeon's Pivot hard rule added) |
| 8 | Price dodge | PASS (after Rule 6 + objection map patch) |
| 9 | Diagnostic format A/B | Deferred — live runtime test, not a spec check |

### Golden archetype

**Tina.** 1M+ YouTube viewers, premium offer, small team (editor + VA, no sales team), no conversion system → built the system → started selling. Any future ICP revision that would have killed her is wrong.

### Open items (runtime tests, not spec work)

1. **Diagnostic format** — call-based vs tool-based. Virgil decides during live testing. Both are valid Stage R asks for now; log which converts better.
2. **Closer / sales-team workflow** — out of scope until Sucana builds that domain expertise. Flagged in service-model.md.
3. **Pricing validation** — $500 + $2K/mo is the starting model; re-evaluate after 10–15 closes.

**Status:** v3.1 spec complete. Internally consistent. Passes all 8 binary Ralph tests. Ready for live Kondo use.
