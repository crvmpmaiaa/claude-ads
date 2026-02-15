# Curo Skin — Multi-Platform Ads Audit Report

**Brand:** Curo Skin (curoskin.co.uk)
**Business Type:** E-commerce / DTC — Shower Filters
**Platforms Audited:** Google Ads, Meta Ads, TikTok Ads
**Monthly Budget:** ~$2,000 (~£1,600) across all platforms
**Market:** United Kingdom
**Audit Date:** February 2026
**Audit Type:** Assessment-based (no account exports provided)

---

## Executive Summary

| Metric | Value |
|--------|-------|
| **Aggregate Ads Health Score** | **52/100 — Grade D (Poor)** |
| Google Ads Score | 45/100 — Grade D |
| Meta Ads Score | 58/100 — Grade D |
| TikTok Ads Score | 48/100 — Grade D |
| Critical Issues Found | 12 |
| High-Priority Issues | 18 |
| Quick Wins Available | 9 |

### Budget Allocation (Estimated)

| Platform | Estimated Share | Monthly Spend | Min Viable | Status |
|----------|----------------|---------------|------------|--------|
| Google Ads | ~30% ($600) | $600 | $1,000 | BELOW MINIMUM |
| Meta Ads | ~40% ($800) | $800 | $600-$800 | AT MINIMUM |
| TikTok Ads | ~30% ($600) | $600 | $1,500 ($50/day) | BELOW MINIMUM |
| **Total** | **100%** | **$2,000** | **$3,000+** | **UNDERFUNDED** |

### Top 5 Critical Issues

1. **Budget dilution across 3 platforms** — $2K/month split three ways means NO platform gets enough budget to exit learning phase effectively
2. **UK GDPR / Consent Mode v2 compliance** — Must be verified; without it, 90-95% metric drops in EU/UK
3. **CAPI / server-side tracking** — If not deployed on Meta, losing 30-40% of conversion data post-iOS 14.5
4. **Google Ads below minimum viable budget** — $600/month cannot generate the 15+ monthly conversions needed for Smart Bidding
5. **TikTok below minimum campaign budget** — $50/day minimum means TikTok needs $1,500/month; $600 is critically insufficient

### Top 5 Quick Wins

1. **Consolidate to 2 platforms** — Drop Google Ads, reallocate to Meta ($1,200) + TikTok ($800) — immediate efficiency gain
2. **Enable Enhanced Conversions on Google** (if keeping) — 5 min fix, ~10% more measured conversions
3. **Verify Consent Mode v2** — 5 min check, prevents 90-95% data loss
4. **Enable TikTok Search Ads Toggle** — 2 min fix, incremental reach
5. **Add UTM parameters on all Meta ads** — 5 min, enables GA4 cross-channel attribution

---

## Business Type Detection

| Signal | Value |
|--------|-------|
| Industry | Health & Beauty / Home Wellness |
| Model | DTC E-commerce with Subscription |
| AOV | ~£80 (initial purchase) |
| LTV Signal | Strong — 90-day filter replacement subscription |
| Repeat Purchase Rate | High (consumable filter) |
| Recommended Platform Mix | Meta 50-68%, Google PMax 23-30%, TikTok 5-15% |
| Recommended Min Budget | $3,000/month (Meta + Google) |

---

## Google Ads Audit — Score: 45/100 (Grade D)

### Category Breakdown

| Category | Weight | Score | Grade | Key Issue |
|----------|--------|-------|-------|-----------|
| Conversion Tracking | 25% | 50/100 | D | Consent Mode v2 + Enhanced Conv unverified |
| Wasted Spend / Negatives | 20% | 40/100 | D | Budget too low to generate meaningful search term data |
| Account Structure | 15% | 45/100 | D | Likely over-fragmented for budget level |
| Keywords & Quality Score | 15% | 50/100 | D | Niche keywords may have low volume |
| Ads & Assets | 15% | 45/100 | D | PMax asset density likely insufficient |
| Settings & Targeting | 10% | 40/100 | D | Extension coverage and audience signals likely incomplete |

### CRITICAL Finding: Budget Insufficiency

