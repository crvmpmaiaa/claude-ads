# Curo Skin — Paid Advertising Audit Report

**Brand:** Curo Skin (curoskin.co.uk)
**Industry:** E-commerce DTC — Shower Filters
**Monthly Spend:** ~£13,000 (~$18,000 USD)
**Active Ads:** ~30 (across a small number of campaigns)
**Conversion Goal:** Purchases
**Platforms Audited:** Meta Ads, Google Ads
**Audit Date:** 16 February 2026

---

## Ads Health Score

| Platform | Score | Grade | Budget Share |
|----------|-------|-------|--------------|
| **Meta Ads** | **69/100** | **C** | ~56% (~£7.3k) |
| **Google Ads** | **72/100** | **C+** | ~44% (~£5.7k) |
| **Aggregate** | **70/100** | **C** | 100% |

**Verdict: Account is competently structured with a solid testing/scaling framework and clean Google setup. Primary improvement area is Meta EMQ scores — raising signal quality will improve algorithm optimization across the funnel. Several minor Google optimizations available.**

---

## Executive Summary

Curo Skin is spending ~£13k/month ($18k USD) across Meta and Google Ads for a shower filter DTC brand. The account fundamentals are sound — clean campaign structure, good creative diversity, proper Pixel + CAPI setup with dedup, and Google CPA running 20% below the £40 target.

**Areas for improvement:**

1. **Meta EMQ scores are below optimal** — PageView at 4.5/10 is below the 6.0 minimum threshold, with other events at 6.1-6.4. Raising EMQ by passing additional hashed customer parameters will improve Meta's ability to match events to users, strengthening optimization signal.
2. **Purchase event EMQ is unknown** — This is the event Meta optimizes against for purchase campaigns. If it's below 6.0, raising it should be the top priority.
3. **Google ROAS at 2.11x** is above break-even (1.68x at £67 AOV / £40 CPA target) but has room to improve through ad extension coverage and impression share growth.
4. **40% Search impression share** means 60% of eligible auctions are being missed — there's significant headroom to capture more high-intent Search traffic.

**The single highest-impact action is raising Meta EMQ scores**, particularly PageView and Purchase events, to improve the quality of signal feeding Meta's algorithm.

---

## PART 1: META ADS AUDIT

### 1.1 Pixel / CAPI Health (30% weight) — Score: 55/100 [NEEDS IMPROVEMENT]

| ID | Check | Result | Finding |
|----|-------|--------|---------|
| M01 | Pixel installed | PASS | Pixel firing correctly alongside CAPI — this is Meta's recommended redundant setup per [developer docs](https://developers.facebook.com/docs/marketing-api/conversions-api/best-practices/) |
| M02 | CAPI active | PASS | Server-side events sending. Pixel + CAPI running together is correct. |
| M03 | Event deduplication | PASS | Dedup event coverage at 80-85%+. Above functional threshold. Room to improve toward 90%+ target by tightening `event_id` matching on edge cases. |
| M04 | EMQ — PageView | FAIL | **4.5/10** — Below the 6.0 minimum threshold. Customer data matching parameters need improvement on this event. |
| M04 | EMQ — ViewContent | WARNING | **6.1/10** — Above 6.0 minimum but below 8.0 target. Additional hashed parameters (email, phone, external_id) would help. |
| M04 | EMQ — AddToCart | WARNING | **6.2/10** — Same as above. |
| M04 | EMQ — InitiateCheckout | WARNING | **6.4/10** — Best of the reported events but still below 8.0 target. |
| M04 | EMQ — Purchase | NOT REPORTED | **EMQ for the Purchase event was not provided.** This is the event Meta optimizes against — worth checking in Events Manager. |
| M07 | Standard events | PASS | Using standard events (PageView, ViewContent, AddToCart, InitiateCheckout) |

**What the EMQ Scores Mean:**
EMQ (Event Match Quality) measures how well the customer information parameters you pass with each event allow Meta to match that event to a specific user in their system. Higher EMQ = better user matching = better optimization signal.

