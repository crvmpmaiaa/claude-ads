# Curo Skin — Prioritized Action Plan

**Brand:** Curo Skin (curoskin.co.uk)
**Audit Date:** February 2026
**Aggregate Score:** 52/100 (Grade D — Poor)

---

## Priority Framework

| Priority | Criteria | Timeline |
|----------|----------|----------|
| **Critical** | Revenue/data loss risk; fix immediately | This week |
| **High** | Significant performance drag | Within 7 days |
| **Medium** | Optimization opportunity | Within 30 days |
| **Low** | Best practice, minor impact | Backlog |

---

## Critical Priority (Fix This Week)

### 1. Consolidate from 3 platforms to 2
**Impact:** Eliminates the #1 issue — budget dilution
**Current:** ~$600 Google / ~$800 Meta / ~$600 TikTok
**Recommended:** $0 Google / $1,000-1,200 Meta / $800-1,000 TikTok

**Steps:**
1. Pause all Google Ads campaigns
2. Reallocate Google budget to Meta (primary) and TikTok (secondary)
3. Google revisit threshold: total budget reaches $3,000+/month

**Why:** $600/month on Google cannot generate enough conversions for Smart Bidding. $600/month on TikTok is below the $50/day campaign minimum. Neither platform can exit learning phase. Consolidation is the single most impactful change.

---

### 2. Verify UK GDPR / Consent Mode v2 compliance
**Impact:** Without compliance, 90-95% metric drops + regulatory risk
**Platform:** All platforms (Google priority)

**Steps:**
1. Check cookie consent banner exists on curoskin.co.uk (opt-in required in UK)
2. Verify Consent Mode v2 implementation in Google Tag Manager
3. Confirm consent signals are firing correctly before ad load
4. Ensure privacy policy is linked and accessible on all pages
5. Verify ICO registration if processing personal data at scale

**Risk:** ICO has issued fines exceeding £millions. UK GDPR non-compliance = legal + data loss risk.

---

### 3. Deploy / verify Meta CAPI (Conversions API)
**Impact:** Recovers 30-40% of lost conversion data; 15-20% performance improvement
**Platform:** Meta Ads

**Steps:**
1. In Shopify Admin → Settings → Data sharing → Enable "Maximum" data sharing
2. Verify CAPI events flowing in Meta Events Manager → Overview
3. Check event deduplication (event_id matching) → target 90%+ dedup rate
4. Check Event Match Quality (EMQ) → target ≥8.0 for Purchase event
5. Pass email, phone, fbp, fbc parameters for maximum match quality

**Note:** 87% of advertisers have poor EMQ. This is likely the highest-ROI single fix.

---

### 4. Verify TikTok Pixel + ttclid passback
**Impact:** Without ttclid, most TikTok conversions cannot be attributed
**Platform:** TikTok Ads

**Steps:**
1. Verify TikTok Pixel fires on all pages (especially checkout + thank-you)
2. Confirm ttclid is being captured from URL parameters on landing
3. Verify ttclid is stored in session/cookie
4. Confirm ttclid is sent back with all conversion events (Purchase, AddToCart)
5. Set up Events API (server-side) for data durability

---

### 5. Set up TikTok Shop
**Impact:** TikTok Shop achieves >10% CVR vs 0.46-2.4% standard e-commerce
**Platform:** TikTok Ads

**Steps:**
1. Apply for TikTok Shop UK seller account
2. Connect product catalog (Shopify integration available)
3. Enable Video Shopping Ads (VSA)
4. Tag products in organic TikTok content
5. Enable Spark Ads to boost shop-enabled organic posts

**Why:** Shower filters are a TikTok-native category. TikTok Shop removes friction (in-app purchase). This is Curo Skin's biggest growth opportunity.

---

## High Priority (Fix Within 7 Days)

### 6. Rebuild Meta account structure for $1,000-1,200/month budget
**Impact:** Proper consolidation enables learning phase exit

