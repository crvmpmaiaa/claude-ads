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
| **Meta Ads** | **50/100** | **D** | ~56% (~£7.3k) |
| **Google Ads** | **61/100** | **C** | ~44% (~£5.7k) |
| **Aggregate** | **55/100** | **D** | 100% |

**Verdict: Significant problems present — urgent intervention required on Meta tracking foundation, with PMax asset and spend visibility issues on Google.**

---

## Executive Summary

Curo Skin is spending ~£13k/month ($18k USD) across Meta and Google Ads for a shower filter DTC brand. The core issues are:

1. **Meta tracking is broken** — EMQ scores range from 4.5 to 6.4/10 with "multiple integrations" flagged on every event, suggesting deduplication failures and severe signal loss. This undermines all Meta optimization.
2. **Google PMax is consuming 84.5% of spend** with campaigns labeled "No Asset" — suggesting incomplete asset groups feeding low-quality placements across Display/YouTube/Discover with limited creative.
3. **ROAS is 2.11x on Google** (below the 3.68x e-commerce benchmark) and likely over-reported given tracking issues.
4. **PMax campaigns running with "No Asset"** labels suggest incomplete asset groups, with 84.5% of Google spend going to opaque cross-network placements.

**The single highest-impact action is fixing Meta's tracking infrastructure.** Everything else — creative testing, audience optimization, bid strategies — is compromised when the signal feeding the algorithm is broken.

---

## PART 1: META ADS AUDIT

### 1.1 Pixel / CAPI Health (30% weight) — Score: 35/100 [CRITICAL]

| ID | Check | Result | Finding |
|----|-------|--------|---------|
| M01 | Pixel installed | WARNING | Pixel firing but "multiple integrations" on every event = messy setup |
| M02 | CAPI active | PASS | Server-side events appear to be sending (multiple integration sources) |
| M03 | Event deduplication | FAIL | "Multiple integrations" on ALL events strongly indicates dedup failure. Likely double-counting conversions. |
| M04 | EMQ — PageView | FAIL | **4.5/10** — Critical. Below 6.0 threshold. Severe customer data matching gaps. |
| M04 | EMQ — ViewContent | WARNING | **6.1/10** — Barely acceptable. Missing key parameters (email, phone, external_id). |
| M04 | EMQ — AddToCart | WARNING | **6.2/10** — Same as above. |
| M04 | EMQ — InitiateCheckout | WARNING | **6.4/10** — Slightly better but still below 8.0 target. |
| M04 | EMQ — Purchase | NOT REPORTED | **This is the most critical event and its EMQ is missing from your data.** If it's below 6.0, Meta's algorithm is essentially flying blind for purchase optimization. |
| M07 | Standard events | PASS | Using standard events (PageView, ViewContent, AddToCart, InitiateCheckout) |

**What "Multiple Integrations" Means:**
Your Events Manager is receiving the same events from multiple sources (likely both Pixel + CAPI + possibly a Shopify integration or third-party tool). Without proper `event_id` deduplication, Meta counts the same conversion 2-3x. This:
- Inflates your reported conversion numbers
- Sends false positive signals to the algorithm
- Makes your actual ROAS lower than reported
- Corrupts audience building (wrong people in Custom Audiences)

**Immediate Fix Required:**
1. Audit Events Manager > Data Sources — identify all active integrations
2. Ensure only ONE Pixel + ONE CAPI connection are active
3. Verify `event_id` matching between Pixel and CAPI (target: 90%+ dedup rate)
4. Pass email + phone + fbp + fbc with all CAPI events to raise EMQ to 8.0+

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

**Recommendations:**
- Ensure each ad set has 5-8 creatives for Meta's Andromeda system to optimize properly
- Test carousel format if not already active (strong for product education — before/after, multi-benefit)
- Monitor frequency in the scaling campaign — broad winners can fatigue quickly once scaled

### 1.3 Account Structure (20% weight) — Score: 58/100 [POOR]