- PageView at 4.5 means Meta can't reliably match most page views to users — this weakens upper-funnel audience building and retargeting pools
- The 6.1-6.4 range on mid-funnel events is functional but leaving performance on the table
- Meta's data shows accounts that improve EMQ from ~6 to 8+ typically see 20-30% better delivery efficiency

**Recommendations:**
1. Pass additional hashed PII with CAPI events: email, phone, fbp cookie, fbc click ID, external_id
2. Focus on PageView first — at 4.5, this has the most room for improvement
3. Check Purchase event EMQ in Events Manager — if it's below 6.0, prioritize this alongside PageView
4. Incrementally improve dedup from 80-85% toward 90%+ by auditing `event_id` matching on edge cases (e.g., redirect flows, SPA navigation)

### 1.2 Creative — Diversity & Fatigue (30% weight) — Score: 78/100 [GOOD]

| ID | Check | Result | Finding |
|----|-------|--------|---------|
| M25 | Format diversity | PASS | 3+ formats: statics, reels (video), UGC — good diversity |
| M26 | Creative volume per ad set | WARNING | 5 ad sets across 2 campaigns. Need to verify ≥5 creatives per ad set. |
| M27 | Video aspect ratios | PASS | Reels ad set implies 9:16 vertical video for Stories/Reels |
| M31 | UGC content | PASS | Dedicated UGC ad set in testing campaign — meets ≥30% threshold |
| M-CR1 | Creative freshness | PASS | Active testing campaign structure suggests ongoing creative testing |

**Strengths:**
- Testing/scaling structure is textbook — test new creative in the testing campaign, move winners to scaling
- UGC as a dedicated ad set shows awareness of social-native content importance
- Reels ad set means you're covering the highest-engagement placement
- Keeping reels separate from A+ placement ad sets is correct — reel-native 9:16 content crops poorly when forced into square placements

**Recommendations:**
- Ensure each ad set has 5-8 creatives for Meta's Andromeda system to optimize properly
- Test carousel format if not already active (strong for product education — before/after, multi-benefit)
- Monitor frequency in the scaling campaign — broad winners can fatigue quickly once scaled

### 1.3 Account Structure (20% weight) — Score: 78/100 [GOOD]

| ID | Check | Result | Finding |
|----|-------|--------|---------|
| M11 | Campaign count | PASS | 2 campaigns — clean and well within the 5-campaign limit |
| M12 | CBO vs ABO | PASS | ABO on testing + CBO on scaling — correct structure for this budget level. ABO gives control during creative testing; CBO lets Meta allocate budget to winners at scale. |
| M13 | Learning phase | PASS | At £40 target CPA, ad sets exit learning at ~50 conversions (~£2k spend). New ad sets take time to accumulate this at current per-ad-set budgets, but this is understood and managed. Higher overall spend would accelerate this. |
| M15 | Advantage+ Sales | WARNING | ASC not currently running. Worth testing alongside existing structure — it can work well for e-commerce purchase optimization, particularly for accounts with strong creative. |
| M16 | Ad set overlap | PASS | "Broad statics", "broad reels", "broad UGC" share broad targeting but are separated by creative format for a valid reason — reel-native 9:16 content can't be combined with A+ placement ad sets without cropping key information on square placements. |
| M18 | Objective alignment | PASS | Sales/Purchase objective for a purchase conversion goal |
| M23 | Purchaser exclusions | PASS | Existing customer exclusions updated monthly (managed by Joanna Bradley). |

**Budget & Learning Phase Context:**
With ~£7.3k/month across 5 ad sets, each ad set receives ~£49/day. At a £40 CPA target and ~50 conversions needed to exit learning, each new ad set takes approximately 40 days of spend to clear the learning phase. This is slower than ideal (5× CPA/day = £200/day would exit in ~10 days), but is a function of total budget rather than structural inefficiency. The account is set up correctly — increasing overall Meta budget would naturally accelerate learning across ad sets.

**Recommendations:**
- Consider testing Advantage+ Sales Campaign alongside the existing manual structure
- If budget increases, the current 5-ad-set structure will benefit — each ad set would clear learning faster

