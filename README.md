# Pain-First Outreach

A Claude Code skill for **discovery and validation outreach**: turn pain signals into a live LinkedIn-first campaign that finds the right people to talk to, with no pitching.

Built for any stage: you can be exploring a space with no product yet, validating a concept, or testing whether the pain still resonates around an early MVP. The first message is always pain-led. Every message validates a pain pattern and asks the prospect to compare notes. The CTA is never "see how to reduce X by Y" or "want to see a demo", because even if a solution exists, leading with it breaks the pain frame and kills the reply rate.

**Default channel: LinkedIn.** Every session, the skill asks: *LinkedIn, email, or both?* It defaults to LinkedIn-only if unsure. LinkedIn connection requests are always drafted first and are hard-capped at **200 characters**, regardless of LinkedIn plan tier. Every first message addresses the prospect by name.

## Two target tiers in every campaign

1. **Primary: champions already hacking their own solution.** People building a workaround (spreadsheet, internal tool, repurposed product, manual process). Highest signal: they care enough to act.
2. **Secondary: pain-aware but not yet acting.** People who feel the pain in their seat but have not built anything around it. Larger pool, weaker signal.

The skill drafts two variants of every step (champion-hacker and pain-aware) and routes each lead to the right one based on enrichment.

**The skill does two things:**

1. **Finds the right leads**: sources and enriches contacts via EnrichLayer (cheap mode), or via Lemlist, Clay, and Apollo (extensive mode). Tags each lead `champion_hacker: true | false | unknown` so the message variant matches the contact. Accepts lead data at any completeness, from a list of company names to a full CSV.
2. **Writes pain-first discovery messages**: pulls validated pain points, ICP, and objection patterns from VSI MCP (or pasted notes), then writes Day-1 LinkedIn / email openers that validate the pain with prospects ("match what you're seeing?") rather than pitch a solution. First message only by default; full sequences on request.

Enter at either end: just messages, just leads, or the full flow.

## Cheap mode vs extensive mode

| Mode | Setup | Channel | Cost | When to use |
|------|-------|---------|------|-------------|
| **Cheap (default)** | EnrichLayer free credits only | Manual LinkedIn outreach | $0 | First campaign, validating the skill, founder-led research |
| **Extensive (on request)** | EnrichLayer + Lemlist + optionally Clay or Apollo | LinkedIn + email + WhatsApp, automated | ~$200-500/mo | Scaled outreach, multi-channel sequences, large prospect lists |

The skill defaults to cheap mode so first-time users can validate end-to-end without any paid subscription. Once it works, upgrade tools incrementally as bottlenecks appear (volume, automation, depth).

## Why "pain-first" and "discovery-only"

Most outreach pitches a product. This skill doesn't. Every message is a discovery message: it surfaces a real pain pattern from your customer calls (via VSI MCP) and asks the prospect to validate it. No case studies, no soft pitch, no benchmark, no "here's what we built." Late-step variation comes from new facets of the same root pain (cost, productivity, process, team friction), never from a solution reveal.

"Pain-first" is a topic rule, not a word-order rule. The message must be *about* the pain and nothing else, but it still opens with `Hi [Name],`.

## The 7 phases

```
1. Pull signals      VSI MCP -> pain points, hack patterns, ICP, objections
2. Find & enrich     Lemlist / Clay / Apollo + EnrichLayer, tag champion_hacker
3. Score & tier      FITS framework -> A / B / C tiers, +1 tier for hackers
4. Sample approval   user reviews top 10 leads + tier + variant assignment
5. Write messages    Signal -> Bridge -> CTA, discovery-only, two variants per step
6. Sequence review   user edits or approves
7. Launch            create campaign in Lemlist via API
```

Users can enter at any phase: "I already have leads, just write the messages" goes to Phase 5.

## Prerequisites

**Minimum for cheap mode (first campaign):**

| Service | Type | Required | Setup |
|---------|------|----------|-------|
| EnrichLayer | REST API or MCP | **Yes** | Sign up at `enrichlayer.com` (free credits on signup, enough for ~50-100 lookups). Set `ENRICHLAYER_API_KEY` in env. |
| VSI | MCP | Recommended (else paste signals manually) | Pre-configured per venture |

**Add for extensive mode (when scaling):**

| Service | Type | Required for | Setup |
|---------|------|--------------|-------|
| Lemlist | REST API | Automated multi-step sequences | Set `LEMLIST_API_KEY` in env. Auth: `--user ":$KEY"` |
| Clay | Export / webhook | Deep waterfall enrichment | User provides Clay table or webhook |
| Apollo | Export or API | High-volume prospecting | User provides Apollo export or API access |

