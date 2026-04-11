# sucana-dm

Claude Code skill — **LinkedIn DM co-pilot** for Virgil Brewster (Sucana). v3.1 conversion-gap model.

Runs as `/dm` in the Claude Code harness. Pulls unread + reminder threads from Kondo, scores every prospect against a diagnosis-first ICP, generates 3 reply options per person, sets drafts + reminders in Kondo, and logs CRM notes.

## What makes v3.1 different

The DM skill went through two pivots. v3.1 is the current canonical version (2026-04-11).

**v1 (March 2026) — Relation Builder / Sucana tool era.** CHARM framework, pitched Sucana-the-SaaS to PPC agency owners. 6-month data: 0% call conversion in DMs. The motion didn't convert.

**v2/v3 (April 10, 2026) — AI sales systems pivot.** Killed Sucana-the-tool. New offer: free automation build → $500 setup → $2K/mo retainer. New ICP: founders selling $2K+ offers with a **sales team** (setter + closer). Better, but still wrong — the sales-team gate would have killed every one of Virgil's past wins.

**v3.1 (April 11, 2026) — conversion-gap model.** Replaces the sales-team gate with a **conversion gap + small team** gate.

- **Real gate:** founders with premium offers (≥$1K), real attention (leads/audience/traffic), a described gap between the click and the sale, and at least 1–2 people helping (VA, editor, ops, contractor — any helper counts; sales team NOT required).
- **Pure lone wolves disqualified.** Not "no sales team" — just "zero humans helping at all."
- **Added Stage D (Diagnose)** as a mandatory step between Analyze and Request. Name the leak in plain English before making any offer.
- **Added Surgeon's Pivot hard rule.** If no pain question has landed by Message 4 of a prospect thread, force a System Reset message.
- **New stage flow:** CHADRM (Capture → Humanize → Analyze → Diagnose → Request → Manifest).

## The canonical archetype: Tina

1M+ YouTube viewers. Premium offer. Small team (video editor + VA). **No sales team.** No conversion system. Built the system → started selling. The v2/v3 sales-team ICP would have killed her on Day 1. v3.1 catches her correctly: offer ✅, attention ✅, conversion gap ✅, small team ✅.

Any future ICP revision that would filter Tina out is broken.

## Files

| File | Purpose |
|---|---|
| `SKILL.md` | The full runtime skill — CHADRM framework, ICP filter, pain-question branches (Branch A = small team, Branch B = team'd), prospect scoring (0–100), Stage D diagnosis vocabulary, Stage R free-diagnostic offer, 11 non-negotiable rules, pre-send checks, breakup flow, voice rules |
| `product.md` | Phase changelog, pivot decisions, Ralph test results, open items |

## Install

This is a personal Claude Code skill — not meant to be pip-installed. To use:

```bash
git clone https://github.com/yours2grab/sucana-dm.git ~/.claude/skills/dm
```

Requires:
- Claude Code CLI
- Kondo MCP server (for LinkedIn inbox access)
- Virgil's Kondo account (this skill is hard-coded to his voice, ICP, and offer ladder)

## Not a SaaS. Not a template.

This repo exists as the **source of truth for Virgil's personal DM playbook**. The spec is open because transparency > secrecy — the pivot history, the 11 non-negotiables, and the Ralph test results are documented in full so future-Virgil (and collaborators) can trace every decision.

If you want to build your own DM skill from this: fork it, strip Virgil-specific voice rules, re-define your own ICP, re-run the Ralph tests against your own past threads. The framework (CHADRM + conversion-gap ICP + pre-send checks + three-prompt architecture) is the reusable part. Everything else is Virgil's lived data.

## The Lead

Weekly newsletter on AI-first sales systems for founders: [thelead.beehiiv.com](https://thelead.beehiiv.com)