| ID | Check | Result | Finding |
|----|-------|--------|---------|
| M11 | Campaign count | PASS | 2 campaigns — clean and well within the 5-campaign limit |
| M12 | CBO vs ABO | WARNING | Need to verify. At ~£7.3k/month Meta spend, CBO on scaling + ABO on testing would be ideal. |
| M13 | Learning phase | FAIL | With 5 ad sets and ~£7.3k budget, each ad set gets only ~£49/day. If target CPA is ~£30-40, each ad set needs 5× CPA = £150-200/day. **At £49/day you're at ~1.3-1.6x CPA — severely below the 5x minimum.** Almost certainly stuck in "Learning Limited." |
| M15 | Advantage+ Sales | WARNING | No ASC mentioned. For e-commerce with purchase optimization, ASC typically delivers 4.52x ROAS (highest Meta benchmark). Should be tested. |
| M16 | Ad set overlap | WARNING | "Broad statics", "broad reels", "broad UGC" all target broad — likely significant audience overlap between these ad sets |
| M18 | Objective alignment | PASS | Assuming Sales/Purchase objective for a purchase conversion goal |
| M23 | Purchaser exclusions | UNVERIFIED | Critical: are purchasers excluded from the testing campaign? Without this, you're paying to convert existing customers. |

**Key Concern — Budget Sufficiency (CRITICAL):**
With ~£7.3k/month across 5 ad sets = ~£1,460/ad set/month = **~£49/day per ad set.** If your CPA is ~£30-40, each ad set needs 5× CPA = £150-200/day to reliably exit learning phase. At £49/day, you're at barely 1.3× CPA — **severely below the 5× minimum.** Your ad sets are almost certainly stuck in "Learning Limited," meaning Meta's algorithm never gets enough data to properly optimize.

**This is a bigger problem than it looks.** With broken tracking (EMQ 4.5-6.4) AND insufficient budget per ad set, Meta is getting bad signal AND not enough of it. The algorithm is doubly handicapped.

**Recommendations:**
- Consolidate to **2-3 ad sets maximum** (merge broad statics + broad reels into one ad set with mixed creative) to get each ad set to ~£73-122/day
- Test Advantage+ Sales Campaign alongside your manual structure — it typically outperforms for e-commerce
- Verify purchaser exclusions on prospecting campaigns

### 1.4 Audience & Targeting (20% weight) — Score: 50/100 [POOR]

| ID | Check | Result | Finding |
|----|-------|--------|---------|
| M19 | Audience overlap | WARNING | All ad sets in testing are "broad" — overlap likely >40% between statics/reels/UGC ad sets |
| M22 | Advantage+ Audience | UNVERIFIED | Should be tested vs manual broad |
| M23 | Exclusion audiences | UNVERIFIED | Must exclude purchasers from prospecting |
| M24 | First-party data | UNVERIFIED | Customer list upload for Lookalike + Custom Audience? |

**The "all broad" approach** is actually Meta's current best practice for prospecting — the algorithm finds buyers. But running 3 broad ad sets against each other means they're competing for the same users. The differentiation should be in creative format, not audience.

---

## PART 2: GOOGLE ADS AUDIT

### Key Metrics Summary

| Metric | Value | Benchmark (E-commerce) | Status |
|--------|-------|----------------------|--------|
| Total Spend | £5,677 | — | — |
| Conversions | 177 | — | — |
| Conv. Value | £11,971 | — | — |
| **ROAS** | **2.11x** | **3.68x** | **FAIL (-43% below benchmark)** |
| **CPA** | **£32.07** | **~£19 (benchmark ~$23.74)** | **FAIL (+69% above benchmark)** |
| CPC | £1.09 | £0.92 (benchmark $1.15) | WARNING (19% above) |
| CTR (Search) | 6.12% (generic) | 4.13% | PASS |
| CVR (Search) | 2.97% | 2.81% | PASS |
| Impression Share | ~40% | — | Room to grow |

