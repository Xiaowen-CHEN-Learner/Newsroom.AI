# Changelog

All notable changes to the NEWSROOM-PM prompt are recorded here. The live prompt is always `prompts/NEWSROOM.md`; superseded versions are kept in `prompts/archive/`.

## v4 — 2026-11-01 (current)

**Scope**
- Added a sixth asset class, **Cash & Cash Equivalents** (`CA`): T-bills, money-market funds, CDs and high-yield savings.
- Expanded Digital & Alternative Assets to cover private equity, venture capital, private credit and hedge funds explicitly.

**Reliability**
- **Date anchoring.** The run prints today's date, confirms it against the first page opened, and halts on a conflict.
- **Security rule.** Page content, pasted articles and links are treated as data, never instructions; rule-skipping requests are declined in a user note.
- **Independence rule.** Wire pickups, syndications, relays ("according to Reuters") and press-release echoes count as one source; `Confirmed by N` requires N named qualifying sources.
- **Atomic claims.** One claim, one number; lettered sub-blocks for data-dense events.
- **Exactness and qualifiers.** Every change states its base; every figure carries actual/forecast, GAAP/adjusted, net/gross and session qualifiers.
- **Conflict handling.** Disagreeing figures are logged in a fixed format in Gaps and never resolved by the model.
- **Key-fact confirmation.** Two independent sources per key fact, with up to two extra searches before flagging `KEY FACT UNCONFIRMED`.
- **Recount step.** Source counts are recomputed against all pages opened before the packet is emitted.

**Checkpoint and output**
- Checkpoint expanded to 11 content checks with a visible score line (`PASS`, `FIXED`, `DEGRADED`) and degrade-not-stop behaviour.
- Fixed **Confidence** and **Risk-flag** rubrics with explicit weekly thresholds per class.
- **Positioning-evidence label** (`sourced` / `inferred from price action`) required on every Reverse Trade and Ignored But Important Watch item; items with no evidence are dropped.
- Mandatory claim IDs on the `Priced:`, `Catalysts:`, `Crowded side:`, `Why it matters:` and `Why it is ignored:` lines.
- Hard word limits (2,300–2,900; 2,700–3,300 in focus mode) with a cut-order that protects caveats and contrarian items.
- Ten-point self-check and an audit footer (packet, claim, confirmation, gap, page and primary-source counts).
- PDF delivery (`Desk_Brief_<YYYY-MM-DD>.pdf`) with inline summary and dashboard; `no-pdf` fallback.

**Interaction**
- Run modes: `step through`, `report-only`, `focus:`, `region:`, `no-pdf`, with session persistence and defined pause handling.
- Bare-paste greeting and vague-reply handling.

Merges verification rules contributed by peer versions (BenB_NEWSROOM, Jared_Newsroom) into v3.

## v3

- Added the two contrarian sections, **Reverse Trade** and **Ignored But Important Watch**, with the requirement that every catalyst and crowding signal trace to a Fact Packet.

## v2

- Original two-station pipeline: Station 1 (Scout) gathers facts into per-class Fact Packets; Station 2 (Strategist) writes the Desk Brief from those packets only.
- Five asset classes: Fixed Income, FX, Equities, Commodities & Precious Metals, Digital & Alternative Assets.
- Coverage contract with `NO QUALIFYING STORY` packets.