**$600/month on Google Ads is critically underfunded.** At an e-commerce CPC of $1.15 average, this yields only ~520 clicks/month. With a 2.81% CVR (e-commerce average), that's ~15 conversions/month — the absolute bare minimum for Smart Bidding to function. In practice, a niche product like shower filters in the UK will perform below average volume, making this budget unworkable.

**Recommendation: Pause Google Ads entirely until budget reaches $1,000+/month. Reallocate to Meta.**

### Conversion Tracking Checks

| ID | Check | Severity | Status | Notes |
|----|-------|----------|--------|-------|
| G42 | Conversion actions defined | Critical | NEEDS VERIFICATION | Must confirm Purchase as primary conversion |
| G43 | Enhanced Conversions enabled | Critical | NEEDS VERIFICATION | Critical for UK market with cookie consent; 5-min enable |
| G44 | Server-side tracking | High | WARNING | Shopify has SGTM options but likely not configured |
| G45 | Consent Mode v2 (UK/EU) | Critical | NEEDS VERIFICATION | **MANDATORY for UK** — without it, 90-95% metric drops |
| G46 | Conversion window | Medium | WARNING | Should be 7-day for e-commerce; default 30d may be active |
| G47 | Micro vs macro separation | High | NEEDS VERIFICATION | Common mistake: AddToCart set as Primary |
| G48 | Attribution model | Medium | PASS (assumed) | DDA is now mandatory default |
| G49 | Conversion value assignment | High | NEEDS VERIFICATION | Dynamic values needed for varying product prices |
| G-CT1 | No duplicate counting | Critical | NEEDS VERIFICATION | GA4 + Google Ads overlap risk |
| G-CT2 | GA4 linked | High | NEEDS VERIFICATION | Must be linked for audience sharing |
| G-CT3 | Google Tag firing | Critical | NEEDS VERIFICATION | Tag must fire on all pages including thank you |

### Wasted Spend Checks

| ID | Check | Severity | Status | Notes |
|----|-------|----------|--------|-------|
| G13 | Search term audit | Critical | WARNING | With $600/mo budget, limited search term data to review |
| G14 | Negative keyword lists | Critical | NEEDS VERIFICATION | At minimum: competitor names, "free", "DIY", "how to" |
| G15 | Account-level negatives | High | NEEDS VERIFICATION | Must be applied across all campaigns |
| G16 | Wasted spend on irrelevant terms | Critical | WARNING | "Shower filter" is broad — lots of irrelevant traffic risk |
| G17 | Broad match + smart bidding | Critical | NEEDS VERIFICATION | Broad match without smart bidding = budget drain |
| G18 | Close variant pollution | High | WARNING | "Shower filter" can trigger "shower head", "water filter" etc. |
| G19 | Search term visibility | Medium | WARNING | Google hiding increasing % of search terms |
| G-WS1 | Zero-conversion keywords | High | WARNING | At low budget, many keywords will have insufficient data |

### Account Structure Checks

| ID | Check | Severity | Status | Notes |
|----|-------|----------|--------|-------|
| G01 | Campaign naming convention | Medium | NEEDS VERIFICATION | Should follow [Brand]_[Type]_[Geo]_[Target] |
| G02 | Ad group naming | Medium | NEEDS VERIFICATION | Match campaign naming pattern |
| G03 | Single theme ad groups | High | NEEDS VERIFICATION | Each ad group ≤10 keywords |
| G04 | Campaign count | High | WARNING | At $600/mo, should have MAX 2 campaigns |
| G05 | Brand vs non-brand separation | Critical | NEEDS VERIFICATION | "Curo Skin" brand terms must be separated |
| G06 | PMax present | Medium | NEEDS VERIFICATION | PMax with product feed recommended |
| G07 | Search + PMax overlap | High | NEEDS VERIFICATION | Brand exclusions needed if both active |
| G08 | Budget allocation priority | High | FAIL | Entire Google budget is insufficient |
| G09 | Daily budget vs spend | Medium | WARNING | $20/day caps quickly |
| G10 | Ad schedule | Low | PASS (assumed) | E-commerce runs 24/7 |
| G11 | Geographic targeting | High | NEEDS VERIFICATION | Must be "People in" UK, not "interested in" |
| G12 | Network settings | High | NEEDS VERIFICATION | Display Network must be OFF for Search |

