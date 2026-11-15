# Crypto Regulation Event Study: Chart Guide and Findings

**Project hypothesis:** Crypto prices are more sensitive to regulatory announcements than to underlying economic and financial factors.

**Events tested:** GENIUS Act Senate passage (2025-06-17), CLARITY Act House passage (2025-07-17), GENIUS Act signed (2025-07-18), CLARITY Act Senate cloture failure (2026-09-15).

**Assets:** Bitcoin, Ethereum, Solana, Coinbase (COIN). **Controls:** S&P 500, VIX, 10-yr Treasury yield.

> All images load from the `Output/` folder. Keep this file in the same folder that contains `Output/` (e.g., `Downloads/README.md` and `Downloads/Output/*.png`).

---

## Bottom line (read this first)

**The data do not support the hypothesis as stated.**

- Of 32 abnormal-return tests (4 events x 4 assets x 2 windows), only **2 are statistically significant**, both for **Coinbase around the GENIUS Senate vote**. At the 5% level, about 1 to 2 false positives are expected from 32 tests by chance alone.
- **Bitcoin shows no meaningful reaction to any event.**
- **Day-to-day returns are driven by the stock market**, not regulation. S&P 500 beta is highly significant for every asset (BTC ~1.0, ETH ~1.4, SOL ~1.4, COIN ~2.8). Event-day dummies are insignificant in every returns regression.
- There is a **real but short-lived intraday reaction on Sept 15, 2026**, and **COIN-specific and altcoin-specific effects** around some events. These are the most interesting findings to build the paper around.

A defensible thesis is a **refined** claim: *regulatory news matters for regulation-exposed assets (Coinbase, and to a lesser degree ETH/SOL) but not for crypto as a whole, and market-wide factors explain far more of daily crypto returns.* Do not force the original hypothesis. Reporting a rejected hypothesis honestly is a legitimate result.

**How to read the stats:** "CAR" is cumulative abnormal return, meaning the return beyond what S&P 500, VIX, and rate moves predicted. A t-stat needs to be above roughly 2 (in absolute value) to count as statistically significant. Values below that are indistinguishable from noise.

---

## Chart 1: Rebased Prices Around Each Event

![Rebased prices](Output/01_rebased_prices.png)

**What it shows:** Each asset's price indexed to 100 on the day before the event, for 10 trading days before and after. One panel per event. The dashed line is the event day.

**What it tells us:**
- **GENIUS Senate passes (top left):** Coinbase jumps ~13% the day after and reaches ~143 by day +6, while Bitcoin stays flat near 100. This is the clearest event reaction in the dataset, and it is specific to Coinbase.
- **CLARITY House passes and GENIUS signed (top right, bottom left):** ETH and SOL spike 10 to 17% around the event, but they were **already rising sharply before it** (ETH rises ~30% from day -10 to day -1 in both panels). We cannot tell whether the event caused the move or whether it was part of an existing rally.
- **CLARITY cloture fails (bottom right):** All assets dip on day 0, Coinbase most (to ~86 at day +1), then **everything rallies 5 to 16% over the next 4 to 8 days**. The failure of the bill did not produce a lasting decline.
- **Bitcoin is flat in every panel** around day 0.

**What it means for the project:** This chart is the intuitive visual for the presentation, but it is *not* controlled for the broader market and shows pre-trends. Use it to illustrate, then lean on Charts 2 and 3 for the formal conclusion. The July 17 and July 18, 2025 events are one day apart, so their panels overlap and should be treated as a single cluster, not independent evidence.

---

## Chart 2a: Abnormal Returns, [-1, +1] Window

![CAR -1 to +1](Output/02_CAR-1_+1.png)

**What it shows:** The return in the three days around each event *after removing* what the S&P 500, VIX, and interest-rate changes would have predicted. This isolates the "regulation effect."