## How to install

Skills run locally. Pasting this repo's URL into a Claude chat will **not** install it; you need to put the skill files where Claude can read them. Two surfaces, two methods.

### Option 1: Claude Code (CLI, VSCode extension, or desktop)

Skills live in `~/.claude/skills/<skill-name>/` and auto-register from their `SKILL.md` frontmatter.

```bash
# Clone the repo to a permanent location
git clone https://github.com/darko-web/pain-first-outreach.git ~/code/pain-first-outreach

# Symlink the skill folder into your Claude Code skills directory
mkdir -p ~/.claude/skills
ln -s ~/code/pain-first-outreach/pain-first-outreach-skill ~/.claude/skills/pain-first-outreach
```

Restart Claude Code. Verify the skill loaded by asking *"What skills do I have available?"*; `pain-first-outreach` should appear.

The symlink approach means future updates are a `git pull` away.

**Alternative (no symlink):** `cp -r pain-first-outreach-skill ~/.claude/skills/pain-first-outreach`. Simpler but you'll need to re-copy after each repo update.

### Option 2: Claude.ai chat (web or desktop)

Claude.ai supports **Custom Skills** uploaded as zip files via Settings -> Capabilities -> Skills (exact location may vary by plan / release).

```bash
git clone https://github.com/darko-web/pain-first-outreach.git
cd pain-first-outreach
zip -r pain-first-outreach.zip pain-first-outreach-skill
```

Upload `pain-first-outreach.zip` in Claude.ai's skill UI and enable it. The skill then activates on the same trigger phrases in any chat.

### Triggering the skill

Once installed, the skill activates automatically on phrases like:

`"build a campaign"`, `"create outreach"`, `"find leads for"`, `"launch in Lemlist"`, `"cold sequence"`, `"ABM campaign"`, `"validate this concept"`, `"test if the pain resonates"`, `"turn calls into outreach"`.

You can also invoke it directly with `/pain-first-outreach` (Claude Code) or by mentioning the skill name in chat.

### First-run setup

Before your first campaign, set the one required environment variable (cheap mode):

```bash
# In ~/.zshrc or ~/.bashrc
export ENRICHLAYER_API_KEY="your_key_here"  # free credits on signup at enrichlayer.com
```

Optional, for extensive mode:
```bash
export LEMLIST_API_KEY="your_key_here"      # only if you want automated sequences
```

VSI MCP, if you use it, is configured separately per venture.

## Key concepts

**Discovery and validation, not sales.** Every campaign is a first-touch probe to confirm the pain is real and find champions. No demo, no benchmark, no case study in any message, even if a product exists. The first touch leads with the prospect's pain, full stop.

**Pain-first messaging.** Trigger events (funding, hiring) tell you *who* to contact and *when*. They are never the message hook. Always lead with a pain pattern from VSI signals. Always address the prospect by name.

**Discovery, not pitch.** Every message validates the pain; it does not present, demo, or even soft-pitch a solution. CTAs stay in the validate-pain register: "compare notes", "hear your take", "how are you handling it today", "is this landing for you?"

**Two variants per step.** Champion-hacker variant for people who built a workaround; pain-aware variant for people who feel the pain but haven't acted. Both stay in research register.

**Signal -> Bridge -> CTA.** Every outreach message follows this structure. Signal = specific pain observation. Bridge = connect to their situation without assuming. CTA = one low-friction discovery ask.

**LinkedIn-first, 200 chars max.** LinkedIn is the default and primary channel. Connection requests are hard-capped at 200 characters regardless of LinkedIn plan; the skill counts characters before shipping each request and trims the least specific phrase if over.

**FITS scoring.** Fit (30%) + Intent (45%) + Timing + Stakeholder, mapped to Tier A (4-step LinkedIn / 6-step both), Tier B (3-step LinkedIn / 4-step both), Tier C (2-step test). Champion-hackers get a one-tier boost.

## Repo layout

```
pain-first-outreach/
├── README.md
└── pain-first-outreach-skill/
    ├── SKILL.md
    ├── references/
    │   ├── vsi-integration.md      VSI MCP tool calls, signal types, filtering
    │   ├── lead-tools.md           Lemlist / Clay / Apollo / EnrichLayer details
    │   ├── message-frameworks.md   Signal->Bridge->CTA, channel rules, two variants
    │   └── lemlist-campaigns.md    Lemlist MCP commands for launch
    └── evals/
        └── evals.json
```
