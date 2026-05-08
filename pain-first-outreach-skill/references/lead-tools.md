# Lead Search & Enrichment Tools

## Tool priority

1. **Lemlist** — default for search + campaign delivery
2. **Clay** — deep enrichment, waterfall search across multiple sources
3. **Apollo** — high-volume prospecting, large databases
4. **EnrichLayer** — enrichment layer for filling gaps (company data, tech stack, funding)

Ask the user which tool(s) they want to use if not obvious from context. Lemlist is always the campaign delivery tool regardless of where leads come from.

---

## Lemlist (MCP)

Lemlist has a built-in lead database and is also where campaigns run.

**Search for leads:**
```
Use Lemlist MCP: search leads
  - Filters: job title, company size, industry, location, etc.
  → Returns: name, email, company, title
```

**Check existing campaigns (dedup):**
```
Use Lemlist MCP: list campaigns
  → Returns: campaign IDs, names, status
```

Before adding leads, check they're not already in an active campaign to avoid double-contacting.

---

## Clay

Clay provides waterfall enrichment — it searches across multiple data providers to find the best match.

**Integration:** Clay doesn't have an MCP yet. The user will either:
- Share a Clay table export (CSV or JSON)
- Paste enriched lead data from Clay
- Provide a Clay webhook URL for real-time enrichment

**What Clay provides:**
- Verified emails
- Phone numbers
- Company firmographics (revenue, headcount, funding)
- Tech stack data
- Job change alerts
- Custom enrichment formulas

**When to use Clay:** When the user needs deep enrichment beyond basic firmographics, or when they want to cross-reference multiple data sources before scoring.

---

## Apollo

Apollo has one of the largest B2B contact databases.

**Integration:** No MCP yet. The user will either:
- Export a lead list from Apollo (CSV)
- Share their Apollo search criteria for you to replicate in another tool
- Use Apollo's API directly (if configured)

**What Apollo provides:**
- Contact search by title, company, industry, size, funding
- Email verification
- Company data
- Buying intent signals

**When to use Apollo:** High-volume prospecting where you need 100+ leads quickly. Less depth than Clay but broader coverage.

---

## EnrichLayer

EnrichLayer fills gaps in lead/company data after initial search. Use the MCP tools if available, otherwise call the REST API directly.

### MCP tools (preferred — if `@enrichlayer/mcp-server` is connected)

The MCP exposes 25 tools. Key ones for GTM:
- `find_company_role` — find a person by role at a company
- `get_profile_email` — get work email for a LinkedIn profile (async — returns 202, poll until ready)
- `enrich_company` — company firmographics by domain
- `enrich_person` — person data by email or LinkedIn URL

### REST API (fallback)

**Find person by role at a company:**
```bash
curl "https://enrichlayer.com/api/v2/find/company/role/" \
  -H "Authorization: Bearer $ENRICH_LAYER_API_KEY" \
  -H "Content-Type: application/json" \
  -d '{"company_name": "Acme Corp", "role": "CFO"}'
```

**Get work email (async — 202 means processing):**
```bash
curl "https://enrichlayer.com/api/v2/profile/email" \
  -H "Authorization: Bearer $ENRICH_LAYER_API_KEY" \
  -H "Content-Type: application/json" \
  -d '{"linkedin_url": "https://linkedin.com/in/person"}'
```

**Company enrichment:**
```bash
curl "https://enrichlayer.com/api/v2/company/enrich" \
  -H "Authorization: Bearer $ENRICH_LAYER_API_KEY" \
  -H "Content-Type: application/json" \
  -d '{"domain": "company.com"}'
```

### Resilience rules (MUST follow)

EnrichLayer rate-limits aggressively and charges per call. Every enrichment script MUST implement:

1. **Retry with exponential backoff on 429 (rate limit):**
   - Wait 2s → 4s → 8s → 16s → give up after 4 retries
   - Log each retry so the user sees what's happening

2. **Immediate stop on 403 (insufficient credits):**
   - Do NOT retry. Print remaining results and stop gracefully.

3. **Incremental save after every batch:**
   - Save results to file after every 5 leads (not at the end)
   - A crash should never lose more than 5 leads of work

4. **Resume support:**
   - Before enriching, check if the output file already has data
   - Skip any leads/companies that already have enrichment results
   - Print "Resuming from lead N of M" so the user knows

5. **Credit cap:**
   - Ask the user for a max credit/call limit before starting (default: 50)
   - Track API calls made and stop when the cap is hit
   - Print "Credit cap reached (X/Y calls used). Saved N enriched leads."

6. **Skip unnecessary company lookups:**
   - If you already have the company domain, don't call company enrichment just to get data you won't use for scoring
   - Only enrich what's needed for FITS scoring (size, funding, industry)

**When to use EnrichLayer:** After initial lead search, to fill missing fields needed for FITS scoring. Particularly useful for:
- Company revenue (needed for Fit scoring)
- Funding status (needed for Timing scoring)
- Tech stack (relevant for some ICP criteria)

---

## DNC (Do Not Contact) handling

Before proceeding to scoring, ask the user:
> "Do you have a DNC list? (Company names, domains, or emails to exclude)"

If provided, remove all matching leads. Match on:
- Exact email match
- Domain match (strip email to domain)
- Company name fuzzy match

---

## Lead list format

Regardless of source, normalize leads to this structure before scoring:

| Field | Required | Source |
|-------|----------|--------|
| email | Yes | Search tool |
| firstName | Yes | Search tool |
| lastName | Yes | Search tool |
| companyName | Yes | Search tool |
| title | Yes | Search tool |
| companySize | Recommended | EnrichLayer |
| fundingStage | Recommended | EnrichLayer |
| industry | Recommended | Search tool |
| linkedinUrl | Recommended | Search tool |
| website | Recommended | Search tool |

This format is compatible with Lemlist's lead import.