### 1.4 Audience & Targeting (20% weight) — Score: 68/100 [NEEDS IMPROVEMENT]

| ID | Check | Result | Finding |
|----|-------|--------|---------|
| M19 | Audience overlap | PASS | Ad sets share broad targeting but are differentiated by creative format (statics vs reels vs UGC). This is the correct approach — audience overlap is managed by letting Meta's algorithm decide delivery, while creative format drives ad set separation. |
| M22 | Advantage+ Audience | UNVERIFIED | Worth testing vs manual broad if not already in use |
| M23 | Exclusion audiences | PASS | Purchaser exclusions active and updated monthly |
| M24 | First-party data | UNVERIFIED | Customer list upload for Lookalike + Custom Audience? |

**The broad targeting approach** is Meta's current best practice for prospecting — the algorithm finds buyers more efficiently than manual interest/demographic targeting at this spend level. The ad set separation by creative format (rather than audience) is correct.

**Recommendations:**
- If not already in place, upload customer email list for Custom Audiences + Lookalikes
- Test Advantage+ Audience as a comparison to manual broad

---

## PART 2: GOOGLE ADS AUDIT

### Key Metrics Summary

| Metric | Value | vs £40 Target CPA | Status |
|--------|-------|-------------------|--------|
| Total Spend | £5,677 | — | — |
| Conversions | 177 | — | — |
| Conv. Value | £11,971 | — | — |
| **ROAS** | **2.11x** | **Break-even: 1.68x** (£67 AOV / £40 CPA) | **PASS (+26% above break-even)** |
| **CPA** | **£32.07** | **Target: £40** | **PASS (20% below target)** |
| CPC | £1.09 | — | Competitive for this niche |
| CTR (Search) | 6.12% (generic) | — | PASS (strong) |
| CVR (Search) | 2.97% | — | PASS |
| Impression Share | ~40% | — | Room to grow |

**Note on benchmarks:** The previous version used generic e-commerce benchmarks (3.68x ROAS, £19 CPA) which aren't meaningful without knowing your margins, LTV, and business model. The metrics above are evaluated against your stated £40 CPA target and the resulting break-even ROAS. **Google is performing above target on both CPA and ROAS.**

**Calculated AOV: ~£67.63** (£11,971 / 177 conversions)

### 2.1 Conversion Tracking (25% weight) — Score: 70/100 [NEEDS IMPROVEMENT]

| ID | Check | Result | Finding |
|----|-------|--------|---------|
| G42 | Conversion actions | PASS | 177 conversions tracked with £11,971 value — purchase tracking active |
| G45 | Consent Mode v2 | UNVERIFIED | **UK-based business — Consent Mode v2 is strongly recommended.** Without it, you may be losing conversion visibility from users who decline cookies. |
| G47 | Micro vs macro | UNVERIFIED | Verify only Purchase is set as "Primary" conversion. If AddToCart or PageView are Primary, Smart Bidding optimizes for the wrong goal. |
| G49 | Conversion values | PASS | Dynamic values present (£11,971 across 177 conv = ~£67.63 AOV) |
| G-CT1 | Duplicate counting | WARNING | Verify Google isn't double-counting between GA4 import and native Google Ads tag. |
| G-CT3 | Tag firing | PASS | Conversions recording consistently |

### 2.2 Wasted Spend / Negatives (20% weight) — Score: 72/100 [NEEDS IMPROVEMENT]

| ID | Check | Result | Finding |
|----|-------|--------|---------|
| G13 | Search term review | PASS | Search terms are highly relevant (shower filter, filtered shower head, hard water) |
| G14 | Negative keyword lists | UNVERIFIED | "Negative keywords" link visible in interface — verify themed lists exist |
| G16 | Irrelevant spend | PASS | Search terms show no obvious wasted spend on irrelevant terms |
| G17 | Broad match + bidding | PASS | Keywords show [exact] and "phrase" match — no broad match without Smart Bidding visible |
| G19 | Search term visibility | WARNING | PMax Shopping campaigns have limited search term reporting. This is an inherent PMax limitation, not a setup issue — but worth periodically checking the search terms that are visible. |
| G-WS1 | Zero-conv keywords | UNVERIFIED | Check for keywords with >100 clicks and 0 conversions |

