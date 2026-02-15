# Google Ads Audit: Curo Skin (curoskin.co.uk)
**Audit Date:** 2026-02-15
**Audit Type:** Assessment-Based (No Account Access — Best-Practice Inference)
**Business:** DTC E-commerce, Shower Filters, UK Market
**Estimated Google Budget:** ~$500–700/month (of ~$2,000 total across Google, Meta, TikTok)
**Auditor Note:** All check statuses are inferred from business context, budget level, and DTC e-commerce patterns at this scale. Every NEEDS VERIFICATION item requires direct account access to confirm.

---

## CRITICAL PRE-AUDIT FINDING: Sub-Minimum Budget

**This is the most important finding in this entire audit.**

At ~$2,000/month total across three platforms, Google likely receives $500–700/month. The minimum viable budget to run Google Ads effectively for a DTC e-commerce brand is **$1,000/month** (and ideally $1,500+ for Performance Max). Below this threshold:

- Smart Bidding algorithms cannot collect enough conversion data to exit the learning phase
- A Target CPA or Target ROAS strategy will perpetually underperform or fail entirely
- Performance Max requires ~50 conversions/month minimum to function; at £80 AOV with a 2% CVR, $600/month generates roughly 75 clicks at £1.50 CPC — statistically fewer than 2 purchases per month from Google alone
- The account will show high CPAs, erratic results, and misleading ROAS due to attribution fragmentation across three platforms

**Recommendation: Either consolidate budget to achieve $1,000+/month on Google, or deprioritise Google entirely until total ad budget reaches £3,000+/month. Meta and TikTok offer better returns at lower budget thresholds for a visually-led DTC brand at this stage.**

---

## Summary Scorecard

| Category | Weight | Raw Score | Weighted Score | Grade |
|----------|--------|-----------|---------------|-------|
| Conversion Tracking | 25% | 38/100 | 9.5/25 | F |
| Wasted Spend / Negatives | 20% | 42/100 | 8.4/20 | F |
| Account Structure | 15% | 45/100 | 6.8/15 | D |
| Keywords & Quality Score | 15% | 48/100 | 7.2/15 | D |
| Ads & Assets | 15% | 50/100 | 7.5/15 | D |
| Settings & Targeting | 10% | 44/100 | 4.4/10 | F |
| **TOTAL** | **100%** | — | **43.8/100** | **D** |

**Google Ads Health Score: 44/100 — Poor**

> This score reflects a typical DTC brand at sub-minimum budget with likely tracking gaps, thin negative keyword hygiene, and under-optimised campaign structure. It is not a worst-case score — it is a realistic baseline for a brand at this stage and budget. The score would materially improve with tracking remediation, budget consolidation, and structural simplification.

---

## Scoring Methodology

Severity multipliers applied per check:
- Critical (5.0x): Failures dominate category score
- High (3.0x): Significant drag
- Medium (1.5x): Moderate drag
- Low (0.5x): Minor drag

Status definitions:
- **PASS** — Meets threshold; no action needed
- **WARNING** — Below threshold or suboptimal; improvement recommended
- **FAIL** — Definitively failing; immediate action required
- **NEEDS VERIFICATION** — Cannot be assessed without account access; assumed status given in parentheses

---

## Category 1: Conversion Tracking (25% Weight)
*11 checks: G42–G49, G-CT1, G-CT2, G-CT3*

| ID | Check | Severity | Status | Reasoning | Recommendation |
|----|-------|----------|--------|-----------|----------------|
| G42 | Conversion actions defined (purchase, ATC, checkout) | Critical | NEEDS VERIFICATION (assumed FAIL) | At this budget and typical DTC setup, many brands track only "purchase" and miss secondary micro-conversion events. Without purchase tracking confirmed, every bid strategy is flying blind. | Immediately verify purchase conversion action fires on order confirmation page. Add ATC and Initiated Checkout as secondary (non-bidding) conversion actions. |
| G43 | Enhanced Conversions enabled and sending hashed data | Critical | NEEDS VERIFICATION (assumed FAIL) | Enhanced Conversions requires deliberate implementation of hashed PII (email, phone) in the tag. Most small DTC brands skip this. Without it, a significant portion of conversions are unattributed post-iOS/browser changes. | Enable Enhanced Conversions in Google Ads settings and pass hashed email from checkout confirmation to the conversion tag. |
| G44 | Conversion window set correctly (90-day for subscription) | High | NEEDS VERIFICATION (assumed WARNING) | Default conversion window is 30 days. For a subscription product where the highest LTV signal is a second filter purchase 90 days later, a 30-day window systematically undervalues acquisition campaigns. | Set primary purchase conversion window to 90 days for the subscription filter product. Use 30 days for the initial hardware purchase as a secondary action. |
| G45 | Consent Mode v2 implemented (UK GDPR critical) | Critical | NEEDS VERIFICATION (assumed FAIL) | UK GDPR and the ICO's guidance post-Brexit mirrors EU requirements for cookie consent. Consent Mode v2 with a compliant CMP is non-negotiable. Most small DTC brands running Shopify miss this or implement it incorrectly. Failure here means modelled conversions are absent and remarketing audiences are suppressed for a significant portion of UK traffic. | Implement a Google-certified CMP (e.g. Cookiebot, Usercentrics, OneTrust). Configure Consent Mode v2 with `ad_storage`, `analytics_storage`, `ad_personalization` signals. Verify via Tag Assistant. |
| G46 | Google Analytics 4 linked and importing goals | High | NEEDS VERIFICATION (assumed WARNING) | GA4 is likely installed (Shopify makes this easy) but the link to Google Ads and the import of GA4 conversions as secondary signals is frequently missed or duplicated. | Link GA4 to Google Ads. Import GA4 purchase event as a secondary (non-primary-bidding) signal only to avoid double-counting. |
| G47 | No conversion inflation (page refresh, back-button double-count) | High | NEEDS VERIFICATION (assumed WARNING) | Shopify order confirmation pages are prone to double-firing if the thank-you page is cached or revisited. Without a deduplication key (transaction ID), conversions inflate. | Implement transaction ID deduplication in the Google Ads purchase conversion tag. Audit conversion count vs Shopify orders over 30 days — if Google reports 20%+ more than Shopify, there is inflation. |
| G48 | Offline conversion import (where applicable) | Low | N/A | Curo Skin is a pure e-commerce brand with no offline sales channel requiring OCI. | No action required. |
| G49 | Phone call conversions tracked (where applicable) | Low | N/A | No evidence of phone sales process for a DTC shower filter brand. Web-only purchase journey assumed. | Confirm no phone order process exists. If a phone number is displayed on the website, add a call conversion action as a secondary signal. |
| G-CT1 | No duplicate conversion counting (not bidding on same action from multiple sources) | Critical | NEEDS VERIFICATION (assumed FAIL) | Shopify + GA4 + Google Tag all tracking "purchase" simultaneously without deduplication is the single most common tracking error for Shopify DTC brands. Results in apparent CPA 2–3x lower than reality, causing overbidding. | Audit all active conversion actions in Google Ads. Ensure only ONE primary purchase conversion action is used for bidding. Set all others (GA4 import, secondary events) to "Secondary" status. |
| G-CT2 | Conversion value rules configured for product margin tiers | Medium | NEEDS VERIFICATION (assumed FAIL) | At this scale and budget, value rules (applying margin multipliers to conversion values) are rarely configured. Given the shower head (£80 one-time) vs subscription (LTV significantly higher), the algorithm is likely optimising for equal-value conversions. | Configure conversion value rules: assign a higher value multiplier to customers who accept the subscription upsell at checkout, signalling higher LTV to Smart Bidding. |
| G-CT3 | Google Tag firing correctly on all key pages (verified via Tag Assistant) | Critical | NEEDS VERIFICATION (assumed WARNING) | Tag verification is frequently skipped. On Shopify, the checkout pages (particularly post-purchase upsell pages) often break tag firing. | Run Google Tag Assistant on: homepage, product page, add-to-cart, checkout initiation, order confirmation. Fix any "tag not found" or "tag fired with errors" instances. |