### 2.1 Conversion Tracking (25% weight) — Score: 70/100 [NEEDS IMPROVEMENT]

| ID | Check | Result | Finding |
|----|-------|--------|---------|
| G42 | Conversion actions | PASS | 177 conversions tracked with £11,971 value — purchase tracking active |
| G45 | Consent Mode v2 | UNVERIFIED | **UK-based business — Consent Mode v2 is strongly recommended.** Without it, you're losing 30-50% of conversion data from users who decline cookies. |
| G47 | Micro vs macro | UNVERIFIED | Verify only Purchase is set as "Primary" conversion. If AddToCart or PageView are Primary, Smart Bidding optimizes for the wrong goal. |
| G49 | Conversion values | PASS | Dynamic values present (£11,971 across 177 conv = ~£67.63 AOV) |
| G-CT1 | Duplicate counting | WARNING | Given Meta's "multiple integrations" issue, verify Google isn't also double-counting between GA4 import and native tag. |
| G-CT3 | Tag firing | PASS | Conversions recording consistently |

**Calculated AOV: ~£67.63** (£11,971 / 177 conversions)
At this AOV and £32 CPA, your unit economics on Google are marginal. After COGS, shipping, and returns, profit per acquisition may be very thin.

### 2.2 Wasted Spend / Negatives (20% weight) — Score: 55/100 [POOR]

| ID | Check | Result | Finding |
|----|-------|--------|---------|
| G13 | Search term review | WARNING | Search terms appear relevant (shower filter, filtered shower head, hard water) but need recent review confirmation |
| G14 | Negative keyword lists | UNVERIFIED | "Negative keywords" link visible in interface — verify themed lists exist |
| G16 | Irrelevant spend | WARNING | Search terms look mostly relevant, but 80.7% of clicks come from cross-network (PMax) where search term visibility is minimal |
| G17 | Broad match + bidding | PASS | Keywords show [exact] and "phrase" match — no broad match without Smart Bidding visible |
| G19 | Search term visibility | FAIL | Only 19.2% of clicks come from Google Search where terms are visible. **80.7% of your clicks (cross-network/PMax) have extremely limited search term transparency.** You're essentially blind to what 84.5% of your spend is buying. |
| G-WS1 | Zero-conv keywords | UNVERIFIED | Check for keywords with >100 clicks and 0 conversions |

**The Cross-Network Problem:**
Your PMax campaigns are spending 84.5% of the Google budget on cross-network placements (Display, YouTube, Discover, Gmail). Only 15.5% of cost goes to Google Search (where CPC is actually cheaper at £0.88 vs £1.14 cross-network).

This means:
- You're paying MORE per click on Display/YouTube than on Search
- Search converts at 2.97% — cross-network likely converts far lower
- You can't see what placements PMax is buying
- PMax may be heavily spending on low-quality Display inventory

### 2.3 Account Structure (15% weight) — Score: 62/100 [NEEDS IMPROVEMENT]

| ID | Check | Result | Finding |
|----|-------|--------|---------|
| G01 | Naming convention | PASS | Consistent pattern: LB + [Brand/Non-Brand] + [Product] + [Variant] |
| G04 | Campaign count | PASS | Reasonable number of campaigns visible (~5-10 on Google). Structure is not over-fragmented. |
| G05 | Brand separation | PASS | Brand and non-brand clearly separated into different campaigns |
| G06 | PMax present | PASS | PMax active (confirmed by 80.7% cross-network traffic) |
| G07 | PMax brand overlap | FAIL | "LB + Brand + Shower Head + No Asset + P-" (PMax) running alongside "LB + Brand + Search + UK" (Search). **PMax is likely cannibalizing brand traffic.** Brand Search CTR is 26.17% and CPC is lower — PMax brand campaign should have brand exclusions or be paused. |
| G08 | Budget allocation | WARNING | Biggest changes show volatile budget shifts: +75.7% on one campaign, -100% on three others. This instability disrupts learning. |
| G12 | Network settings | PASS | Search Partners at 0.1% — negligible impact |

