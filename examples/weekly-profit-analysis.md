# `/ss:weekly-profit-analysis` — SAMPLE OUTPUT

**Profit lever:** Improve operational efficiency
**Deploy to:** Internal decision / spreadsheet
**Type:** Ongoing (every Monday before 10am)

---

## Inputs received

- **Store:** [STORE_NAME] — Sample: Lume Home (mid-spend home/decor brand)
- **Reporting week:** Mon 2026-04-21 → Sun 2026-04-27
- **Comparison week:** Mon 2026-04-14 → Sun 2026-04-20
- **Contribution margin:** 58%
- **Break-even ROAS:** 1.72 (1 / 0.58)
- **Target ROAS (blended):** 2.30
- **Target CAC (blended):** $42
- **LTV (12-month, blended):** $164

### Pasted from Triple Whale dashboard (or Shopify + each ad platform, week-over-week)

| Metric | This week | Last week | Δ % | YoY |
|--------|-----------|-----------|-----|-----|
| Revenue | $58,420 | $54,210 | +7.8% | +18% |
| Net new customers | 412 | 384 | +7.3% | +12% |
| Repeat customers | 218 | 240 | -9.2% | -4% |
| Total orders | 740 | 712 | +3.9% | +9% |
| AOV | $78.95 | $76.14 | +3.7% | +6% |
| Sessions | 28,140 | 26,890 | +4.6% | +14% |
| CVR (blended) | 2.63% | 2.65% | -0.02 pts | flat |
| CVR (mobile) | 2.10% | 2.18% | -0.08 pts | -8% |
| CVR (desktop) | 4.18% | 4.10% | +0.08 pts | +6% |
| Total ad spend | $14,890 | $13,402 | +11.1% | +24% |
| Blended ROAS | 3.92 | 4.04 | -3.0% | flat |
| Blended CAC | $36.14 | $34.90 | +3.5% | +9% |
| Email/SMS revenue | $14,540 | $11,680 | +24.5% | +42% |
| Email % of total | 24.9% | 21.5% | +3.4 pts | +6 pts |
| Refund rate | 4.1% | 3.6% | +0.5 pts | +0.8 pts |
| Gross margin (avg) | 58.2% | 58.1% | flat | flat |

### Per-channel performance

| Channel | Spend | Revenue | ROAS | CPA | vs target CAC ($42) |
|---------|-------|---------|------|-----|---------------------|
| Meta Ads | $9,820 | $26,140 | 2.66 | $39 | within target |
| Google Search | $2,140 | $10,820 | 5.06 | $24 | well below — under-invested |
| Google Shopping | $1,640 | $4,720 | 2.88 | $36 | within target |
| TikTok Ads | $1,290 | $2,810 | 2.18 | $58 | above target |
| **Paid total** | **$14,890** | **$44,490** | **2.99** | **$36** | within target |
| Email/SMS | $0 | $14,540 | — | $0 | best ROI |
| **Blended** | $14,890 | $58,420 | **3.92** | $36 | within target |

---

## Diagnosis

### What is improving 🟢
1. **Email/SMS revenue +24.5% WoW.** Email's share of revenue jumped from 21.5% to 24.9% — moving into the healthy 20-35% range. Whatever shipped in flows or campaigns last week is working. Identify and replicate.
2. **AOV +3.7% WoW.** Likely from the bundle-strategy push on the top-3 SKUs deployed two weeks ago. Margin held at 58.2% so this is real lift, not discount-driven.
3. **Net new customers +7.3%** with paid spend up only 11% — efficiency is improving on cold acquisition, even though blended CAC ticked up slightly.

### What is declining 🟠
1. **Mobile CVR -0.08 pts WoW (-8% YoY).** Mobile is where the volume is — this is the single biggest profit drag. Run `/ss:mobile-optimization` and `/ss:product-page-optimizer` this week.
2. **Repeat customers -9.2% WoW.** This is concerning. Two possible roots:
   - Not enough campaigns to existing customers (check Klaviyo campaign volume; sample showed only 2 campaigns vs typical 4)
   - Restock issues on hero SKU (check inventory and bestseller-identification)
3. **Refund rate +0.5 pts WoW.** Small but worth flagging. Run `/ss:returns-reduction` if it persists 2 more weeks. If a single SKU is driving it, isolate and act.

### What to investigate 🔵
1. **TikTok CPA $58 vs target $42** — drifting above budget, but volume is small. Two-week call: either creative-fatigue refresh or pause and reallocate to Google Search where ROAS is best.
2. **Google Search ROAS 5.06 with only $2,140/week spend** — this is the most under-invested channel. Run `/ss:google-budget-allocation` to test a 30-50% budget shift from Meta into Google Search next week.

---

## Action items (prioritized by profit impact)

### Priority 1 — Recover mobile CVR
- **Estimated impact:** Mobile is ~64% of sessions. +0.4 pts mobile CVR = ~$2,800/week revenue lift
- **Run:** `/ss:mobile-optimization` (today), `/ss:product-page-optimizer` (this week)
- **Owner:** Web/dev
- **Deadline:** End of week

### Priority 2 — Reallocate $1,500/week from TikTok → Google Search
- **Estimated impact:** $1,500 at Google Search ROAS 5.06 = $7,590 revenue. Same $1,500 at TikTok ROAS 2.18 = $3,270. Net **+$4,320/week** at constant spend.
- **Run:** `/ss:google-budget-allocation` and `/ss:tiktok-scaling-plan` (kill underperformers, hold winners)
- **Owner:** Ads operator
- **Deadline:** Tuesday morning

### Priority 3 — Increase Klaviyo campaign volume to existing customers
- **Estimated impact:** Bringing repeat-customer count back to last week's 240 (vs 218) recovers ~22 orders × $79 AOV = **$1,738/week**
- **Run:** `/ss:klaviyo-campaign-calendar` for the next 4 weeks (target 4 campaigns/week)
- **Owner:** Email operator
- **Deadline:** Wednesday

### Priority 4 — Refund rate watch
- **Estimated impact:** 0.5 pts × $58K weekly revenue = $290/week saved if reversed
- **Run:** Pull refund reasons by SKU from Shopify; if one SKU >40% of refunds, run `/ss:product-improvement` on it
- **Owner:** Ops
- **Deadline:** Friday

---

## Scale readiness assessment

**Current state:** Blended ROAS 3.92 vs target 2.30 = 70% above target. ✅

**Should you scale paid spend?** Conditional yes:
- Scale Google Search aggressively (currently leaving money on the table)
- Hold Meta steady (within target, mobile-CVR fix unlocks ROAS lift before raising spend)
- Pause-or-fix TikTok before scaling

**Recommended weekly spend next week:**
- Meta: $9,820 (hold)
- Google Search: $3,200 (+$1,060)
- Google Shopping: $1,640 (hold)
- TikTok: $640 (-$650, run with kept winners only)
- **Total:** $15,300 (+$410 vs this week)

---

## Coverage gaps in execution log this week

Categories with **zero** entries this week (worth scheduling):
- ss_creative — no creative fatigue check or new concept brief logged
- ss_seasonal — Memorial Day (US) is 4 weeks out; no `/ss:promotion-calendar` entry
- ss_inventory — no `/ss:bestseller-identification` since Apr 06; running blind on which SKUs deserve more spend

Run `/ss:weekly-operator-rhythm` Monday to fold these into the week's plan.
