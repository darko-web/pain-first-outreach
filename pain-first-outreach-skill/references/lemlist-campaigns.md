# Lemlist Campaign Operations

## Setup

Lemlist MCP must be configured:

```bash
npx @lemlist/mcp-server --api-key $LEMLIST_API_KEY
```

Or in Claude Code settings (`~/.claude/settings.json`):
```json
{
  "mcpServers": {
    "lemlist": {
      "command": "npx",
      "args": ["@lemlist/mcp-server"],
      "env": {
        "LEMLIST_API_KEY": "your_api_key_here"
      }
    }
  }
}
```

API key location: Lemlist app -> Settings -> Integrations -> API.

---

## Campaign creation flow

Execute in this order:

### 1. Create campaign
```
Use Lemlist MCP: create a new campaign
  - Name: [campaign name]
  - Type: email (or multiChannel if using LinkedIn/WhatsApp)
```

### 2. Add email steps
For each email step:
```
Use Lemlist MCP: add email step to campaign [campaign_id]
  - Step number: [N]
  - Delay: [days after previous step]
  - Subject: [subject line]
  - Body: [message body]
```

For A/B subject testing, add both variants on the same step.

### 3. Add LinkedIn steps
Requires LinkedIn integration connected in Lemlist (Settings -> Integrations -> LinkedIn).
```
Use Lemlist MCP: add LinkedIn step to campaign [campaign_id]
  - Type: connection_request | message
  - Message: [copy]
  - Delay: [days]
```

### 4. Add WhatsApp steps
Requires Lemlist Growth/Enterprise + WhatsApp Business connected.
```
Use Lemlist MCP: add WhatsApp step to campaign [campaign_id]
  - Message: [copy]
  - Delay: [days]
```

### 5. Add leads
```
Use Lemlist MCP: add leads to campaign [campaign_id]
  - Leads: [{email, firstName, lastName, companyName, ...}]
```

Minimum required: email. Recommended: firstName, lastName, companyName, website.

### 6. Activate
```
Use Lemlist MCP: activate campaign [campaign_id]
```

Return the Lemlist campaign URL to the user.

---

## Pulling stats (for gtm-campaign-operations skill)

```
Use Lemlist MCP: list all campaigns
  → Returns: campaign IDs, names, status, creation date

Use Lemlist MCP: get campaign stats for campaign [campaign_id]
  → Returns: sent, opened, clicked, replied, bounced (counts + rates)

Use Lemlist MCP: get LinkedIn stats for campaign [campaign_id]
  → Returns: connection requests sent/accepted, DMs sent/replied
```

---

## File export format (fallback)

If Lemlist MCP is unavailable, export as JSON:

```json
{
  "campaign_name": "...",
  "segment": "...",
  "tier": "A",
  "created": "YYYY-MM-DD",
  "steps": [
    {
      "step": 1,
      "day": 0,
      "channel": "email",
      "subject": "...",
      "subject_variant_b": "...",
      "body": "..."
    },
    {
      "step": 2,
      "day": 3,
      "channel": "linkedin",
      "type": "connection_request",
      "body": "..."
    }
  ]
}
```

---

## Troubleshooting

- **MCP not responding**: Restart with `npx @lemlist/mcp-server --api-key $LEMLIST_API_KEY`
- **LinkedIn steps failing**: Connect LinkedIn in Lemlist Settings -> Integrations -> LinkedIn
- **WhatsApp steps failing**: Requires WhatsApp Business + Growth/Enterprise plan
- **Lead import errors**: Check for malformed emails and duplicates in active campaigns