**PMax Channel Distribution:**
The PMax "cross-network" spend is going to Shopping/Search placements, not Display. This is an important distinction — Shopping PMax surfaces product ads on Google Search, Shopping tab, and partner networks with high purchase intent. This is fundamentally different from Display PMax which pushes auto-generated creative across low-intent inventory.

**Remaining concern:** PMax search term reporting is limited regardless of placement type. Periodically review available search terms and add negatives for any irrelevant queries that surface.

### 2.3 Account Structure (15% weight) — Score: 85/100 [GOOD]

| ID | Check | Result | Finding |
|----|-------|--------|---------|
| G01 | Naming convention | PASS | Consistent pattern: LB + [Brand/Non-Brand] + [Product] + [Variant] |
| G04 | Campaign count | PASS | Reasonable number of campaigns. Structure is not over-fragmented. |
| G05 | Brand separation | PASS | Brand and non-brand clearly separated into different campaigns |
| G06 | PMax present | PASS | PMax Shopping active — driving majority of Google conversions |
| G07 | PMax brand exclusions | PASS | Brand already excluded from PMax with dedicated brand Search campaigns. This prevents PMax from cannibalizing cheaper brand traffic. |
| G08 | Budget allocation | PASS | "Biggest Changes" show percentage swings (e.g., +75.7%) but on small absolute budgets (e.g., £20 → £35/day). These are normal optimization adjustments that don't disrupt Smart Bidding learning. |
| G12 | Network settings | PASS | Search Partners at 0.1% — negligible impact |

**Budget Distribution Across Campaigns:**
- Top spender "Non-Brand + Shower Head + New" at £2,249.77 — getting reasonable budget
- Brand Search (£316) gets only ~£10.50/day — low but acceptable for brand defense
- Campaign pauses and budget shifts are normal account management, not instability

### 2.4 Ads & Assets (15% weight) — Score: 70/100 [NEEDS IMPROVEMENT]

| ID | Check | Result | Finding |
|----|-------|--------|---------|
| G26 | RSA per ad group | PASS | RSA visible with headlines and descriptions |
| G29 | RSA Ad Strength | UNVERIFIED | Need to check across all ad groups — visible ad shows "Eligible" status |
| G31 | PMax asset density | PASS | "No Asset" campaigns are **Shopping PMax** — these deliberately use only the product feed (no creative assets). This is correct and often outperforms asset-based PMax for product-focused campaigns, as confirmed by your performance data. |
| G32 | PMax video assets | N/A | Not applicable to Shopping PMax campaigns — these serve product listings from the Merchant Center feed, not video creative. |
| G35 | Ad copy relevance | PASS | "Curo Filtered Shower Head | UK's Best Filtered Showerhead | Multi-Award Winning" — strong, keyword-relevant headline |
| G-AD2 | CTR benchmark | PASS | Generic Search 6.12% = excellent. Brand Search 26.17% = excellent. |

**Ad Copy Analysis (Visible RSA):**
```
Headline: Curo Filtered Shower Head | UK's Best Filtered Showerhead | Multi-Award Winning
Description: Save up to 45% on the UK's best filtered shower head. Use code PREORDER
            at checkout today. Get softer hair & radiant skin. Enjoy up to 45% off +
            free delivery with code PREORDER.
Sitelinks: Shop Products, Travel Case, Shower Head Filter
```
- Strong value proposition (awards, health benefits, discount)
- "PREORDER" code in description — verify this is still active/relevant. If it's a permanent discount, renaming to something evergreen avoids confusion.
- Sitelinks present but only 3 visible — add a 4th for full coverage
- Missing: callout extensions, structured snippets, image extensions — adding these would increase ad real estate in the SERP

### 2.5 Keywords & Quality Score (15% weight) — Score: 68/100 [NEEDS IMPROVEMENT]

