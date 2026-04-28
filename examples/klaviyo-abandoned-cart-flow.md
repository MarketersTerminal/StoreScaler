# `/ss:klaviyo-abandoned-cart` — SAMPLE OUTPUT

**Profit lever:** Increase revenue
**Deploy to:** Klaviyo
**Type:** Setup (one-time build, then ongoing optimization quarterly)

---

## Inputs received

- **Store:** [STORE_NAME]
- **Vertical:** [VERTICAL]
- **AOV:** $[AOV]
- **Contribution margin:** [MARGIN]%
- **Email list size:** [LIST_SIZE]
- **SMS enabled:** [YES/NO]
- **Current abandoned cart RPR:** $[CURRENT_RPR] (or "none — flow does not exist")
- **Reviews app:** [REVIEWS_APP]

### Klaviyo benchmarks (Klaviyo 2025)

- Average abandoned cart RPR: **$3.07** per recipient
- Top 10% RPR: **$27.12**
- Average placed-order rate: **2.68%**
- Average open rate: **46.97%**
- Average click rate: **5.21%**

If your current RPR is below $3.07, this build moves you toward average. If it is at $3.07-$10, this build pushes toward top-10%.

---

## Flow architecture

**Trigger:** Klaviyo "Checkout Started" metric, **filtered to exclude "Placed Order Since Started Checkout"**.

**Filters (set on the flow, not individual messages):**
- Skip if profile is suppressed or unsubscribed
- Skip if last cart-recovery email was sent within 24 hours (prevents loops)
- Skip if order placed since trigger fired

**Total messages:** 3 emails + 1 SMS (if SMS enabled). 4 total touches across 48 hours.

**Timing:**

```
Trigger (cart abandoned)
    │
    ├── +1h ──── Email 1: Reminder (no discount)
    ├── +4h ──── SMS 1: One-line nudge (if SMS enabled)
    ├── +24h ─── Email 2: Social proof + soft urgency
    └── +48h ─── Email 3: Discount or value reinforcement
```

The 1-hour first touch matters: cart recovery rates drop by ~50% if the first email goes out 24h later. Klaviyo data confirms.

---

## Email 1 — `+1 hour` — Reminder, no discount

**Subject line A/B test:**
- A: "You left something behind"
- B: "Still thinking about [PRODUCT_NAME]?"
- C: "[FIRST_NAME], your cart is waiting"

Run as A/B/C with 33% of trigger traffic each, declare winner at 500+ opens per variant.

**Preview text:** "Quick — items in carts here only stay for 24 hours."

**Content direction:**
- Hero: dynamic product image of the abandoned item (use Klaviyo product blocks pulling from cart data)
- Headline: "You left this in your cart"
- Body: 1-2 sentences only. The job of email 1 is to bring them back, not to sell. They already wanted this.
- CTA button: "Complete your order" → links to recovered checkout URL (Klaviyo provides this token)
- Below CTA: 3-4 review quotes pulled from [REVIEWS_APP], each ~12 words
- No discount.
- No fake urgency.

**Why no discount yet:** ~30% of cart abandoners come back at full price within 4 hours when reminded. Discounting in email 1 trains them to abandon for the discount. Discount belongs in email 3 only, and only as the closer.

---

## SMS 1 — `+4 hours` — One-line nudge (only if SMS enabled and consented)

**Message:**
> [STORE_NAME]: still thinking about [PRODUCT_NAME]? Your cart is here → [CART_URL]
>
> Reply STOP to opt out

**Character count:** ~145 (under SMS 160 limit). No emojis. No exclamation points.

**Why this works:** SMS click rate avg is 5.76% / top 10% is 14.89% (Klaviyo 2025). The 4-hour delay catches the "I meant to come back tonight" buyer before bedtime in their timezone (Klaviyo handles timezone routing).

**Compliance:** Only fire if profile has explicit SMS consent + valid phone. TCPA violations cost $500 to $1,500 per text.

---

## Email 2 — `+24 hours` — Social proof + soft urgency

