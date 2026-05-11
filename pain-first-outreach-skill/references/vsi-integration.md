# VSI MCP Integration

VSI (Venture Signal Intelligence) processes call recordings and extracts structured market signals. Use these MCP tools to pull signals directly instead of asking for file uploads.

---

## Available tools

### get_signals
Pull market signals filtered by type and status.

```
Use VSI MCP: get_signals
  - venture_id: [from list_ventures]
  - signal_type: pain_point | workflow | objection | trigger | pattern
  - status: candidate | emerging | validated | decision_grade
  - date_from / date_to: ISO date range (default: last 30 days)
```

**For campaign building, pull in this order:**
1. `signal_type: pain_point, status: validated`. strongest hooks for Step 1
2. `signal_type: pain_point, status: emerging`. newer patterns, good for testing
3. `signal_type: objection`. pre-empt in Step 3+

### get_artifacts
Pull structured documents: ICP definitions, positioning, objection matrices.

```
Use VSI MCP: get_artifacts
  - venture_id: [from list_ventures]
  - artifact_type: icp | problem_space | value_proposition | positioning | objection_matrix
  - list_only: true (to browse available artifacts first)
```

**Key artifacts for campaigns:**
- `icp`. targeting criteria for lead search (Phase 2)
- `objection_matrix`. objections ranked by frequency, use to pre-empt in sequences
- `positioning`. framing language, use in Bridge section of messages

### get_aggregated_reflections
Behavioral patterns from calls. what helped, what hurt, what was missed.

```
Use VSI MCP: get_aggregated_reflections
  - venture_id: [from list_ventures]
  - time_scope: week | month | quarter
  - direction: hurt | helped | missed
```

**For campaigns:** Pull `hurt` and `missed` reflections. these surface pain points that prospects experienced but may not articulate directly.

### list_ventures
Discover available ventures. Call this first if you don't know the venture_id.

```
Use VSI MCP: list_ventures
  → Returns: venture IDs, names, descriptions
```

### search_conversations
Find specific call conversations by keyword or topic.

```
Use VSI MCP: search_conversations
  - venture_id: [from list_ventures]
  - query: "keyword or phrase"
```

Use when you need to find direct quotes or specific call context to make messages more specific.

---

## Signal weighting

Not all signals are equal. When multiple signals are available, prioritize:

1. **Validated > Emerging > Candidate**: validated signals have been confirmed across multiple calls
2. **Recent > Old**: signals from last 4 weeks outweigh older ones
3. **Specific > General**: "Series A SaaS founders lose first 3 sales hires in 18 months" beats "founders struggle with GTM"
4. **Frequent > Rare**: signals mentioned in 3+ calls are patterns; 1-2 mentions are anecdotes

Use the strongest, most specific, most recent signal as your Step 1 opener. Use weaker signals as supporting angles in later steps.

---

## Fallback: no VSI MCP

If VSI MCP is not connected, ask the user to provide signals manually:
- Paste a VSI export (any text format)
- Describe what's been coming up in calls
- Share 2-3 call excerpts

Extract pain points, triggers, objections, ICP patterns, and proof points from whatever they provide. See the extraction guide in the main SKILL.md Phase 1.