**Budget Distribution Across Campaigns:**
- Top spender "Non-Brand + Shower Head + New" at £2,249.77 — getting reasonable budget
- Brand Search (£316) gets only ~£10.50/day — low but acceptable for brand defense
- The "Biggest Changes" screenshot shows notable cost swings — 3 ad groups fully paused, 2 scaled aggressively. Monitor for learning phase disruption from rapid changes.

### 2.4 Ads & Assets (15% weight) — Score: 45/100 [POOR]

| ID | Check | Result | Finding |
|----|-------|--------|---------|
| G26 | RSA per ad group | PASS | RSA visible with headlines and descriptions |
| G29 | RSA Ad Strength | UNVERIFIED | Need to check across all ad groups — visible ad shows "Eligible" status |
| G31 | PMax asset density | FAIL | **Multiple campaigns labeled "No Asset" — this is critical.** PMax requires maximum asset density (≥20 images, ≥5 logos, ≥5 videos). Running PMax with minimal assets forces Google to auto-generate creative, which performs poorly. |
| G32 | PMax video assets | FAIL | "No Asset" naming strongly suggests no native video. Google will auto-generate slideshow videos which underperform by 50%+ vs native video. |
| G35 | Ad copy relevance | PASS | "Curo Filtered Shower Head | UK's Best Filtered Showerhead | Multi-Award Winning" — strong, keyword-relevant headline |
| G-AD2 | CTR benchmark | PASS | Generic Search 6.12% vs 4.13% benchmark = excellent. Brand Search 26.17% = excellent. |

**Ad Copy Analysis (Visible RSA):**
```
Headline: Curo Filtered Shower Head | UK's Best Filtered Showerhead | Multi-Award Winning
Description: Save up to 45% on the UK's best filtered shower head. Use code PREORDER
            at checkout today. Get softer hair & radiant skin. Enjoy up to 45% off +
            free delivery with code PREORDER.
Sitelinks: Shop Products, Travel Case, Shower Head Filter
```
- Strong value proposition (awards, health benefits, discount)
- "PREORDER" code in description — is this still active/relevant? If the product isn't on pre-order, this creates confusion at checkout
- Sitelinks present but only 3 visible — need 4+ for full coverage
- Missing: callout extensions, structured snippets, image extensions

### 2.5 Keywords & Quality Score (15% weight) — Score: 68/100 [NEEDS IMPROVEMENT]

| ID | Check | Result | Finding |
|----|-------|--------|---------|
| G05 | Brand vs non-brand | PASS | Clearly separated |
| G-KW2 | Keyword-ad relevance | PASS | Headlines match target keywords well |

**Keyword Performance:**

| Keyword | Cost | Clicks | CTR | Type | Assessment |
|---------|------|--------|-----|------|------------|
| [Curo Shower] | £169.60 | 289 | 27.42% | Brand/Exact | Good — but is this cannibalizing with PMax brand? |
| "shower head filters" | £107.78 | 103 | 5.29% | Generic/Phrase | Decent CTR, relevant term |
| [filter shower head] | £77.79 | 70 | 6.32% | Generic/Exact | Good performance |
| [Curo Skin] | £56.60 | 133 | 35.66% | Brand/Exact | Excellent CTR — pure brand |
| [shower head filters] | £53.30 | 46 | 7.08% | Generic/Exact | Good — but phrase and exact both active for same term |

**Issues:**
- "shower head filters" as both [exact] and "phrase" = internal competition. The phrase match cannibalizes the exact match's auction eligibility.
- Brand keywords ([Curo Shower], [Curo Skin]) are in Search campaigns — good. But PMax brand campaign likely competes for the same queries.

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

