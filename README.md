# Cross-Market Analysis: Brent Crude vs LSGO Diesel

**Comparative forward curve analysis of global crude oil and European diesel markets**

---

## Project Overview

This project compares the **ICE Brent Crude** and **ICE LSGO (diesel)** forward curves over the period **January 2025 to February 2026** to understand:
- how crude and diesel markets differ in structure and stress behavior,
- whether there are systematic relationships between the two curves,
- what drives these differences (supply chain, geography, market structure),
- how cross-market information can be used for trading and risk management.

**Period:** Jan 2025 – Feb 2026 (288 trading days)  
**Assets:** ICE Brent Crude Futures + ICE Low Sulphur Gasoil Futures  
**Focus:** comparative analysis, correlation, lead-lag relationships, structural differences

The objective is to build a **research-grade comparative framework** showing how two related but distinct commodity markets behave under similar macro conditions.

---

## Project Logic & Motivation

### Why This Project?

Crude oil and diesel are part of the same supply chain: crude is refined into diesel. Yet they trade as separate futures contracts with distinct forward curves. Understanding their relationship is critical for:

1. **Refinery economics**: crack spreads (diesel minus crude) drive refinery margins
2. **Cross-market arbitrage**: opportunities arise when curves diverge
3. **Risk management**: hedging diesel exposure may require crude positions
4. **Market structure understanding**: why do similar commodities behave differently?

This project answers four key questions:

1. **How different are Brent and LSGO in terms of tightness and stress?**
2. **Are the two markets correlated? Do they move together?**
3. **Does one market lead the other? Is there a predictive relationship?**
4. **What explains the differences?**

---

## What Was Built

### 1. Data Integration
- Loads results from LSGO Analysis (Project 1) and Brent Analysis (Project 2)
- Both use identical methodology (rolling contracts, spreads, Z-scores, regimes)
- Enables direct comparison

### 2. Comparative Statistics
- Side-by-side comparison of 12 key metrics
- Backwardation frequency, spreads, Z-scores, distributions
- Ratio analysis to quantify differences

### 3. Correlation Analysis
- Price, spread, and volatility correlations
- Rolling correlations (time-varying relationships)
- Scatter plots and correlation matrices

### 4. Lead-Lag Analysis
- Lagged correlations (-10 to +10 days)
- Cross-correlation functions
- Tests whether Brent leads LSGO or vice versa

### 5. Structural Interpretation
- Supply chain logic (crude → refining → diesel)
- Storage economics (why diesel is tighter)
- Market structure (global vs regional)
- Volatility drivers (prompt vs structure)

---

## Main Findings

### Comparative Statistics

| Metric | LSGO (Diesel) | Brent (Crude) | Ratio/Difference |
|--------|---------------|---------------|------------------|
| **Backwardation %** | 99.7% | 88.9% | +10.8pp |
| **M1-M3 average** | 18.43 USD/MT | 1.14 USD/bbl | 16.2x |
| **M1-M6 average** | 33.65 USD/MT | 2.25 USD/bbl | 14.9x |
| **M1-M3 max** | 85.25 USD/MT | 3.27 USD/bbl | 26.1x |
| **M1-M6 max** | 118.50 USD/MT | 5.75 USD/bbl | 20.6x |
| **Max Z-score** | 5.25 (5-sigma) | 3.96 (4-sigma) | 1.33x |
| **Max volatility** | 78% | 52% | 1.5x |
| **Skewness** | 2.12 | 1.02 | 2.1x |
| **Kurtosis** | 5.72 (fat tails) | 1.37 (thin tails) | 4.2x |
| **Corr(M1-M3, Vol)** | 0.476 | 0.516 | -0.041 |
| **Corr(M1-M6, Vol)** | 0.525 | 0.241 | +0.285 |
| **Days Z > 3** | 14 (4.9%) | 5 (1.7%) | 2.9x |

### Correlation Results

- **Price (M1):** 0.574 - Moderate (common macro drivers)
- **M1-M3 spread:** 0.088 - Weak (different structural drivers)
- **M1-M6 spread:** 0.294 - Weak (different structural drivers)
- **Volatility:** 0.651 - Moderate (common stress periods)
- **Rolling price (60D):** 0.730 average (strong and stable)
- **Rolling spread (60D):** 0.203 average (weak and variable)

### Lead-Lag Results

- **Max price correlation:** 0.574 at lag 0 days
- **Max spread correlation:** -0.147 at lag -10 days (weak, negative)
- **Interpretation:** Markets move **simultaneously** (no predictive relationship)
- Crude doesn't lead diesel, diesel doesn't lead crude

