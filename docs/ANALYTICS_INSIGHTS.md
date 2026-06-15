# Analytics Insights and Discovery Framework

## Key Performance Indicator Architecture

### Tier 1: Executive Health Metrics

These four metrics answer the fundamental business question: "Are we on track?"

**Revenue Performance:**

- Metric: Total Revenue vs Weekly Target
- Calculation: Sum of completed orders across all channels
- Why it matters: Direct visibility into business performance
- Benchmark: Tracks weekly and year-to-date performance against forecasted targets

**Conversion Rate:**

- Metric: Sessions converting to completed purchase
- Calculation: (Completed Purchases / Total Sessions) x 100
- Why it matters: Indicates website effectiveness independent of traffic volume
- Typical range: 1–4% for e-commerce (varies by vertical)

**Average Order Value:**

- Metric: Mean transaction value across all orders
- Calculation: Total Revenue / Total Orders
- Why it matters: Key multiplier in the revenue equation
- Strategic insight: Often easier to increase than conversion rate

**Blended Return on Ad Spend (ROAS):**

- Metric: Revenue attributed to paid advertising / Ad spend
- Calculation: Sum of Google Ads revenue + Meta revenue / Total spend
- Why it matters: Indicates efficiency of paid marketing investment
- Target benchmark: Minimum 3:1 ROAS for profitability

### Tier 2: Acquisition Channel Metrics

These metrics segment performance by marketing source, answering: "Where do profitable customers come from?"

**Traffic by Channel:**

- Organic Search: 35–45% typical (free traffic, typically high quality)
- Paid Social: 15–25% typical (Meta, TikTok, Snap)
- Paid Search: 10–20% typical (Google Ads, Bing)
- Email: 5–15% typical (highest ROI channel typically)
- Direct: 5–10% typical (brand searches, bookmarks)
- Social Organic: 5–15% typical (influencer-driven)

**Customer Acquisition Cost (CAC):**

- Calculation: Total marketing spend / New customers acquired
- By channel: Spend by channel / New customers from channel
- Comparison: Email typically £15–£40 per customer; paid social £80–£200 per customer
- Profitability check: CAC must be lower than customer lifetime value

**New vs Returning User Ratio:**

- New users: First-time site visitors
- Returning users: Previous visitors making a repeat purchase
- Target: 60–70% new, 30–40% returning (varies by strategy)
- Strategic insight: Increasing repeat rate is 5–7x cheaper than new customer acquisition

### Tier 3: Product and Merchandising Metrics

These metrics identify revenue drivers and underperformers, answering: "Which products should we optimise and why?"

**Revenue by Product Category:**

- Rank: Top performers vs bottom performers
- Margin analysis: Category profitability (including cost of goods sold)
- Trend: Week-over-week and month-over-month performance
- Alert: Categories with declining revenue for two or more consecutive weeks

**Product Unit Economics:**

- Units sold by product
- Average price per unit
- Margin per unit
- Inventory turnover rate

**Checkout Abandonment Rate by Device:**

- Desktop abandonment: Typical 20–30%
- Mobile abandonment: Typical 40–50% (indicates UX friction)
- Root causes: Form complexity, limited payment options, shipping costs
- Benchmarking: Mobile abandonment at 2–3x the desktop rate indicates a design issue

**Hero/Banner Creative Performance:**

- Click-through rate on homepage creative
- Scroll depth by creative type
- Conversion rate by above-the-fold experience
- Seasonal performance variations

### Tier 4: Retention and Lifetime Value Metrics

These metrics focus on building recurring revenue, answering: "How do we maximise customer lifetime value?"

**Repeat Purchase Rate by Cohort:**

- 30-day repeat rate: Percentage making a purchase within 30 days
- 60-day repeat rate: Percentage making a purchase within 60 days
- 90-day repeat rate: Percentage making a purchase within 90 days
- Benchmark: Strong cohort retention starts at 15–25% for the 30-day repeat window

**Customer Lifetime Value (CLV):**

