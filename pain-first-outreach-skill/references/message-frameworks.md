# Message Frameworks & Channel Rules

## Context reminder: discovery and validation, not sales

Every message this skill produces is a discovery or validation probe, not a soft pitch. No case studies. No benchmarks. No "see how we can." The CTA always asks the prospect to compare notes, share how they handle the pain today, or react to a pattern.

This rule holds whether the user has nothing built yet, a concept on paper, a prototype, or an early MVP. Even if a product exists, the first message never leads with it, because the goal of first-touch is to validate that the pain is real and the prospect cares, not to introduce a fix. If a draft message could be read as implying we have a solution, rewrite it.

## Two target tiers, two message variants

Every step gets drafted in two variants:

- **Champion-hacker variant**: speaks to people already building a workaround. Validates that the hack pattern is common, asks how they built it, asks where it falls over.
- **Pain-aware variant**: speaks to people who feel the pain but have not acted. Validates that the pain exists in their seat, asks how they manage today.

Tag each lead in Phase 2 with `champion_hacker: true | false | unknown`. Route true to the champion-hacker variant; false and unknown to the pain-aware variant.

## Channel order: LinkedIn first

LinkedIn is the **default and primary** channel. Always draft the LinkedIn connection request first, even when the user has also asked for email. Connection requests are hard-capped at **200 characters** regardless of LinkedIn plan tier.

If the user picked email-only at session start, skip LinkedIn entirely. If they picked LinkedIn or both, LinkedIn leads the sequence.

## Signal -> Bridge -> CTA

Every message follows this structure regardless of channel. Every first message addresses the prospect by name.

**Opener pattern:** `Hi [Name], [signal]. [bridge]. [CTA]`

**Signal**: open with a pain pattern from VSI signals. This is the most important rule. Trigger events (funding, hiring, launches) tell you *who* to contact and *when*. They are never the hook.

Sources for the Signal opener:
- A pattern across calls: "We've been hearing from a lot of [persona] that X is becoming a real blocker."
- A tension that keeps surfacing: "The question that keeps coming up is..."
- A shared moment of anxiety: "Most [persona] at this stage are wrestling with..."
- A hack pattern (champion-hacker variant only): "Most [persona] I talk to end up building their own [thing] in [tool] because [reason]."

Carry verbatim numbers from VSI signals when they exist. "Loses two workdays per week" beats "loses time." Never fabricate numbers.

**Step 1 portability test:** Could you send this message to someone who *hasn't* had the trigger event? If yes, the pain is strong. If no, you've made the trigger the hook. Fix it.

**Bridge**: connect the pain to their specific situation without assuming.
- "Given you're at [stage], I'd guess..."
- "For teams in [context], this usually shows up as..."
- Champion-hacker bridge: "Most folks I talk to have a spreadsheet doing this and it falls over around [scale]."
- Never: "I'm sure you're experiencing this too" (presumptuous).

**CTA**: one ask. Low friction. Easy to say yes or no. Always discovery-shaped: validate the pain, never sell the solution.

**Sound human, never shorthand.** Every closing question must pass two tests:
1. *Say-it-out-loud test:* would a real person actually say this in conversation? If it reads like a chat-bot survey prompt, rewrite.
2. *Clear-subject test:* does the question have an unambiguous noun it's asking about? Orphan pronouns ("yours", "it", "that") with vague antecedents fail.

**Good (conversational, full clauses):**
- "Match what you're seeing?"
- "Familiar pattern, or different on your end?"
- "How does it actually play out on your end?"
- "Where does that start to break for you?"
- "Curious how it plays out for you."
- "Does that line up with how it feels day-to-day?"
- "Any of that landing, or wide of the mark?"
- "Worth 15 mins to compare notes?"
- "How are you handling it today?"

**Better still, "ask for advice" framing:**
- "We're trying to learn what people in your seat are actually doing about this. Mind sharing a few notes?"
- "Would value your read on this if you have 10 mins."

This flips the dynamic from "let me talk to you" to "I want to learn from you" and is especially strong for discovery and validation outreach.

**Banned (AI shorthand, robotic):**
- "Match yours?"
- "Sound familiar?"
- "Make sense?"
- "Resonate?"
- "Land?"
- "Track?"
- "Worth a chat?"

**Banned (solution-mode):**
- "Would you be open to a 30-minute exploratory conversation?"
- "Want to see a demo?"
- "Open to a pilot?"
- "See how to reduce X by Y%"