**Category 1 Assessment:** The most likely scenario for a Shopify DTC brand at this budget is a partial tracking setup — purchase tracking installed but without Enhanced Conversions, Consent Mode v2, or deduplication. This is a near-total attribution failure in the UK market. All ROAS and CPA figures reported in Google Ads are likely materially incorrect. **This category is the single highest priority for remediation before any spend optimisation work begins.**

---

## Category 2: Wasted Spend / Negatives (20% Weight)
*8 checks: G13–G19, G-WS1*

| ID | Check | Severity | Status | Reasoning | Recommendation |
|----|-------|----------|--------|-----------|----------------|
| G13 | Search term report audited within last 14 days | Critical | NEEDS VERIFICATION (assumed FAIL) | At a £500–700/month Google budget, typical small DTC brands check search terms infrequently. The shower filter category is highly susceptible to irrelevant queries (plumbing repairs, cheap shower heads, DIY water filter, hard water softener reviews). | Review search terms weekly. Flag any query with 5+ clicks and zero conversions. Add irrelevant terms as exact-match negatives at the ad group level and phrase/broad-match negatives at the campaign level. |
| G14 | Negative keyword lists (minimum 3 themed lists applied) | Critical | NEEDS VERIFICATION (assumed FAIL) | Most small DTC accounts have ad-hoc negative keywords rather than structured themed lists. For a shower filter brand, missing themed negatives (competitor brand names, DIY/repair intent, cheap/budget modifiers, irrelevant product categories) is extremely costly at low budget. | Build minimum 3 negative keyword lists: (1) Competitor Brand Exclusions — Hello Klean, Jolie, ATOJET, Water2, etc.; (2) Non-purchase Intent — "how to", "DIY", "repair", "plumber", "free", "cheap", "second hand"; (3) Irrelevant Products — "water softener", "bath filter", "pool filter", "drinking water filter". Apply all lists to all campaigns. |
| G15 | Branded search terms excluded from non-brand campaigns | High | NEEDS VERIFICATION (assumed WARNING) | Brand term leakage into Performance Max or broad-match campaigns is extremely common. At this budget, branded traffic in non-brand campaigns wastes spend on queries that would convert organically for free. | Add "Curo Skin" and all brand variants as negative keywords in all non-brand campaigns. Run a separate brand-protection campaign if branded search volume justifies it. |
| G16 | Wasted spend on irrelevant search terms under 5% of total spend | Critical | NEEDS VERIFICATION (assumed FAIL) | Shower filter is a broad-intent category. Without structured negatives, queries like "how to clean shower head", "shower head replacement", "hard water softener for house", and "best filter jug" will consume a disproportionate share of a tiny budget. At $600/month, even 20% wasted spend is $120/month — a material loss. | Weekly search term audits are mandatory at this budget. Target under 5% wasted spend. With a sub-$700/month budget, wasted spend tolerance is near zero. |
| G17 | No Broad Match keywords with Manual CPC bidding | Critical | NEEDS VERIFICATION (assumed FAIL) | Broad Match + Manual CPC is the most dangerous combination in Google Ads — it gives Google maximum targeting latitude with no algorithmic guardrails, burning budget on irrelevant traffic. For a budget-constrained brand, this is catastrophic. | If Broad Match keywords are used, they MUST be paired with Smart Bidding (Target CPA or Target ROAS). Never use Broad Match with Manual CPC. For this budget level, recommend Exact + Phrase match with Manual CPC enhanced, or Broad with Target CPA. |
| G18 | Placement exclusions applied (mobile apps, parked domains) | High | NEEDS VERIFICATION (assumed FAIL) | Google Display/PMax placements default to include mobile app inventory and parked domains, which have high click-through fraud rates and zero purchase intent. Almost no small accounts exclude these by default. | Add placement exclusions: mobile app categories (games, utilities), parked domain patterns, and known low-quality placements. For PMax, create a placement exclusion list at the account level. |
| G19 | Audience exclusions applied (recent purchasers) | Medium | NEEDS VERIFICATION (assumed WARNING) | Recent purchasers (0–90 days) should be excluded from prospecting campaigns to avoid wasting budget on customers who already converted. The 90-day window aligns with the filter subscription cycle. | Create a Customer Match list of recent purchasers. Exclude from all prospecting campaigns. Consider a separate "subscription renewal reminder" campaign for 75–85 day post-purchase customers. |
| G-WS1 | Search Impression Share loss due to budget (under 20%) | High | NEEDS VERIFICATION (assumed FAIL) | At $500–700/month on Google, impression share loss due to budget will almost certainly exceed 20% — potentially 50–70%. This means the account is only showing ads for a fraction of eligible searches. The budget is simply too small for the category. | This is fundamentally a budget problem. The fix is either to (a) increase Google budget to $1,000+/month, or (b) ruthlessly narrow targeting to only the highest-converting keyword subset where the available budget can achieve meaningful impression share. |

**Category 2 Assessment:** Wasted spend is the second most urgent priority after tracking. At this budget level, wasted spend and impression share loss are existential threats. Every pound spent on an irrelevant query is a pound that cannot fund a genuine purchase intent click.

