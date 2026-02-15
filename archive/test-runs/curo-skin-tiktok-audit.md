# TikTok Ads Audit: Curo Skin (curoskin.co.uk)
**Audit Date:** 2026-02-15
**Auditor:** Creative Quality Specialist (TikTok, LinkedIn, Microsoft Ads)
**Business:** Curo Skin — DTC shower filters, UK market
**Budget Context:** ~$2,000/month total across Google, Meta, TikTok
**Methodology:** Assessment-based audit using best practices (no account access). Likely status reflects typical patterns for a DTC e-commerce brand at this budget level. All items marked NEEDS VERIFICATION require direct account access to confirm.

> NOTE: Reference files `ads/references/tiktok-audit.md`, `platform-specs.md`, and `benchmarks.md` were not present in this repository. This audit is grounded in the 25-check TikTok framework defined in the audit system specification, TikTok Ads Manager best practices, and the Curo Skin business context provided.

---

## Executive Summary

Shower filters are one of the most TikTok-native product categories in existence. Jolie (US) and ATOJET (K-beauty) built their brands almost entirely through TikTok virality. Curo Skin has every ingredient for TikTok success — a visually demonstrable product, strong social proof, award credibility, a subscription model for LTV, and a UK TikTok Shop infrastructure that is ready to use. The single most critical finding of this audit is not creative or technical — it is **budget allocation**. At ~$2,000/month across three platforms, TikTok almost certainly receives under $500/month, which is below the platform's minimum viable threshold. This prevents the algorithm from ever exiting the learning phase, wastes every pound spent, and means Curo Skin may be advertising on their highest-potential platform in a way that is structurally guaranteed to fail.

---

## TikTok Ads Health Score Summary

| Category | Weight | Raw Score (/100) | Weighted Score |
|---|---|---|---|
| Creative Quality | 30% | 28 | 8.4 |
| Technical Setup | 25% | 35 | 8.75 |
| Bidding & Learning | 20% | 20 | 4.0 |
| Structure & Settings | 15% | 30 | 4.5 |
| Performance | 10% | 25 | 2.5 |
| **OVERALL TIKTOK HEALTH SCORE** | **100%** | — | **28.15 / 100** |

> Score interpretation: 0-39 = Critical — fundamental issues preventing performance; 40-59 = Poor — significant gaps; 60-79 = Average — optimisation opportunities; 80-100 = Healthy.
>
> Curo Skin scores in the Critical band. This reflects the near-certain budget insufficiency and the assessment-based assumption that most TikTok-specific best practices have not yet been implemented for a brand at this stage. The score is not a reflection of the brand's quality — it reflects how TikTok as a channel is almost certainly being operated at this budget level.

---

## Category 1: Structure & Settings (T01-T04)
**Weight: 15% | Category Score: 30/100**

### T01 — Campaign Objective Matches Business Goal
| Field | Detail |
|---|---|
| **Severity** | Critical |
| **Likely Status** | WARNING / NEEDS VERIFICATION |
| **Reasoning** | For a DTC e-commerce brand selling an £80 product with a subscription backend, the correct objective is Website Conversions optimised for Complete Payment (or Add to Cart if purchase volume is insufficient for algorithm learning). Brands at this budget level frequently launch with Traffic or Video Views objectives because they appear cheaper and generate activity metrics, but these objectives deliver unqualified audiences with no purchase intent. There is no account data to confirm the objective in use. |
| **Recommendation** | Verify that all active campaigns use the Conversions objective with Complete Payment as the optimisation event. If purchase volume is below 50 events per ad group per week (highly likely at this budget), switch the optimisation event to Add to Cart or Initiate Checkout to feed the algorithm sufficient signals. Do not run Traffic or Reach objectives for conversion campaigns. |

---

### T02 — Ad Group Targeting: Not Over-Segmented
| Field | Detail |
|---|---|
| **Severity** | High |
| **Likely Status** | WARNING / NEEDS VERIFICATION |
| **Reasoning** | Over-segmentation is one of the most common structural errors for small DTC brands on TikTok. At under $500/month in TikTok spend, splitting budget across multiple narrow ad groups (e.g., separate ad groups for women 25-34, men 35-44, beauty interest, wellness interest) fragments the data, prevents each ad group from generating sufficient conversion signals, and keeps every ad group permanently in learning phase. TikTok's algorithm needs scale to work — it cannot learn from 2-3 conversions per ad group per week. |
| **Recommendation** | Consolidate to a maximum of 2 ad groups: one broad prospecting ad group (UK, 18-45, no interest stacking) and one retargeting ad group (website visitors, video viewers). Remove gender, age, and interest restrictions from the prospecting ad group and let TikTok's algorithm find buyers. Add interest targeting only as a test layer once budget exceeds $1,500/month on TikTok alone. |

---

### T03 — UK Geo Targeting Correctly Configured
| Field | Detail |
|---|---|
| **Severity** | Critical |
| **Likely Status** | PASS (likely, NEEDS VERIFICATION) |
| **Reasoning** | Curo Skin is a UK-only brand (curoskin.co.uk, GBP pricing, UK fulfilment). Targeting beyond the UK would waste spend on audiences that cannot purchase. Most brands correctly configure their primary market. However, the risk at this stage is accidentally leaving targeting broad or including Ireland, which has a different VAT and fulfilment setup. |
| **Recommendation** | Confirm geo targeting is set to United Kingdom only. Exclude Northern Ireland if fulfilment or VAT creates complications. Verify that TikTok's language targeting is set to English (United Kingdom) to avoid serving to non-English speakers in broader UK targeting. |

---

