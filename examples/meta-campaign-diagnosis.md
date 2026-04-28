# `/ss:meta-campaign-diagnosis` — SAMPLE OUTPUT

**Profit lever:** Reduce acquisition cost
**Deploy to:** Meta Ads Manager
**Type:** Ongoing (run when CPA drifts >20% above target for 7+ days)

---

## Inputs received

- **Store:** Aria Skincare (mid-spend beauty brand)
- **Vertical:** Beauty / skincare
- **Monthly Meta spend:** $18,400
- **Contribution margin:** 62%
- **Break-even ROAS:** 1.61 (1 / 0.62)
- **Target ROAS:** 2.30 (target CPA $32 against $74 AOV)

### Last 30 days, Meta Ads Manager → Campaigns tab

| Metric | Value | Vertical benchmark | Status |
|--------|-------|--------------------|--------|
| Spend | $18,412 | — | — |
| Purchases | 412 | — | — |
| ROAS | 1.78 | 2.30 (target) | -22.6% |
| CPA | $44.69 | $32 (target) | +39.7% |
| CPM | $24.10 | $18-22 (beauty avg) | +9.5% |
| CTR | 1.42% | 1.20-1.60% | within range |
| CPC | $1.70 | — | — |
| AOV | $74.30 | — | — |
| Conversion rate (LP) | 1.10% | 2.40-3.20% (beauty CRO) | -54% |

---

## Diagnosis (CPM / CTR / CVR framework)

The framework isolates whether the breakdown is in **the auction (CPM)**, **the creative (CTR)**, or **the landing page (CVR)**.

| Test | Aria's data | Verdict |
|------|------------|---------|
| Is CPM elevated? | $24.10 vs $18-22 benchmark → +9.5% | Slightly elevated, not catastrophic |
| Is CTR healthy? | 1.42% vs 1.20-1.60% benchmark → in band | **Creative is fine** |
| Is on-site CVR healthy? | 1.10% vs 2.40-3.20% benchmark → -54% | **CVR is the bottleneck** |

**Verdict:** This is a **landing page / on-site conversion problem**, not a creative problem and not an audience problem. The ad is doing its job — pulling clicks at a normal rate at slightly elevated CPM. The site is failing to close them.

A creative refresh here would burn time without moving CPA. The fix is downstream of the click.

---

## What is actually broken (root cause estimate)

Based on beauty-vertical benchmarks and the 54% gap:

1. **Mobile PDP friction** — beauty stores see 60-70% mobile traffic. Sticky add-to-cart, mobile gallery, and load speed under 2s are critical. Aria's last Lighthouse score (per audit history) was 38 mobile.
2. **Insufficient social proof above the fold** — beauty buyers need 50+ reviews visible without scrolling. Many beauty stores show review count but not lifestyle/UGC near the buy button.
3. **No quiz / guided selection** — skincare's choice paralysis kills CVR. Quiz-driven flows lift beauty CVR 30-50% (Klaviyo + Octane data).

---

## Recommendations (ranked by impact × effort)

### Priority 1 — Fix mobile PDP load + sticky ATC
- **Estimated impact:** +0.7 to +1.0 pts on CVR (1.10% → ~1.95%)
- **Estimated CPA impact:** $44 → $25-28 at current CTR
- **Estimated $/month:** Recovering ~$12-16K of monthly Meta spend efficiency
- **Effort:** 2-3 dev days
- **Run next:** `/ss:mobile-optimization` and `/ss:product-page-optimizer`

### Priority 2 — Lift social proof above fold + 50+ reviews
- **Estimated impact:** +0.2 to +0.4 pts on CVR
- **Effort:** 1 day (theme edit + review widget configuration)
- **Run next:** `/ss:product-page-optimizer` (focuses on hero + proof above fold)

### Priority 3 — Launch quiz funnel for top 2 collections
- **Estimated impact:** +20-30% CVR on quiz-driven sessions
- **Effort:** 1 week (Octane / Shopify Quiz app + question logic)
- **Run next:** `/ss:popup-strategy` (covers quiz architecture)

### What NOT to do
- **Do not refresh creative.** CTR is healthy. New creative will not move CPA — it will burn budget testing.
- **Do not raise budget.** ROAS is sub-target; raising budget compounds the bleed.
- **Do not pause campaigns.** Audiences and account history have value; fix the LP and re-evaluate in 14 days.

---

## Action items (in order)

| # | Action | Where | Owner | Deadline |
|---|--------|-------|-------|----------|
| 1 | Lighthouse audit + image compression + lazy load | Shopify theme | Dev | 48h |
| 2 | Sticky add-to-cart on mobile PDP | Shopify theme | Dev | 48h |
| 3 | Move review widget + UGC carousel above fold | Shopify theme | Dev | 72h |
| 4 | Run `/ss:mobile-optimization` for full mobile spec | Claude Code | Operator | Today |
| 5 | Hold Meta spend flat for 14 days | Meta Ads Manager | Operator | Ongoing |
| 6 | Re-run `/ss:meta-campaign-diagnosis` Day 14 | Claude Code | Operator | +14 days |

---

## Estimated dollar impact of deployment

If CVR moves from 1.10% to 1.95% (Priority 1 alone):
- Same traffic, same CTR, +77% conversion lift
- Monthly purchases: 412 → ~730
- Monthly revenue: $30,612 → $54,239
- ROAS: 1.78 → 2.95 (above target)
- **Net additional contribution margin / month: ~$14,600**

Payback on Priority 1 dev investment: < 1 week.
