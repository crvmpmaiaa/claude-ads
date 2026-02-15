# Curo Skin — Quick Wins

**Brand:** Curo Skin (curoskin.co.uk)
**Audit Date:** February 2026
**Criteria:** Severity = Critical or High AND fix time < 15 minutes
**Sorted by:** (Severity multiplier x Estimated impact) DESC

---

## Quick Wins Summary

| # | Action | Platform | Severity | Time | Impact |
|---|--------|----------|----------|------|--------|
| 1 | Consolidate to 2 platforms (pause Google) | All | Critical | 10 min | Eliminates budget dilution across all platforms |
| 2 | Enable/verify Meta CAPI via Shopify | Meta | Critical | 15 min | Recovers 30-40% lost conversion data |
| 3 | Verify Consent Mode v2 is active | Google/All | Critical | 5 min | Prevents 90-95% metric drops in UK |
| 4 | Verify domain in Meta Business Manager | Meta | High | 5 min | Enables Aggregated Event Measurement |
| 5 | Set Meta attribution to 7-day click / 1-day view | Meta | High | 2 min | Proper measurement window for e-commerce |
| 6 | Enable TikTok Search Ads Toggle | TikTok | High | 2 min | Captures "shower filter" search traffic on TikTok |
| 7 | Add UTM parameters to all Meta ad URLs | Meta | Medium | 5 min | Enables GA4 cross-channel attribution |
| 8 | Exclude purchasers from Meta prospecting | Meta | High | 10 min | Stops wasting budget retargeting existing customers |
| 9 | Select proper CTA on TikTok ads ("Shop Now") | TikTok | Medium | 2 min | Better conversion signal vs default CTA |

**Total estimated time: ~56 minutes for all 9 quick wins**

---

## Detailed Instructions

### 1. Consolidate to 2 Platforms (Pause Google Ads)

**Time:** 10 minutes
**Severity:** Critical
**Impact:** Eliminates the #1 audit finding — budget dilution

**Steps:**
1. Log into Google Ads at ads.google.com
2. Go to Campaigns → Select all active campaigns
3. Click "Pause" on each campaign
4. Note current spend allocation for records
5. Redistribute budget: add ~$200-400 to Meta, ~$200-400 to TikTok

**Why this matters:** $600/month on Google cannot generate the 15+ monthly conversions Smart Bidding needs. Every dollar on Google right now is essentially wasted learning-phase spend. Meta and TikTok will perform better with the consolidated budget.

**Revisit when:** Total budget reaches $3,000+/month

---

### 2. Enable/Verify Meta CAPI via Shopify

**Time:** 15 minutes
**Severity:** Critical
**Impact:** Recovers 30-40% of lost conversion data; 15-20% performance improvement

**Steps:**
1. Shopify Admin → Settings → Customer events (or Apps → Facebook & Instagram)
2. Ensure "Maximum" data sharing level is selected
3. Go to Meta Events Manager → Data Sources → Select your Pixel
4. Click "Overview" → Check that server events appear alongside browser events
5. Check "Diagnostics" tab for any active issues
6. Check Event Match Quality: Navigate to each event → EMQ score should be ≥8.0
7. If EMQ < 8.0, ensure you're passing: email, phone, fbp, fbc, external_id

**Verification:**
- Events Manager → Overview → You should see both "Browser" and "Server" columns
- Deduplication rate should be ≥90%
- If "Server" column is empty, CAPI is not active

---

### 3. Verify Consent Mode v2 Is Active

**Time:** 5 minutes
**Severity:** Critical
**Impact:** Without it, 90-95% metric drops in UK/EU

**Steps:**
1. Open curoskin.co.uk in Chrome Incognito
2. Before accepting cookies, open Developer Tools → Console
3. Type: `dataLayer.push({event:'consent_check'})` and check consent state
4. Or: Check GTM → Tags → Consent Overview → Verify tags respect consent
5. Verify the cookie banner appears and functions correctly (opt-in model for UK)

**What to look for:**
- Cookie consent banner loads before any tracking tags
- Google tags show consent status: `ad_storage`, `ad_user_data`, `analytics_storage`
- After user accepts, tags begin firing
- If no consent banner exists: **this is a Critical fail** — implement immediately

---

### 4. Verify Domain in Meta Business Manager

**Time:** 5 minutes
**Severity:** High
**Impact:** Enables Aggregated Event Measurement (AEM) for iOS attribution

**Steps:**
1. Go to Meta Business Manager → Business Settings
2. Click "Brand Safety" → "Domains"
3. If curoskin.co.uk is not listed, click "Add" and enter the domain
4. Follow DNS or meta-tag verification method
5. Once verified, go to Events Manager → Configure Web Events → Prioritize top 8 events