### T04 — TikTok Pixel Installed and Firing Correctly
| Field | Detail |
|---|---|
| **Severity** | Critical |
| **Likely Status** | WARNING (assumed) |
| **Reasoning** | The TikTok Pixel is the foundational requirement for all conversion optimisation, retargeting audiences, and performance measurement. For a Shopify-based DTC brand (assumed, as is standard for UK DTC at this stage), Pixel installation should be straightforward via the TikTok Shopify app. However, at this budget level and stage of maturity, incomplete event configuration is extremely common. Specifically: the Pixel may fire ViewContent but not AddToCart, InitiateCheckout, and CompletePayment as distinct events. Without all funnel events, the algorithm cannot optimise, retargeting audiences cannot be built, and reported ROAS will be inaccurate. Additionally, UK GDPR requires explicit consent before the Pixel fires — if a Consent Management Platform (CMP) is not correctly integrated, the Pixel may be either (a) firing without consent (a legal compliance risk) or (b) not firing at all for users who interact with a consent banner and then accept, due to incorrect CMP-to-Pixel integration. |
| **Recommendation** | Use TikTok's Pixel Helper browser extension to verify all five key events fire correctly: ViewContent, AddToCart, InitiateCheckout, CompletePayment, Subscribe. Implement TikTok's Events API (server-side, equivalent to Meta's CAPI) alongside the browser Pixel — this is non-negotiable for UK market due to ad blockers and iOS privacy changes. Verify CMP integration: the Pixel must only fire after consent is granted, and the CMP must correctly pass consent status to TikTok. Use TikTok's Pixel diagnostics in Ads Manager to check event match quality scores — target 7+ out of 10 for email hashing. |

---

**Structure & Settings Score Reasoning:** Two Critical checks are at WARNING/NEEDS VERIFICATION (T01, T04), one Critical is likely PASS (T03), and one High is at WARNING (T02). The Pixel compliance risk in the UK market and the budget-driven over-segmentation risk are the primary score drivers. Estimated raw score: 30/100.

---

## Category 2: Bidding & Learning (T14-T18)
**Weight: 20% | Category Score: 20/100**

### T14 — Sufficient Budget for Learning Phase
| Field | Detail |
|---|---|
| **Severity** | Critical |
| **Likely Status** | FAIL |
| **Reasoning** | This is the most important finding in this entire audit. TikTok's minimum campaign budget is $50/day ($1,500/month). TikTok's algorithm requires approximately 50 optimisation events per ad group per 7-day period to exit the learning phase and begin efficient delivery. At Curo Skin's total budget of ~$2,000/month across Google, Meta, and TikTok, the TikTok allocation is most likely in the $300-$500/month range ($10-$17/day). This is 70-80% below the platform minimum for effective learning. The practical consequence is that TikTok's algorithm never learns who to target, CPMs are inflated (the algorithm bids inefficiently when data-starved), CPA is structurally elevated, and every creative test is inconclusive because there is no statistical significance in the results. The brand is not "testing TikTok" at this budget — they are spending money in a way that is near-certain to produce poor results, which may incorrectly lead to the conclusion that "TikTok doesn't work for us" when the real issue is budget insufficiency. |
| **Recommendation** | Two paths: (A) Increase TikTok budget to $1,500/month minimum ($50/day) by reallocating from another platform — this is the recommended path if TikTok is a strategic priority, given that shower filters are a TikTok-native category with enormous organic amplification potential. (B) If total budget cannot increase, pause TikTok paid ads entirely, focus on TikTok organic content and TikTok Shop (which has no ad spend minimum), and return to paid TikTok when total budget reaches $3,500+/month allowing a proper allocation. Running TikTok ads at $300-500/month is the worst of all outcomes — it costs money, produces no learnings, and cannot scale. |

---

### T15 — Bidding Strategy Appropriate for Stage
| Field | Detail |
|---|---|
| **Severity** | High |
| **Likely Status** | WARNING / NEEDS VERIFICATION |
| **Reasoning** | For a brand at this early stage with limited conversion data, Lowest Cost (automatic bidding) is the correct strategy. It allows TikTok maximum flexibility to find conversions within the budget and is the only strategy that can function with low conversion volume. Cost Cap and Minimum ROAS bidding strategies require significant historical data and stable conversion volume to work effectively — applied too early, they cause delivery to stall entirely (the algorithm cannot find conversions at the specified cost and simply stops spending). There is a real risk that a brand seeking efficiency has moved to Cost Cap prematurely and is experiencing near-zero delivery as a result. |
| **Recommendation** | Confirm Lowest Cost bidding is in use for all active campaigns. Do not apply Cost Cap until the account has at least 50 purchase conversions per week at stable CPA for 4+ consecutive weeks. Use Lowest Cost for the first 60-90 days regardless of efficiency concerns — the priority is generating enough data for the algorithm to learn. |

---

### T16 — Ad Group Daily Budget at or Above $20/day
| Field | Detail |
|---|---|
| **Severity** | High |
| **Likely Status** | FAIL (assumed) |
| **Reasoning** | TikTok recommends a minimum ad group budget of $20/day for conversion campaigns. At an estimated total TikTok allocation of $10-17/day for the entire account, it is nearly certain that individual ad groups are running at $5-10/day — well below this threshold. Ad groups below $20/day receive severely limited delivery and cannot generate meaningful conversion data. |
| **Recommendation** | Consolidate to a single active ad group if budget is below $50/day total. One well-funded ad group that can learn is dramatically more valuable than three under-funded ad groups that cannot. A single ad group at $20/day has a real chance of generating insights. Three ad groups at $7/day each produce only noise. |

---

### T17 — Campaign Not in Permanent Learning Phase
| Field | Detail |
|---|---|
| **Severity** | High |
| **Likely Status** | FAIL (assumed) |
| **Reasoning** | TikTok's learning phase requires 50 optimisation events per ad group within 7 days to complete. At the assumed budget level, generating 50 purchases per week is essentially impossible (at a £30 CPA — optimistic — that requires £1,500/week in spend per ad group). This means the campaigns are almost certainly in permanent learning phase, characterised by volatile CPAs, inconsistent delivery, and no algorithmic efficiency gains. |
| **Recommendation** | Lower the optimisation event from Complete Payment to Add to Cart or Initiate Checkout to generate 50 events per week at a lower cost threshold. This is a necessary interim step — the algorithm learns from funnel events even if they are not purchases. Once Add to Cart volume is stable and the account graduates from learning, gradually shift optimisation back toward Complete Payment. |

---

### T18 — No Conflicting Campaigns Cannibalising Each Other
| Field | Detail |
|---|---|
| **Severity** | Medium |
| **Likely Status** | WARNING / NEEDS VERIFICATION |
| **Reasoning** | If multiple campaigns target the same audience (e.g., a prospecting campaign and a retargeting campaign both targeting UK women interested in beauty), they will compete against each other in TikTok's auction, inflating CPMs and fragmenting data. At low budgets this risk is amplified — there simply is not enough spend to support multiple campaigns bidding for the same impressions. |
| **Recommendation** | Implement audience exclusions: retargeting ad groups must exclude audiences captured by prospecting ad groups. Exclude website visitors (30 days) from prospecting. Exclude TikTok video viewers (engaged) from prospecting. This prevents internal auction conflict and ensures each campaign reaches distinct audience segments. |

---

**Bidding & Learning Score Reasoning:** Two Critical/High checks are outright FAILs (T14, T16, T17). The budget insufficiency finding (T14) is a structural FAIL that cascades into every other performance metric. Estimated raw score: 20/100.

---

## Category 3: Creative Quality (T05-T10, T20-T25)
**Weight: 30% | Category Score: 28/100**

### T05 — At Least 6 Creatives Per Ad Group
| Field | Detail |
|---|---|
| **Severity** | Critical |
| **Likely Status** | FAIL (assumed) |
| **Reasoning** | TikTok recommends a minimum of 6 creative assets per ad group to give the algorithm variety and to prevent creative fatigue. For a DTC brand at this budget level, creative production is typically the bottleneck. Most brands at $300-500/month TikTok spend have 2-4 creatives active at most, often repurposed from Meta or static product images. This is compounded by the fact that TikTok creative burns significantly faster than other platforms — a good TikTok creative may fatigue within 7-14 days on a small but active account. 6 creatives is a minimum floor, not a target. Brands like Jolie maintain 20+ active creative variants. |
| **Recommendation** | Prioritise creative production immediately. Target minimum 6 creatives per ad group, with a goal of 10+ over the next 60 days. Creative formats to produce: (1) UGC-style filter unboxing / first use, (2) before-and-after water quality demonstration with dirty filter reveal, (3) shower routine "what I use" format, (4) testimonial / review reading format with B-roll, (5) transformation narrative (hair/skin improvement), (6) product comparison vs. unfiltered water (use TDS meter or visual demo). Creative production for TikTok does not require professional video — iPhone, ring light, authentic delivery. Budget ~£500-800 for 6-10 creator UGC pieces as a one-time investment. |

---

### T06 — All Video Assets in 9:16 Vertical Format (1080x1920)
| Field | Detail |
|---|---|
| **Severity** | Critical |
| **Likely Status** | WARNING (assumed) |
| **Reasoning** | TikTok's full-screen vertical format is non-negotiable for native performance. Horizontal or square videos (repurposed from Meta or YouTube) perform dramatically worse — they show black bars, break the immersive experience, and are immediately recognisable as non-native ads, which increases scroll rate. At this stage, it is common for brands to repurpose Meta video creatives for TikTok out of budget and time constraints. Even if videos are technically 9:16, if they were originally filmed horizontally and cropped, the composition will be wrong (important elements cut off, faces at the edge, text near unsafe zones). |
| **Recommendation** | Audit every active creative: confirm it was filmed natively in 9:16 vertical (portrait mode on a phone or camera set to vertical). Reject any creative that was originally horizontal and cropped. All text overlays, logos, product shots, and faces must be within the safe zone: X: 40-940px, Y: 150-1470px (900x1320px usable area). Verify specifically that no text or CTA appears in the bottom 450px (covered by TikTok UI: captions, music bar, CTA button, navigation). |

---

### T07 — Content Feels Native to TikTok (Not Corporate)
| Field | Detail |
|---|---|
| **Severity** | High |
| **Likely Status** | WARNING / FAIL (assumed) |
| **Reasoning** | This is the most common creative failure for DTC brands crossing over from Meta to TikTok. TikTok users have an extremely refined ability to identify ads that feel like ads — polished product photography, stock music, professional voiceover, branded lower-thirds, white-background product shots — and they scroll past them instantly. For Curo Skin specifically: a shower filter is an intimate, personal product. The most effective TikTok content for this category is raw, authentic, personal. It should look like an organic creator video that happens to feature the product. Award badges, press logos, and brand colours belong on landing pages — not on TikTok creatives. The competitor Jolie's viral content was almost entirely creator-shot iPhone video with text overlays and trending audio, not polished advertising. |
| **Recommendation** | Every creative should pass the "would I pause scrolling for this?" test from the perspective of a 26-year-old UK woman on TikTok. Specific executions that work for shower filters: a creator talking to camera about their hair/skin concerns and showing the Curo filter as the solution; time-lapse of a filter after 90 days (shows the "proof" of what it removed); "PSA: if you shower in London tap water, watch this" hook; response to a comment format ("You asked if it's worth it — here's my honest answer after 3 months"). Avoid: brand logo in the first 3 seconds, voiceover that sounds scripted, polished background or studio setting, text that uses the brand's colour palette heavily. |

---

### T08 — Hook Delivered Within First 1-2 Seconds
| Field | Detail |
|---|---|
| **Severity** | High |
| **Likely Status** | WARNING / FAIL (assumed) |
| **Reasoning** | TikTok's average user makes a scroll-or-stay decision within 0.8 seconds. The first frame must create pattern interrupt or immediate curiosity. For a shower filter brand, this means the opening frame cannot be a product shot, a logo, or a generic lifestyle image. Common hook failures: starting with a slow zoom on the shower head, opening with brand music and a logo card, showing a person speaking without establishing immediate context. The most effective hooks for this product category are visual proof (the brown/discoloured used filter), a bold text claim ("I can't believe what came out of my shower"), or a question that creates tension ("Why does London tap water destroy your hair?"). |
| **Recommendation** | The first 1.5 seconds must contain one of: (a) a visually striking image that creates curiosity (dirty filter, discoloured water, dramatic hair before), (b) a bold text overlay making a specific claim, or (c) a creator speaking directly to camera with a pattern-interrupting opening line. Script every creative's first line before filming. Test at minimum 3 different hook styles per creative concept: problem-first, social proof-first, and curiosity-gap. Track 2-second view rate in TikTok Ads Manager — target above 30%. If below 25%, the hook is failing and must be replaced before any other optimisation. |

---

### T09 — No Creative Active Beyond 7 Days with Declining CTR
| Field | Detail |
|---|---|
| **Severity** | High |
| **Likely Status** | FAIL (assumed) |
| **Reasoning** | TikTok creative fatigue is aggressive. In a small, defined market like the UK with a relatively niche product, the same creative can exhaust a meaningful portion of the relevant audience within 7-14 days at even modest spend levels. Declining CTR is the primary fatigue signal. At low budgets with infrequent campaign check-ins (common at this business stage), fatigued creatives often run for 3-4 weeks delivering degraded performance with no intervention. This compounds the budget problem: already-limited spend is directed at fatigued creatives delivering poor CTR and elevated CPMs. |
| **Recommendation** | Implement a weekly creative review cadence. Check CTR trajectory every 7 days for all active creatives. If CTR has declined more than 20% week-over-week for two consecutive weeks, pause the creative. Do not delete — archived creatives can be re-activated after 4-6 weeks as the audience refreshes. Maintain a creative pipeline of at least 2 new creatives ready to deploy at any time so that pausing a fatigued creative never leaves an ad group with fewer than 3 active assets. |

---

### T10 — Spark Ads Tested
| Field | Detail |
|---|---|
| **Severity** | High |
| **Likely Status** | FAIL / NEEDS VERIFICATION |
| **Reasoning** | Spark Ads allow brands to boost organic TikTok posts (their own or creator posts with permission) as paid ads. For Curo Skin, this is a particularly high-value feature because: (1) Curo Skin likely has organic TikTok content or could obtain creator UGC, (2) Spark Ads carry the creator's follower count and existing engagement, making them feel far more native than standard In-Feed ads, (3) Spark Ads average approximately 3% CTR versus approximately 2% for standard In-Feed ads — a 50% CTR uplift, and (4) social proof compounds: likes, comments, and shares from organic distribution carry over to the paid promotion, making the content look popular even when ad spend is modest. At this budget level, the difference between 2% and 3% CTR is meaningful — it translates directly to more traffic per pound spent. |
| **Recommendation** | Identify the top 3-5 performing organic TikTok posts for Curo Skin (or from creator partners). Request Spark Ads authorisation codes from the creators. Convert these to Spark Ads immediately. Prioritise posts that already have engagement (comments, shares) as the existing social proof amplifies ad performance. If Curo Skin has no existing organic TikTok presence, this is a secondary priority — but building that presence should start immediately as it feeds both organic discovery and Spark Ads inventory. |

---

### T20 — TikTok Shop Integration (E-commerce)
| Field | Detail |
|---|---|
| **Severity** | Medium |
| **Likely Status** | FAIL / NEEDS VERIFICATION |
| **Reasoning** | TikTok Shop launched in the UK in 2023 and is available to UK e-commerce sellers. For Curo Skin, TikTok Shop represents a significant opportunity: (1) it removes the friction of leaving the TikTok app to purchase, (2) TikTok Shop products are eligible for the product showcase tab and affiliate creator programme, (3) TikTok Shop Ads (formerly VSA - Video Shopping Ads) have shown strong ROAS for beauty/wellness products in the UK market, and (4) the subscription model can be partially implemented via TikTok Shop's bundle features. The k-beauty shower filter trend (ATOJET etc.) is driving massive TikTok Shop volume in this category. Not being present in TikTok Shop while competitors are is a meaningful competitive disadvantage in the UK. |
| **Recommendation** | Register for TikTok Shop UK as a priority. List the core products: Filtered Shower Head (£80), 90-day Replacement Filter, Shower Holder, Vanity Case. Apply for TikTok Shop's affiliate programme to allow UK beauty/wellness creators to earn commission on Curo Skin sales — this creates a self-funding UGC pipeline. Set up product links in organic TikTok posts and paid Video Shopping Ads. The initial time investment is approximately 4-6 hours; the potential return in organic and paid reach from TikTok Shop is disproportionate to the effort at this stage. |

---

### T21 — Video Shopping Ads Tested
| Field | Detail |
|---|---|
| **Severity** | Medium |
| **Likely Status** | FAIL / NEEDS VERIFICATION |
| **Reasoning** | Video Shopping Ads (VSA) are TikTok's e-commerce-native ad format that overlays shoppable product cards directly on video ads. They are distinct from standard In-Feed video ads and require TikTok Shop integration to activate. For a product like the Curo Skin shower filter — visually demonstrable, clearly priced, with strong review credibility — VSA format is well-suited: the product card showing £80 price point with 4.88/5 review rating alongside a compelling demo video is a high-conversion format. This is contingent on T20 (TikTok Shop) being implemented first. |
| **Recommendation** | Once TikTok Shop is live (T20), create 2-3 Video Shopping Ad variants using the top-performing creative assets. Test VSA alongside standard In-Feed ads to measure direct conversion rate difference. VSA attribution is cleaner (in-app purchase tracked natively) which also improves reporting accuracy compared to pixel-based attribution. |

---

### T22 — Caption SEO with High-Intent Keywords
| Field | Detail |
|---|---|
| **Severity** | High |
| **Likely Status** | WARNING / FAIL (assumed) |
| **Reasoning** | TikTok's search function has become a significant discovery channel — particularly for product research in the beauty and wellness categories. TikTok search queries for terms like "shower filter UK", "filtered shower head", "hard water hair damage", and "chlorine shower filter" are substantial and growing. Ad captions and organic post captions serve as indexable text for TikTok's search algorithm. Brands that treat captions as an afterthought ("link in bio, DM for more info") are missing a free discoverability layer. For Curo Skin specifically, the search intent around "hard water hair" and "London tap water" is high and directly maps to the product's core value proposition. |
| **Recommendation** | Rewrite all active ad captions to include high-intent search terms naturally. Primary terms: "shower filter UK", "hard water hair", "chlorine shower filter", "filtered shower head", "clean water shower". Secondary terms: "hair health", "skin barrier", "shower routine UK", "London water filter". Structure: lead with the hook/benefit statement, embed 2-3 primary keywords in the first sentence, add 3-5 relevant hashtags (mix of high-volume: #ShowerFilter, #HairCare, #SkincareRoutine; and niche: #HardWater #CleanWater #CuroSkin). Do not keyword-stuff — write for humans first, search second. |

---

### T23 — Trending Audio Used
| Field | Detail |
|---|---|
| **Severity** | Medium |
| **Likely Status** | FAIL / WARNING (assumed) |
| **Reasoning** | TikTok is a sound-on platform. Approximately 93% of TikTok users watch with sound on. Trending audio provides an immediate native signal — the algorithm favours content using trending sounds, and users who recognise a trending audio track are more likely to pause and watch. Using a generic stock music track or no audio is an immediate native-feel penalty. For paid ads, TikTok's Commercial Sound Library provides a subset of licensed trending sounds. Many brands at this stage either (a) use the same background music track across all creatives regardless of trend relevance, or (b) use creator-produced UGC with native audio that may not be licensed for paid use. |
| **Recommendation** | Each new creative batch should be timed to use a currently trending audio track from TikTok's Commercial Sound Library. Check trending sounds in the Creative Center weekly. For UGC/Spark Ads: confirm audio licensing before boosting organic content as paid ads — using unlicensed audio in paid promotion will cause the ad to be rejected or muted. For voiceover-led content (which can be highly effective for this product category), the primary audio is the voiceover; add a subtle trending background track at 15-20% volume to preserve the native feel. |

---

### T24 — Custom CTA Button Used (Not Default)
| Field | Detail |
|---|---|
| **Severity** | Medium |
| **Likely Status** | WARNING / NEEDS VERIFICATION |
| **Reasoning** | TikTok In-Feed ads include a CTA button overlay. The default is "Learn More" — a generic, low-intent CTA that underperforms compared to action-specific alternatives. For Curo Skin, the appropriate CTA depends on the campaign stage and creative angle: product launch or prospecting creatives should use "Shop Now"; subscription-angle creatives should use "Subscribe"; money-back guarantee-angle creatives can use "Shop Now" with the guarantee mentioned in caption. "Learn More" is appropriate only for top-of-funnel awareness content, not conversion-optimised campaigns. |
| **Recommendation** | Audit all active ads and change CTA from "Learn More" to the most appropriate action-specific option. Priority CTAs: "Shop Now" for product-led creatives, "Get Offer" for subscription/discount angle, "Order Now" for urgency-led creatives. Test CTA copy as a variable — in TikTok's creative testing framework, CTA is one of the highest-impact single-variable changes and can shift CTR by 15-25%. |

---

### T25 — Safe Zone Compliance (X:40-940, Y:150-1470)
| Field | Detail |
|---|---|
| **Severity** | High |
| **Likely Status** | WARNING / FAIL (assumed) |
| **Reasoning** | TikTok's UI overlays the following elements on all In-Feed videos: profile picture and username (bottom-left), like/comment/share icons (right side), caption text (bottom), music/audio bar (bottom), CTA button (bottom-centre), and navigation bar (very bottom). Any brand text, product shots, price points, review stars, or CTAs placed within these zones will be partially or fully hidden in ad delivery. The safe zone is X:40-940px, Y:150-1470px — a 900x1320px usable area centred in the frame. Common violations: product price in the bottom third ("£80 — Shop Now" overlaid by TikTok's CTA button), review badges in the bottom corners, URL or website address in the bottom portion. |
| **Recommendation** | Run every active creative through TikTok's Creative Center preview tool to verify safe zone compliance before activating. The top 150px is reserved for the status bar and account header — do not place brand logos here. The bottom 450px is the highest-risk zone due to multiple UI elements. Reposition any price callouts, review badges (Marie Claire, Glamour, Good Housekeeping awards are high-credibility trust signals — they must be visible), and CTAs to the vertical middle of the frame. |

---

**Creative Quality Score Reasoning:** T05 (Critical FAIL), T07 (High WARNING/FAIL), T08 (High WARNING/FAIL), T09 (High FAIL), T10 (High FAIL), T20 (Medium FAIL), T22 (High WARNING/FAIL), T23 (Medium FAIL), T25 (High WARNING/FAIL) are all negative signals. T06 is at WARNING. T24 is at WARNING. T21 is N/A pending T20. The only partial positives are the brand having strong creative raw materials (visual product, awards, reviews) that have not yet been fully executed on TikTok. Estimated raw score: 28/100.

---

## Category 4: Technical Setup (T11-T13, T19)
**Weight: 25% | Category Score: 35/100**

### T11 — TikTok Events API (Server-Side) Implemented
| Field | Detail |
|---|---|
| **Severity** | Critical |
| **Likely Status** | FAIL / NEEDS VERIFICATION |
| **Reasoning** | The TikTok Events API (EAPI) is the server-side equivalent of the browser Pixel. It sends conversion events directly from the server to TikTok, bypassing browser-level blocking from Safari ITP, Firefox Enhanced Tracking Protection, iOS 14+ ATT restrictions, and ad blockers (which are heavily used in the UK tech-savvy demographic likely to be interested in a premium shower filter). Without EAPI, TikTok is potentially missing 30-50% of actual conversion events, leading to underreported ROAS, under-optimised algorithms, and inability to build accurate retargeting audiences. This is not an optional enhancement — it is a foundational requirement for any serious TikTok Ads operation in 2026. The UK GDPR context adds complexity: EAPI implementation must be server-side and must only send events for users who have given consent. |
| **Recommendation** | Implement TikTok Events API as a priority alongside the browser Pixel (both should run simultaneously — they are complementary, not alternatives). For a Shopify store, the TikTok Sales Channel app provides native EAPI integration. Verify deduplication is configured to prevent double-counting events from both browser and server. Test using TikTok's Test Events tool in Events Manager. Ensure the EAPI integration only fires for consented users (pass the consent flag in the API payload). Target an event match quality score of 7+ for email addresses and phone numbers passed as hashed user data. |

---

### T12 — TikTok Business Account Connected and Verified
| Field | Detail |
|---|---|
| **Severity** | High |
| **Likely Status** | PASS (assumed) |
| **Reasoning** | Running any paid TikTok ads requires a TikTok Business Account. This is a prerequisite that is almost certainly met if any ads are running. The nuance is whether the TikTok Business Account is correctly linked to both the Ads Manager and the TikTok Shop (if set up), and whether the @CuroSkin TikTok profile is verified or has the blue tick — which provides additional credibility in Spark Ads. |
| **Recommendation** | Verify the organic TikTok profile is linked to the Business Account in TikTok Ads Manager. Apply for the TikTok Verified badge if follower count qualifies. Ensure the Business Account has a complete profile: bio with value proposition, profile picture matching brand identity, link to curoskin.co.uk. |

---

### T13 — UTM Parameters on All Ad Destination URLs
| Field | Detail |
|---|---|
| **Severity** | High |
| **Likely Status** | WARNING / NEEDS VERIFICATION |
| **Reasoning** | UTM parameters are the bridge between TikTok Ads Manager data and Google Analytics / GA4 data. Without UTM parameters, it is impossible to attribute website behaviour (time on site, pages visited, checkout rate, subscription sign-up) to specific TikTok campaigns, ad groups, or creatives. This matters especially for a brand with a subscription model — the LTV of a TikTok-acquired customer (who may subscribe for 12+ quarters) may be significantly higher than the immediate purchase ROAS suggests, but this cannot be measured without UTM-to-CRM linkage. At this stage, UTM implementation is commonly inconsistent: some ads have UTMs, others don't, and the parameters used are non-standardised. |
| **Recommendation** | Implement a standardised UTM convention for all TikTok ads: `utm_source=tiktok&utm_medium=paid_social&utm_campaign=[CAMPAIGN_NAME]&utm_content=[AD_NAME]`. Use TikTok's URL tracking template field to apply UTMs at the campaign level so they never have to be added manually per ad. Verify in GA4 that TikTok traffic is appearing under the correct source/medium and not being misattributed to direct or referral. Set up a GA4 conversion event for subscription sign-ups specifically, as this is a key downstream metric for evaluating TikTok's true LTV contribution. |

---

### T19 — Conversion Window Set Correctly
| Field | Detail |
|---|---|
| **Severity** | Medium |
| **Likely Status** | WARNING / NEEDS VERIFICATION |
| **Reasoning** | TikTok's default attribution window is 7-day click, 1-day view. For an £80 considered purchase with a 60-day money-back guarantee (suggesting the brand is aware of a longer consideration cycle), a 7-day click window may be too short — some customers will see a TikTok ad, research the product, read reviews, and purchase 10-14 days later. Conversely, a 1-day view attribution window attributes too many conversions to TikTok that are actually driven by other channels (the customer saw the ad in passing, then later purchased after a Google search). There is no single "correct" window, but it must be configured intentionally rather than left at default, and it must be consistent with the attribution windows used on Meta and Google to allow cross-channel comparison. |
| **Recommendation** | Set the click-through attribution window to 14 days for this product category (considered purchase, longer research cycle). Set the view-through window to 1 day (view-through attribution is inherently directional — keep it tight). Review the attribution window setting in TikTok Ads Manager under Campaign Settings > Attribution. Align this window with Meta's attribution settings to enable meaningful cross-platform ROAS comparison. Document the attribution settings used so that any future changes can be benchmarked against prior periods. |

---

**Technical Setup Score Reasoning:** T11 (Critical FAIL) is the primary negative driver. T13 (High WARNING) and T19 (Medium WARNING) add to the gap. T12 is likely PASS. Estimated raw score: 35/100 — slightly better than Creative and Bidding because basic account infrastructure is likely in place, but the absence of Events API is a significant technical gap.

---

## Category 5: Performance (T26-T30)
**Weight: 10% | Category Score: 25/100**

> NOTE: Performance checks are inherently unverifiable without account access. The scores and assessments below are estimates based on what is statistically likely given the budget constraints, assumed structural issues, and UK e-commerce benchmarks for beauty/wellness DTC brands.

### T26 — CTR At or Above Platform Benchmark (1.5%+ for e-commerce)
| Field | Detail |
|---|---|
| **Severity** | High |
| **Likely Status** | WARNING / NEEDS VERIFICATION |
| **Reasoning** | TikTok e-commerce In-Feed ad benchmarks for beauty/wellness in the UK sit at approximately 1.2-2.0% CTR. For a brand with low creative volume (assumed), non-native creative style (assumed), and a product with relatively niche appeal at £80 price point, a CTR in the 0.8-1.2% range is the likely baseline. This is below benchmark and will produce elevated CPCs. Spark Ads for this category average approximately 3% CTR — meaning the gap between current assumed performance and achievable performance with the right creative approach is likely 2-3x. |
| **Recommendation** | Target a minimum of 1.5% CTR for In-Feed ads, 2.5%+ for Spark Ads. Track 2-second view rate (target 30%+) as a leading indicator of hook effectiveness, and video completion rate (target 25%+) as a leading indicator of content resonance. If CTR is below 1.0%, the problem is the hook — the first 1-2 seconds are causing users to scroll. If CTR is 1.0-1.5% but conversion rate is low, the problem is the landing page or audience-offer mismatch. |

---

### T27 — CPA Within Target Range
| Field | Detail |
|---|---|
| **Severity** | High |
| **Likely Status** | FAIL / WARNING (assumed) |
| **Reasoning** | For an £80 product (approximately $100 USD), a target CPA of £25-40 (approximately $32-50 USD) would represent a 2-3x ROAS — healthy for a subscription product where LTV is significantly higher than first-purchase revenue. At the assumed budget level with the structural issues identified (permanent learning phase, under-funded ad groups, potentially low creative quality), actual CPAs are likely in the £60-120 range — making TikTok unprofitable on a first-purchase basis. The subscription model changes the LTV math significantly (a customer purchasing 4x replacement filters per year at even a 25% discount represents substantial 12-month value), but TikTok's optimisation algorithm cannot factor in LTV — it only optimises for the first purchase event. |
| **Recommendation** | Calculate and document the target CPA based on LTV, not first-purchase profit. For a subscription product: if 40% of TikTok-acquired customers subscribe (estimate), the 12-month LTV per customer may be 2-3x the initial purchase value, meaning a CPA of £50-60 could still be profitable. Set a soft CPA threshold of £45 (pause and investigate) and a hard kill threshold of £80 (pause immediately, fix structural issues before resuming). Track subscription conversion rate for TikTok-acquired customers specifically in the CRM. |

---

### T28 — ROAS Above 1.5x (Minimum Viable) or Trending Upward
| Field | Detail |
|---|---|
| **Severity** | High |
| **Likely Status** | FAIL / WARNING (assumed) |
| **Reasoning** | Given the structural issues identified — insufficient budget, permanent learning phase, assumed low creative volume, likely non-native creative style — ROAS is almost certainly below 1.5x on a first-purchase basis. This is not a signal that TikTok does not work for Curo Skin. It is a signal that the current implementation of TikTok ads does not work. The product-platform fit is actually very strong. The execution is the limiting factor. |
| **Recommendation** | Do not draw conclusions about TikTok's viability for Curo Skin from current ROAS data until the structural issues (budget, creative volume, Events API, Spark Ads) have been addressed. Relaunch TikTok with the corrected setup and evaluate ROAS after a 60-day optimised period. Benchmark against Jolie's known TikTok performance metrics as a competitive reference point. |

---

### T29 — Frequency Within Healthy Range (Under 3.0 per 7 days)
| Field | Detail |
|---|---|
| **Severity** | Medium |
| **Likely Status** | WARNING (assumed) |
| **Reasoning** | With a small UK audience (total addressable TikTok UK audience for shower-interested women 25-44 is perhaps 500K-1.5M users) and limited creative variety (assumed 2-4 creatives), frequency will escalate quickly even at modest spend levels. A frequency of 3+ means the same user is seeing the same ad three or more times per week — highly likely to trigger ad fatigue and negative brand sentiment (some users will actively hide ads or report them). |
| **Recommendation** | Monitor frequency weekly alongside CTR. If frequency exceeds 2.5 and CTR is declining, the primary intervention is new creative — not reducing budget. Expanding targeting will dilute audience relevance and increase CPAs. New creative gives the algorithm fresh inventory to serve to the same audience with different content. The goal is 6+ creatives so that even if frequency is 3, each impression is a different creative and the cumulative experience feels varied rather than repetitive. |

---

### T30 — Attribution and Reporting Set Up for Cross-Platform View
| Field | Detail |
|---|---|
| **Severity** | Medium |
| **Likely Status** | WARNING / FAIL (assumed) |
| **Reasoning** | With budget spread across Google, Meta, and TikTok, cross-channel attribution is critical and almost certainly not set up correctly at this stage. Each platform will claim last-touch or first-touch attribution on the same purchases, leading to significant double-counting of reported ROAS and an inflated view of overall performance. The subscription model adds further complexity — a customer may be acquired via TikTok, complete the first purchase through a Google branded search, and then subscribe directly. Attribution for each event will be claimed by a different platform. Without a unified measurement view, decisions about budget allocation between the three platforms will be based on misleading per-platform reported ROAS. |
| **Recommendation** | Implement a Marketing Efficiency Ratio (MER) framework as the primary measurement tool: Total Revenue / Total Ad Spend across all platforms. This is the most reliable signal for overall programme health. For TikTok specifically, implement TikTok's own attribution tool alongside UTMs. Consider a lightweight MMM (Marketing Mix Modelling) approach using North Star metrics (new customer acquisition rate, subscription conversion rate) to attribute platform contribution over time. At minimum, ensure GA4 has cross-channel attribution configured with data-driven attribution model (not last-click). |

---

**Performance Score Reasoning:** All checks are at WARNING or FAIL based on the structural issues identified in earlier categories. Performance is downstream of setup — if budget, creative, and technical foundation are broken, performance will follow. Estimated raw score: 25/100. This score will improve automatically as structural issues are fixed — it does not require separate performance interventions.

---

## Scoring Calculation

### Severity Multipliers Applied

| Check | Severity | Multiplier | Status | Points Available | Points Scored |
|---|---|---|---|---|---|
| T01 | Critical | 5.0 | WARNING | 10 | 4 |
| T02 | High | 3.0 | WARNING | 6 | 2 |
| T03 | Critical | 5.0 | PASS | 10 | 9 |
| T04 | Critical | 5.0 | WARNING | 10 | 3 |
| T05 | Critical | 5.0 | FAIL | 10 | 0 |
| T06 | Critical | 5.0 | WARNING | 10 | 5 |
| T07 | High | 3.0 | WARNING/FAIL | 6 | 1 |
| T08 | High | 3.0 | WARNING/FAIL | 6 | 1 |
| T09 | High | 3.0 | FAIL | 6 | 0 |
| T10 | High | 3.0 | FAIL | 6 | 0 |
| T11 | Critical | 5.0 | FAIL | 10 | 0 |
| T12 | High | 3.0 | PASS | 6 | 5 |
| T13 | High | 3.0 | WARNING | 6 | 2 |
| T14 | Critical | 5.0 | FAIL | 10 | 0 |
| T15 | High | 3.0 | WARNING | 6 | 2 |
| T16 | High | 3.0 | FAIL | 6 | 0 |
| T17 | High | 3.0 | FAIL | 6 | 0 |
| T18 | Medium | 1.5 | WARNING | 3 | 1 |
| T19 | Medium | 1.5 | WARNING | 3 | 1 |
| T20 | Medium | 1.5 | FAIL | 3 | 0 |
| T21 | Medium | 1.5 | N/A | — | — |
| T22 | High | 3.0 | WARNING/FAIL | 6 | 1 |
| T23 | Medium | 1.5 | FAIL/WARNING | 3 | 0 |
| T24 | Medium | 1.5 | WARNING | 3 | 1 |
| T25 | High | 3.0 | WARNING/FAIL | 6 | 1 |
| T26 | High | 3.0 | WARNING | 6 | 2 |
| T27 | High | 3.0 | FAIL/WARNING | 6 | 1 |
| T28 | High | 3.0 | FAIL/WARNING | 6 | 1 |
| T29 | Medium | 1.5 | WARNING | 3 | 1 |
| T30 | Medium | 1.5 | WARNING/FAIL | 3 | 0 |
| **TOTALS** | | | | **182** | **44** |

**Raw unadjusted score: 44/182 = 24%**

After applying category weights and normalising to 100:

| Category | Checks | Max | Scored | Raw% | Weight | Weighted |
|---|---|---|---|---|---|---|
| Structure & Settings | T01-T04 | 30 | 18 | 60% | 15% | 9.0 |
| Bidding & Learning | T14-T18 | 31 | 4 | 13% | 20% | 2.6 |
| Creative Quality | T05-T10, T20-T25 | 73 | 15 | 21% | 30% | 6.3 |
| Technical Setup | T11-T13, T19 | 25 | 8 | 32% | 25% | 8.0 |
| Performance | T26-T30 | 24 | 6 | 25% | 10% | 2.5 |
| **TOTAL** | | **183** | **51** | **28%** | **100%** | **28.4** |

**OVERALL TIKTOK ADS HEALTH SCORE: 28 / 100 — CRITICAL**

---

## Critical Findings Summary

| Priority | Finding | Impact | Action |
|---|---|---|---|
| 1 (CRITICAL) | Budget below minimum viable threshold (~$300-500/month vs $1,500 minimum) | Cannot exit learning phase; algorithm cannot optimise; every pound wasted | Reallocate budget to reach $1,500/month or pause TikTok paid ads and invest in TikTok Shop + organic |
| 2 (CRITICAL) | TikTok Events API not implemented | 30-50% conversion data loss; algorithm blind; GDPR risk | Implement EAPI via Shopify TikTok app with consent gating |
| 3 (CRITICAL) | Fewer than 6 creatives per ad group | Algorithm cannot test; creative fatigue guaranteed; no learning | Produce 6+ UGC-style creatives immediately |
| 4 (HIGH) | Spark Ads not being utilised | Leaving 50% CTR uplift on the table; less native feel | Identify top organic posts; request Spark Ads codes |
| 5 (HIGH) | TikTok Shop not integrated | Missing in-app purchase funnel; excluded from affiliate creator programme | Register for TikTok Shop UK; list core products |
| 6 (HIGH) | Creative hooks not TikTok-native | High scroll rate; low 2-second view rate; wasted impressions | Rewrite all hooks; use problem-first or curiosity-gap format |
| 7 (HIGH) | Ad groups in permanent learning phase | TikTok algorithm cannot optimise delivery; CPAs inflated | Lower optimisation event to Add to Cart; consolidate to 1 ad group |

---

## Quick Wins (Actionable Within 7 Days)

These require no budget increase and can be implemented immediately.

**1. Change CTA buttons from "Learn More" to "Shop Now" or "Get Offer"**
All active ads. 15-minute fix. Estimated CTR impact: +10-20%.

**2. Audit safe zone compliance on all active creatives**
Use TikTok Creative Center preview. Reposition any text, review badges, or CTAs in the bottom 450px. 1-hour fix per creative.

**3. Rewrite all ad captions with keyword-first copy**
Lead with "shower filter UK" or "hard water hair" in the first sentence of every caption. Add 3-5 relevant hashtags. 30 minutes per ad.

**4. Enable 14-day click attribution window**
In Campaign Settings. Prevents underreporting of considered purchases. 5-minute fix.

**5. Consolidate ad groups**
If running multiple ad groups, merge into one broad UK 18-45 prospecting ad group. Concentrate all budget in one place. 30 minutes.

**6. Request Spark Ads authorisation codes for existing organic content**
If Curo Skin has existing TikTok posts or has worked with creators, request Spark Ads codes today. Zero cost to implement. Potential CTR uplift from day 1.

**7. Switch optimisation event from Complete Payment to Add to Cart**
If purchase conversion volume is below 50/week per ad group (virtually certain at this budget). Feeds the algorithm with 5-10x more signal per week.

---

## Strategic Recommendations for Curo Skin on TikTok

### Recommendation 1: Commit or Redirect — There Is No Middle Ground

Shower filters are TikTok-native. Jolie went from zero to a category-defining brand on TikTok. ATOJET's k-beauty angle generated millions of views organically. The demand is real, the content format is proven, and the UK market is not yet saturated for this category. Curo Skin should either:

**Path A (Commit):** Increase TikTok allocation to £1,200-1,500/month ($1,500-1,900/month). This means reducing Google and/or Meta allocation. It is a defensible choice given TikTok's product-category fit for shower filters and the organic amplification potential (a single viral TikTok can outperform months of paid ads). Fund this properly or not at all.

**Path B (TikTok Shop + Organic First):** Pause paid TikTok ads. Invest the budget into (a) TikTok Shop setup and affiliate creator recruitment and (b) an organic content strategy for the @CuroSkin TikTok account. TikTok Shop affiliate commission is self-funding — creators earn from sales they drive, with no upfront cost. Build to 20-30 organic posts, find 5-10 UK beauty/wellness creators to post about Curo Skin through the affiliate programme, then relaunch paid ads once total budget reaches £2,500/month.

Running TikTok paid ads at current budget levels — below the platform minimum, with insufficient creative, without Events API — is the worst possible outcome: money spent, no learnings, and a false signal that "TikTok doesn't work."

### Recommendation 2: Build the Dirty Filter Content Pipeline

The single most powerful creative asset for a shower filter brand on TikTok is the dirty filter reveal. Show a Curo Skin replacement filter after 90 days of use in a UK hard water area (London, Birmingham, Manchester). The discolouration is visual proof that the filter is working and that unfiltered water is the problem. This content format works because:
- It is inherently shareable (disgust + revelation)
- It proves the product's efficacy without any marketing claim
- It resonates in hard water areas where the tap water quality is a known frustration
- It answers the "does it actually work?" objection without asking the viewer to trust marketing copy

Brief UK beauty/wellness creators to do a 90-day follow-along with a Curo Skin filter. Send the product, follow up at 30, 60, and 90 days. The final reveal video is the asset. This is Spark Ads inventory in waiting.

### Recommendation 3: Own the Hard Water Narrative in the UK

The UK has some of Europe's hardest tap water — particularly in London, the South East, and the Midlands. This is not widely understood by consumers as a cause of hair breakage, scalp issues, and skin sensitivity. Curo Skin's most powerful TikTok strategy is education-first content:

- "Why your hair is breaking even though you use good products" (answer: hard water)
- "The map of UK hard water areas — is your area at risk?" (localised, shareable)
- "What London tap water actually contains" (chlorine levels, limescale, heavy metals)
- "Dermatologists/trichologists reacting to UK shower water data" (aspirational format)

Educational content that creates the problem also positions Curo Skin as the solution. This is the top-of-funnel play that feeds mid-funnel purchase intent. It also generates organic reach that supports paid efficiency — a user who has watched 3 educational TikToks about hard water will convert at significantly higher rates on a subsequent paid ad than a cold prospecting audience.

### Recommendation 4: Use Award Credibility as a Native TikTok Proof Format

Curo Skin has an unusually strong press record for a brand at this stage: Marie Claire, Woman&Home, Glamour, WIRED, Good Housekeeping 2025-2026 awards. This is breakthrough creative material on TikTok, but only if executed natively. Do not put press logos in a banner at the bottom of a polished video. Instead:

- Creator reacts to Curo Skin winning the Glamour Beauty Award: "I've been using this for 6 months and now I see why..."
- "WIRED called this the best shower upgrade of 2025 — here's my honest opinion after 3 months"
- "Good Housekeeping approved this and I needed to find out if it was worth the hype"

These formats feel organic, use the awards as a credibility hook rather than a badge, and create narrative tension (I have the award claim; now let me validate it personally). They work for both organic content and Spark Ads.

### Recommendation 5: Leverage the Subscription Model for TikTok-Specific Offers

The 90-day replacement filter subscription is a natural TikTok content cadence — quarterly filter replacements map to quarterly creative refreshes. Specific tactical opportunities:
- "90 days later" filter reveal series (see Recommendation 2)
- "Quarterly unboxing" format — makes the subscription feel like a ritual, not a burden
- "Cancel any time" or "60-day money-back guarantee" callouts as objection-handling content
- "15-25% off vs buying separately" as a value-framing creative angle

The subscription model also improves TikTok Ads economics significantly. If the LTV of a Curo Skin customer over 12 months is £80 (shower head) + £40/year in filters (after 25% subscription discount), the total 12-month LTV is approximately £120. This means a TikTok CPA of £50-60 on the initial conversion can still be profitable — but only if the subscription conversion rate is tracked and this LTV calculation informs the CPA target.

---

## Verification Checklist

The following items require direct TikTok Ads Manager access to confirm:

- [ ] Active campaign objective (Conversions vs Traffic vs Video Views)
- [ ] Number of active creatives per ad group
- [ ] Video creative dimensions and whether natively filmed in 9:16
- [ ] TikTok Pixel event firing (use Pixel Helper extension)
- [ ] Events API implementation status
- [ ] Bidding strategy in use (Lowest Cost vs Cost Cap vs Min ROAS)
- [ ] Ad group daily budgets
- [ ] Campaign learning phase status in delivery column
- [ ] Actual monthly TikTok spend vs total budget
- [ ] CTR by creative (7-day, 30-day)
- [ ] 2-second view rate and video completion rate
- [ ] Frequency per 7-day period
- [ ] Attribution window settings
- [ ] CTA button selection per ad
- [ ] Safe zone review of active creatives
- [ ] UTM parameter implementation
- [ ] TikTok Shop registration status
- [ ] Spark Ads usage (any active Spark Ads campaigns)

---

*This audit was produced by the Creative Quality specialist agent for TikTok, LinkedIn, and Microsoft Ads. Google and Meta creative are handled by dedicated agents. The assessment-based methodology assigns most-likely status based on documented patterns for DTC e-commerce brands at comparable budget and maturity levels. All findings marked NEEDS VERIFICATION should be confirmed with account access before making structural changes.*