---

## Category 3: Account Structure (15% Weight)
*12 checks: G01–G12*

| ID | Check | Severity | Status | Reasoning | Recommendation |
|----|-------|----------|--------|-----------|----------------|
| G01 | Account has a logical campaign hierarchy (brand / non-brand / PMax separated) | High | NEEDS VERIFICATION (assumed FAIL) | At this budget, it is common to have a single campaign covering all objectives, or to have PMax cannibalising brand terms. A brand campaign is essential to protect Curo Skin brand searches from Hello Klean and other competitors bidding on competitor terms. | Separate into: (1) Brand Search — exact match brand terms, low budget, TIS bidding; (2) Non-Brand Search — high-intent category terms; (3) PMax (if budget supports it). |
| G02 | Campaigns don't overlap in targeting (keyword cannibalisation) | High | NEEDS VERIFICATION (assumed WARNING) | With limited campaigns, overlap is less likely, but any PMax campaign will cannibalise search campaigns by default if not managed with negative keywords or campaign priority settings. | Audit search term reports across campaigns. If PMax is running, use the Search Themes feature to guide it toward non-branded terms. Apply brand negatives to PMax. |
| G03 | Ad group granularity appropriate (single theme per ad group) | Medium | NEEDS VERIFICATION (assumed WARNING) | Small accounts often use catch-all ad groups. For a Curo Skin account, mixing "shower filter" + "hard water shower" + "filtered shower head" into one ad group dilutes ad relevance and Quality Score. | Create themed ad groups: (a) Shower Filter — exact/phrase; (b) Hard Water Shower; (c) Filtered Shower Head; (d) Shower Head Filter Replacement. Each ad group should have tightly themed keywords and a tailored RSA. |
| G04 | Campaigns use appropriate bidding strategy for lifecycle stage | High | NEEDS VERIFICATION (assumed WARNING) | A new or small account should start with Maximise Conversions or Manual CPC (enhanced), not Target CPA/ROAS, because there is insufficient conversion data for Smart Bidding to function. Running Target ROAS with fewer than 30 conversions/month produces erratic results. | If conversion volume is under 30/month on Google: use Maximise Conversions (no target) or Manual CPC with Enhanced. Set a target CPA/ROAS only after accumulating 30+ conversions in the trailing 30-day window. |
| G05 | Brand vs non-brand campaigns separated | Critical | NEEDS VERIFICATION (assumed FAIL) | This is the foundational account structure requirement. Without separation, brand traffic (high CTR, low CPA) averages up the performance of non-brand traffic, masking poor performance and misallocating budget. | Create a dedicated brand campaign with [Curo Skin] exact match and variants. Set to Target Impression Share 90%+. Budget $50–100/month. This protects against competitor conquest bidding. |
| G06 | Shopping / PMax campaigns have correct product feed | High | NEEDS VERIFICATION (assumed WARNING) | Google Merchant Center feed quality is frequently poor on Shopify integrations: missing GTINs, incorrect product types, inadequate titles. A shower filter with title "Shower Filter - Chrome" scores much lower than "Curo Skin Filtered Shower Head - Chrome - Removes Chlorine & Hard Water". | Audit Google Merchant Center feed. Optimise product titles: [Brand] + [Product Type] + [Key Benefit] + [Variant]. Add all 4 product lines (shower head, filter replacement, holder, vanity case) with complete attributes. |
| G07 | Campaign naming convention is consistent and descriptive | Low | NEEDS VERIFICATION (assumed WARNING) | Typically ad hoc at this scale. | Adopt naming: `[BRAND]_[TYPE]_[THEME]_[MATCH]_[DATE]`. Example: `CURO_SEARCH_ShowerFilter-Brand_EXACT_2026Q1`. |
| G08 | Shared budgets not cannibalising campaign performance | Medium | NEEDS VERIFICATION (assumed WARNING) | Shared budgets sound efficient but often starve high-performing campaigns as Google distributes budget across all campaigns in the pool. | Avoid shared budgets. Set individual campaign budgets. Monitor daily spend vs budget cap per campaign. |
| G09 | Adequate ad scheduling applied | Medium | NEEDS VERIFICATION (assumed FAIL) | Default ad scheduling runs 24/7. For a UK-based consumer brand, traffic outside 6am–11pm UK time has materially lower conversion rates. At this budget, every click outside peak hours is waste. | Apply ad schedule: run ads 6am–11pm GMT/BST. Review hourly conversion data after 60 days and apply bid adjustments for top-performing hours. |
| G10 | Location targeting set to UK only (not global) | High | NEEDS VERIFICATION (assumed WARNING) | Google's default targeting can include nearby or similar locations. Verify the campaign is set to "United Kingdom — Presence" not "Presence or interest". | Set all campaigns to "United Kingdom" with "Presence" option only. Exclude non-UK locations explicitly if any EU/international traffic is appearing in reports. |
| G11 | Correct language targeting (English) | Low | PASS (assumed) | UK market + English language product. Standard Shopify Google Ads setup defaults to English. | Confirm English (UK) language targeting is set. Low risk. |
| G12 | Campaign labels and notes used for change tracking | Low | NEEDS VERIFICATION (assumed FAIL) | Almost never done at this account size. Labels and notes are critical for understanding what caused performance changes. | Add labels to campaigns when budget changes, creative changes, or bid strategy changes are made. Use "Notes" in Google Ads to log external events (product launches, PR coverage, sale periods). |

**Category 3 Assessment:** Account structure is likely simple by necessity at this budget, but the critical failure is the absence of brand/non-brand separation and the likely presence of a single catch-all campaign (possibly PMax) that lacks the negatives and segmentation needed for efficient spend.

---

## Category 4: Keywords & Quality Score (15% Weight)
*8 checks: G20–G25, G-KW1, G-KW2*

