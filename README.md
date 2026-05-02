# Store Scaler

Private vault command system for Shopify stores. Built on Claude Code. No SaaS. No servers. No data goes to us.

## What It Is
Store Scaler is a system of Claude Code commands that execute locally on your machine. Each command generates ad copy, audits, strategies, and execution plans specific to your Shopify store.

## Pricing

| Tier | Price | What You Get |
|---|---|---|
| Standard | $500/month | Vault commands via Claude Code CLI — type /mt/command-name |
| Premium | $1,000/month | Same commands + UniTrack4D desktop workstation |

## Privacy
No data goes to us. We can't see your store, your prompts, or your outputs. Architecturally impossible — no MT server exists.
Your only data path is between you and Anthropic (Claude Code's provider) — a relationship you already have, with your own API key.

## Architecture
PV = Local Files + Claude Code + Output Signals

- **Local Files** — /commands/, /reference/, /clients/ stored on your machine
- **Claude Code** — Anthropic's CLI reads and executes commands with your API key
- **Output Signals** — pulse.sh fires a signed transaction to Base after execution (random address + timestamp only)

## Network Transparency
Only 2 internet connections. Ever.

| Connection | Destination | Content | MT Role |
|---|---|---|---|
| API Call | api.anthropic.com | Your prompts (your key) | Zero |
| Pulse | Base RPC | Random address + timestamp | Zero |

Everything else is local. No server. No middleware. No telemetry.

## On-Chain Verification
- **StoreScalerVerifier.sol** — stores SHA-256 hash per vault version (Basescan verified)
- **UniTrackPulse.sol** — records execution pulses (Basescan verified)
- Both contracts under 100 lines. No proxy. No UUPS. Immutable.
- Verify at [unitrackmt.org](https://unitrackmt.org)

## Update Protocol (5-Day Verification Window)
1. Hash published on-chain 5 days before release
2. Update delivered via git pull
3. User runs `make hash` — compares local hash to on-chain hash
4. Match = authentic, untampered update

## Command Categories

50+ commands across 24 categories. Each command produces finished, deployable outputs — not advice.

| Category | What It Does |
|---|---|
| Meta Ads | Campaign builds, audience structures, creative briefs |
| Google Ads | Search campaigns, keyword architecture, RSA copy |
| TikTok Ads | Spark ads, creative angles, campaign structure |
| Klaviyo | Email flows, SMS sequences, segmentation |
| Creative Production | Ad scripts, hooks, visual briefs, UGC frameworks |
| Landing Pages | Full page builds, A/B variants, funnel copy |
| Pricing Strategy | Margin analysis, bundle builds, discount frameworks |
| Inventory Management | Stock velocity, reorder signals, dead stock plans |
| Shipping Optimization | Rate analysis, carrier comparison, free shipping thresholds |
| Storefront | Collection structure, product pages, conversion elements |
| Retention | Loyalty loops, win-back sequences, LTV maximization |
| CX (Customer Experience) | Support scripts, review systems, NPS workflows |
| Organic Growth | SEO, content clusters, social media calendars |
| Influencer | Outreach scripts, contract templates, ROI tracking |
| Affiliate | Program structure, commission tiers, partner recruitment |
| Feeds | Product feed optimization, Google Shopping, Meta catalog |
| Reporting | Monthly reports, KPI dashboards, campaign diagnostics |
| Profit Ops | P&L analysis, margin optimization, cost reduction |
| Wholesale | B2B pricing, wholesale portal, volume discounts |
| International | Market entry, localization, multi-currency strategy |
| Product Dev | Launch playbooks, line extension, sourcing frameworks |
| Legal & Compliance | Privacy policies, ad compliance, terms templates |
| Team | SOPs, hiring briefs, onboarding sequences |
| Supplier | Negotiation frameworks, vendor scoring, backup sourcing |
| Workflows | Cross-category automations, multi-step execution chains |

Commands execute locally through Claude Code. No data goes to us.

## Links
- [UniTrack Protocol](https://github.com/MarketersTerminal/UniTrackProtocol) — smart contracts (public, auditable)
- [UniTrack4D](https://github.com/MarketersTerminal/UniTrack4D) — desktop GUI (public source)
- [Marketers Terminal](https://github.com/MarketersTerminal/MarketersTerminal) — organization hub
- [unitrackmt.org](https://unitrackmt.org) — on-chain verification page