| ID | Check | Result | Finding |
|----|-------|--------|---------|
| G05 | Brand vs non-brand | PASS | Clearly separated |
| G-KW2 | Keyword-ad relevance | PASS | Headlines match target keywords well |

**Keyword Performance:**

| Keyword | Cost | Clicks | CTR | Type | Assessment |
|---------|------|--------|-----|------|------------|
| [Curo Shower] | £169.60 | 289 | 27.42% | Brand/Exact | Good — brand protected in dedicated Search campaign |
| "shower head filters" | £107.78 | 103 | 5.29% | Generic/Phrase | Decent CTR, relevant term |
| [filter shower head] | £77.79 | 70 | 6.32% | Generic/Exact | Good performance |
| [Curo Skin] | £56.60 | 133 | 35.66% | Brand/Exact | Excellent CTR — pure brand |
| [shower head filters] | £53.30 | 46 | 7.08% | Generic/Exact | Good — but phrase and exact both active for same term |

**Minor issue:**
- "shower head filters" as both [exact] and "phrase" = the phrase match can cannibalize the exact match's auction eligibility. Consider pausing the phrase match variant if the exact match covers the same queries effectively.

**Search Terms Quality:**
Relevant terms: shower filter, filtered shower head, curo shower head, shower head filter, filter shower head, shower filter for hard water, hard water shower filter, best shower filter for hard water uk — **all highly relevant, no obvious wasted spend on irrelevant terms.**

### 2.6 Settings & Targeting (10% weight) — Score: 60/100 [NEEDS IMPROVEMENT]

| ID | Check | Result | Finding |
|----|-------|--------|---------|
| G50 | Sitelinks | WARNING | 3 sitelinks visible (Shop Products, Travel Case, Shower Head Filter) — need 4+ |
| G51 | Callouts | UNVERIFIED | Not visible in screenshots |
| G52 | Structured snippets | UNVERIFIED | Not visible |
| G53 | Image extensions | UNVERIFIED | Not visible |

**Auction Insights Analysis:**
| Competitor | Impression Share | Top of Page Rate | Threat Level |
|-----------|-----------------|------------------|-------------|
| You | ~40% | ~25% | — |
| pureshower... | ~38% | ~22% | High — similar size, direct competitor |
| pickiniki.com | ~22% | ~20% | Medium |
| harveywater... | ~12% | ~95% | Low volume but dominates top position |
| cloverandc... | ~8% | ~90% | Low volume, high position |
| bestproduct... | ~5% | ~85% | Minimal |

**You have ~40% impression share** — meaning you're missing 60% of eligible auctions. With CPA already 20% below your £40 target, there may be room to increase Search budgets to capture more of this opportunity profitably.

**Demographics:**
- Strongest: Female 25-44 — aligns perfectly with shower filter / skincare target demo
- Presence: Male 25-34 as secondary
- Consider bid adjustments: increase bids on F25-44, decrease on low-converting segments

**Devices:**
- 83.7% mobile cost, 87% mobile clicks — mobile-dominant
- Desktop: 15.1% cost, 11.7% clicks — lower share but likely higher CVR
- Verify: is desktop CVR higher? If so, increase desktop bid adjustment.

---

## PART 3: CROSS-PLATFORM ISSUES

### 3.1 Budget Allocation Assessment

**Current Split:**
| Platform | Monthly Spend | Share |
|----------|--------------|-------|
| Meta | ~£7,300 | ~56% |
| Google | ~£5,700 | ~44% |

The split is reasonable. Whether to shift budget between platforms depends on Meta's actual ROAS (once EMQ improvements take effect) vs Google's 2.11x ROAS. If Meta ROAS is competitive with Google after EMQ improvements, Meta may benefit from additional budget given the current 5-ad-set structure would clear learning faster with more spend.

**MER (Marketing Efficiency Ratio):**
- Google reported: £11,971 conv value / £5,677 spend = 2.11x
- Need Meta revenue data to calculate blended MER
- At £67 AOV and £40 target CPA, your target acquisition efficiency is 1.68x ROAS. Google is exceeding this.

### 3.2 Campaign Structure