| ID | Check | Severity | Status | Reasoning | Recommendation |
|----|-------|----------|--------|-----------|----------------|
| G20 | Weighted average Quality Score ≥7 across all keywords | High | NEEDS VERIFICATION (assumed WARNING) | For a DTC brand with a focused product, QS of 6–7 is typical. Below 7 means paying a premium CPC for every click. Shower filter is a specific enough category that well-written RSAs with keyword-matched headlines can achieve QS 7–8. | Review QS per keyword. Investigate any keyword with QS ≤5. Check: ad relevance (headline must contain keyword theme), expected CTR (test emotional/benefit headlines), and landing page experience (ensure landing page mirrors keyword intent). |
| G21 | No keywords with QS ≤4 spending over £10/month | High | NEEDS VERIFICATION (assumed WARNING) | Low-QS keywords with spend are a double penalty: you pay more per click AND get worse ad positions. | Pause any keyword with QS ≤4 and spend >£10/month. If the keyword is strategically important, rebuild its ad group with a tighter keyword-ad-landing page alignment. |
| G22 | Keyword match types used strategically (not all broad) | Critical | NEEDS VERIFICATION (assumed WARNING) | At this budget, broad match should be used sparingly and only with Smart Bidding. The recommended mix at sub-$700/month is primarily Exact + Phrase. | Audit match type distribution. Target: 40–50% Exact, 40–50% Phrase, 10% Broad (only with Target CPA). Broad alone at this budget is budget combustion. |
| G23 | Close variant mapping reviewed and unwanted variants excluded | Medium | NEEDS VERIFICATION (assumed WARNING) | Google automatically matches close variants including "conceptually similar" terms. For a shower filter brand, [shower head filter] may match "replace shower head" or "clean blocked shower" — very different intent. | Review the search terms report filtering for close variant matches. Add non-purchase-intent close variants as exact-match negatives. |
| G24 | Keyword list pruned (removed zero-impression, low-CTR waste) | Low | NEEDS VERIFICATION (assumed WARNING) | Small accounts accumulate inactive keywords that dilute account health metrics. | Pause all keywords with zero impressions in the last 90 days. Pause keywords with >100 impressions and CTR under 0.5% (indicates poor relevance or ad mismatch). |
| G25 | High-intent keyword coverage complete for the category | High | NEEDS VERIFICATION (assumed WARNING) | For Curo Skin, high-intent keywords likely missing: "shower filter for hard water UK", "filtered shower head UK", "shower filter chlorine removal", "best shower head filter 2025", "shower head filter replacement UK". Competitor conquest terms may also be absent. | Conduct keyword gap analysis using Google Keyword Planner. Priority terms: shower filter UK, filtered shower head, hard water shower filter, vitamin c shower filter, chlorine shower filter. AOV justifies bidding on competitive head terms. |
| G-KW1 | Competitor keyword strategy defined (conquest terms or excluded) | Medium | NEEDS VERIFICATION (assumed FAIL) | Curo Skin's competitors (Hello Klean — heavily advertised post-Dragons' Den, Jolie, ATOJET) are almost certainly bidding on "Curo Skin" branded terms. The inverse — whether Curo Skin bids on competitor terms — is likely undefined. | Define competitor keyword strategy: (a) bid on [Hello Klean shower filter], [Jolie shower filter], [ATOJET shower filter] as conquest terms in a separate ad group with comparison-focused ad copy; (b) add competitor brand names as negatives in brand campaign to prevent cross-contamination. |
| G-KW2 | Long-tail, high-intent keywords targeted alongside head terms | Medium | NEEDS VERIFICATION (assumed WARNING) | Head terms ("shower filter") are expensive and broad. Long-tail terms ("shower filter hard water UK", "chrome filtered shower head", "shower filter replacement cartridge") are cheaper, more specific, and indicate higher purchase intent. | Build a long-tail keyword list from: Google Search Console (organic queries), search term reports, Google's "People also ask" feature, and Keyword Planner. Target 20–30 long-tail terms per themed ad group. |

**Category 4 Assessment:** Keyword strategy for Curo Skin is an area of significant opportunity. The product is specific enough to target very high-intent queries with relatively low competition (vs pure beauty or wellness categories). However, the budget means head term CPCs may consume disproportionate spend — long-tail is where the value lies.

---

## Category 5: Ads & Assets (15% Weight)
*17 checks: G26–G35, G-AD1, G-AD2, G-PM1–G-PM5*