**Priority order for events:**
1. Purchase
2. InitiateCheckout
3. AddToCart
4. Subscribe (for filter subscription)
5. ViewContent
6. AddPaymentInfo
7. Lead (email capture)
8. Search

---

### 5. Set Meta Attribution to 7-Day Click / 1-Day View

**Time:** 2 minutes
**Severity:** High
**Impact:** Proper measurement window for e-commerce conversions

**Steps:**
1. Meta Ads Manager → Select each active ad set
2. Click "Edit"
3. Scroll to "Attribution Setting" (in the ad set settings)
4. Select "7-day click, 1-day view"
5. Save

**Note:** If currently set to "1-day click" only, you're missing conversions that happen 2-7 days after clicking. Most e-commerce purchases (especially £80 shower filters) involve consideration time.

---

### 6. Enable TikTok Search Ads Toggle

**Time:** 2 minutes
**Severity:** High
**Impact:** Captures users actively searching "shower filter" on TikTok

**Steps:**
1. TikTok Ads Manager → Campaigns → Select each campaign
2. Click "Edit"
3. Look for "Search Ads Toggle" setting
4. Toggle to ON
5. Save

**Why:** "Shower filter" is a heavily searched term on TikTok. Search Ads appear when users search — this is high-intent traffic at no additional cost.

---

### 7. Add UTM Parameters to All Meta Ad URLs

**Time:** 5 minutes
**Severity:** Medium
**Impact:** Enables GA4 cross-channel attribution; stops Meta from being "dark traffic"

**Steps:**
1. Meta Ads Manager → Campaign level → Edit
2. Go to "Tracking" section
3. Add URL Parameters:
```
utm_source=facebook&utm_medium=paid&utm_campaign={{campaign.name}}&utm_content={{ad.name}}&utm_term={{adset.name}}
```
4. Apply to all active campaigns
5. Repeat for any TikTok campaigns:
```
utm_source=tiktok&utm_medium=paid&utm_campaign=__CAMPAIGN_NAME__&utm_content=__AID_NAME__
```

---

### 8. Exclude Purchasers from Meta Prospecting

**Time:** 10 minutes
**Severity:** High
**Impact:** Stops paying to show ads to people who already bought

**Steps:**
1. Meta Ads Manager → Audiences → Create Custom Audience
2. Select "Website" → Event: "Purchase" → Last 180 days
3. Name it: "Purchasers - 180d"
4. Save
5. Go to each prospecting ad set → Edit → Exclusions → Add "Purchasers - 180d"
6. If running ASC: Set Existing Customer Cap to 20% in campaign settings

**Also create (while you're there):**
- "Website Visitors - 30d" (for future retargeting)
- "Add to Cart - 14d" (for cart abandonment retargeting later)

---

### 9. Select Proper CTA on TikTok Ads

**Time:** 2 minutes
**Severity:** Medium
**Impact:** Proper CTA improves click-through; default CTA is generic

**Steps:**
1. TikTok Ads Manager → Select each active ad
2. Click "Edit"
3. Change CTA button from default to "Shop Now" (for direct product sales)
4. Or use "Learn More" for awareness/educational content
5. Save

---

## Post-Quick-Wins Checklist

After completing all 9 quick wins, verify:

- [ ] Google Ads campaigns are paused
- [ ] Meta budget increased to $1,000-1,200/month
- [ ] TikTok budget increased to $800-1,000/month
- [ ] CAPI showing server events in Meta Events Manager
- [ ] EMQ score ≥8.0 for Purchase event
- [ ] Consent Mode v2 confirmed active
- [ ] Domain verified in Business Manager
- [ ] Attribution set to 7-day click / 1-day view
- [ ] Search Ads Toggle ON in TikTok
- [ ] UTM parameters on all ad URLs
- [ ] Purchaser exclusion active on prospecting
- [ ] CTA buttons customized on TikTok

**Expected score improvement:** These quick wins alone should move the aggregate score from 52/100 (Grade D) to approximately 65-70/100 (Grade C), primarily through fixing budget allocation and tracking infrastructure.

---

## Next Steps After Quick Wins

Once quick wins are complete, move to the full Action Plan:
1. Rebuild Meta account structure (ASC + Testing campaigns)
2. Build creative pipeline (6+ assets including UGC, demos, award badges)
3. Set up TikTok Shop (>10% CVR opportunity)
4. Implement post-purchase survey for attribution validation
5. Set up email/SMS retention flows for subscription model
