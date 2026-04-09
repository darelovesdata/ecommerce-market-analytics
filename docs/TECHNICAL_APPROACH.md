# Technical Implementation Approach

## System Architecture Overview

The dashboard operates as an integrated analytics platform connecting five data sources into a unified visualization layer.

### Data Flow Architecture

Data sources pass through processing logic into a centralized warehouse structure, then surface through Looker Studio visualization layer.

**Source Layer:**

- GA4 (Google Analytics): Event-level user behavior via API
- Shopify API: Product, order, customer data
- Google Ads API: Campaign performance metrics
- Meta Ads Manager API: Advertising spend and conversions
- HubSpot API: Customer engagement and email metrics

**Processing Layer:**

- Data validation and transformation (reconciling different data schemas)
- Combining sales data with attribution data
- Standardizing dimensions across systems (time zones, currency conversion)
- Calculating derived metrics (ROAS, CAC, CLV)

**Storage Layer:**

- Database schema organized by entity (customers, orders, campaigns, sessions)
- Retention policy: 24 months rolling history
- Indexing strategy: Optimized for date-range and segmentation queries

**Presentation Layer:**

- Looker Studio dashboards (interactive visualization)
- Scheduled email reports (automated distribution)
- API endpoint (programmatic access for third-party tools)

## Data Integration Strategy

### Challenge 1: Multiple Attribution Models

Different systems track conversions differently:

- GA4: Last-click model with 30-day lookback
- Shopify: Direct order attribution (no multichannel view)
- Google Ads / Meta: Click-based conversion windows

Solution: Create standardized attribution schema that maps:

- GA4 session ID to Shopify order ID
- Ad click to Shopify customer ID
- Email interaction to purchase within 7-day window

### Challenge 2: Data Lag and Consistency

API update frequencies vary:

- GA4: Updated within 48-72 hours (5-7 day delay for full processing)
- Shopify: Real-time webhook for orders
- Google Ads: Updated within 24 hours
- Meta Ads: Updated within 6 hours

Solution: Implement tiered refresh schedule:

- Real-time layer: Live traffic and revenue
- Near-real-time: 1-hourly refresh for most metrics
- Batch: Overnight reconciliation and historical updates

### Challenge 3: Data Quality and Validation

Source systems have different quality baselines and completeness.

Solution: Implement validation rules:

- Revenue reconciliation: Dashboard revenue must match Shopify within 2% daily
- Session tracking: GA4 sessions must correlate with Shopify traffic
- Currency standardization: Convert all metrics to base currency
- Missing data handling: Display data confidence intervals where applicable

## KPI Calculation Logic

### Tier 1: Executive Metrics

**Revenue (Daily):**

```data
SUM(Shopify.order_total) WHERE order_status = "completed"
Filters: Date range, exclude refunds
```

**Conversion Rate (Session-Level):**

```
COUNT(DISTINCT Shopify.order_id) / COUNT(DISTINCT GA4.session_id)
Segmented by: Channel, device, day of week
Applied to: All sessions that visited checkout
Calculated: Daily, with 7-day rolling average for trend
```

**Average Order Value:**

```
SUM(Shopify.order_total) / COUNT(Shopify.order_id)
Segmented by: Channel, device, day of week
```

**Blended ROAS (Multichannel):**

```
(Google_Ads.converted_value + Meta.purchase_value) /
(Google_Ads.spend + Meta.spend)
Calculation: Daily, with 7-day rolling for stability
```

### Tier 2: Acquisition Channel Metrics

**Sessions by Channel:**

```
COUNT(DISTINCT GA4.session_id) BY ga:source/medium
Example: google.organic / facebook.cpc / direct.none
```

**Customer Acquisition Cost:**

```
Ad_Spend_by_Channel / New_Customers_from_Channel
Example: $400 Google Ads spend / 8 new customers = $50 CAC
```

**New vs Returning Ratio:**

```
COUNT(new_users) / COUNT(all_users)
Source: GA4 dimension: firstUserDate vs current date
```