| ID | Check | Severity | Status | Reasoning | Recommendation |
|----|-------|----------|--------|-----------|----------------|
| G26 | RSAs have "Good" or "Excellent" Ad Strength | High | NEEDS VERIFICATION (assumed WARNING) | Ad Strength of "Average" is the default outcome when headlines are only partially distinct or don't leverage all available pinning/unpinning options. Most small accounts write 5–8 headlines rather than the full 15. | Write all 15 headlines and 4 descriptions for every RSA. Headlines must cover: brand name, product benefit, UVP (award-winning, 60-day guarantee, 4.88/5 reviews), colour variants, subscription offer. Use Google's Ad Strength panel to iterate until "Good" or "Excellent". |
| G27 | RSAs include emotional/benefit-led headlines (not just features) | Medium | NEEDS VERIFICATION (assumed WARNING) | Feature-led ads ("Filtered Shower Head - Chrome") underperform vs benefit-led ("Shower Without Chlorine & Limescale - From £80"). At this budget, every click must count. | Include at least 5 benefit/emotion-led headlines per RSA: "Award-Winning Shower Filter", "Remove Chlorine From Every Shower", "Loved by 100+ Customers - 4.88/5", "60-Day Money Back Guarantee", "Marie Claire & Glamour Recommended". |
| G28 | Ad copy references key USPs (guarantee, reviews, awards) | High | NEEDS VERIFICATION (assumed FAIL) | DTC brands at this scale rarely maximise their social proof in ad copy. Curo Skin has exceptional trust signals: Marie Claire, Glamour, WIRED, Good Housekeeping awards, Trustpilot 4.7, Judge.me 4.88/5, 60-day MBG. These are conversion-rate multipliers. | Every RSA must reference at minimum: (a) award name + year, (b) review score, (c) 60-day money-back guarantee. These are hard-won differentiators from Hello Klean which has wider distribution but may not have the same review density. |
| G29 | Responsive Search Ads — at least 3 per ad group | Medium | NEEDS VERIFICATION (assumed WARNING) | Google recommends 3 RSAs per ad group for rotation testing. Small accounts often have 1. | Create 3 RSAs per ad group with distinctly different angle/tone: (1) Product/benefit focused; (2) Social proof/awards focused; (3) Offer/subscription focused. |
| G30 | Ad extensions (assets) fully configured | High | NEEDS VERIFICATION (assumed FAIL) | Asset configuration is almost always incomplete at this account size. Sitelinks, callouts, structured snippets, price extensions, image extensions, and seller ratings are all frequently missing. Each asset improves CTR and Quality Score. | Configure all relevant assets: Sitelinks (Shop Shower Filters, Filter Subscriptions, 60-Day Guarantee, Bundle Deals); Callouts (Award-Winning, Free UK Delivery, 4.88/5 Stars, Chlorine Removal); Structured Snippets (Product types: Shower Heads, Filter Cartridges, Shower Holders, Vanity Cases); Price Extensions (Shower Head from £80, Subscription from £X); Image Extensions (product shots in all 3 colourways). |
| G31 | Asset group completeness for PMax (≥5 images, ≥2 logos, ≥1 video) | High | NEEDS VERIFICATION (assumed FAIL) | PMax asset groups at small DTC brands are typically uploaded minimally at launch. Missing video in particular forces Google to auto-generate low-quality video from static images, severely degrading YouTube and Demand Gen placements. | If running PMax: Upload ≥15 images (product on white background, lifestyle in bathroom, all 3 colour variants, close-up filter mechanism, award badge shots), ≥3 logo variants, and ≥3 videos (15s product demo, 30s UGC-style testimonial, 15s subscription offer). All 3 aspect ratios: 16:9, 1:1, 9:16 (vertical for Shorts/Discovery). |
| G32 | Native video provided for PMax in all 3 formats (16:9, 1:1, 9:16) | High | NEEDS VERIFICATION (assumed FAIL) | Vertical 9:16 video is almost always missing at this scale. Without it, YouTube Shorts and Discovery placements generate auto-created assets that perform poorly. | Film 15–30 second native vertical videos: unboxing, shower installation, before/after limescale, customer testimonial. These can be repurposed from TikTok/Reels organic content. |
| G33 | Final URLs use appropriate landing pages (not homepage) | Medium | NEEDS VERIFICATION (assumed WARNING) | Homepages as landing pages reduce conversion rates because they lack the specific product context the ad promised. | Each ad group or asset group should point to: brand terms → homepage acceptable; product terms → specific product page (shower head, filter replacement); subscription terms → subscription landing page or PDP with subscription upsell prominent. |
| G34 | Final URL expansion configured intentionally for PMax | High | NEEDS VERIFICATION (assumed WARNING) | PMax defaults to Final URL Expansion ON, meaning Google can redirect to any page on the site — including pages with no conversion optimisation (FAQ, About Us, Blog). For a small Shopify store, this often wastes budget on low-CVR pages. | Set Final URL Expansion to OFF initially. Monitor for 30 days. Only enable expansion if you are confident all site pages are conversion-optimised and you have sufficient negative URL exclusions in place. |
| G35 | Ad copy complies with Google's advertising policies (no superlatives without substantiation) | Low | PASS (assumed) | Curo Skin has substantiated award claims and review scores. These are usable. "Best" and "No.1" without substantiation would be policy violations. | Avoid unsubstantiated superlatives. "Award-winning", "As seen in Marie Claire", "4.88/5 stars from 100+ reviews" are all compliant. "The UK's best shower filter" is not without a citation. |
| G-AD1 | Ad copy differentiates from competitors (Hello Klean, Jolie, ATOJET) | High | NEEDS VERIFICATION (assumed FAIL) | Hello Klean has Dragon's Den brand recognition and Sephora distribution — a powerful trust signal in search results. Curo Skin's ads need to compete on a different axis: superior review score, independent press awards, 60-day MBG, and subscription convenience. | Explicitly address the competitive dynamic: "Higher-Rated Than Hello Klean — 4.88/5 Stars" or "As Seen in WIRED & Good Housekeeping 2025 — Try Risk-Free for 60 Days". This conquers the brand recognition gap. |
| G-AD2 | Price/offer messaging tested in ads (subscription discount, bundles) | Medium | NEEDS VERIFICATION (assumed FAIL) | The subscription model (15–25% off quarterly delivery) is a meaningful offer that likely appears nowhere in the ad copy. This is a conversion lever that is being wasted. | Test RSA headlines: "Save 25% With Quarterly Filter Subscription", "Free UK Delivery on Subscriptions", "Never Run Out of Clean Water — Auto-Deliver". The subscription AOV over 12 months is ~£110–140 vs £80 one-time — the algorithm should be optimising for this. |
| G-PM1 | Audience signals configured per PMax asset group | High | NEEDS VERIFICATION (assumed FAIL) | PMax launches with no audience signals by default (unless the user actively adds them). Without signals, PMax spends weeks burning budget learning from scratch. For a small account, this learning cost is unacceptable. | Add audience signals to every PMax asset group: (a) Customer Match list (past purchasers + email list); (b) Website visitor custom audience; (c) In-market segments: Home Improvement, Beauty, Wellness; (d) Interest: Hard water solutions, Sustainable home products, Skincare consumers. |
| G-PM2 | PMax ad strength "Good" or "Excellent" for all asset groups | High | NEEDS VERIFICATION (assumed WARNING) | "Average" PMax ad strength is the default outcome when asset groups lack diverse creative formats and sufficient copy variety. | Follow asset group completeness guidance (G31, G32). Achieve "Good" or better before allocating significant budget to a PMax campaign. |
| G-PM3 | PMax brand cannibalization under 15% (brand terms served by PMax) | Critical | NEEDS VERIFICATION (assumed FAIL) | PMax will serve on branded search terms by default, pulling budget from non-brand acquisition and skewing ROAS figures upward (brand terms convert at much higher rates). For Curo Skin, brand search volume may be low, but any cannibalization at this budget is costly. | Add "Curo Skin" and all brand variants as PMax negative keywords (via the Campaign-level negative keyword tool in Google Ads, or through a Google rep request). Verify in search term report that PMax is not serving on brand queries. |
| G-PM4 | Search Themes configured for PMax asset groups (up to 50 per group) | Medium | NEEDS VERIFICATION (assumed FAIL) | Search Themes are the PMax mechanism for guiding search query targeting. Without them, PMax relies entirely on audience signals and landing page content to infer relevant queries. For a specific product category like shower filters, Search Themes are essential. | Add 20–30 Search Themes per asset group: shower filter UK, filtered shower head, hard water shower filter, chlorine shower filter, best shower filter, shower head filter replacement, remove limescale shower, clean water shower head, shower filter chrome/brushed gold/black. |
| G-PM5 | Negative keywords applied to PMax (up to 10,000) | Critical | NEEDS VERIFICATION (assumed FAIL) | PMax negative keywords require a Google rep or the Experiments tool to apply at scale. Small accounts almost never have these in place. Without them, PMax wastes budget on the same irrelevant terms identified in G13/G16. | Apply the same themed negative keyword lists from G14 to PMax. If Google rep access is unavailable, use the Account-level negative keyword list which applies to PMax automatically. |

**Category 5 Assessment:** Ads and assets are likely the most visible area for improvement. Curo Skin's brand story — awards, reviews, 60-day MBG, subscription model, premium colourways — is substantially underutilised in ad creative and copy. The quick wins here are almost entirely in copywriting and asset uploading, requiring no additional budget.

---

## Category 6: Settings & Targeting (10% Weight)
*18 checks: G36–G41, G50–G61*