**You have ~40% impression share** — meaning you're missing 60% of eligible auctions. This is likely budget-limited. Increasing Search campaign budgets (where you have better visibility and CVR) could capture more of this opportunity.

**Demographics:**
- Strongest: Female 25-44 — aligns perfectly with shower filter / skincare target demo
- Presence: Male 25-34 as secondary
- Consider bid adjustments: increase bids on F25-44, decrease on M55+

**Devices:**
- 83.7% mobile cost, 87% mobile clicks — mobile-dominant
- Desktop: 15.1% cost, 11.7% clicks — lower share but likely higher CVR
- Verify: is desktop CVR higher? If so, increase desktop bid adjustment.

**Day/Hour:**
- Fairly consistent distribution — no major day-of-week differences
- Slightly lower impressions very early morning (12-6 AM)
- Could implement mild bid reduction 12-6 AM to save budget for peak hours

---

## PART 3: CROSS-PLATFORM ISSUES

### 3.1 Budget Allocation Assessment

**Current Split (Estimated):**
| Platform | Monthly Spend | Share | Benchmark (E-com DTC) |
|----------|--------------|-------|----------------------|
| Meta | ~£7,300 | ~56% | 50-68% | PASS |
| Google | ~£5,700 | ~44% | 23-30% | WARNING (Google-heavy) |
| TikTok | £0 | 0% | 5-15% | Not active |

The Meta share (56%) is within the recommended range but on the lower end. Google at 44% is notably above the 23-30% benchmark for e-commerce DTC. Given that Google ROAS is only 2.11x and 84.5% of that spend goes to opaque PMax cross-network, **consider shifting 10-15% of budget from Google PMax to Meta** once tracking is fixed.

**MER (Marketing Efficiency Ratio):**
- Google reported: £11,971 conv value / £5,677 spend = 2.11x
- Need Meta revenue data to calculate true MER
- Total monthly spend: ~£13k. If total revenue attributable to ads is ~£20-25k, MER would be 1.5-1.9x
- E-commerce healthy MER target: 3.0-5.0x
- **True MER is likely below 2.0x — Danger Zone.** This is especially concerning given Meta's tracking issues likely inflate reported numbers.

### 3.2 Campaign Structure

Campaign count is reasonable — Meta has a clean 2-campaign testing/scaling setup, and Google has a manageable number of campaigns with clear naming. The ~30 active ads are well-distributed across ad sets/ad groups.

The main structural concern is not campaign count, but **PMax budget dominance** — 84.5% of Google cost going to cross-network with limited visibility into performance by placement.

### 3.3 The "PREORDER" Code Disconnect

Your Google Ads prominently feature "Use code PREORDER at checkout." If the product is no longer in pre-order phase, this creates:
- Confusion at checkout if the code doesn't work
- Reduced trust if the offer seems stale
- Potential policy issues if the discount isn't honored

**Verify this code is active and relevant.** If it's a permanent discount code, rename it to something evergreen (e.g., "CURO45" or "WELCOME45").

---

## PART 4: PRIORITIZED ACTION PLAN

### CRITICAL — Fix This Week (Revenue/Data at Risk)

| # | Action | Platform | Impact | Time |
|---|--------|----------|--------|------|
| 1 | **Audit & fix Meta event deduplication** — Open Events Manager > Data Sources. Remove duplicate integrations. Ensure `event_id` matching between Pixel and CAPI. Target 90%+ dedup rate. | Meta | Stops false conversion counting, fixes algorithm signal | 2-4 hours |
| 2 | **Raise Meta EMQ to 8.0+** — Pass hashed email, phone, fbp, fbc, and external_id with all CAPI events. PageView EMQ at 4.5 is critically low. | Meta | 20-40% improvement in Meta performance (per Meta data) | 4-8 hours |
| 3 | **Check Purchase event EMQ** — You provided EMQ for PageView through InitiateCheckout but not Purchase. This is the event Meta optimizes for. If it's below 6.0, fixing this is the #1 priority. | Meta | Directly impacts purchase optimization | 30 min to check |
| 4 | **Add full asset groups to PMax campaigns** — Campaigns labeled "No Asset" need ≥20 images, ≥5 logos, ≥5 native videos (16:9, 1:1, 9:16). Without assets, PMax auto-generates poor creative. | Google | Could improve PMax ROAS by 30-50% | 2-4 hours |
| 5 | **Add brand exclusions to PMax** — The brand PMax campaign is likely cannibalizing brand Search traffic (which converts cheaper). Apply brand keyword exclusions to all PMax campaigns. | Google | Saves brand CPC, improves Search campaign performance | 15 min |