### Tier 3: Product Performance

**Revenue by Category:**

```
SUM(Shopify.order_total) WHERE product_category = "X"
Segmented by: Day, week, month
Trend: Current period vs previous period
```

**Checkout Abandonment by Device:**

```
(Sessions_reaching_checkout - Sessions_completing_purchase) /
Sessions_reaching_checkout
Segmented by: desktop.web, mobile.web, mobile.app
```

### Tier 4: Retention Metrics

**30-Day Repeat Purchase Rate:**

```
Customers_purchasing_in_days_1_30 / Customers_purchasing_on_day_0
Grouped by: Cohort (acquisition week or month)
Trended: 12-month rolling view by cohort
```

**Customer Lifetime Value:**

```
AVERAGE(order_value_per_customer) x
AVERAGE(purchase_frequency_per_year) x
AVERAGE(customer_lifespan_years)
```

**Email Attribution:**

```
SUM(revenue_with_email_touchpoint_in_customer_journey) /
SUM(total_revenue)
Lookback window: 30 days before purchase
```

## Dashboard Design Decisions

### Page 1: Executive Summary

- Most critical metrics visible without scrolling
- Color-coded status indicators (green/yellow/red)
- Comparison to target and prior period
- Single-page printing capability

### Page 2: Traffic & Acquisition

- Channel performance ranked by revenue contribution
- CAC by channel vs benchmark
- New user growth trend
- Device performance comparison

### Page 3: Product Performance

- Top 10 and bottom 10 products ranked by revenue
- Category breakdown with margin analysis
- Abandonment rate by device
- Creative performance metrics

### Page 4: Retention Analysis

- Cohort retention matrix (new customer cohorts on Y-axis, day ranges on X-axis)
- CLV trending by acquisition month
- Repeat purchase rate targets vs actual
- Segment-specific retention analysis

### Page 5: Alert Dashboard

- Automated red flags triggering action
- Anomaly detection for unusual patterns
- Forecast vs actual performance
- Recommended optimizations based on data

## Implementation Tools

**Data Ingestion:**

- Google Sheets for initial prototyping (direct API reads)
- (Scalable option: BigQuery for enterprise volume)

**Visualization:**

- Looker Studio for interactive dashboards
- (Scalable option: Tableau or Looker for deeper BI)

**Automation:**

- Google Apps Script for scheduled data pulls
- Zapier for webhook triggers

**Documentation:**

- Data lineage documentation (which metric comes from which source)
- SQL queries stored in version control
- Refresh schedule published to stakeholders

## Performance Optimization

**Query Efficiency:**

- Pre-aggregate daily totals to reduce query scope
- Index heavily used dimensions (date, channel, device)
- Use cached tables for consistent metric calculations

**Update Frequency Trade-offs:**

- Real-time metrics: 1 to 2 key indicators only (server load)
- Near-real-time (hourly): Most operational metrics
- Daily batch: Historical trend analysis and comparisons

**Scalability Considerations:**

- Current: 5 clients, 50-100 GB data annually
- Growth path: Migrate to data warehouse (BigQuery) at 500 GB+
- Multi-client dashboard: Requires tenant isolation logic

## Testing and Validation

**Data Accuracy Testing:**

- Weekly reconciliation reports (Google Analytics vs Shopify vs ads platform)
- Variance thresholds documented
- Alert if reconciliation exceeds threshold

**Calculation Verification:**

- Manual spot-check of top 10 metrics monthly
- Compare dashboard to source system exports
- Document any discrepancies and root causes

**Performance Monitoring:**

- Track dashboard load time (target: under 3 seconds)
- Monitor API usage against rate limits
- Alert on data latency exceeding expected windows

## Version Control and Documentation

**What Gets Tracked:**

- SQL queries for database-based calculations
- Data schema definitions
- Transformation logic rules
- Configuration files for metric definitions

**Documentation Standards:**

- Every metric has documented calculation
- Source of truth identified for each dimension
- Refresh schedule and latency expectations documented
- Known limitations and assumptions listed