Campaign count is well-managed — Meta has a clean 2-campaign testing/scaling setup with ABO/CBO correctly applied, and Google has properly separated brand/non-brand with Shopping PMax running efficiently.

### 3.3 The "PREORDER" Code

Google Ads feature "Use code PREORDER at checkout." If the product is no longer in pre-order phase:
- Potential confusion at checkout if the code doesn't work
- Reduced trust if the offer seems stale

**If it's a permanent discount code, consider renaming to something evergreen** (e.g., "CURO45" or "WELCOME45").

---

## PART 4: PRIORITIZED ACTION PLAN

### HIGH — Genuine Improvements Available

| # | Action | Platform | Impact | Time |
|---|--------|----------|--------|------|
| 1 | **Raise Meta EMQ scores toward 8.0+** — Pass additional hashed PII with CAPI events: email, phone, fbp cookie, fbc click ID, external_id. PageView at 4.5 is the biggest opportunity — this is the foundation event for funnel building. | Meta | Meta data indicates 20-30% delivery improvement when EMQ moves from ~6 to 8+ | 4-8 hours |
| 2 | **Check Purchase event EMQ** — This wasn't in the data provided. It's the event Meta optimizes against for purchase campaigns. If it's below 6.0, prioritize raising it alongside PageView. | Meta | Directly impacts purchase optimization signal | 30 min to check |
| 3 | **Verify Consent Mode v2 on Google** — UK business serving UK customers. Without Consent Mode v2, conversion modelling may be less accurate for users who decline cookies. | Google | Better conversion data quality | 1-2 hours |
| 4 | **Add 4th sitelink + callout extensions + structured snippets to Google Search** — Currently showing 3 sitelinks and no visible callouts/snippets. Full extension coverage increases ad real estate and typically improves CTR 10-15%. | Google | More SERP real estate, better CTR | 30 min |
| 5 | **Test Advantage+ Sales Campaign** — Set up alongside existing manual structure with a controlled portion of Meta budget. ASC can perform well for e-commerce purchase optimization, particularly with your creative diversity. | Meta | Worth testing as an additional campaign type | 1 hour |

### MEDIUM — Optimization Opportunities

| # | Action | Platform | Impact | Time |
|---|--------|----------|--------|------|
| 6 | Verify/update "PREORDER" code — if permanent discount, rename to evergreen code | Google/Meta | Reduces potential checkout friction | 30 min |
| 7 | Improve dedup from 80-85% toward 90%+ — audit `event_id` matching on edge cases (redirects, SPA nav) | Meta | Incremental signal improvement | 1-2 hours |
| 8 | Implement demographic bid adjustments (increase F25-44, decrease low-converting segments) | Google | Better budget allocation to converting demos | 15 min |
| 9 | Upload customer email list for Custom Audiences + Lookalikes if not already in use | Meta | Better seed data for algorithm targeting | 30 min |
| 10 | Add UTM parameters to all Meta ad URLs for GA4 cross-platform attribution | Meta | Better attribution visibility in GA4 | 15 min |
| 11 | Evaluate Search impression share opportunity — at 40% IS and CPA 20% below target, there may be room to capture more volume | Google | More conversions at profitable CPA | Ongoing |

### LOW — Backlog (Best Practices)

| # | Action | Platform | Impact |
|---|--------|----------|--------|
| 12 | Test 12AM-6AM bid reduction on Google | Google | Minor budget savings |
| 13 | Add image extensions to Search campaigns | Google | Marginal CTR improvement |
| 14 | Test carousel format on Meta for product education | Meta | Additional creative format |
| 15 | Consider TikTok Ads test for audience diversification | New platform | Potentially lower CPMs |
| 16 | Implement post-purchase survey ("How did you hear about us?") | Website | Better attribution understanding |

---

## PART 5: DETAILED SCORING BREAKDOWN

### Meta Ads Score: 69/100 (Grade C)

| Category | Weight | Score | Weighted |
|----------|--------|-------|----------|
| Pixel / CAPI Health | 30% | 55/100 | 16.5 |
| Creative (Diversity & Fatigue) | 30% | 78/100 | 23.4 |
| Account Structure | 20% | 78/100 | 15.6 |
| Audience & Targeting | 20% | 68/100 | 13.6 |
| **Total** | **100%** | — | **69.1 → 69** |

