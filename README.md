# Multi-Indicator Regime-Filtered Trading Strategy

This project builds a multi-indicator trading system that adapts to different market environments using regime filters. The idea is simple:

Use momentum signals during trending, low-volatility markets,
and switch to mean-reversion signals during choppy or high-volatility markets.

The strategy combines:

- Volatility regimes (using VIX)
- Trend strength filters (moving average slope)
- Momentum indicators (20-day return)
- Mean-reversion indicators (RSI-14)
- Volatility-targeted position sizing
- This project explores whether combining multiple signals and market regimes can create a more robust, adaptive trading framework.

## 📈 Strategy Overview
- Volatility Regime (VIX-based)

  - VIX < 20 → Favor momentum (markets trending, smooth)
  - VIX ≥ 20 → Favor mean-reversion or stay defensive

- Trend Regime

  - Defined using the slope/direction of MA50 vs MA200:
  - Strong uptrend → Momentum enabled
  - Weak trend / sideways → Mean-reversion enabled

- Indicators Used

  - Momentum: 20-day return
  - Mean Reversion: RSI(14)
  - Position Sizing: Volatility-scaled exposure

- Benchmark

  - SPY buy-and-hold
 
## 📉 Backtest Results (Summary)

- The equity curve and performance metrics showed that:
- The system underperformed SPY during the tested period.
- Momentum signals were frequently whipsawed.
- Mean-reversion signals struggled in certain trending environments.
- Regime filters reduced noise but did not create a performance edge.
- The benchmark remained hard to beat due to strong long-term market uptrend
- Numbers:
    - Strategy Stats:
        - CAGR : 0.1759
        - AnnVol: 0.4055
        - Sharpe: 0.6023
        - MaxDrawdown: -0.6483
        - TotalReturn: 12.1725

    - Benchmark stats:
        - CAGR: 0.3922
        - AnnVol: 0.2987
        - Sharpe: 1.2580
        - MaxDrawdown: -0.4836
        - TotalReturn: 192.2380
     
## 🔍 Key Discovery: Not All Strategies Work on All Assets

A major learning outcome from this project:

**A strategy failing on the tickers you tested does not mean the strategy itself is bad, it may simply be mismatched to the assets.**

Different tickers have different structural behaviors:

- Momentum-friendly assets:

  - Trendy tech stocks (e.g., NVDA, TSLA)
  - Long-term compounders
  - Commodities with persistent trends

- Mean-reversion-friendly assets:

  - Range-bound ETFs
  - Currency pairs
  - Low-volatility equities

- Volatility-sensitive assets:

  - Small caps
  - Leveraged ETFs
  - Biotech

Because of these behavioral differences:

A **momentum signal** on a choppy stock will **fail**.

An **RSI mean-reversion signal** on a strongly trending asset will **fail**.

A **regime filter** helps, but cannot compensate for structural mismatch.

## 📌 Core Conclusion

**The underperformance of the strategy does not mean the strategy is ineffective.
It means the chosen tickers were not well-suited to the multi-indicator framework used.**

This is one of the most important lessons in quantitative trading:

  ✔ Strategy design matters
  ✔ But asset selection matters just as much