**Recommended structure:**
```
Meta Ads Account
│
├── Campaign 1: Advantage+ Shopping (ASC)
│   ├── Budget: $800/mo ($27/day)
│   ├── Objective: Sales
│   ├── Bidding: Lowest Cost
│   ├── Optimization: Purchase (switch to AddToCart if <10 purchases/week)
│   ├── Existing Customer Cap: 20%
│   └── Creatives (5-8):
│       ├── UGC: Customer showing skin improvement
│       ├── Demo: Dirty filter after 90 days
│       ├── Award badge: "Marie Claire Best New Skin Tool"
│       ├── Carousel: 3 colors + subscription pricing
│       ├── Video: Installation in 30 seconds
│       └── Review overlay: 4.88/5 stars
│
└── Campaign 2: Testing / Prospecting
    ├── Budget: $200-400/mo ($7-13/day)
    ├── Purpose: Test new creatives and audiences
    ├── Rotate winners into ASC
    └── Kill losers after $20-30 spend with no signal
```

---

### 7. Build creative pipeline (6+ assets)
**Impact:** Creative is 70% of Meta campaign results; TikTok is creative-first

**Production list:**
| Asset | Format | Platform | Priority |
|-------|--------|----------|----------|
| Dirty filter after 90 days (UGC video) | 9:16 video | TikTok + Meta | Immediate |
| Award badge lifestyle image | 4:5 image | Meta | Immediate |
| Customer eczema/dry skin testimonial | 9:16 video | TikTok + Meta | Immediate |
| "What's in your water" educational | 9:16 video | TikTok | Immediate |
| 3-color product carousel | 1:1 carousel | Meta | This week |
| Quick installation demo | 9:16 video | Both | This week |
| "Shower routine" / GRWM | 9:16 video | TikTok | This week |
| Subscription value proposition | 4:5 image | Meta | Next week |

---

### 8. Configure Meta audience architecture
**Impact:** Proper exclusions prevent wasting budget on existing customers

**Steps:**
1. Create Custom Audience: Website visitors (30 days)
2. Create Custom Audience: Purchasers (180 days)
3. Exclude Purchasers from all prospecting campaigns
4. Upload customer email list for Custom Audience + Lookalike
5. Set existing customer cap to 20% in ASC
6. Create interest targeting: Skincare + Hard Water + Eczema + Shower/Bath

---

### 9. Restructure TikTok for proper budget
**Impact:** Proper structure enables learning phase optimization

**Recommended structure (at $800-1,000/month):**
```
TikTok Ads Account
│
├── Campaign 1: Spark Ads — Creator/UGC Content
│   ├── Budget: $600/mo ($20/day)
│   ├── Objective: Website Conversions (or TikTok Shop)
│   ├── Bidding: Lowest Cost
│   ├── Search Ads Toggle: ON
│   │
│   └── Ad Group 1: Skincare & Wellness Audience
│       ├── Targeting: Skincare, Hair care, Hard water, Eczema interests
│       ├── Age: 18-45
│       ├── Location: United Kingdom
│       └── Creatives: 6+ native-style videos
│
└── Campaign 2: TikTok Shop (if approved)
    ├── Budget: $400/mo
    ├── Video Shopping Ads (VSA)
    └── Product catalog linked
```

**Note:** Even at $800/month, this is below the $1,500 ideal minimum. Consider starting with TikTok Shop only (free organic reach) while building ad budget.

---

### 10. Enable Google Enhanced Conversions (if keeping Google)
**Impact:** ~10% more measured conversions
**Time:** 5 minutes

**Steps:**
1. Google Ads → Goals → Conversions → Settings
2. Turn on Enhanced Conversions
3. Select tag-based method (easiest with Shopify)
4. Verify hashed data (email, phone) is being sent

---

## Medium Priority (Fix Within 30 Days)

### 11. Add UTM parameters to all Meta and TikTok ads
**Impact:** Enables GA4 cross-channel attribution
**Steps:**
1. Meta: Campaign Settings → URL Parameters → Add UTM template
2. TikTok: Ad-level URL tracking → Add UTM parameters
3. Format: `utm_source=meta&utm_medium=paid&utm_campaign={{campaign.name}}`

---

### 12. Optimize Meta ad copy with award authority
**Impact:** Marie Claire, Glamour, WIRED badges = instant credibility vs Hello Klean