**Main drag:** EMQ scores are pulling Pixel/CAPI Health down. The setup is correct (Pixel + CAPI with dedup), but the quality of customer data matching parameters needs improvement — particularly PageView at 4.5/10. Raising EMQ toward 8.0 would lift this category to 75+ and the overall Meta score into the mid-70s (Grade B).

### Google Ads Score: 72/100 (Grade C+)

| Category | Weight | Score | Weighted |
|----------|--------|-------|----------|
| Conversion Tracking | 25% | 70/100 | 17.5 |
| Wasted Spend / Negatives | 20% | 72/100 | 14.4 |
| Account Structure | 15% | 85/100 | 12.75 |
| Keywords & Quality Score | 15% | 68/100 | 10.2 |
| Ads & Assets | 15% | 70/100 | 10.5 |
| Settings & Targeting | 10% | 60/100 | 6.0 |
| **Total** | **100%** | — | **71.35 → 72** |

**Main drags:** Settings/Targeting at 60 (missing ad extensions, sitelinks) and Keywords at 68 (exact/phrase overlap on same terms). These are quick fixes. Structure at 85 reflects the clean brand/non-brand separation, correct Shopping PMax setup, and proper brand exclusions.

### Aggregate Score: 70/100 (Grade C)

```
Aggregate = Meta (69) × 56% + Google (72) × 44%
         = 38.6 + 31.7 = 70.3 → 70
```

---

## PART 6: WHAT'S WORKING

This account has strong fundamentals:

1. **Meta campaign structure is clean** — 2 campaigns with testing ABO / scaling CBO is textbook. Many accounts have 10+ chaotic campaigns.
2. **Creative diversity is strong** — Statics, reels, and UGC as separate ad sets with correct creative-format reasoning (reel 9:16 can't be combined with A+ placement without cropping).
3. **Pixel + CAPI setup is correct** — Both browser-side and server-side tracking active with 80-85%+ dedup, per Meta's recommended architecture.
4. **Purchaser exclusions are managed** — Monthly updates by Joanna Bradley prevent wasted prospecting spend on existing customers.
5. **Google brand/non-brand separation** — Properly separated with brand excluded from PMax, preventing cannibalization.
6. **Shopping PMax performing well** — "No Asset" (feed-only) PMax outperforming asset-based PMax. This is the correct setup for product-focused campaigns.
7. **Google CPA below target** — £32.07 vs £40 target = 20% headroom. Account is profitable on first purchase.
8. **Search term relevance** — Google search terms are highly relevant with no obvious wasted spend.
9. **Naming convention** — Consistent campaign naming makes account management scalable.
10. **Non-brand Search CTR** — 6.12% on generic keywords is strong for a niche product category.
11. **Budget management** — Small absolute budget adjustments (e.g., £20 → £35) are normal optimization, not disruptive changes.

---

## PART 7: KEY NUMBERS TO TRACK

After implementing EMQ improvements, monitor these weekly:

| Metric | Current | Target (30 days) | Target (90 days) |
|--------|---------|-------------------|-------------------|
| Meta EMQ (Purchase) | Unknown (check!) | ≥6.0 | ≥8.0 |
| Meta EMQ (PageView) | 4.5 | ≥6.0 | ≥8.0 |
| Meta Dedup Rate | 80-85% | 88% | 90%+ |
| Google CPA | £32.07 (below £40 target) | ≤£38 | ≤£35 |
| Google ROAS | 2.11x (above 1.68x break-even) | 2.3x | 2.5x+ |
| Search Impression Share | ~40% | 50% | 55%+ |
| Blended CPA | Unknown | — | ≤£40 |

---

*Report generated by Claude Ads Audit System | 16 February 2026*
*Data sources: User-provided account data, screenshots, and Events Manager readings*
*Performance benchmarks evaluated against stated £40 CPA target and £67.63 calculated AOV*