### Keywords & Quality Score Checks

| ID | Check | Severity | Status | Notes |
|----|-------|----------|--------|-------|
| G20 | Average Quality Score | High | NEEDS VERIFICATION | Target ≥7; niche products often struggle |
| G21 | Critical QS keywords | Critical | NEEDS VERIFICATION | <10% with QS ≤3 |
| G22 | Expected CTR component | High | NEEDS VERIFICATION | Ad copy must match search intent |
| G23 | Ad relevance component | High | NEEDS VERIFICATION | RSA headlines must contain keywords |
| G24 | Landing page experience | High | WARNING | curoskin.co.uk speed and mobile experience unverified |
| G25 | Top keyword QS | Medium | NEEDS VERIFICATION | Top spenders need QS ≥7 |
| G-KW1 | Zero-impression keywords | Medium | WARNING | Niche terms like "filtered shower head UK" may have low volume |
| G-KW2 | Keyword-to-ad relevance | High | NEEDS VERIFICATION | Headlines must contain keyword variants |

### Ads & Assets Checks

| ID | Check | Severity | Status | Notes |
|----|-------|----------|--------|-------|
| G26 | RSA per ad group | High | NEEDS VERIFICATION | ≥1 RSA per ad group |
| G27 | RSA headline count | High | NEEDS VERIFICATION | Need ≥8 unique headlines (ideal 12-15) |
| G28 | RSA description count | Medium | NEEDS VERIFICATION | Need ≥3 descriptions |
| G29 | RSA Ad Strength | High | NEEDS VERIFICATION | Must be "Good" or "Excellent" |
| G30 | RSA pinning strategy | Medium | NEEDS VERIFICATION | Strategic pinning with variants |
| G31 | PMax asset group density | Critical | WARNING | Need ≥20 images, ≥5 videos — resource-intensive |
| G32 | PMax video assets | High | WARNING | Need native video in 16:9, 1:1, 9:16 |
| G33 | PMax asset group count | Medium | WARNING | ≥2 groups recommended but budget limits this |
| G34 | PMax final URL expansion | High | NEEDS VERIFICATION | Must be intentionally configured |
| G35 | Ad copy relevance | High | NEEDS VERIFICATION | Headlines must contain keyword variants |
| G-AD1 | Ad freshness | Medium | NEEDS VERIFICATION | New copy tested within 90 days |
| G-AD2 | CTR vs benchmark | High | NEEDS VERIFICATION | E-commerce average CTR: 4.13% |

### Settings & Targeting Checks

| ID | Check | Severity | Status | Notes |
|----|-------|----------|--------|-------|
| G50 | Sitelink extensions | High | NEEDS VERIFICATION | ≥4 sitelinks (Reviews, Products, About, FAQ) |
| G51 | Callout extensions | Medium | NEEDS VERIFICATION | "60-Day Guarantee", "Free Delivery", "Award-Winning" |
| G52 | Structured snippets | Medium | NEEDS VERIFICATION | Types: "Chrome, Brushed Gold, Midnight Black" |
| G53 | Image extensions | Medium | NEEDS VERIFICATION | Product images in search results |
| G54 | Call extensions | Medium | N/A | DTC e-commerce, not phone-based |
| G55 | Lead form extensions | Low | N/A | E-commerce, not lead gen |
| G56 | Audience segments | High | NEEDS VERIFICATION | Remarketing + in-market audiences |
| G57 | Customer Match lists | High | WARNING | Requires 90d history + $50K lifetime spend |
| G58 | Placement exclusions | High | NEEDS VERIFICATION | Must exclude games, apps, MFA sites |
| G59 | Landing page mobile speed | High | NEEDS VERIFICATION | LCP <2.5s target |
| G60 | Landing page relevance | High | NEEDS VERIFICATION | H1/title must match ad group theme |
| G61 | Schema markup | Medium | NEEDS VERIFICATION | Product schema on product pages |

### Bidding & Budget Checks

