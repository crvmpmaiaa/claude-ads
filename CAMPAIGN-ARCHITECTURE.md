# Campaign Architecture: Climbing/Bouldering E-commerce

## Naming Convention

```
[Platform]_[Objective]_[Audience]_[Geo]_[Date]
```

**Examples:**
- `META_CONV_Prospecting-Climbing_US_2026Q1`
- `META_CONV_ASC-AllProducts_US_2026Q1`
- `META_CONV_Retargeting-WebVisitors_US_2026Q1`
- `TIKTOK_CONV_Spark-ClimbingUGC_US_2026Q2` (when ready)

---

## Phase 1: Meta Ads Architecture ($1,000/month)

### Account Structure

```
Meta Ads Account
│
├── Campaign 1: Advantage+ Shopping Campaign (ASC)
│   ├── Budget: $700/mo ($23/day)
│   ├── Objective: Sales
│   ├── Bidding: Lowest Cost (no cap)
│   ├── Optimization: Purchase
│   ├── Audience: Broad (let ASC optimize)
│   ├── Existing Customer Cap: 20% max
│   └── Creatives (4-6 minimum):
│       ├── UGC video: Climber chalking up + using product
│       ├── Lifestyle image: Product at the crag/gym
│       ├── Carousel: Product collection (chalk + brush + bag)
│       ├── Before/after: Dirty vs clean holds
│       ├── Product demo: Chalk application close-up
│       └── Social proof: Review overlay on lifestyle image
│
├── Campaign 2: Prospecting — Interest Targeting
│   ├── Budget: $200/mo ($7/day)
│   ├── Objective: Sales
│   ├── Bidding: Lowest Cost
│   ├── Optimization: Purchase (switch to AddToCart if <10 purchases/week)
│   │
│   └── Ad Set 1: Climbing & Bouldering Stack
│       ├── Interests: Rock climbing + Bouldering + Indoor climbing
│       ├── AND/OR: La Sportiva, Black Diamond, Petzl, Metolius
│       ├── Age: 18-45
│       ├── Gender: All
│       ├── Geo: United States
│       ├── Placements: Advantage+ (automatic)
│       ├── Exclusions: Past purchasers (180 days)
│       └── Creatives: Top 3 from ASC testing
│
└── Campaign 3: Testing Budget
    ├── Budget: $100/mo ($3.30/day)
    ├── Purpose: Test new creatives, angles, audiences
    ├── Rotate winners into Campaign 1 & 2
    └── Kill losers after $20-30 spend with no signal
```

### Campaign Decision Logic

```
IF ASC gets 50+ conversions/week:
  → Scale ASC budget by 20%, reduce Prospecting to testing role

IF ASC is "Learning Limited":
  → Add more creatives (target 10+)
  → Check if Purchase volume too low → switch to AddToCart optimization
  → Ensure existing customer cap isn't too restrictive

IF Prospecting outperforms ASC:
  → Shift budget toward Prospecting
  → Test new interest stacks in Testing campaign

IF both campaigns unprofitable after 30 days:
  → Audit: creative quality, landing page, product-market fit
  → Test different product focus (best-sellers only)
  → Consider AddToCart optimization + email nurture for purchase
```

---

## Phase 2: Add TikTok (When Budget Reaches $1,500+/month)

### Account Structure

```
TikTok Ads Account
│
├── Campaign 1: Spark Ads — Creator/UGC Content
│   ├── Budget: $300/mo ($10/day)
│   ├── Objective: Website Conversions
│   ├── Bidding: Lowest Cost
│   ├── Optimization: Complete Payment (or AddToCart)
│   │
│   └── Ad Group 1: Climbing Community
│       ├── Targeting: Climbing, Bouldering, Outdoor Sports interests
│       ├── Age: 18-45
│       ├── Placements: TikTok only
│       └── Creatives (Spark Ads — boost organic posts):
│           ├── Gym session featuring your chalk/brush
│           ├── "What's in my climbing bag" format
│           ├── Product review / first impression
│           └── Send problem + chalk application
│
└── Campaign 2: Smart+ (when available & budget allows)
    ├── Budget: $200/mo
    ├── Let TikTok AI optimize across audiences
    └── Upload 6+ creatives per asset group
```

### TikTok Creative Rules

