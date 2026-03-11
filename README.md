# Value at Risk (VaR) — Portfolio Risk Analysis

Calculates the daily Value at Risk of a multi-asset portfolio using three industry-standard methods. Built as a quantitative finance project demonstrating risk management techniques used by banks and hedge funds worldwide.

---

## What is Value at Risk?

> *"What is the maximum amount I could lose on my portfolio on a bad day?"*

```
95% VaR = $1,947 means:

"On 95% of days this portfolio will not lose more than $1,947.
 Only on the worst 5% of days will losses exceed $1,947."
```

This is the core metric used by every major bank daily to determine how much capital to set aside as a buffer against potential losses — a requirement mandated by regulators after the 2008 financial crisis.

---

## Portfolio

| Asset | Ticker | Weight | Allocation |
|---|---|---|---|
| Apple | AAPL | 50% | $50,000 |
| JP Morgan | JPM | 30% | $30,000 |
| Gold | GC=F | 20% | $20,000 |
| **Total** | | **100%** | **$100,000** |

Data: January 2015 — December 2025 (2,761 trading days)

---

## Three Methods Compared

### Method 1 — Historical VaR
```
Uses actual past returns directly
Sorts all daily losses from worst to best
Takes the 5th percentile as the VaR threshold
Honest — includes all real market events (COVID, rate hikes)
```

### Method 2 — Parametric VaR
```
Assumes returns follow a normal distribution
Uses mean and standard deviation mathematically
Applies z-score of -1.645 for 95% confidence
Fast but assumes perfect bell curve
```

### Method 3 — Monte Carlo VaR
```
Simulates 10,000 possible future trading days
Uses same mean and std as real data
Takes 5th percentile of simulated outcomes
Most flexible and widely used in industry
```

---

## Results

```
Method          VaR %     VaR $
──────────────────────────────
Historical    -1.73%    $1,731
Parametric    -1.94%    $1,935
Monte Carlo   -1.95%    $1,947
──────────────────────────────
Recommended   →         $1,947  (most conservative)
```

A bank holding this portfolio would set aside **$1,947 per day** as a capital buffer.

---

## Key Findings

**1. Diversification reduces risk**
```
Apple     std = 1.82% per day
JPMorgan  std = 1.71% per day
Gold      std = 0.97% per day

Portfolio std = 1.23% per day  ← lower than 2 of 3 assets
Combining assets reduced daily volatility significantly
```

**2. Fat tails make normal distribution underestimate risk**
```
Apple std = 1.82% → normal distribution predicts max loss ~5.5%
Actual worst day  → -12.86%  (more than double the prediction!)

Extreme events happen far more often than bell curve predicts
This is why the 2008 crisis caught most bank models off guard
```

**3. Historical VaR gave lowest estimate**
```
2015-2025 was largely a bull market period
Real 5th percentile was less extreme than bell curve predicted
This shows why using multiple methods matters —
each tells a slightly different story
```

**4. Banks always use the most conservative estimate**
```
Underprepared → bank collapses during crisis
Overprepared  → holds extra capital, slightly less profitable
               but safe — always the right choice
```

---

## Individual Asset Statistics (2015-2025)

```
Asset       Avg Daily Return   Std Dev    Worst Day    Best Day
Apple            +0.10%        1.82%      -12.86%      +15.33%
JPMorgan         +0.08%        1.71%      -14.96%      +18.01%
Gold             +0.05%        0.97%       -5.74%       +5.95%
Portfolio        +0.09%        1.23%           —            —
```

---

## What I Learned

- The mathematical foundation of Value at Risk and why banks use it
- Why diversification reduces portfolio risk below individual asset risk
- The difference between Historical, Parametric and Monte Carlo approaches
- Why fat tails cause normal distribution models to underestimate real risk
- How to use Monte Carlo simulation for financial risk modelling
- Why regulators require banks to hold capital equal to their daily VaR

---

## Tech Stack

```
Language   : Python 3
Libraries  : yfinance, scikit-learn, pandas, numpy, matplotlib, scipy
Data       : Yahoo Finance via yfinance API (2015-2025)
```

---

> Built as a self-directed learning project in quantitative finance and risk management.
> Completed with AI assistance (Claude by Anthropic) as a guided learning exercise.