| Event | Bitcoin | Ethereum | Solana | Coinbase |
|---|---|---|---|---|
| GENIUS Senate passes | -1.4% (t=-0.32) | -1.4% (t=-0.19) | -0.9% (t=-0.10) | **+20.4% (t=3.01)** |
| CLARITY House passes | 0.0% (t=-0.01) | +12.6% (t=1.72) | +7.9% (t=0.92) | +6.7% (t=0.92) |
| GENIUS signed | -1.1% (t=-0.27) | +11.6% (t=1.58) | +12.2% (t=1.42) | +3.1% (t=0.42) |
| CLARITY cloture fails | -0.1% (t=-0.02) | -2.2% (t=-0.41) | -2.0% (t=-0.37) | -2.3% (t=-0.36) |

**What it tells us:**
- Only **Coinbase on GENIUS Senate passage** is statistically significant (bold).
- ETH and SOL show large positive CARs after the CLARITY House vote and the GENIUS signing (around +8 to +13%), but they fall short of significance (t between 0.9 and 1.7). They are suggestive, not proven.
- The **direction is consistent with the hypothesis**: pro-regulation news (passage, signing) is positive for ETH/SOL/COIN, and the one negative event (cloture failure) is negative for ETH/SOL/COIN. The sizes are small and noisy for the failure event.
- Bitcoin never moves.

**What it means for the project:** The sign pattern supports a *directional* story (good regulatory news = up, bad = down) for non-Bitcoin assets, but the statistical evidence is weak. State this precisely: "directionally consistent, but only 1 of 16 tests reaches significance."

---

## Chart 2b: Abnormal Returns, [0, +5] Window

![CAR 0 to +5](Output/02_CAR0_+5.png)

**What it shows:** The same abnormal return, accumulated over the event day and the next five trading days.

| Event | Bitcoin | Ethereum | Solana | Coinbase |
|---|---|---|---|---|
| GENIUS Senate passes | -0.3% (t=-0.04) | -4.1% (t=-0.39) | -5.2% (t=-0.42) | **+31.4% (t=3.27)** |
| CLARITY House passes | -1.2% (t=-0.20) | +10.1% (t=0.97) | +5.3% (t=0.43) | -3.7% (t=-0.36) |
| GENIUS signed | -2.3% (t=-0.38) | +7.3% (t=0.71) | +6.1% (t=0.50) | -7.7% (t=-0.76) |
| CLARITY cloture fails | +7.9% (t=1.50) | +5.9% (t=0.76) | +11.8% (t=1.51) | +2.5% (t=0.27) |

**What it tells us:**
- Coinbase's GENIUS reaction **persists and grows** (+20% to +31%), so it is not a one-day blip.
- For the July 2025 events, Coinbase's initial gain **reverses** (+6.7% becomes -3.7%; +3.1% becomes -7.7%), which looks like an overreaction that faded.
- **The cloture failure is followed by a positive 5-day abnormal return** for all four assets (BTC +7.9%, SOL +11.8%). This is the opposite of what "regulatory failure hurts crypto" predicts. Likely explanations are a rebound after an initial dip, relief that stricter rules were not imposed, or an unrelated market event. We cannot separate these from the data.

**What it means for the project:** The market's reaction to bad regulatory news was brief (see Chart 5) and then reversed. This is evidence that regulatory shocks may cause short-term sentiment moves, not lasting repricing, which weakens the original hypothesis.

---

## Chart 3: Trading Volume Heatmap

![Volume heatmap](Output/03_volume_heatmap.png)

**What it shows:** Average volume on the event day and the day after, divided by the prior 30-day average. 1.0x is normal activity; green is below normal and red is above.

**What it tells us:**
- **Coinbase volume is elevated (1.5x to 1.8x) on every event.** COIN is the one asset consistently pulled by regulatory news.
- **ETH and SOL volume surged 2.5x to 2.7x on the GENIUS signing**, the strongest volume reaction in the dataset.
- **Bitcoin volume is mostly normal** (0.72x to 1.57x), reinforcing that BTC is not regulation-driven.
- **Volume was *below* normal for crypto on the GENIUS Senate vote** (0.66x to 0.72x) even though Coinbase's price jumped. Price and volume do not tell a consistent story across events.
- **Cloture failure:** Only Coinbase shows heavy volume (1.81x). BTC, ETH, SOL were at or below normal (0.80x to 0.97x), so most crypto traders did not react on a daily basis.