### Key Insights

**1. LSGO is structurally much tighter than Brent**
- 16.2x larger M1-M3 spreads
- 99.7% vs 88.9% backwardation
- Operates with minimal inventory buffers (just-in-time logistics)

**2. Opposite tail behavior**
- LSGO: Fat tails (kurtosis 5.72) - extreme events 4.9% of days
- Brent: Thin tails (kurtosis 1.37) - extreme events 1.7% of days
- 4.2x difference reflects market structure (regional vs global)

**3. Different volatility drivers**
- LSGO: Structure-driven (M1-M6 correlation 0.525) - refinery capacity, storage
- Brent: Prompt-driven (M1-M3 correlation 0.516) - OPEC, geopolitics

**4. Weak spread correlation despite price correlation**
- Prices move together (0.574) - common macro drivers
- Spreads move independently (0.088) - different structural drivers
- Cross-hedging only partially effective

**5. Simultaneous movement (no lead-lag)**
- Both markets react to same macro news at same time
- No arbitrage from lead-lag patterns

---

## Trading Implications

### 1. Cross-Hedging Effectiveness

**Partially effective for price risk:**
- Price correlation 0.574 → Brent hedge reduces LSGO price risk by ~57%
- Remaining 43% is basis risk

**Not effective for spread risk:**
- Spread correlation 0.088 → Brent hedge doesn't protect against LSGO curve tightening
- Need diesel-specific hedges for spread exposure

### 2. Crack Spread Opportunities

- LSGO - Brent spread = refinery margin proxy
- Weak correlation (0.088) → spread can diverge significantly
- Extreme LSGO tightness (Z > 3) → refinery margins expand
- Mean reversion opportunities when spread diverges

### 3. Risk Management

**Different VaR for each market:**
- LSGO: Higher VaR (fat tails, 4.9% extreme events)
- Brent: Lower VaR (thin tails, 1.7% extreme events)

**Position sizing:**
- Smaller positions in LSGO (higher tail risk)
- Larger positions in Brent (more predictable)

**Tail hedging:**
- More critical for LSGO (fat tails)
- Less critical for Brent (thin tails)

### 4. Market Monitoring

- Track both markets separately (weak spread correlation 0.088)
- LSGO stress ≠ Brent stress
- Use different thresholds: LSGO Z > 3 = stress, Brent Z > 3 = moderate
- Volatility spikes tend to coincide (correlation 0.651)

---

## Technical Highlights

### Data Sources
- LSGO Analysis results (Project 1)
- Brent Analysis results (Project 2)
- Identical methodology for comparability

### Analytical Methods
- Pearson correlation (prices, spreads, volatility)
- Rolling correlations (60-day window)
- Lagged correlations (-10 to +10 days)
- Distribution analysis (skewness, kurtosis)

### Visualization
- Scatter plots (correlation)
- Rolling correlation charts
- Cross-correlation functions
- Comparative tables

---

## Limitations

- 13-month sample (cannot establish long-term relationships)
- No fundamental data (refinery runs, crack spreads, inventories)
- Correlation ≠ causation
- Lead-lag results may be sample-specific

This should be viewed as a **structured comparative framework**, not a production trading system.

---

## Next Extensions

- Extend to multi-year history
- Add crack spread analysis (LSGO - Brent)
- Include refinery utilization data
- Test trading strategies based on spread divergence
- Expand to other crude-product pairs (WTI-ULSD, etc.)

---

## Conclusion

This cross-market analysis reveals that **crude and diesel behave fundamentally differently** despite being part of the same supply chain:

**Structural Differences:**
- LSGO 16x tighter than Brent (spreads)
- LSGO fat tails vs Brent thin tails (4.2x kurtosis)
- LSGO extreme events 2.9x more frequent

**Correlation Patterns:**
- Prices moderately correlated (0.574) - common macro
- Spreads weakly correlated (0.088) - different drivers
- Markets move simultaneously (no lead-lag)

**Market Drivers:**
- LSGO: Structure-driven (refinery capacity, storage)
- Brent: Prompt-driven (OPEC, geopolitics)

**Trading Implications:**
- Cross-hedging partially effective (price OK, spread not)
- Crack spread opportunities (weak correlation)
- Different risk management (fat tails vs thin tails)

**Why These Differences?**
- Diesel: Just-in-time logistics, limited storage, regional market
- Crude: Flexible storage, global benchmark, highly liquid

Understanding these relationships is critical for refinery economics, cross-market hedging, and risk management.
