# 8Raise: investor discovery for AI assistants

**Find investors for your startup, fund or real estate deal directly inside Claude, ChatGPT or Perplexity.**

8Raise is a hosted MCP server. It searches our own investor database of VCs, LPs, family offices, angels and wealth advisers, and returns ready-to-contact investors: names, titles, firms, LinkedIn profiles, emails and fund data, without leaving your AI assistant.

- **Website:** https://8raise.com
- **Setup guide (with screenshots):** https://8raise.com/connect
- **Server URL:** `https://mcp.8raise.com/mcp`
- **Support:** hi@8raise.com

---

## Who it's for

- **Founders raising a round** (pre-seed to Series B): VCs and angels that match your stage, sector and geography.
- **Fund managers raising LP capital:** pension funds, endowments, foundations, family offices, fund-of-funds, sovereign wealth funds and insurers.
- **Real estate operators:** capital partners with real estate mandates.
- **Anyone selling through wealth advisers:** US registered investment advisers (RIAs) by size and state.

## What it does

Four search modes, picked automatically from your request:

| Mode | Finds |
|---|---|
| **VC** | Partners and principals at VC and PE firms, angel networks, corporate VCs, accelerators. Filters: stage, sector, geography, investor type, and Advanced filters (2+ sectors, fund size, fund vintage, deal type). |
| **Real Estate** | RE private equity, REITs, developers and operators, RE investors. Filters: geography, RE investor type, strategy. |
| **LP** | Allocators who invest into funds. Filters: LP type, minimum AUM, geography (country). |
| **RIA** | US registered investment advisers. Filters: AUM band and US state. |

Four ways to find investors:

- **Describe the people** you want and 8Raise runs a search.
- **You already have firm names:** 8Raise finds the right contacts at each firm (enrich a list).
- **Lookalike:** investors who backed companies like yours.
- **Firm Finder:** describe the firms you want (for example "multi-family offices in Brazil that invest pre-IPO") and get a firm list to review.

Each investor comes with name, title, firm, LinkedIn profile, email (about 65-75% hit rate; we never guess an address, and any we cannot confirm is left out), phone where available, fund data and a relevance score. Tiers 1.5 and 2 add research: recent deals, news, talks, a fit summary and an opener, and at tier 2 the firm's thesis and recent deals.

Results show in chat (top 3), on your dashboard (the full list), and as a CSV or Excel export. You can push them to HeyReach for LinkedIn outreach.

## How it works in chat

1. You describe who you want.
2. 8Raise shows the search it will run. Nothing runs until you say go.
3. You pick the delivery tier (1, 1.5 or 2 credits per investor).
4. It runs. Big searches run in the background and are checked every 30 seconds.

## Install

Use this URL in every client: `https://mcp.8raise.com/mcp` (with `/mcp` at the end). Step-by-step screenshots for each client are at https://8raise.com/connect.

- **Claude (claude.ai or Claude Desktop):** Customize > Connectors > + > Add custom connector, paste the URL, then sign in. Start a new chat and say "hi".
- **ChatGPT:** turn on Developer Mode, then create an app with the URL and sign in.
- **Perplexity (Pro, Max or Enterprise):** Customize > Connectors > + Custom connector, choose Remote, Authentication OAuth, paste the URL.
- **Claude Code and config-file clients:** use an API key from Dashboard > Settings > API key: `claude mcp add --transport http 8raise https://mcp.8raise.com/mcp --header "Authorization: Bearer 8r_..."`.

Any client that supports the [Model Context Protocol](https://modelcontextprotocol.io) with OAuth 2.1 (PKCE) can connect.

## Example prompts

```
"Find 20 seed-stage fintech VCs in Germany and France."

"Find family offices in Spain that invest in real estate."

"I'm raising a $20M emerging-manager fund. Find US endowments and
 fund-of-funds that back first-time managers."

"Find wealth advisers in Texas and Colorado managing $100M to $500M."

"Here are 30 firm names: find the partners and their emails."

"Find investors who backed companies like ours: an AI code-review tool raising a seed round."
```

## Tools

28 tools become available to your assistant:

**Search**
- `get_started` (welcome, plan and credits), `search_tips` (how to get the best results)
- `refine_query` (turns your request into a search), `search_investors` (runs it), `check_search_status` (polls a long search)
- `list_advanced_options` (Advanced, LP and RIA filter menus)
- `export_results` (CSV or Excel)

**Enrich a list, Lookalike and Firm Finder**
- `enrich_companies`, `check_enrichment_status`
- `discover_investors` (Lookalike), `find_firms` (Firm Finder), `check_discovery_status`, `approve_discovery`

**Saved leads and searches**
- `save_lead`, `unsave_lead`, `list_saved_leads`, `tag_lead`
- `save_search`, `list_saved_searches`, `rerun_search`, `delete_saved_search`

**Outreach (HeyReach)**
- `list_outreach_destinations`, `send_to_heyreach`

**Exclusions**
- `upload_exclusion_list` (people or firms to skip), `import_linkedin_connections` (skip your LinkedIn network). Both apply to the workspace that is active on your dashboard.

**Account**
- `get_usage` (credits left), `get_billing_info` (plans and prices), `manage_subscription` (your plan; for upgrades and cancelling it gives you the dashboard link)

Schedules, memory and HeyReach campaign building live in the 8Raise Agent on the dashboard, not in the connector.

## Credits and plans

You pay in credits, per new investor delivered:

- **Tier 1:** 1 credit (investor details).
- **Tier 1.5:** +0.5 for investor research, charged only when it finds a real deal, news item or talk.
- **Tier 2:** another +0.5 for firm research, given back when it finds nothing.
- RIA advisers are always 1 credit. Investors already delivered to you are free. Failed or cancelled searches cost nothing.
- Lookalike and Firm Finder: 0.25 credits per new firm on the delivered list; contacts at the firms you approve cost the normal rate.

| Plan | Credits / month | Per-search max | Price |
|---|---|---|---|
| Free trial | 10 | 10 | $0 |
| Solo | 150 | 50 | $59 / mo |
| Starter | 500 | 100 | $179 / mo |
| Growth | 1,500 | 300 | $529 / mo |
| Pro | 3,000 | 1,000 | $1,059 / mo |

Every plan has every feature; only Pro removes the export watermark. Quarterly billing saves 10% and annual saves 20%. Full pricing: https://8raise.com/#pricing. Change or cancel your plan on the dashboard.

## Privacy and data

- **Sign-in:** OAuth 2.1 with PKCE
- **What we store:** your account, search history, saved leads and searches, exclusion lists, credit usage. Saved leads, saved searches and exclusion lists belong to your account only.
- **What we do not store:** your chats with the AI assistant
- **Privacy policy:** https://8raise.com/privacy
- **Terms:** https://8raise.com/terms

Where the data comes from: our own investor database, built by our team over 7+ years of fundraising work. Every search then checks and enriches each lead with our own system. We never share account data with third parties.

## Support

- **Bugs:** open an issue in this repo
- **Questions, billing, partnerships:** hi@8raise.com

## License

MIT, see [LICENSE](./LICENSE).

This repository holds public metadata, install instructions and the MCP manifest. The server is closed-source and hosted by 8Raise. Using `https://mcp.8raise.com/mcp` is governed by the [8Raise Terms of Service](https://8raise.com/terms).