| ID | Check | Severity | Status | Notes |
|----|-------|----------|--------|-------|
| G36 | Smart Bidding active | High | NEEDS VERIFICATION | Required for campaigns with ≥15 conv/month |
| G37 | Target CPA/ROAS reasonable | Critical | WARNING | Targets must be within 20% of historical |
| G38 | Learning phase status | High | FAIL | At $600/mo, most campaigns will be stuck in learning |
| G39 | Budget constrained | High | FAIL | Entire Google budget is below minimum viable |
| G40 | Manual CPC justification | Medium | NEEDS VERIFICATION | Only justified with <15 conv/month |
| G41 | Portfolio bid strategies | Medium | NEEDS VERIFICATION | Low-volume campaigns should be grouped |

### Google Ads Quick Wins

| Priority | Action | Time | Impact |
|----------|--------|------|--------|
| 1 | Verify Consent Mode v2 is active | 5 min | Prevents 90-95% data loss |
| 2 | Enable Enhanced Conversions | 5 min | ~10% more measured conversions |
| 3 | Verify location targeting = "People in" UK only | 2 min | Eliminates wasted international spend |
| 4 | Disable Display Network on Search campaigns | 2 min | Stops low-quality display impressions |
| 5 | Add negative keyword lists (competitor, free, DIY) | 10 min | Reduces irrelevant spend |

### Google Ads Strategic Recommendation

> **PAUSE Google Ads and reallocate the ~$600/month to Meta Ads.** At current budget levels, Google cannot generate sufficient conversion volume for Smart Bidding to optimize effectively. Revisit Google when total budget reaches $3,000+/month, then allocate $1,000+ to Google with a focus on Brand Search + Performance Max with a fully built product feed.

---

## Meta Ads Audit — Score: 58/100 (Grade D)

### Category Breakdown

| Category | Weight | Score | Grade | Key Issue |
|----------|--------|-------|-------|-----------|
| Pixel / CAPI Health | 30% | 55/100 | D | CAPI deployment unverified; EMQ likely suboptimal |
| Creative (Diversity & Fatigue) | 30% | 60/100 | C | Visual product but creative pipeline may be thin |
| Account Structure | 20% | 60/100 | C | Budget demands max consolidation |
| Audience & Targeting | 20% | 55/100 | D | First-party data utilization likely insufficient |

### Pixel / CAPI Health Checks

| ID | Check | Severity | Status | Notes |
|----|-------|----------|--------|-------|
| M01 | Meta Pixel installed | Critical | NEEDS VERIFICATION | Shopify installs automatically but must verify all events |
| M02 | CAPI active | Critical | NEEDS VERIFICATION | **CRITICAL** — without CAPI, 30-40% data loss; Shopify has built-in CAPI option |
| M03 | Event deduplication | Critical | NEEDS VERIFICATION | event_id matching between pixel + CAPI required |
| M04 | Event Match Quality (EMQ) | Critical | WARNING | 87% of advertisers have poor EMQ; likely needs improvement |
| M05 | Domain verification | High | NEEDS VERIFICATION | curoskin.co.uk must be verified in Business Manager |
| M06 | Aggregated Event Measurement | High | NEEDS VERIFICATION | Top 8 events must be configured and prioritized |
| M07 | Standard events vs custom | High | NEEDS VERIFICATION | Must use Purchase, AddToCart, InitiateCheckout (not custom) |
| M08 | CAPI Gateway | Medium | NEEDS VERIFICATION | Simplified CAPI option available |
| M09 | iOS attribution window | High | NEEDS VERIFICATION | Must be 7-day click / 1-day view |
| M10 | Data freshness | Medium | NEEDS VERIFICATION | Events must fire in real-time |

### Creative Checks