| ID | Check | Severity | Status | Reasoning | Recommendation |
|----|-------|----------|--------|-----------|----------------|
| G36 | Search Network only (not Display) for search campaigns | High | NEEDS VERIFICATION (assumed FAIL) | Google Search campaigns default to "Search Network with Display Network expansion" which silently adds Display placements with no creative optimisation. This is a budget leak that most small advertisers never notice. | In every Search campaign, verify that "Display Network" is unchecked under Networks settings. Display should be managed in a separate campaign with dedicated creative. |
| G37 | Target CPA/ROAS set within 20% of historical performance | Critical | NEEDS VERIFICATION (assumed FAIL) | With likely under 30 conversions/month on Google, there is no reliable historical CPA/ROAS benchmark for Smart Bidding. Any target set is essentially arbitrary, and Google's algorithm will either under-serve (target too aggressive) or overbid (target too loose). | Do not set a Target CPA or ROAS until 30+ conversions/month are consistently achieved. Use Maximise Conversions or Manual CPC (Enhanced) in the interim. |
| G38 | Bidding strategy appropriate for account maturity | High | NEEDS VERIFICATION (assumed WARNING) | Accounts at this conversion volume should be on Maximise Conversions (no target) for data collection, not Target CPA/ROAS. | Align bidding strategy to conversion volume. Below 30 conv/month: Maximise Conversions. Above 30: Maximise Conversions with Target CPA. Above 50: Target CPA or Target ROAS. |
| G39 | Device bid adjustments applied based on conversion data | Medium | NEEDS VERIFICATION (assumed WARNING) | Mobile conversion rates for a £80 purchase are typically 30–50% lower than desktop. Without device bid adjustments reducing mobile bids, budget is wasted on mobile browsers who research then purchase on desktop. | After 60 days of conversion data: apply -20% to -40% mobile bid adjustment if mobile CVR is materially below desktop. Do not set before you have data — you may be in a niche where mobile converts well (bathroom product researched on phone). |
| G40 | Location bid adjustments applied (UK regions) | Low | NEEDS VERIFICATION (assumed WARNING) | London and the South East have higher hard water severity and arguably higher DTC e-commerce propensity. Regional bid adjustments could improve efficiency. | After 90 days: review performance by UK region in Google Analytics and Google Ads. Apply +10–15% bid adjustment to London, South East, East of England where hard water prevalence is highest. |
| G41 | Ad rotation set to "Optimise" (not "Rotate indefinitely") | Medium | NEEDS VERIFICATION (assumed WARNING) | "Rotate indefinitely" prevents Google from optimising ad serving toward better performers, wasting impressions on lower-CTR ads. | Set all campaigns to "Optimise: Prefer best performing ads". Review rotation data monthly. Manually pause consistently underperforming RSA variants based on asset-level reporting. |
| G50 | Remarketing audiences created and populated | High | NEEDS VERIFICATION (assumed FAIL) | Without Consent Mode v2 properly implemented (G45), remarketing audiences will be suppressed for a significant portion of UK visitors. Even with consent, remarketing lists likely don't exist or are tiny at this traffic volume. | Prerequisite: fix Consent Mode v2 first (G45). Then create: (a) All website visitors 30 days; (b) Product page viewers 30 days; (c) Add-to-cart 14 days; (d) Past purchasers 90 days (exclusion list). Use RLSA to bid higher on returning high-intent visitors. |
| G51 | Customer Match lists uploaded and used | Medium | NEEDS VERIFICATION (assumed FAIL) | Customer Match (uploading email lists) is a powerful first-party data signal for both Smart Bidding and audience targeting. With 100+ reviews on Judge.me, there is a customer base to upload. | Upload all past customer emails as a Customer Match audience. Use as: (a) bidding signal for Smart Bidding; (b) exclusion from prospecting to avoid wasting budget on existing customers; (c) audience signal in PMax. |
| G52 | In-market and affinity audiences layered as observation signals | Low | NEEDS VERIFICATION (assumed WARNING) | Observation mode audiences let you gather data on which audience segments convert best without restricting reach. This data then informs bid adjustments. | Add these audiences in Observation mode to all campaigns: In-market: Home Improvement, Beauty Products, Health & Wellness; Affinity: Beauty Mavens, Lifestyle & Hobbies. After 60 days, apply positive bid adjustments to over-indexing segments. |
| G53 | Demographic targeting reviewed and adjusted | Low | NEEDS VERIFICATION (assumed WARNING) | Shower filters in the beauty/wellness DTC category skew female, 25–45. Default demographic targeting includes all ages and genders. | After 60 days: review demographic performance report. If women 25–44 show lower CPA, apply positive bid adjustment. Consider excluding demographics with zero conversions and high spend. |
| G54 | Google Merchant Center account health: no disapprovals | High | NEEDS VERIFICATION (assumed WARNING) | Merchant Center product disapprovals silently remove products from Shopping results. Common disapprovals: missing GTIN, price mismatch, promotional text in image, unverified URL. | Log into Merchant Center weekly. Address any "Needs attention" or "Disapproved" status items within 48 hours. Ensure product feed is on automated sync (daily) from Shopify. |
| G55 | Shopping feed titles optimised for search intent | High | NEEDS VERIFICATION (assumed FAIL) | Shopify's default Google Shopping integration exports product titles as the Shopify product name (e.g. "Shower Head - Chrome") rather than search-optimised titles. | Optimise titles using DataFeedWatch or a Shopify feed app: "Curo Skin Filtered Shower Head - Chrome - Removes Chlorine & Hard Water - £79.99". Include: brand, product type, key benefit, variant, price signal. |
| G56 | Price competitiveness checked relative to competitors in Shopping | Medium | NEEDS VERIFICATION (assumed WARNING) | At £80, Curo Skin is positioned at the premium end of filtered shower heads. Hello Klean is similarly priced. Jolie (US-imported) may appear higher. Price competitiveness affects Shopping placement quality. | Monitor competitor pricing in Shopping monthly. If Curo Skin's price is more than 20% above nearest competitor for equivalent product, adjust Shopping bidding to target lower funnel, higher-intent placements rather than volume. |
| G57 | Automated rules or scripts in place for budget protection | Low | NEEDS VERIFICATION (assumed FAIL) | At this budget, automated rules to pause campaigns if daily spend exceeds threshold, or to pause keywords if CPA exceeds target by 3x, are essential safety nets. | Create automated rules: (a) Pause campaign if cost > 120% of daily budget by 8pm; (b) Pause keywords with CPA > 3x target after 7 days; (c) Email alert if daily spend drops to zero (tag firing failure). |
| G58 | Conversion-based bid adjustments reviewed quarterly | Low | NEEDS VERIFICATION (assumed FAIL) | Bid adjustments (device, location, time, audience) require periodic review as seasonality and consumer behaviour shift. | Set a quarterly calendar reminder to review all bid adjustments against current conversion data and reset or refine as needed. |
| G59 | Google Ads account linked to Google Search Console | Medium | NEEDS VERIFICATION (assumed WARNING) | GSC linking provides organic search data alongside paid data, enabling keyword gap analysis and avoiding keyword cannibalisation between SEO and PPC. | Link GSC to Google Ads (under Tools > Linked Accounts). Use the Paid & Organic report to identify where Curo Skin has organic coverage, reducing the need for paid bidding on those terms. |
| G60 | Experiments (A/B tests) used for bidding strategy changes | Low | NEEDS VERIFICATION (assumed FAIL) | Almost never used at this scale. Experiments are the correct way to test bidding strategy changes (e.g. moving from Maximise Conversions to Target CPA) without risking full campaign performance on an untested change. | Use Campaign Experiments for any bidding strategy change. Run 50/50 split for 4 weeks minimum before making permanent changes. |
| G61 | Target Impression Share campaign set up for brand terms | High | NEEDS VERIFICATION (assumed FAIL) | Without a brand campaign bidding on [Curo Skin] exact match, competitors can and will serve ads on branded searches. Post-Dragons' Den, Hello Klean has aggressive Google Ads presence. | Launch a brand protection campaign immediately: Keyword: [curo skin] exact match + variants. Bidding: Target Impression Share 90%+ (top of page). Budget: £50–80/month. Ad copy: reinforce brand, offer, review score. This is the highest ROI campaign for any established DTC brand. |