If trimming to fit 200 chars forces a shorthand CTA, retrim somewhere else first. The closing question is the handshake; it has to feel like one human talking to another.

## Late-step variation: same root pain, different facet

Across a sequence, every step is about the *same root pain*, but each step hits a different *facet* of it:

- **Financial facet**: cost, lost revenue, wasted spend.
- **Productivity facet**: time, throughput, capacity.
- **Process facet**: workflow breaks, handoff failures, manual stitching.
- **Team facet**: morale, turnover, role confusion, escalation patterns.

Pick a different facet for each follow-up. This gives the prospect a new reason to reply without ever introducing a solution.

## Specificity rule

Name the exact mechanic, not the category. "Streamline your data integration process" is weak. "The HRIS-to-LinkedIn skills mismatch nobody trusts" is strong. Use the role-specific language from your VSI signals; reading like a generic vendor kills reply rates.

---

## Email rules

**Subject lines:**
- Under 7 words.
- Two shapes: pain-as-question (`"Is onboarding still a 60-day slog?"`) or pain-as-statement (`"Most COOs can't see their own skills bench"`).
- Curiosity or specificity, not cleverness.
- A/B test 2 variants in Lemlist.

**Body, Step 1 (cold opener):**
- Opens with the prospect's name.
- 3-5 sentences max.
- No bullet points (reads as broadcast).
- No links (or one max).
- No product mention, no pitch, no benchmark.
- Sign off with just your name.

```
Hi [Name],

[Signal: 1 sentence, specific pain, verbatim VSI numbers if available]

[Bridge: 1-2 sentences connecting to their world, optionally referencing the hack pattern for champion-hacker variant]

[CTA: 1 sentence, research-shaped, low friction]

[Your name]
```

**Step 3+ (new facet):**
```
Hi [Name],

[Callback to step 1, never "just following up"]

[New facet: financial, productivity, process, or team angle on the same root pain. Or a different persona's quote on the same pain. Never a case study or product proof.]

[CTA: still discovery, still research register]
```

**Breakup email (final step):**
```
Hi [Name],

[Acknowledge silence without guilt-tripping]

[One last validation question, brief, still about the pain]

[Exit: "Happy to reconnect if timing changes."]
```

---

## LinkedIn rules

**Connection request character limits:**

Hard rule: 200 characters max, always. This skill enforces a universal 200-char cap on every LinkedIn connection request, regardless of the user's LinkedIn plan tier. 200 chars is the safe limit across paid LinkedIn plans and produces tighter, sharper copy on free plans too.

Process:
1. Draft the connection request, including the prospect's name.
2. Count characters (including spaces and punctuation).
3. If over 200, trim the least specific phrase first ("at your stage", "right now", "I'd guess") until <=200.
4. Never ship a request at 201+ chars.

Reference (informational only, do not raise the cap):

| Plan | Platform limit |
|------|-------|
| LinkedIn Free | 300 characters |
| Premium / Sales Nav (most tiers) | 200 characters |
| Sales Nav Advanced | 300 characters |

**Connection request rules:**
- Address by name (always).
- Make it about *their* situation, not about you.
- Name a specific pain; vague topic references earn nothing.
- Never say "no pitch", "no agenda", "just want to connect". Wastes characters, sounds defensive.
- Don't ask for their time. Earn the connection first, ask in the DM.
- Close with a question or observation that creates curiosity.

**Always present two options for every first message**

Every Day-1 connection request and cold email opener is delivered to the user as **two side-by-side versions**:

1. **Without referral remix** (pure pain-led opener).
2. **With referral remix** (soft "a colleague flagged your name" hook prepended).

Show both with character counts. The user picks per lead or per segment. Not everyone is comfortable with the referral framing, so the choice stays theirs.

If the core (without-referral) version cannot be trimmed below ~170 chars while preserving the pain specificity, the with-referral version may not fit under 200. In that case, surface only the without-referral option and explicitly note "no room for referral on this one."

**Referral remix must include a recognition payoff.** A first-touch discovery or validation message cannot lead with product value or information value, even when a product exists, because that would break the pain frame. The only honest currency we have at first touch is **emotional value**: recognition that the prospect is one of the sharper / more thoughtful / more engaged people in the space. The referral phrase must answer *why* a colleague flagged them, and the answer must be a compliment about their work or thinking.

**Good referral framings (include recognition):**
- "A colleague flagged you as one of the sharper [persona] thinking about [topic],"
- "A teammate kept seeing your name come up when looking at thoughtful [persona] on [topic],"
- "A colleague mentioned you as one of the few [persona] actually [verb-phrase about the pain],"
- "Someone on my team flagged you as a [persona] who's been genuinely wrestling with [pain],"