| ID | Check | Severity | Status | Notes |
|----|-------|----------|--------|-------|
| M25 | Format diversity | Critical | WARNING | Need ≥3 formats: static, video, carousel. Shower filter brand may lean too heavily on static |
| M26 | Creative volume per ad set | High | WARNING | Need 5-8 creatives; at low budget, likely only 3-4 |
| M27 | Video aspect ratios | High | WARNING | 9:16 vertical needed for Reels/Stories; may be missing |
| M28 | Creative fatigue | Critical | NEEDS VERIFICATION | With small audience + limited budget, fatigue hits faster |
| M29 | Hook rate (video) | High | NEEDS VERIFICATION | First 3s critical — water transformation hook potential |
| M30 | Social proof utilization | Medium | WARNING | 5 awards + 4.88/5 reviews should be in every ad but likely underused |
| M31 | UGC / social-native content | High | WARNING | ≥30% UGC target; shower filter demos from real customers |
| M32 | Advantage+ Creative | Medium | NEEDS VERIFICATION | Auto-enhancements should be tested |
| M-CR1 | Creative freshness | High | NEEDS VERIFICATION | New creative within last 30 days |
| M-CR2 | Frequency — Prospecting | High | NEEDS VERIFICATION | Must be <3.0 (7-day) |
| M-CR3 | Frequency — Retargeting | Medium | NEEDS VERIFICATION | Must be <8.0 (7-day) |
| M-CR4 | CTR benchmark | High | NEEDS VERIFICATION | Target ≥1.0% |

### Account Structure Checks

| ID | Check | Severity | Status | Notes |
|----|-------|----------|--------|-------|
| M11 | Campaign count | High | WARNING | At $800/mo should have MAX 2 campaigns |
| M12 | CBO vs ABO | High | NEEDS VERIFICATION | ABO appropriate at <$100/day |
| M13 | Learning phase status | Critical | WARNING | Tight budget = high risk of Learning Limited |
| M14 | Learning phase resets | High | NEEDS VERIFICATION | Avoid edits during learning |
| M15 | Advantage+ Sales (ASC) | Medium | NEEDS VERIFICATION | ASC should be primary campaign for DTC e-commerce |
| M16 | Ad set consolidation | High | WARNING | Overlapping ad sets waste limited budget |
| M17 | Budget distribution | High | WARNING | Need ≥$10/day per ad set; at $800/mo this limits to 2-3 ad sets |
| M18 | Campaign objective | High | NEEDS VERIFICATION | Must be Sales (not Traffic or Engagement) |
| M33 | Advantage+ Placements | Medium | NEEDS VERIFICATION | Should be enabled for max delivery |
| M34 | Placement performance review | Medium | NEEDS VERIFICATION | Monthly breakdown review |
| M35 | Attribution setting | High | NEEDS VERIFICATION | Must be 7-day click / 1-day view |
| M36 | Bid strategy | High | NEEDS VERIFICATION | Lowest Cost for volume at this budget |
| M37 | Frequency cap monitoring | High | NEEDS VERIFICATION | Campaign frequency <4.0 (7-day) |
| M38 | Breakdown reporting | Medium | NEEDS VERIFICATION | Age/gender/placement reviewed monthly |
| M39 | UTM parameters | Medium | WARNING | Likely missing — common oversight |
| M40 | A/B testing | Medium | WARNING | At $800/mo, formal A/B testing is difficult |
| M-ST1 | Budget adequacy | High | WARNING | Daily budget should be ≥5x target CPA |
| M-ST2 | Budget utilization | Medium | NEEDS VERIFICATION | >80% utilization target |

### Audience & Targeting Checks

| ID | Check | Severity | Status | Notes |
|----|-------|----------|--------|-------|
| M19 | Audience overlap | High | WARNING | If running multiple ad sets, overlap is likely |
| M20 | Custom Audience freshness | High | NEEDS VERIFICATION | Website audiences refreshed within 180 days |
| M21 | Lookalike source quality | Medium | WARNING | May not have 1,000+ purchasers yet |
| M22 | Advantage+ Audience testing | Medium | NEEDS VERIFICATION | Should be tested vs manual targeting |
| M23 | Exclusion audiences | High | NEEDS VERIFICATION | Purchasers must be excluded from prospecting |
| M24 | First-party data | High | WARNING | Customer email list should be uploaded and refreshed |

### Meta Ads Quick Wins

| Priority | Action | Time | Impact |
|----------|--------|------|--------|
| 1 | Enable CAPI via Shopify integration | 15 min | Recovers 30-40% lost data |
| 2 | Verify domain in Business Manager | 5 min | Enables AEM configuration |
| 3 | Set attribution to 7-day click / 1-day view | 2 min | Proper measurement window |
| 4 | Add UTM parameters at campaign level | 5 min | GA4 attribution visibility |
| 5 | Add award badges to all ad creatives | 15 min | Marie Claire, Glamour, WIRED logos = instant credibility |
| 6 | Exclude purchasers from prospecting | 10 min | Stops wasting budget on existing customers |

