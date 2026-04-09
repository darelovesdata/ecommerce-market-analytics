# Analytics Insights and Discovery Framework

## Key Performance Indicator Architecture

### Tier 1: Executive Health Metrics

These four metrics answer the fundamental business question: "Are we on track?"

**Revenue Performance;**

- Metric: Total Revenue vs Weekly Target
- Calculation: Sum of completed orders across all channels
- Why it matters: Direct visibility into business performance
- Benchmark: Tracks weekly and YTD performance against forecasted targets

**Conversion Rate (CR):**

- Metric: Sessions converting to completed purchase
- Calculation: (Completed Purchases / Total Sessions) x 100
- Why it matters: Indicates website effectiveness independent of traffic volume
- Typical range: 1-4% for e-commerce (varies by vertical)

**Average Order Value (AOV);**

- Metric: Mean transaction value across all orders
- Calculation: Total Revenue / Total Orders
- Why it matters: Key multiplier in revenue equation
- Strategic insight: Often easier to increase than conversion rate

**Blended Return on Ad Spend (ROAS):**

- Metric: Revenue attributed to paid advertising / Ad spend
- Calculation: Sum of Google Ads revenue + Meta revenue / Total spend
- Why it matters: Indicates efficiency of paid marketing investment
- Target benchmark: Minimum 3:1 ROAS for profitability

### Tier 2: Acquisition Channel Metrics

These metrics segment performance by marketing source, answering: "Where do profitable customers come from?"

**Traffic by Channel:**

- Organic Search: 35-45% typical (free traffic, typically high-quality)
- Paid Social: 15-25% typical (Meta, TikTok, Snap)
- Paid Search: 10-20% typical (Google Ads, Bing)
- Email: 5-15% typical (highest ROI channel typically)
- Direct: 5-10% typical (brand searches, bookmarks)
- Social Organic: 5-15% typical (influencer-driven)

**Customer Acquisition Cost (CAC):**

- Calculation: Total marketing spend / New customers acquired
- By channel: Spend by channel / New customers from channel
- Comparison: Email typically 10-30 per customer; Paid social 50-150 per customer
- Profitability check: CAC must be lower than customer lifetime value

**New vs Returning User Ratio:**

- New users: First-time site visitors
- Returning users: Previous visitors making repeat purchase
- Target: 60-70% new, 30-40% returning (varies by strategy)
- Strategic insight: Increasing repeat rate is 5-7x cheaper than acquisition

### Tier 3: Product and Merchandising Metrics

These metrics identify revenue drivers and underperformers, answering: "Which products should we optimize and why?"

**Revenue by Product Category:**

- Rank: Top performers vs bottom performers
- Margin analysis: Category profitability (including C.O.G.S)
- Trend: Week-over-week and month-over-month performance
- Alert: Categories with declining revenue (2+ weeks down indicating trend)

**Product Unit Economics:**

- Units sold by product
- Average price per unit
- Margin per unit
- Inventory turnover rate

**Checkout Abandonment Rate by Device:**

- Desktop abandonment: Typical 20-30%
- Mobile abandonment: Typical 40-50% (indicates UX friction)
- Root causes: Form complexity, payment options, shipping costs
- Benchmarking: Mobile abandonment 2-3x higher than desktop indicates design issue

**Hero/Banner Creative Performance:**

- Click-through rate on homepage creative
- Scroll depth by creative type
- Conversion rate by above-the-fold experience
- Seasonal performance variations

### Tier 4: Retention and Lifetime Value Metrics

These metrics focus on building recurring revenue, answering: "How do we maximize customer lifetime value?"

**Repeat Purchase Rate by Cohort:**

- 30-day repeat rate: Percentage making purchase within 30 days
- 60-day repeat rate: Percentage making purchase within 60 days
- 90-day repeat rate: Percentage making purchase within 90 days
- Benchmark: Strong cohort retention starts at 15-25% for 30-day repeat

**Customer Lifetime Value (CLV):**