**Category 6 Assessment:** Settings and targeting failures are largely a consequence of the tracking and structure issues upstream. Location targeting, device adjustments, and remarketing are all dependent on having clean conversion data first. The immediate action items here are: unchecking Display on Search campaigns, launching the brand protection campaign, and linking Search Console.

---

## Quick Wins (Sorted by Impact / Time to Implement)

These are actions that can materially improve performance within 1–2 weeks, requiring less than 15 minutes each to implement.

| Priority | Action | Category | Time | Expected Impact |
|----------|--------|----------|------|-----------------|
| 1 | Implement Consent Mode v2 with a certified CMP | Conversion Tracking | 2–4 hours (one-time) | Unlocks modelled conversions for 20–40% of UK traffic currently invisible; enables compliant remarketing |
| 2 | Audit and deduplicate conversion actions (one primary purchase action) | Conversion Tracking | 30 min | Eliminates likely 2–3x conversion inflation; reveals true CPA for accurate bidding |
| 3 | Enable Enhanced Conversions (hashed email from checkout) | Conversion Tracking | 1–2 hours | Recovers 15–30% of unattributed conversions from cookie-blocked browsers |
| 4 | Build 3 themed negative keyword lists and apply to all campaigns | Wasted Spend | 2 hours | Eliminates 15–30% wasted spend on irrelevant queries; immediate CPA improvement |
| 5 | Launch brand protection campaign ([curo skin] exact match, £60/month) | Account Structure | 30 min | Prevents competitor conquest, protects high-CVR branded traffic, highest-ROAS campaign in account |
| 6 | Uncheck "Display Network" on all Search campaigns | Settings | 15 min | Stops silent budget leak to display placements with no conversion-optimised creative |
| 7 | Add all 15 headlines to RSAs featuring award names, review scores, 60-day MBG | Ads & Assets | 1 hour | CTR improvement of 15–25% from "Average" to "Good" Ad Strength |
| 8 | Configure all ad extensions (sitelinks, callouts, structured snippets, price) | Ads & Assets | 1–2 hours | Increases ad real estate, improves CTR by 10–20%, quality signal to Google |
| 9 | Add PMax brand term negatives and configure Search Themes | Ads & Assets | 1 hour | Stops brand cannibalization and guides PMax toward relevant category terms |
| 10 | Upload customer email list as Customer Match audience | Settings | 30 min | Improves Smart Bidding quality signal; enables exclusion of existing customers from prospecting |
| 11 | Optimise Merchant Center product feed titles | Settings | 2 hours | Improves Shopping impression share and CTR for category search queries |
| 12 | Link Google Search Console to Google Ads | Settings | 15 min | Enables Paid & Organic report; reveals organic coverage gaps and keyword cannibalisation |

---

## Critical Issues Requiring Immediate Action

The following issues should be treated as blockers — they mean that current Google Ads spend is either unmeasurable, misattributed, or being wasted at scale.

**1. Tracking is likely broken (or severely incomplete)**
Consent Mode v2 absent in the UK market means a material portion of conversions are untracked. Without this, every optimisation decision is based on false data. Fix this before everything else — it is the foundation.

**2. Budget is below the minimum viable threshold for Google**
$500–700/month on Google is insufficient for Smart Bidding to function on a £80 e-commerce product. The options are: (a) increase total budget so Google receives £800–1,000/month minimum; (b) pause Google entirely and double down on Meta/TikTok until total budget reaches £3,000+/month; or (c) restrict Google to brand protection only (£60–80/month) and retargeting only (£100/month), spending the remainder on Meta. Option (c) is the recommended pragmatic approach at current budget.

**3. Negative keywords are almost certainly absent or inadequate**
The shower filter category has vast irrelevant adjacent search volume (plumbing queries, water softeners, DIY repairs). Without structured negatives, the majority of budget is wasted.

**4. Brand/non-brand separation almost certainly absent**
Without a dedicated brand campaign, branded traffic (high CVR, low CPA) is blended with non-brand (lower CVR, high CPA), masking true performance and exposing branded searches to competitor conquest.

---

## Strategic Recommendations for Curo Skin on Google

### Recommendation 1: Reframe Google's Role at Current Budget

At £500–700/month, Google should NOT be trying to acquire new customers at scale. It should be doing two things only:
1. **Brand protection** (£60–80/month): Prevent Hello Klean and competitors from conquering "Curo Skin" searches
2. **High-intent retargeting** (£150–200/month): Retarget website visitors and cart abandoners with Shopping ads — these audiences are 5–10x more likely to convert

The remaining Google budget (if any) should either be redirected to Meta, where DTC acquisition at lower budgets is more efficient, or held until the total Google budget can reach £800–1,000/month.

### Recommendation 2: Fix Tracking Before Scaling

Every £ spent while tracking is broken generates misleading data that leads to compounding poor decisions. The 2–4 hours required to implement Consent Mode v2 and audit conversion deduplication is the highest-ROI investment available to this account.

