# Pain-First Outreach

A Claude Code skill for B2B outreach that turns pain signals into a live campaign — **LinkedIn-first**, no pitching.

**Default channel: LinkedIn.** Every session, the skill asks: *LinkedIn, email, or both?* It defaults to LinkedIn-only if unsure. LinkedIn connection requests are always drafted first and are hard-capped at **200 characters**, regardless of LinkedIn plan tier.

**Two things it does well:**

1. **Finds the right people** — searches and enriches leads via Lemlist, Clay, Apollo, and EnrichLayer. Accepts lead data at any completeness, from a list of company names to a full CSV.
2. **Writes pain-first discovery messages from VSI MCP** — pulls validated pain points, ICP, and objection patterns from VSI MCP, then writes sequences that validate the pain with prospects ("does this match what you're seeing?") rather than pitch a solution.

## Why "pain-first" and "discovery-only"

Most outreach pitches a product. This skill doesn't. Every message is a discovery message — it surfaces a real pain pattern from your customer calls (via VSI MCP) and asks the prospect to validate it. No case studies, no soft pitch, no "here's what we built." Late-step variation comes from sharper framings of the same pain or asking how they handle it today, never from a solution reveal.

## The 7 phases

```
1. Pull signals      VSI MCP → pain points, ICP, objections, proof
2. Find & enrich     Lemlist / Clay / Apollo + EnrichLayer
3. Score & tier      FITS framework → A / B / C tiers
4. Sample approval   user reviews top 10 leads + tier assignments
5. Write messages    Signal → Bridge → CTA, discovery-only
6. Sequence review   user edits or approves
7. Launch            create campaign in Lemlist via API
```

Users can enter at any phase: "I already have leads, just write the messages" → skip to Phase 5.

## Prerequisites

| Service | Type | Required | Setup |
|---------|------|----------|-------|
| VSI | MCP | Recommended (else paste signals manually) | Pre-configured per venture |
| Lemlist | REST API | Yes | Set `LEMLIST_API_KEY` in env. Auth: `--user ":$KEY"` |
| EnrichLayer | REST API | Yes | Set `ENRICHLAYER_API_KEY` in env |
| Clay / Apollo | Export or API | Optional | User provides export or API access |

## Install

Drop the `pain-first-outreach-skill/` folder into your Claude Code skills directory. The skill self-registers via its `SKILL.md` frontmatter.

Trigger phrases: `"build a campaign"`, `"create outreach"`, `"find leads for"`, `"launch in Lemlist"`, `"cold sequence"`, `"ABM campaign"`.

## Key concepts

**Pain-first messaging.** Trigger events (funding, hiring) tell you *who* to contact and *when* — they are never the message hook. Always lead with a pain pattern from VSI signals.

**Discovery, not pitch.** Every message validates the pain — it does not present, demo, or even soft-pitch a solution. CTAs stay in the validate-pain register: "compare notes", "hear your take", "is this landing for you?"

**Signal → Bridge → CTA.** Every outreach message follows this structure. Signal = specific pain observation. Bridge = connect to their situation without assuming. CTA = one low-friction discovery ask.

**LinkedIn-first, 200 chars max.** LinkedIn is the default and primary channel. Connection requests are hard-capped at 200 characters regardless of LinkedIn plan — the skill counts characters before shipping each request and trims the least specific phrase if over.

**FITS scoring.** Fit (30%) + Intent (45%) + Timing + Stakeholder → Tier A (4-step LinkedIn / 6-step both), Tier B (3-step LinkedIn / 4-step both), Tier C (2-step test).

## Repo layout

```
pain-first-outreach/
├── README.md
└── pain-first-outreach-skill/
    ├── SKILL.md
    ├── references/
    │   ├── vsi-integration.md      VSI MCP tool calls, signal types, filtering
    │   ├── lead-tools.md           Lemlist / Clay / Apollo / EnrichLayer details
    │   ├── message-frameworks.md   Signal→Bridge→CTA, channel rules, archetypes
    │   └── lemlist-campaigns.md    Lemlist MCP commands for launch
    └── evals/
        └── evals.json
```