- Calculation: (Average order value x Purchase frequency x Customer lifespan)
- Example: $75 AOV x 3 purchases/year x 4 years = $900 CLV
- Strategic: Compare CLV to CAC (target 3:1 minimum ratio)
- Margin on CLV: Should account for cost of goods and fulfillment

**Email-Attributed Revenue:**

- Percentage of total revenue attributed to email touchpoints
- Open rates: Typical 15-25% (strong performers 25-35%)
- Click rates: Typical 2-5% (strong performers 5-8%)
- Unsubscribe rate: Typical 0.1-0.3% (above 0.5% indicates list quality issue)

**Churn Rate by Cohort:**

- Definition: Customers not making repeat purchase within expected window
- Calculation: (Customers lost in period / Customers at start of period) x 100
- By cohort: Track customers acquired in same month
- Inverse indicator: 1 - Churn rate = Retention rate

## Data Quality Standards

### Accuracy Checkpoints

1. **Revenue reconciliation**: Dashboard revenue matches Shopify backend within 2%
2. **Attribution consistency**: GA4 transactions match Shopify revenue within 500 USD daily variance
3. **Channel tracking**: All traffic sources properly tagged with UTM parameters
4. **Conversion lag**: Account for 1-2 day Google Analytics processing delay

### Data Update Frequency

- Real-time metrics: Updated every 30 minutes (live session count)
- Near real-time: Updated hourly (revenue, conversions)
- Daily refresh: Overnight batch for historical analysis
- Weekly freeze: Friday 5pm for reporting period finalization

## Insights and Decision Framework

### Weekly Decision Triggers

**Red Flag Thresholds (Immediate Action Required):**

- Revenue down 20% week-over-week
- Conversion rate down 15% week-over-week
- Any channel ROAS below 1.5:1 (losing money)
- Checkout abandonment rate above 60%

**Green Flag Patterns (Optimize for Growth):**

- Email-attributed revenue growing 5%+ week-over-week
- Repeat purchase rate increasing each cohort
- Organic traffic growing while paid efficiency improves
- Device-specific performance variance (opportunity for targeted UX fix)

### Root Cause Investigation Process

When a metric declines:

1. Check data quality first (tracking issues vs. real performance)
2. Isolate by channel or segment (organic vs paid, desktop vs mobile)
3. Review external factors (promotions, traffic changes, platform updates)
4. Compare to baseline (weekly average, seasonal patterns, year-over-year)
5. Propose specific action and test hypothesis

## Reporting Cadence

**Daily Check-in** (10 minutes)

- Revenue vs target
- Any red flags triggered

**Weekly Review** (30 minutes)

- All Tier 1-2 metrics analyzed
- Channel performance deep dive
- Decision recommendations for marketing spend adjustment

**Monthly Strategy** (2 hours)

- Tier 3 product analysis
- Tier 4 cohort retention review
- Quarterly forecast update
- Strategic priority shifts based on data trends

## Benchmarking Context

Performance standards vary by e-commerce vertical. The ranges below reflect 2024-2026 market conditions with emphasis on profitability optimization over traffic growth.

**Fashion & Apparel:**

- Conversion rate: 1-2%
- AOV: 50-75 USD
- Repeat rate (30d): 8-12%
- 2026 note: Brands focusing on margin optimization and brand repeat rather than new customer acquisition

**Health & Supplements:**

- Conversion rate: 2-4%
- AOV: 40-60 USD
- Repeat rate (30d): 25-40%
- 2026 note: Strong repeat-purchase dynamics; focus shifting to subscription models and cohort retention

**Consumer Electronics:**

- Conversion rate: 0.5-1.5%
- AOV: 150-400 USD
- Repeat rate (30d): 3-8%
- 2026 note: AOV improvements primarily through bundle optimization and complement-product recommendations

Actual performance depends on market maturity, customer acquisition strategy, product positioning and inventory health. In current economic environment, improvement typically comes from channel optimization and merchandising reallocation rather than new customer growth.