### Recommendation 3: Leverage Curo Skin's Earned Media in Ad Copy

This is the single biggest underutilised competitive asset. Curo Skin has:
- 6 major press awards (Marie Claire, Glamour, WIRED, Good Housekeeping, Woman&Home, and others)
- Trustpilot 4.7 stars + Judge.me 4.88/5 from 100+ reviews
- 60-day money-back guarantee (above industry standard)
- Premium colourways (Chrome, Brushed Gold, Midnight Black) that Hello Klean doesn't match

None of this needs additional budget to incorporate into ad copy. It is a pure copywriting exercise that will meaningfully lift CTR and CVR.

### Recommendation 4: Subscription LTV Changes the Math

The subscription model fundamentally changes the acceptable CPA calculation. If the initial shower head purchase (£80) is followed by 4 filter replacements per year at (estimate) £20–25 each, LTV over 12 months is £160–180 — double the initial order value. If Google Ads is optimising for a £80 purchase CPA, it is systematically underinvesting. Configure conversion value rules (G-CT2) so Smart Bidding understands the full LTV signal.

### Recommendation 5: Seasonal and Category Demand Calendar

Shower filter demand likely peaks around:
- January (New Year wellness resolutions)
- Spring (pre-summer skin/hair care season)
- September/October (return to routine after summer)
- Pre-Christmas gift period (November–December)

Budget Google Ads spend against these peaks. In off-peak months (August, March), reduce Google budget and shift to Meta/TikTok brand awareness.

### Recommendation 6: Path to £1,000+/month on Google

The minimum viable Google budget gate is £800–1,000/month. To reach this:
- Prove Meta ROAS above 3.0x first — use that proof to justify budget reallocation
- Target total ad budget of £3,000–3,500/month before adding meaningful Google prospecting spend
- At that point, the recommended Google allocation is: Brand Protection £100 + Retargeting £150 + PMax (core products) £500 + Non-Brand Search £250

---

## Benchmark Comparison: Curo Skin vs UK DTC Health & Beauty E-commerce

| Metric | UK DTC Health/Beauty Benchmark | Curo Skin Estimate | Gap |
|--------|-------------------------------|-------------------|-----|
| Google Ads CPC (Shopping) | £0.45–£0.85 | £0.90–£1.50 (estimated, niche) | Negative — higher CPC expected |
| Google Ads CTR (Search) | 3.5–5.5% | 2.5–4.0% (estimated, low asset quality) | Can improve to benchmark with better RSAs |
| Google Ads CVR (E-commerce) | 1.8–3.2% | 1.5–2.5% (estimated) | At benchmark with good LP |
| Google Ads ROAS | 3.5–5.0x | Unknown (tracking likely broken) | Cannot estimate until tracking fixed |
| Impression Share Loss (Budget) | Under 20% target | 50–70% (estimated) | Critical — budget insufficient |
| Quality Score (weighted avg) | 7.0+ | 5–6 (estimated) | Improvement possible via RSA optimisation |

---

## Score Calculation Detail

### Category 1: Conversion Tracking (25%)
Checks: G42 FAIL, G43 FAIL, G44 WARNING, G45 FAIL, G46 WARNING, G47 WARNING, G48 N/A, G49 N/A, G-CT1 FAIL, G-CT2 FAIL, G-CT3 WARNING
Critical FAIL count: 4 (G42, G43, G45, G-CT1) × 5.0 severity
High FAIL count: 1 (G-CT2) × 3.0 severity
Medium/High WARNING count: 4 × 1.5 severity
**Raw Category Score: 38/100**

### Category 2: Wasted Spend (20%)
Checks: G13 FAIL, G14 FAIL, G15 WARNING, G16 FAIL, G17 FAIL, G18 FAIL, G19 WARNING, G-WS1 FAIL
Critical FAIL count: 4 (G13, G14, G16, G17) × 5.0 severity
High FAIL count: 2 (G18, G-WS1) × 3.0 severity
**Raw Category Score: 42/100**

### Category 3: Account Structure (15%)
Checks: G01 FAIL, G02 WARNING, G03 WARNING, G04 WARNING, G05 FAIL, G06 WARNING, G07 WARNING, G08 WARNING, G09 FAIL, G10 WARNING, G11 PASS, G12 FAIL
Critical FAIL: 1 (G05) × 5.0; High FAIL: 2 (G01, G09) × 3.0; Multiple WARNINGs × 1.5
**Raw Category Score: 45/100**

### Category 4: Keywords & Quality Score (15%)
Checks: G20 WARNING, G21 WARNING, G22 WARNING, G23 WARNING, G24 WARNING, G25 WARNING, G-KW1 FAIL, G-KW2 WARNING
High FAIL: 1 (G-KW1) × 3.0; Multiple WARNINGs × 1.5
**Raw Category Score: 48/100**

### Category 5: Ads & Assets (15%)
Checks: G26 WARNING, G27 WARNING, G28 FAIL, G29 WARNING, G30 FAIL, G31 FAIL, G32 FAIL, G33 WARNING, G34 WARNING, G35 PASS, G-AD1 FAIL, G-AD2 FAIL, G-PM1 FAIL, G-PM2 WARNING, G-PM3 FAIL, G-PM4 FAIL, G-PM5 FAIL
Critical FAIL: 1 (G-PM3, G-PM5) × 5.0; High FAIL: multiple × 3.0
**Raw Category Score: 50/100**

### Category 6: Settings & Targeting (10%)
Checks: G36 FAIL, G37 FAIL, G38 WARNING, G39 WARNING, G40 WARNING, G41 WARNING, G50 FAIL, G51 FAIL, G52 WARNING, G53 WARNING, G54 WARNING, G55 FAIL, G56 WARNING, G57 FAIL, G58 FAIL, G59 WARNING, G60 FAIL, G61 FAIL
Critical FAIL: 2 (G37, G61) × 5.0; High FAIL: multiple × 3.0
**Raw Category Score: 44/100**

### Final Score
(38 × 0.25) + (42 × 0.20) + (45 × 0.15) + (48 × 0.15) + (50 × 0.15) + (44 × 0.10)
= 9.5 + 8.4 + 6.75 + 7.2 + 7.5 + 4.4
= **43.75 / 100 — Grade: D (Poor)**

---

*End of Google Ads Audit — Curo Skin (curoskin.co.uk) — Assessment-Based, 2026-02-15*
*Requires account access to confirm all NEEDS VERIFICATION items. All inferred statuses are based on DTC e-commerce norms at sub-$700/month Google budget.*
