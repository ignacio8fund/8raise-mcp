# 8Raise — Investor discovery for AI assistants

**Find investors for your startup or fund directly inside Claude, ChatGPT, or Perplexity.**

8Raise is a hosted MCP server that searches a curated database of VCs, LPs, family offices, and angel investors and returns ready-to-contact leads — names, titles, firms, LinkedIn URLs, and verified emails — without leaving your AI assistant.

- 🌐 **Website:** https://8raise.com
- 📚 **Docs:** https://8raise.com/dashboard/how-to-use
- 🔌 **Server endpoint:** `https://mcp.8raise.com/mcp`
- 📨 **Support:** support@8raise.com

---

## Who it's for

- **Founders raising rounds** (pre-seed → Series B): find the right VCs and angels with the right thesis, stage, geography, and check size.
- **Fund managers raising LP capital:** find limited partners — fund-of-funds, endowments, family offices, HNWIs — that back funds like yours.
- **Real-estate operators:** find capital partners across PE, family offices, and pension funds with real-estate mandates.

## What it does

Three search modes:

| Mode | Use case |
|---|---|
| **VC** | Find venture investors by stage, sector, geography, check size, lead/follow preference |
| **LP** | Find limited partners that back emerging or established managers |
| **Real Estate** | Find capital allocators with explicit real-estate or alternatives mandates |

Each search returns ranked leads with:
- Full name, title, firm
- LinkedIn URL
- Verified email (Growth plan and above)
- Phone (Pro plan)
- Firm metadata: AUM/check-size range, fund stage focus, geographic preference
- Relevance score

Results download as CSV or Excel directly from the chat.

## Install

8Raise is a hosted MCP server. You authenticate once via OAuth — no API keys to manage.

### Claude (claude.ai or Claude Desktop)

1. Open **Settings → Connectors → Add custom connector**
2. Enter the URL: `https://mcp.8raise.com`
3. Click **Connect** and complete the sign-in flow
4. Start a new chat and say _"hi"_ — 8Raise will introduce itself and walk you through your first search

### ChatGPT

1. Open **Settings → Apps & Connectors → Add custom app**
2. Enter the URL: `https://mcp.8raise.com`
3. Authorize via OAuth
4. Open a chat with the app enabled and ask _"find me 10 seed-stage SaaS investors in the US"_

### Perplexity

1. Open **Settings → Connectors → Add connector**
2. Enter the URL: `https://mcp.8raise.com`
3. Sign in to authorize
4. Use 8Raise from any conversation by mentioning your investor target

### MCP-compatible clients (general)

The server speaks the standard [Model Context Protocol](https://modelcontextprotocol.io). Any MCP client supporting OAuth 2.1 PKCE flow can connect to `https://mcp.8raise.com/mcp`.

## Example prompts

```
"Find pre-seed fintech investors in Europe with check sizes between $250K and $1M.
 I want their LinkedIn and email."

"Find family offices in Madrid that invest in real estate.
 Pull 30 leads with verified emails."

"I'm raising a $20M emerging-manager fund. Find LPs in the US that back
 first-time managers — fund-of-funds, endowments, and high-net-worth family offices."

"Find Series A SaaS investors in London who've led rounds in B2B vertical
 software in the last 12 months."
```

## Tools exposed

After connecting, the following tools become available to your assistant:

**Search & discovery**
- `get_started` — onboarding tour and current usage
- `refine_query` — turn free-text into a structured investor search
- `search_investors` — run an investor search and return ranked leads
- `check_search_status` — poll long-running searches
- `export_results` — download results as CSV or Excel

**Saved leads & searches**
- `save_lead`, `unsave_lead`, `list_saved_leads`, `tag_lead`
- `save_search`, `rerun_search`, `list_saved_searches`, `delete_saved_search`

**Outreach integration (HeyReach)**
- `list_outreach_destinations` — list your HeyReach campaigns / lead lists
- `send_to_heyreach` — push leads from a search into HeyReach

**Personal data**
- `upload_exclusion_list` — exclude contacts from future searches (CSV)
- `import_linkedin_connections` — exclude your existing LinkedIn network

**Account**
- `get_usage` — see remaining leads in your plan
- `get_billing_info` — current plan, renewal date, plan options
- `manage_subscription` — view, upgrade, downgrade, cancel

## Plans

| Plan | Monthly leads | Per-search cap | Price |
|---|---|---|---|
| Free trial | 10 | 10 | $0 |
| Solo | 150 | 50 | $59 / mo |
| Starter | 500 | 100 | $179 / mo |
| Growth | 1,500 | 300 | $529 / mo |
| Pro | 3,000 | 1,000 | $1,059 / mo |

Quarterly and annual discounts available. Full pricing at https://8raise.com/#pricing.

## Privacy & data

- **Authentication:** OAuth 2.1 PKCE via Supabase
- **Data we store:** your account, search history, saved leads, exclusion lists, plan usage
- **Data we do NOT store:** message contents from your AI assistant, chat history with the assistant
- **Privacy policy:** https://8raise.com/privacy
- **Terms:** https://8raise.com/terms

Leads delivered through 8Raise are sourced from publicly available investor data and curated through licensed providers. We never share user account data with third parties.

## Support & feedback

- **Issues / bugs:** open an issue in this repo
- **Feature requests / billing questions:** support@8raise.com
- **Sales / partnerships:** hello@8raise.com

## License

MIT — see [LICENSE](./LICENSE).

This repository contains public metadata, install instructions, and the MCP manifest. The server implementation is closed-source and hosted by 8Raise. Connecting to `https://mcp.8raise.com` is governed by the [8Raise Terms of Service](https://8raise.com/terms).