**Headline angles to test:**
- "Marie Claire's Best New Skin Tool 2025"
- "The Award-Winning Shower That Changed My Skin"
- "5 Awards. 4.88/5 Stars. 99% Chlorine Removed."
- "From 33p/Day: The Shower Filter Behind Softer Skin & Hair"
- "Why 100+ Customers Rate Us 4.88 Stars"

**CTA angles:**
- "Try Risk-Free for 60 Days"
- "Join 100+ Happy Customers"
- "Your Best Skin Starts in the Shower"

---

### 13. Set up Meta Advantage+ Sales campaign (if not already)
**Impact:** ASC achieves median ROAS of 4.52 — highest-performing campaign type

**Steps:**
1. Create new campaign → Select "Sales" objective → Toggle "Advantage+ Shopping"
2. Set existing customer cap: 20%
3. Upload 5-8 diverse creatives
4. Set budget to 60-70% of total Meta spend
5. Let run for 7 days minimum before judging

---

### 14. Implement post-purchase survey
**Impact:** Fills ~30% of attribution gap that tracking misses

**Steps:**
1. Add to Shopify order confirmation page
2. Question: "How did you first hear about Curo Skin?"
3. Options: TikTok, Instagram/Facebook, Google Search, Friend/Family, Magazine/PR, Other
4. Track monthly to validate platform-reported conversions

---

### 15. Set up email/SMS for subscription retention
**Impact:** Reduces churn on 90-day filter subscription; increases LTV

**Flows:**
1. Welcome series (post-purchase): Installation tips, expected results timeline
2. Filter reminder (day 75): "Your filter is due for replacement"
3. Reorder prompt (day 85): "Don't let your skin suffer — auto-ship savings"
4. Win-back (day 120 if no reorder): "We miss you — 20% off your next filter"

---

## Low Priority (Backlog)

### 16. Schema markup on product pages
**Impact:** Improved Google search appearance (when Google ads restart)

### 17. Landing page speed audit
**Impact:** 1-second delay = 7% fewer conversions
**Check:** curoskin.co.uk mobile LCP target <2.5 seconds

### 18. Competitor ad monitoring
**Impact:** Track Hello Klean, Water2, Jolie ad strategies monthly
**Tool:** Meta Ad Library, TikTok Creative Center

### 19. Test Microsoft Ads (future)
**Impact:** 20-35% lower CPCs than Google; older/higher-income audience
**When:** Total budget reaches $3,000+/month

### 20. Incrementality testing
**Impact:** Validates true contribution of each platform
**When:** Total budget reaches $5,000+/month; geo-lift test with holdout regions

---

## Implementation Timeline

```
Week 1 (Critical):
  ✓ Pause Google Ads, reallocate budget
  ✓ Verify UK GDPR / Consent Mode compliance
  ✓ Deploy/verify Meta CAPI
  ✓ Verify TikTok Pixel + ttclid
  ✓ Apply for TikTok Shop

Week 2 (High):
  ✓ Rebuild Meta account structure
  ✓ Produce first 4 creative assets
  ✓ Configure Meta audience architecture
  ✓ Restructure TikTok campaigns

Week 3-4 (Medium):
  ✓ Add UTM parameters everywhere
  ✓ Launch ASC on Meta
  ✓ Set up post-purchase survey
  ✓ Begin email/SMS retention flows
  ✓ Produce remaining creative assets

Month 2+:
  ✓ Monitor and optimize weekly
  ✓ Refresh creative every 3-4 weeks
  ✓ Scale winning campaigns by 20% increments
  ✓ Evaluate Google re-entry when budget grows
```

---

## Budget Growth Roadmap

| Budget Level | Platform Mix | Key Milestone |
|-------------|-------------|---------------|
| **$2,000/mo (current)** | Meta 55% + TikTok 45% | Prove DTC profitability |
| **$3,000/mo** | Meta 50% + TikTok 30% + Google 20% | Add Google Brand + PMax |
| **$5,000/mo** | Meta 45% + TikTok 25% + Google 30% | Scale all platforms |
| **$10,000/mo** | Meta 40% + Google 30% + TikTok 20% + Microsoft 10% | Full platform coverage |

**Target:** Reinvest 10-15% of DTC revenue into ad spend for sustainable growth.