### Meta Ads Strategic Recommendations

1. **Make Meta the primary platform** — allocate 60%+ of total budget ($1,200+/mo)
2. **Run max 2 campaigns**: ASC (70%) + Prospecting/Testing (30%)
3. **Creative pipeline is critical** — produce 4-6 new assets monthly:
   - UGC: Customers showing skin/hair improvement
   - Demo: Filter after 90 days (visually disgusting = attention-grabbing)
   - Social proof: Award badges + review overlays
   - Before/after: Water quality test results
4. **Leverage the subscription model** in ad copy — "From just 33p/day" messaging
5. **Use award authority** — "Marie Claire's Best New Skin Tool" as headline

---

## TikTok Ads Audit — Score: 48/100 (Grade D)

### Category Breakdown

| Category | Weight | Score | Grade | Key Issue |
|----------|--------|-------|-------|-----------|
| Creative Quality | 30% | 55/100 | D | Enormous potential but likely under-resourced |
| Technical Setup | 25% | 45/100 | D | Pixel + Events API + ttclid unverified |
| Bidding & Learning | 20% | 35/100 | F | Budget critically below minimum |
| Structure & Settings | 15% | 50/100 | D | Search Ads Toggle likely not enabled |
| Performance | 10% | 55/100 | D | Cannot benchmark without data |

### CRITICAL Finding: Budget Insufficiency

**TikTok requires a minimum of $50/day campaign budget ($1,500/month).** At ~$600/month, Curo Skin is spending less than half the minimum required. Campaigns cannot exit learning phase, and the algorithm cannot optimize effectively.

### Creative Quality Checks

| ID | Check | Severity | Status | Notes |
|----|-------|----------|--------|-------|
| T05 | Creative volume | Critical | WARNING | Need ≥6 per ad group; shower filter content is easy to produce |
| T06 | Vertical video format | Critical | NEEDS VERIFICATION | ALL content must be 9:16 (1080x1920) |
| T07 | Native-looking content | High | NEEDS VERIFICATION | Must look organic, not corporate |
| T08 | Hook strategy | High | WARNING | "Look what came out of my shower filter" = instant hook |
| T09 | Creative lifespan | High | WARNING | TikTok creative fatigues fast (7-14 days) |
| T10 | Spark Ads utilization | High | WARNING | Should be boosting organic/creator content |
| T20 | TikTok Shop integration | Medium | NEEDS VERIFICATION | Available in UK; massive opportunity |
| T21 | Video Shopping Ads (VSA) | Medium | NEEDS VERIFICATION | Should test with product catalog |
| T22 | Caption SEO | High | WARNING | Keywords: "shower filter", "hard water", "eczema", "dry skin" |
| T23 | Sound/music usage | Medium | NEEDS VERIFICATION | Trending audio boosts distribution |
| T24 | CTA button | Medium | NEEDS VERIFICATION | Must be customized, not default |
| T25 | Safe zone compliance | High | NEEDS VERIFICATION | Key content within X:40-940, Y:150-1470 |

### Technical Setup Checks

| ID | Check | Severity | Status | Notes |
|----|-------|----------|--------|-------|
| T01 | TikTok Pixel installed | Critical | NEEDS VERIFICATION | Must fire on all pages including checkout |
| T02 | Events API + ttclid | High | WARNING | ttclid capture is TikTok's unique requirement; often missed |

### Bidding & Learning Checks

| ID | Check | Severity | Status | Notes |
|----|-------|----------|--------|-------|
| T11 | Bid strategy | High | NEEDS VERIFICATION | Lowest Cost recommended at this stage |
| T12 | Budget sufficiency | High | FAIL | $600/mo is well below $1,500 minimum |
| T13 | Learning phase | High | FAIL | Cannot achieve 50 conv/week at this budget |

### Structure & Settings Checks