**Bad referral framings (no recognition, no value):**
- "A teammate flagged your name while mapping [vertical] leads" (no why)
- "A colleague passed me your profile" (bare, no recognition)

**Rules for the referral remix:**
- First message only. Never repeat in DMs or follow-ups.
- Defensibility: the user must be able to point to something about the prospect (LinkedIn activity, posts, talks, role, public work) that plausibly justifies the recognition. Never recognise someone for something they didn't do.
- Restrained language only. Avoid "brilliant", "incredible", "world-class" (reads fake). Use "sharper", "thoughtful", "genuinely", "actually", "few people who".
- Skip the remix entirely for warm re-engagement and event-triggered archetypes (you already have a stronger reason to be there).

**With referral remix (good example, 200 chars):**
- "Hi Priya, a colleague flagged you as one of the few COOs in healthtech who's actually tackled the skills-visibility piece. Most end up building it in Sheets because HRIS data feels stale. Sound right?"

---

## Brevity discipline and trim cheatsheet

Write tight on the **first draft**. Aim for 140-170 chars on the core (pre-referral) so the with-referral version still fits inside 200. Avoid the cycle of "draft long, then trim aggressively"; if you trim too much you lose the pain specificity that makes the message work.

When a draft goes over 200, trim in this priority order:

**Cut first (fillers and hedges):**

| Cut | Why |
|------|------|
| "we talk to", "we hear from" | Implied by the framing already |
| "honestly", "just", "really", "actually" | Pure filler |
| "at your stage", "right now", "these days" | Cut only if the timing isn't load-bearing |
| "I'd guess", "I'd imagine", "I suspect" | Often replaceable with a direct claim |
| "in order to" | Use "to" |
| "have been doing", "are doing" | Use simple present tense |
| "is becoming" | Use "becomes" or "is" |
| Repeated qualifiers (e.g., "supply chain leaders in the supply chain space") | Dedupe |
| "and"-joins where one half already lands | Drop the weaker half |

**Keep at all costs:**
- The prospect's name.
- The specific pain mechanic (the exact noun/verb that makes them feel seen).
- Verbatim numbers from VSI signals.
- Role/persona descriptor ("COOs", "supply chain leads").
- The CTA question.

**Sensible abbreviations and tightenings:**
- Drop "the" before plurals when meaning is preserved: "the knock-ons" -> "knock-ons".
- "Most X end up doing Y" beats "Most X tend to end up doing Y".
- Industry shorthand the persona uses every day: "CRMA", "GTM", "HRIS", "ICP", "MQL".
- Active over passive: "Decisions get made one bottleneck at a time" beats "Decisions are being made on a bottleneck-by-bottleneck basis".
- Verb over noun phrase: "modelling CRMA in Excel" beats "doing CRMA modelling work in Excel".

**Hard rule:** if the only way to fit the referral remix is to gut the pain specificity, **drop the referral, not the pain**. The pain is the point.

**Worked trim example:**

Bloated draft (218 chars, over cap):
> "Hi Anders, most heads of supply chain we talk to right now are tending to end up running their CRMA scenarios in Excel just one bottleneck at a time, and then they're guessing at all of the knock-on effects. Curious where yours starts to wobble?"

Trimmed (148 chars, well under cap, ready for referral remix):
> "Hi Anders, most supply chain leads end up modelling CRMA in Excel one bottleneck at a time, then guessing at the knock-ons. Where does yours wobble?"

Cuts applied: "we talk to right now" (filler), "are tending to" (hedge), "just" (filler), "they're guessing at all of" -> "guessing at" (tighter), "knock-on effects" -> "knock-ons" (industry-OK shorthand), "starts to wobble" -> "wobble" (active verb).

**Good examples (under 200 chars):**

Pain-aware variant:
- "Hi Maria, most fintech founders I talk to at your stage have the same doubt: 'do we actually know who we're selling to?' Hit you at a good moment?" (148 chars)
- "Hi Tom, pattern with SaaS teams at your stage: ICP feels solid until the first sales hire, then the motion doesn't transfer. Live question for you?" (148 chars)

Champion-hacker variant:
- "Hi Priya, most COOs I talk to end up building their own skills tracker in Notion or Sheets because HRIS data feels untrustworthy. Sound familiar?" (146 chars)
- "Hi Sam, keep meeting heads of ops who built their own attrition dashboard because the HRIS one is months out of date. Curious where yours lives?" (146 chars)

