# Trader Performance vs Market Sentiment Analysis

## Objective

This project analyzes how Bitcoin market sentiment (Fear & Greed Index) influences trader behavior and performance on Hyperliquid.

The goal is to identify performance patterns across sentiment regimes and derive actionable strategy recommendations.

---

## Datasets

### 1. Bitcoin Market Sentiment (Fear & Greed Index)
- Fields: timestamp, value, classification, date
- Sentiment categories:
  - Extreme Fear
  - Fear
  - Neutral
  - Greed
  - Extreme Greed

### 2. Historical Trader Data (Hyperliquid)
- 211,224 trade records (Jan 2024 – Dec 2024)
- Key fields:
  - Account
  - Size USD
  - Side (BUY/SELL)
  - Closed PnL
  - Timestamp IST

---

## Data Preparation

- Converted timestamps to datetime format
- Aggregated trades to **daily trader-level**
- Merged sentiment data at daily granularity
- Removed 6 unmatched rows (<0.003% of total records)
- Verified:
  - No missing values
  - No duplicate rows

### Key Features Engineered

- `daily_pnl` – Daily PnL per trader
- `win_rate` – Ratio of profitable trades per day
- `trades_per_day`
- `avg_trade_size`
- Volatility-based risk segmentation
- Frequency-based activity segmentation

---

## Methodology

To reduce noise, analysis was conducted at the **daily trader level** rather than raw trade level.

The study evaluates:

1. Performance differences across sentiment regimes
2. Behavioral shifts in:
   - Trade frequency
   - Trade size
   - Win rate
3. Segment-level responses:
   - High vs Low Risk traders
   - Frequent vs Infrequent traders
   - Consistent vs Inconsistent traders

---

## Key Findings

### 1. Performance Peaks at Sentiment Extremes
- Fear and Extreme Greed regimes show the highest average daily PnL.
- Moderate Greed periods show comparatively lower profitability.

This indicates trader performance is **non-linear** with sentiment.

### 2. Volatility-Driven Opportunity
Higher profitability during Fear periods suggests volatility-driven opportunity rather than simple bullish bias.

### 3. Behavioral Sensitivity by Segment
High-risk and frequent traders display stronger performance dispersion across sentiment regimes.

---

## Strategy Recommendations

### Strategy 1 — Volatility-Regime Allocation

Increase capital allocation for consistent traders during:
- Fear
- Extreme Fear
- Extreme Greed

Reduce exposure during:
- Neutral
- Moderate Greed

### Strategy 2 — Greed Risk Control

During Greed regimes:
- Cap exposure for high-risk traders
- Limit excessive trade frequency
- Prioritize traders with stable historical win rates

These dynamic adjustments aim to improve risk-adjusted returns.

---

## Reproducibility

Install dependencies:

```bash
pip install pandas numpy matplotlib seaborn