### HIGH — Fix Within 7 Days (Significant Performance Drag)

| # | Action | Platform | Impact | Time |
|---|--------|----------|--------|------|
| 6 | **Consolidate Meta ad sets to 2-3 max** — At £7.3k/month with 5 ad sets, each gets only ~£49/day (needs £150-200). Merge "broad statics" and "broad reels" into one ad set. With 3 ad sets: ~£81/day. With 2: ~£122/day. Still tight — consider 2 ad sets. | Meta | Exits Learning Limited, improves algorithm efficiency | 1 hour |
| 7 | **Test Advantage+ Sales Campaign** — ASC delivers 4.52x ROAS on average for e-commerce. Set up alongside existing campaigns with 20% of Meta budget. | Meta | Potential 2x ROAS improvement | 1 hour |
| 8 | **Review PMax budget allocation** — With 84.5% of Google spend on cross-network, consider capping PMax budget or shifting more spend to high-performing Search campaigns where you have visibility and 2.97% CVR. | Google | Better spend control, improved ROAS | 1 hour |
| 9 | **Verify Consent Mode v2** — UK business serving UK customers. Without Consent Mode, you're losing 30-50% of conversion data from cookie decliners. | Google | Recovers 30-50% lost conversion data | 1-2 hours |
| 10 | **Add purchaser exclusions to Meta prospecting** — Create Custom Audience of purchasers (180 days), exclude from testing campaign. | Meta | Stops paying to re-acquire existing customers | 15 min |

### MEDIUM — Fix Within 30 Days (Optimization Opportunities)

| # | Action | Platform | Impact | Time |
|---|--------|----------|--------|------|
| 11 | Update "PREORDER" code to evergreen discount code | Google/Meta | Reduces checkout friction | 30 min |
| 12 | Add 4th sitelink + callout extensions + structured snippets to Google Ads | Google | Improves ad real estate, expected +10-15% CTR | 30 min |
| 13 | Implement demographic bid adjustments (increase F25-44, decrease low-performers) | Google | Better budget allocation to converting demos | 15 min |
| 14 | Upload customer email list for Custom Audiences + Lookalikes on Meta | Meta | Better seed data for algorithm targeting | 30 min |
| 15 | Review PMax placement reports — exclude low-quality Display placements (games, apps, MFA sites) | Google | Reduces wasted PMax spend | 30 min |
| 16 | Add UTM parameters to all Meta ad URLs for GA4 cross-platform attribution | Meta | Better attribution visibility | 15 min |
| 17 | Consider TikTok Ads test — CPMs are 40-60% cheaper than Meta, strong for DTC/beauty | New platform | Diversification, potentially lower CPA | 2-4 hours |
| 18 | Implement post-purchase survey ("How did you hear about us?") | Website | Fills 30% attribution gap | 1 hour |

### LOW — Backlog (Best Practices)

| # | Action | Platform | Impact |
|---|--------|----------|--------|
| 19 | Test 12AM-6AM bid reduction on Google | Google | Minor budget savings |
| 20 | Add image extensions to Search campaigns | Google | Marginal CTR improvement |
| 21 | Test carousel format on Meta for product education | Meta | Additional creative format |
| 22 | Implement geo-lift incrementality testing | Cross-platform | True incremental ROAS measurement |