```
MUST:
  → Vertical 9:16 (1080×1920)
  → Hook in first 1-3 seconds
  → Native TikTok feel (NOT polished ads)
  → All key content within safe zone (900×1320px center)
  → Audio on (music or voiceover)
  → Captions/text overlay

MUST NOT:
  → Repurpose horizontal Meta ads
  → Use stock footage
  → Corporate tone
  → Text/logos in bottom 450px (UI overlay zone)
```

---

## Phase 3: Add Google (When Budget Reaches $3,000+/month)

### Account Structure (Future)

```
Google Ads Account
│
├── Brand Search Campaign
│   ├── Budget: $100/mo
│   ├── Bidding: Target Impression Share (95%+)
│   ├── Keywords: [your brand name], [brand] chalk, etc.
│   └── Purpose: Protect brand terms from competitors
│
├── Performance Max — Core Products
│   ├── Budget: $600/mo
│   ├── Bidding: Maximize Conversion Value
│   │
│   ├── Asset Group: Best Sellers
│   │   ├── Products: Top 5-10 by revenue
│   │   ├── Images: 20 (lifestyle + white background)
│   │   ├── Videos: 5 (product demos)
│   │   └── Headlines/descriptions: full set
│   │
│   └── Asset Group: Chalk & Consumables
│       ├── Products: All chalk variants
│       └── Angle: Repeat purchase, bulk savings
│
└── Standard Shopping (optional)
    ├── Budget: $300/mo
    ├── For price-sensitive categories
    └── More manual control than PMax
```

### Product Feed Requirements (Pre-requisite for Google)

```
BEFORE launching Google Shopping:
  ✓ Google Merchant Center account
  ✓ Product feed with optimized titles:
    [Brand] + [Product] + [Key Attribute] + [Size/Color]
    Example: "YourBrand Climbing Chalk Ball 2oz — Fine Grain"
  ✓ High-quality images (white background + lifestyle)
  ✓ Accurate pricing and inventory
  ✓ Custom labels: best-sellers, margin tiers, seasonal
```

---

## Ad Set / Ad Group Budget Rules

| Rule | Threshold | Action |
|------|-----------|--------|
| **Minimum daily budget** | ≥5x target CPA | Ensures learning phase data |
| **Learning phase** (Meta) | 50 conv/week per ad set | Consolidate if not hitting |
| **Learning phase** (TikTok) | 50 conv/7 days | Broader targeting or higher-funnel event |
| **Scale up** | CPA < target by 10%+ for 7 days | Increase budget by 20% max |
| **Kill** | 3x target CPA spent, 0 conversions | Pause immediately |
| **Creative kill** | $20-30 spend, 0 purchases | Replace creative |
| **Frequency cap** (Meta prospecting) | >3.0 (7-day) | Refresh creative or expand audience |
| **Frequency cap** (Meta retargeting) | >8.0 (7-day) | Reduce budget or expand window |
| **Frequency cap** (TikTok) | >3.0 | Replace creative assets |

---

## Audience Architecture

### Meta Audiences

| Audience | Type | Size Target | Use |
|----------|------|-------------|-----|
| Climbing Interest Stack | Saved | 500K-2M | Prospecting |
| Website Visitors (7d) | Custom | Build over time | Retargeting (when volume allows) |
| Website Visitors (30d) | Custom | Build over time | Retargeting |
| Add to Cart (14d) | Custom | Build over time | Cart abandonment |
| Past Purchasers (180d) | Custom | Build over time | Exclusion + cross-sell |
| Purchaser Lookalike 1% | Lookalike | ~2M | Prospecting (need 100+ source) |
| Video Viewers 75% (30d) | Custom | Build over time | Warm retargeting |

### Audience Build Priority

```
Week 1-4:   Install Pixel + CAPI → Build visitor/event audiences passively
Month 2:    If 50+ AddToCarts → Create ATC custom audience for retargeting
Month 3:    If 100+ Purchases → Create Purchaser Lookalike 1%
Month 4+:   Layer Lookalikes into Prospecting or let ASC handle
```

### Exclusion Strategy

```
ALL Prospecting campaigns:
  → Exclude: Past Purchasers (180d)
  → Exclude: Current email subscribers (sync from ESP)

ASC (Advantage+ Shopping):
  → Set existing customer cap: 20%
  → This limits retargeting spend within ASC

Retargeting (when launched):
  → Exclude: Purchasers (30d) — don't retarget recent buyers
  → Show: Cross-sell/upsell to purchasers (60-180d)
```