**Bad:** "Working closely with fintech founders on GTM, the ICP question keeps coming up. No pitch, just want to be connected." Vague, about you, disclaimer, no name.

**Follow-up DM (after accept):**
- Wait 24h after acceptance.
- 2-3 sentences max.
- Reference why you connected.
- Don't pitch, open a conversation.

```
"Hi [Name], thanks for connecting. [Callback to connection context.]

[Signal -> Bridge in 1-2 sentences. Champion-hacker variant: ask how they built their workaround. Pain-aware variant: ask how they manage today.]

[Soft CTA: "Worth a quick chat?" or "Happy to share what we've heard if useful."]"
```

---

## WhatsApp rules

High-trust, high-attention channel. Tier A only, Step 5+.

- Max 3 sentences.
- Conversational tone, reads like a text from a colleague.
- Addresses by name.
- No links, no attachments.
- Must reference prior contact ("following up from my emails").
- Easy opt-out always.

```
"Hey [Name], [Your name] here from [Co]. Following up on a few emails, I know things get busy.

[Signal in 1 sentence, conversational, can reference the hack pattern for champion-hacker variant]

[Soft CTA] happy to leave it there if not relevant right now."
```

---

## Campaign type archetypes

### Cold (LinkedIn-first default)
- Step 1: LinkedIn connection request (<=200 chars). Hi [Name], Signal, Bridge, curiosity CTA.
- Step 2: LinkedIn DM after accept. Sharper pain framing, ask how they handle it today (pain-aware) or how they built their workaround (champion-hacker).
- Step 3: LinkedIn DM. New facet of the same pain (cost / productivity / process / team).
- Step 4 (optional, "both" channel mode): Email. Pain-first opener that doesn't repeat the LinkedIn DM.
- Step 5: LinkedIn DM or email breakup. One last validation question, no guilt.

### Cold (email-only, if user opts out of LinkedIn)
- Step 1: Email. Hi [Name], Signal opener, Bridge, curiosity CTA.
- Step 2: Email. Sharper version of the pain or question about how they handle it today.
- Step 3: Email. New facet of the same pain.
- Step 4: Breakup email. One last validation question, no guilt.

### Warm re-engagement
- Step 1: Acknowledge prior contact by name, lead with what's changed (a new pain pattern from recent calls).
- Step 2: LinkedIn DM with new facet.
- Step 3: New angle on the original pain. A fresh question or recent pattern from other calls. No case studies, no product reveals.

### Event-triggered
The trigger tells you *who* and *when*. The pain is still the opener.
- Step 1: Pain pattern characteristic of people in this trigger moment. Address by name.
- Step 2: LinkedIn connection. No reference to trigger, no pitch.
- Step 3: Value-add email. New facet.
- Step 4: LinkedIn DM. Soft conversation opener.

### ABM (Account-Based)
- Research the specific account first.
- Step 1: Account-specific signal, Bridge, CTA. Address by name.
- Each step: new account-level facet on the same pain.
- Coordinate LinkedIn + email on same account in parallel.
- All steps stay in discovery mode. Account-specific signals validate the pain, never pitch the solution.

---

## Common mistakes

- **Skipping the name**: feels like broadcast. Always lead with "Hi [Name],".
- **Shorthand closing question**: "Match yours?", "Sound familiar?", "Resonate?" sound like AI tells. Use full conversational form ("Match what you're seeing?", "Familiar pattern, or different on your end?").
- **Trigger as hook**: "Congrats on the raise" has no value, no pain, no reason to reply.
- **Flattery opener**: "Came across your impressive work at..." gets skipped immediately.
- **Wall of text**: more than 100 words in step 1 won't be read.
- **Following up on following up**: "Just bumping this" earns deletion.
- **Vague CTA**: "Let me know your thoughts" on what?
- **Same facet repeated**: each step needs a new reason to respond. Cycle through cost / productivity / process / team facets of the same root pain.
- **"No pitch" disclaimers**: everyone knows you have an agenda. Disclaiming it wastes space.
- **Pitching the solution (even softly)**: breaks the discovery/validation frame. Even if a product exists, the first touch never leads with it. Every message validates the pain; no demos, case studies, benchmarks, "see how we can," or "see how to reduce X to Y." Late-step variation comes from new pain facets, never solution reveals.
- **Fabricated numbers**: never invent stats. Use only what's in VSI signals.