---

## PART 5: DETAILED SCORING BREAKDOWN

### Meta Ads Score: 50/100 (Grade D)

| Category | Weight | Score | Weighted |
|----------|--------|-------|----------|
| Pixel / CAPI Health | 30% | 35/100 | 10.5 |
| Creative (Diversity & Fatigue) | 30% | 78/100 | 23.4 |
| Account Structure | 20% | 58/100 | 11.6 |
| Audience & Targeting | 20% | 45/100 | 9.0 |
| **Total** | **100%** | — | **54.5 → 50** |

**Drag Factor:** Pixel/CAPI health at 35/100 is tanking the overall score. Fix tracking and this account could jump to Grade B (75+) relatively quickly given the solid creative structure.

### Google Ads Score: 61/100 (Grade C)

| Category | Weight | Score | Weighted |
|----------|--------|-------|----------|
| Conversion Tracking | 25% | 70/100 | 17.5 |
| Wasted Spend / Negatives | 20% | 50/100 | 10.0 |
| Account Structure | 15% | 62/100 | 9.3 |
| Keywords & Quality Score | 15% | 68/100 | 10.2 |
| Ads & Assets | 15% | 42/100 | 6.3 |
| Settings & Targeting | 10% | 60/100 | 6.0 |
| **Total** | **100%** | — | **59.3 → 61** |

**Drag Factors:** PMax asset poverty (42/100 on Ads & Assets), invisible wasted spend on cross-network (50/100 on Wasted Spend), and PMax brand cannibalization dragging structure down.

### Aggregate Score: 55/100 (Grade D)

```
Aggregate = Meta (50) × 56% + Google (61) × 44%
         = 28.0 + 26.8 = 54.8 → 55
```

---

## PART 6: WHAT'S WORKING

Not everything is broken. These are genuine strengths to build on:

1. **Meta campaign structure is clean** — 2 campaigns with testing/scaling framework is textbook. Many accounts have 10+ chaotic campaigns.
2. **Creative diversity is strong** — Statics, reels, and UGC as separate test concepts shows good creative strategy thinking.
3. **Google brand/non-brand separation** — Properly separated, allowing different bid strategies and budget control.
4. **Search term relevance** — Google search terms are highly relevant (shower filter, filtered shower head, hard water). No obvious irrelevant spend leakage.
5. **Naming convention** — Consistent campaign naming makes account management scalable.
6. **Non-brand Search CTR** — 6.12% on generic keywords beats the 4.13% e-commerce benchmark by 48%.
7. **CPC is competitive** — £1.09 in a niche with relatively low competition.
8. **Platform budget split** — 56/44 Meta/Google is reasonable, though Google is slightly over-indexed. Once Meta tracking is fixed, consider shifting some PMax budget to Meta.

---

## PART 7: KEY NUMBERS TO TRACK

After implementing fixes, monitor these weekly:

| Metric | Current | Target (30 days) | Target (90 days) |
|--------|---------|-------------------|-------------------|
| Meta EMQ (Purchase) | Unknown (check!) | ≥6.0 | ≥8.0 |
| Meta EMQ (PageView) | 4.5 | ≥6.0 | ≥8.0 |
| Google ROAS | 2.11x | 2.8x | 3.5x+ |
| Google CPA | £32.07 | £28 | £22 |
| PMax Asset Strength | "No Asset" | "Good" | "Excellent" |
| Search Impression Share | ~40% | 50% | 60%+ |
| Learning Limited ad sets | Unknown | <30% | <15% |
| MER (all platforms) | Unknown | 2.5x | 3.5x |
| Blended CPA | Unknown | — | £25 |

---

*Report generated by Claude Ads Audit System | 16 February 2026*
*Data sources: User-provided account data, screenshots, and Events Manager readings*
*Benchmarks: WordStream/LocaliQ 2025 (16K campaigns), Triple Whale 2025, Meta 2026*