**What it means for the project:** Volume gives a second dimension that mirrors the price findings: **regulation affects Coinbase and, in one case, ETH/SOL, not the crypto market broadly.** Caveat: the July 17 and July 18 windows overlap, so the July 18 baseline includes the July 17 spike. COIN is a stock, so its volume is measured differently from crypto volume.

---

## Chart 4: Rolling 20-Day Volatility

![Rolling volatility](Output/04_rolling_volatility.png)

**What it shows:** Annualized volatility over a rolling 20-day window for BTC, ETH, and SOL from mid-2024 to now. Dashed lines mark the events (three clustered in June to July 2025, one in September 2026).

**What it tells us:**
- Volatility did **not spike around the regulatory events.** The 2025 cluster sits in a calm period (BTC volatility at ~25%, near its lowest of the whole sample).
- The **largest volatility spikes** (Aug 2024, spring 2025, and especially Feb 2026, where SOL and ETH exceed 100% and BTC hits ~85%) **do not line up with any regulatory event.** Market-wide shocks dwarf anything tied to legislation.
- Around the Sept 2026 line, volatility is slightly elevated but within the normal range.

**What it means for the project:** This is some of the strongest visual evidence **against** the hypothesis. If regulation were the dominant driver of crypto risk, volatility should jump at these dates. It does not. Use this chart to argue that the largest risk episodes come from other sources.

---

## Chart 5: Hourly Prices on September 14 to 16, 2026

![Intraday Sept 15](Output/05_intraday_sept15.png)

**What it shows:** Hourly Coinbase prices for BTC, ETH, and SOL (indexed to 100 at the start) with hourly BTC volume below. The dashed line marks the cloture vote.

**What it tells us:**
- Around the vote, prices fell: **BTC about -1.4%, SOL about -2%, ETH about -2.8%**, and they stayed lower through Sept 16 (ETH ~96.5, SOL ~97.5, BTC ~98.5 to 99).
- BTC volume **spiked to ~1,300 in the hour of the vote** and ~1,000 in the next, versus a typical 100 to 500.
- This is the **cleanest evidence of a regulatory reaction** in the whole project, and it is visible only at hourly frequency. The daily data (Charts 2a/2b) wash it out.

**Caveats (important):**
- The sharpest ETH drop occurs **in the hour(s) *before* the dashed line**, and all assets were already falling from a Sept 14 afternoon peak (~103). Either the vote timestamp is off, news leaked earlier, or the decline was in progress. **Confirm the exact vote time** (converted to UTC) and update `INTRADAY_EVENT_UTC` in the script.
- A similar BTC volume spike (~1,400) appears on the evening of Sept 16 with no known event, so volume spikes are not unique to regulation.
- The decline reversed within days (see Chart 2b).

**What it means for the project:** Present this as evidence of a **fast, short-lived reaction** to regulatory news. This supports "sensitive to announcements" at the intraday level while also showing the effect is not lasting.

---

## Chart 6: Variance Explained, Macro vs. Event Days

![R-squared decomposition](Output/06_r2_decomposition.png)

**What it shows:** For each asset, how much of the size of daily moves (absolute return) is explained by S&P 500, VIX, and rates (gray), and how much extra is explained by adding event-day dummies (red). This is the direct test of "regulation vs. economic factors."

| Asset | R² macro only | R² gain from events | Event coefficient p-value |
|---|---|---|---|
| Bitcoin | 2.31% | +0.19 pp | 0.046 (negative sign) |
| Ethereum | 2.38% | +0.01 pp | 0.68 |
| Solana | 1.12% | +0.01 pp | 0.85 |
| Coinbase | 1.01% | +0.52 pp | 0.24 |