**Subject line A/B test:**
- A: "Why [N] people picked [PRODUCT_NAME]"
- B: "[PRODUCT_NAME] is almost gone"
- C: "[FIRST_NAME], one quick thing about your cart"

**Preview text:** "Real reviews from real customers."

**Content direction:**
- Hero: same product image with a "[N] reviews ★★★★★" overlay (pull from [REVIEWS_APP])
- Headline: "Here's what others are saying about [PRODUCT_NAME]"
- 3 testimonial blocks, each with reviewer name, star count, and 1-2 sentence quote
- Soft urgency: "Cart will clear in 24 hours" (only true if you actually do clear carts — be honest, otherwise skip)
- Single CTA: "Recover my cart"
- Trust footer: shipping policy, return policy, customer service email/chat

**Why social proof here:** 24-hour-out abandoners didn't buy because they're either price-comparing or trust-checking. Social proof addresses the trust check.

---

## Email 3 — `+48 hours` — Discount or value reinforcement (closer)

Choose **one path** based on contribution margin:

### Path A — Margin allows discount (margin ≥ 50%)
- Offer: 10% off, valid 48 hours, code `BACK10`
- Subject: "Last chance — 10% off your cart"
- Hero: product image + visible discount badge
- Body: short. "We saved your cart. Use BACK10 at checkout to take 10% off, valid for 48 hours."
- CTA: "Apply 10% off" → recovered checkout URL with `?discount=BACK10` parameter so it auto-applies
- Margin impact: -10% revenue, but recovers ~30-40% of otherwise-lost orders. Net positive at >50% margin.

### Path B — Margin too thin for discount (margin < 50%)
- No discount. Reinforce non-price value instead.
- Subject: "Why [PRODUCT_NAME] is worth it"
- Body: explain the 1-2 things that make this product different (not "premium quality" — specifics: ingredient X, certification Y, lifetime warranty Z)
- Add: free shipping reminder, return guarantee, trust badge bar
- CTA: "Complete my order"

Whichever path you take, this is the last cart-recovery touch. After this email, the contact moves to the browse-abandonment / general nurture flow.

---

## Variables to fill before deployment

```
[STORE_NAME]
[VERTICAL]
[AOV]
[MARGIN]
[LIST_SIZE]
[YES/NO] (SMS enabled)
[CURRENT_RPR]
[REVIEWS_APP]
[PRODUCT_NAME] (Klaviyo dynamic — auto-fills from cart data)
[FIRST_NAME] (Klaviyo dynamic — falls back to "there" if unknown)
[N] (review count — Klaviyo dynamic from reviews app)
[CART_URL] (Klaviyo built-in token: {{ event.extra.checkout_url }})
```

---

## Deployment checklist

- [ ] Verify Klaviyo "Checkout Started" metric is firing (check via Klaviyo → Analytics → Metrics, last 24h volume)
- [ ] Confirm reviews-app integration pulls the right star count and recent quotes
- [ ] Confirm Klaviyo SMS sender registered with carrier (10DLC compliance for US)
- [ ] Set the flow filter to exclude "Placed Order Since Started Checkout"
- [ ] A/B test subject lines on all 3 emails (winner declared at 500+ opens per variant)
- [ ] Set "Smart Sending" 16-hour cap (avoid double-sending if user is also in welcome flow)
- [ ] Test the recovered checkout URL on mobile and desktop
- [ ] If using Path A, test the auto-apply discount link end-to-end before going live

---

## Estimated dollar impact

For a store with [LIST_SIZE] active subscribers, ~5-8% will trigger Checkout Started monthly:
- 5,000 list × 6% trigger rate = 300 trigger events / month
- At avg RPR $3.07: **$921 / month recovered revenue**
- At top-10% RPR $27.12: **$8,136 / month recovered revenue**
- Most stores deploying this for the first time hit $5-12/RPR within 60 days, putting them in the upper quartile.

Run `/ss:klaviyo-ab-testing` quarterly to push toward top-10% RPR.