- Calculation: (Average order value x Purchase frequency x Customer lifespan)
- Example: £95 AOV x 3 purchases/year x 4 years = £1,140 CLV
- Strategic: Compare CLV to CAC (target 3:1 minimum ratio)
- Margin on CLV: Should account for cost of goods and fulfilment

**Email-Attributed Revenue:**

- Percentage of total revenue attributed to email touchpoints
- Open rates: Typical 15–25% (strong performers 25–35%)
- Click rates: Typical 2–5% (strong performers 5–8%)
- Unsubscribe rate: Typical 0.1–0.3% (above 0.5% indicates a list quality issue)

**Churn Rate by Cohort:**

- Definition: Customers not making a repeat purchase within the expected window
- Calculation: (Customers lost in period / Customers at start of period) x 100
- By cohort: Track customers acquired in the same month
- Inverse indicator: 1 minus churn rate = retention rate

---

## Data Quality Standards

### Accuracy Checkpoints

1. **Revenue reconciliation**: Dashboard revenue matches Shopify backend within 2%
2. **Attribution consistency**: GA4 transactions match Shopify revenue within an acceptable daily variance
3. **Channel tracking**: All traffic sources are properly tagged with UTM parameters
4. **Conversion lag**: Account for the 1–2 day Google Analytics processing delay

### Data Update Frequency

- Real-time metrics: Updated every 30 minutes (live session count)
- Near real-time: Updated hourly (revenue, conversions)
- Daily refresh: Overnight batch for historical analysis
- Weekly freeze: Friday 5pm for reporting period finalisation

---

## Insights and Decision Framework

### Weekly Decision Triggers

**Red Flag Thresholds (Immediate Action Required):**

- Revenue down 20% week-over-week
- Conversion rate down 15% week-over-week
- Any channel ROAS below 1.5:1 (losing money)
- Checkout abandonment rate above 60%

**Green Flag Patterns (Optimise for Growth):**

- Email-attributed revenue growing 5%+ week-over-week
- Repeat purchase rate increasing each cohort
- Organic traffic growing while paid efficiency improves
- Device-specific performance variance (opportunity for targeted UX improvement)

### Root Cause Investigation Process

When a metric declines:

1. Check data quality first (tracking issues vs real performance decline)
2. Isolate by channel or segment (organic vs paid, desktop vs mobile)
3. Review external factors (promotions, traffic changes, platform updates)
4. Compare to baseline (weekly average, seasonal patterns, year-over-year)
5. Propose a specific action and test the hypothesis

These five steps keep investigation structured and prevent reactive decision-making based on noise rather than genuine trends. The process feeds directly into the reporting cadence below.

---

## Reporting Cadence

**Daily Check-in** (10 minutes)

- Revenue vs target
- Any red flags triggered

**Weekly Review** (30 minutes)

- All Tier 1–2 metrics analysed
- Channel performance deep dive
- Decision recommendations for marketing spend adjustment

**Monthly Strategy** (2 hours)

- Tier 3 product analysis
- Tier 4 cohort retention review
- Quarterly forecast update
- Strategic priority shifts based on data trends

---

## Benchmarking Context

Performance standards vary by e-commerce vertical. The ranges below reflect 2024–2026 market conditions with emphasis on profitability optimisation over traffic growth.

**Fashion & Apparel:**

- Conversion rate: 2–4%
- AOV: £85–£120
- Repeat rate (30d): 8–12%
- 2026 note: Brands are focusing on margin optimisation and repeat customer value rather than new customer acquisition. UK clothing return rates run at 23.6%, so net AOV after returns is the more meaningful metric to track.

**Health & Supplements:**

- Conversion rate: 3–5%
- AOV: £60–£95
- Repeat rate (30d): 25–40%
- 2026 note: Strong repeat-purchase dynamics; focus is shifting to subscription models and cohort retention

**Consumer Electronics:**

- Conversion rate: 0.5–1.5%
- AOV: £150–£300
- Repeat rate (30d): 3–8%
- 2026 note: AOV improvements are driven primarily through bundle optimisation and complementary product recommendations

Actual performance depends on market maturity, customer acquisition strategy, product positioning and inventory health. In the current economic environment, improvement typically comes from channel optimisation and merchandising reallocation rather than new customer growth. 