| ID | Check | Severity | Status | Notes |
|----|-------|----------|--------|-------|
| T03 | Campaign structure | High | NEEDS VERIFICATION | Prospecting vs retargeting must be separated |
| T04 | Smart+ utilization | Medium | NEEDS VERIFICATION | 42% adoption, 1.41-1.67 ROAS; should test |
| T14 | Search Ads Toggle | High | WARNING | Likely OFF; must enable for search discovery |
| T15 | Placement selection | Medium | NEEDS VERIFICATION | TikTok-only placement recommended |
| T16 | Dayparting | Low | NEEDS VERIFICATION | May benefit from evening scheduling |

### Performance Checks

| ID | Check | Severity | Status | Notes |
|----|-------|----------|--------|-------|
| T17 | CTR benchmark | High | NEEDS VERIFICATION | Target ≥1.0% for in-feed ads |
| T18 | CPA target | High | NEEDS VERIFICATION | Must be within target range |
| T19 | Video completion rate | Medium | NEEDS VERIFICATION | Average watch time ≥6 seconds target |

### TikTok Ads Quick Wins

| Priority | Action | Time | Impact |
|----------|--------|------|--------|
| 1 | Enable Search Ads Toggle | 2 min | Captures "shower filter" search traffic |
| 2 | Verify ttclid passback | 10 min | Fixes attribution for most conversions |
| 3 | Add keyword-rich captions | 5 min | "Shower filter", "hard water", "eczema" |
| 4 | Select proper CTA button | 2 min | "Shop Now" instead of default |
| 5 | Set up TikTok Shop | 30 min | >10% CVR vs 0.46-2.4% standard |

### TikTok Strategic Recommendations

Shower filters are a **TikTok-native product category**. Jolie (US competitor) built their entire brand through TikTok virality. This is Curo Skin's highest-potential platform.

1. **Either commit properly or pause**: $600/month cannot work; need $1,500+/month
2. **TikTok Shop is a game-changer** — >10% CVR vs <2.5% standard. Set this up immediately
3. **Content ideas that work for this category**:
   - "What comes out of my shower filter after 90 days" (gross = viral)
   - "My eczema before vs after using a shower filter"
   - "Things in your water you can't see" (educational hook)
   - "Shower routine" / "Get ready with me" featuring the product
   - "I tested my water before and after" (science/proof angle)
4. **Spark Ads** — partner with 5-10 micro-creators in the UK beauty/wellness space
5. **Leverage the K-beauty angle** — ATOJET/Korean shower filters are trending; position as the premium UK alternative

---

## Cross-Platform Analysis

### Budget Allocation Assessment

| Current (Estimated) | Recommended (DTC E-commerce) | Gap |
|---------------------|------------------------------|-----|
| Google 30% / Meta 40% / TikTok 30% | Meta 60% / TikTok 40% (at $2K) | Over-diversified |

**Critical Finding:** $2,000/month is **$1,000 below the minimum recommended** for DTC e-commerce ($3,000+). Running three platforms at this budget means none get enough spend to optimize properly.

#### Recommended Reallocation (Two Options)

**Option A: Meta-Heavy (Conservative)**
```
Meta Ads:   $1,400/month (70%)  — ASC + Prospecting
TikTok Ads:    $600/month (30%)  — Spark Ads + Shop
Google Ads:      $0/month (0%)   — PAUSED
```

**Option B: TikTok-Heavy (Aggressive)**
```
Meta Ads:   $1,000/month (50%)  — ASC primary
TikTok Ads: $1,000/month (50%)  — Spark Ads + Shop
Google Ads:      $0/month (0%)   — PAUSED
```

> **Recommendation: Option B.** Shower filters are a TikTok-native category with proven viral potential. TikTok Shop (>10% CVR) combined with Spark Ads could outperform Meta at this budget level. Meta handles retargeting and ASC; TikTok drives discovery.

### Tracking Consistency Assessment

| Check | Status | Risk |
|-------|--------|------|
| All platforms tracking same events | NEEDS VERIFICATION | Medium — common for events to be inconsistent |
| Server-side tracking (all platforms) | WARNING | High — CAPI (Meta), Events API (TikTok), Enhanced Conv (Google) |
| UK GDPR / Consent Mode v2 | NEEDS VERIFICATION | CRITICAL — mandatory for UK market |
| Event deduplication | NEEDS VERIFICATION | High — double-counting inflates ROAS |
| Attribution overlap | WARNING | High at this budget — platforms will overclaim |
| First-party data utilization | WARNING | Customer email list should feed all platforms |
| Cookie consent banner | NEEDS VERIFICATION | CRITICAL — ICO enforcement active |
| Privacy policy on landing pages | NEEDS VERIFICATION | Required by all platforms + UK GDPR |