**What it tells us:**
- Event days add almost nothing to explanatory power. The largest gain is Coinbase at +0.52 percentage points, and it is not significant.
- **Bitcoin is the only significant event coefficient, and its sign is negative**: BTC moves were *smaller* on event days. This contradicts the hypothesis.
- **Neither side explains much** of the *magnitude* of daily moves (R² of 1% to 2.4%), because crypto volatility is mostly idiosyncratic.

**The stronger macro evidence is in `regression_results.csv`, not in this chart.** For *signed* returns:

| Asset | R² (macro only) | S&P 500 beta | S&P p-value | Event dummy p-value |
|---|---|---|---|---|
| Bitcoin | 19.5% | 0.98 | <0.001 | 0.28 |
| Ethereum | 22.2% | 1.45 | <0.001 | 0.18 |
| Solana | 17.4% | 1.41 | <0.001 | 0.43 |
| Coinbase | 30.6% | 2.80 | <0.001 | 0.74 |

Macro factors explain **17% to 31%** of daily returns, driven by the S&P 500. Event dummies add **under 0.15 percentage points** and are never significant.

**What it means for the project:** This is the core quantitative answer to the hypothesis: **macro/market factors explain far more of crypto returns than regulatory event days do.** Consider adding a second R² chart for signed returns, because it makes this point more clearly than the absolute-return version.

---

## How the Pieces Fit Together

| Question | Evidence | Verdict |
|---|---|---|
| Do crypto prices move more on regulatory news than on macro factors? | Charts 2 and 6, regression table | **No.** S&P beta is highly significant; event dummies are not |
| Does regulation move any asset? | Charts 1, 2a, 2b, 3 | **Coinbase yes** (GENIUS Senate); ETH/SOL directionally yes, not significant; **BTC no** |
| Does regulation raise volatility? | Chart 4 | **No visible effect** |
| Is there a fast reaction at all? | Chart 5 | **Yes, intraday on Sept 15, 2026**, but it reversed |
| Does volume respond? | Chart 3 | **Coinbase consistently; ETH/SOL on GENIUS signing; BTC no** |

## Limitations to State in the Paper

1. **Small sample:** 4 events and 8 event-day observations in a 615-day regression, so low statistical power. "Not significant" does not prove "no effect."
2. **Overlapping events:** July 17 and 18, 2025 are one day apart. Treat as one cluster.
3. **Confounding news:** Other events within the windows (crypto-specific or macro) cannot be separated from regulation.
4. **Pre-trends:** ETH/SOL were rallying before the July 2025 events (Chart 1), which makes the abnormal returns hard to attribute.
5. **Weak market model:** Estimation R² is only 12% to 22% for crypto (23% to 42% for Coinbase), so "abnormal" returns carry a lot of leftover noise. The S&P 500 is not an ideal benchmark for crypto.
6. **Multiple testing:** With 32 tests, some significance by chance is expected.
7. **Daily alignment:** Crypto is aligned to US trading days, so weekend moves roll into Monday.

## Suggested Next Steps (if time permits)

- Add more events (committee markups, other hearings, the dates the bills were introduced) to increase the sample.
- Run a **placebo test**: apply the same method to random non-event dates and show how often CARs this large occur by chance.
- For COIN, add Bitcoin returns as a control factor to separate "crypto market" moves from "regulation" moves.
- Pool the events into an **average CAR across events** for each asset to improve power.
- Confirm and fix the Sept 15 vote timestamp, then re-run Chart 5.

## Files

| File | Contents |
|---|---|
| `Output/01_rebased_prices.png` | Price reaction by event |
| `Output/02_CAR-1_+1.png`, `Output/02_CAR0_+5.png` | Abnormal returns |
| `Output/03_volume_heatmap.png` | Event-day volume vs. normal |
| `Output/04_rolling_volatility.png` | 20-day volatility with events |
| `Output/05_intraday_sept15.png` | Hourly prices and BTC volume |
| `Output/06_r2_decomposition.png` | Macro vs. event explanatory power |
| `Output/event_study_results.csv` | All CARs, t-stats, volume ratios |
| `Output/regression_results.csv` | Macro vs. event regressions |
| `Output/prices.csv` | Daily closing prices |