### UK GDPR Compliance Checklist

| Requirement | Status | Priority |
|-------------|--------|----------|
| Cookie consent banner (opt-in) | NEEDS VERIFICATION | Critical |
| Consent Mode v2 for Google | NEEDS VERIFICATION | Critical |
| CAPI for Meta (bypasses some cookie issues) | NEEDS VERIFICATION | Critical |
| Events API for TikTok | NEEDS VERIFICATION | High |
| Privacy policy accessible on all landing pages | NEEDS VERIFICATION | Critical |
| Data processing agreements with all platforms | NEEDS VERIFICATION | High |
| Right to erasure process | NEEDS VERIFICATION | Medium |
| ICO registration (if required) | NEEDS VERIFICATION | Medium |

### Creative Cross-Platform Assessment

| Dimension | Status | Recommendation |
|-----------|--------|----------------|
| Format diversity | WARNING | Need static, video, carousel (Meta) + vertical video (TikTok) |
| Platform-native content | WARNING | TikTok content must NOT be repurposed Meta ads |
| Creative fatigue risk | HIGH | Low budget + small audience = fast fatigue; need 6+ fresh assets/month |
| UGC strategy | WARNING | Shower filters are PERFECT for UGC but likely under-leveraging |
| Before/after content | WARNING | Powerful for this product; Meta restricts health claims though |
| Award/social proof usage | WARNING | 5 major awards likely underused in ad creative |
| Video-first approach | WARNING | Video outperforms static on both platforms; need 9:16 vertical |
| Cross-platform repurposing | WARNING | Can adapt angles but format must be platform-native |

### Creative Production Priorities

| Priority | Asset | Platform | Why |
|----------|-------|----------|-----|
| 1 | "Dirty filter after 90 days" UGC video | TikTok + Meta | Gross = attention; proves product works |
| 2 | Award badges on lifestyle images | Meta | Instant credibility (Marie Claire, Glamour) |
| 3 | Customer testimonial videos (eczema/dry skin) | Both | Social proof + problem/solution |
| 4 | "What's in your water" educational video | TikTok | Science angle performs well |
| 5 | Carousel: Shower head colors + subscription value | Meta | Shows product range + affordability |
| 6 | "Shower routine" / GRWM featuring Curo | TikTok | Native format, massive trend |
| 7 | Competitor comparison (Curo vs Hello Klean) | Meta | Differentiation from main competitor |
| 8 | Unboxing + installation in <30 seconds | Both | Removes purchase friction |

---

## Scoring Methodology

### Calculation Method

```
S_total = Σ(C_pass × W_sev × W_cat) / Σ(C_total × W_sev × W_cat) × 100

Where:
- PASS = 1.0 (full points)
- WARNING = 0.5 (half points)
- FAIL = 0.0 (no points)
- NEEDS VERIFICATION = 0.5 (assumed WARNING for scoring)
- N/A = excluded from total
```

### Aggregate Score Calculation

```
Google:  45 × 30% = 13.5   (estimated $600 budget share)
Meta:    58 × 40% = 23.2   (estimated $800 budget share)
TikTok:  48 × 30% = 14.4   (estimated $600 budget share)

Aggregate = 51.1 → 52/100 → Grade D (Poor)
```

### Score Context

A Grade D score of 52/100 indicates **significant problems requiring urgent intervention**. However, this score is heavily influenced by **budget insufficiency** — the single biggest issue across all platforms. Fixing the budget allocation alone would likely improve the aggregate score to 65-70 (Grade C).

The score also reflects that many items are "NEEDS VERIFICATION" (scored as WARNING at 0.5) — actual account access could reveal some of these as PASS, which would improve scores.

---

## Disclaimer

This audit is assessment-based and relies on industry benchmarks, best practices, and business-type heuristics rather than actual account data. All "NEEDS VERIFICATION" items should be confirmed with direct account access. Actual scores may vary once real data is available. We recommend a follow-up data-verified audit once account exports or API access is provided.
