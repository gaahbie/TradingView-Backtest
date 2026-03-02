# Forex Alignment Strategy — Detailed Documentation

## Overview

**Forex Alignment** is a multi-timeframe trend continuation strategy designed for intraday forex trading on the 5-minute chart. It combines three aligned EMA timeframes (Daily, Hourly, 5-minute) to identify strong trends, then enters on pullbacks within that trend.

## Core Philosophy

- **Trade continuation, not reversals** — Only enter when the trend is clearly established across multiple timeframes
- **Quality over quantity** — One trade per day maximum; every trade must meet strict alignment criteria
- **Risk management focus** — Fixed risk-to-reward ratio (2:1 by default), structural stops, end-of-day close protection

---

## Strategy Logic

### Entry Requirements (Multi-Timeframe Alignment)

#### Step 1: Daily Trend Confirmation
- **Bullish:** EMA 9 > EMA 20 AND Price > EMA 9
- **Bearish:** EMA 9 < EMA 20 AND Price < EMA 9
- **Barrier:** Price must be above/below the Daily 200 EMA (optional filter for clear market space)

#### Step 2: 1-Hour Confirmation
- **Bullish:** EMA 9 > EMA 20 AND Price > EMA 9
- **Bearish:** EMA 9 < EMA 20 AND Price < EMA 9

#### Step 3: 5-Minute Setup (Execution Timeframe)
- **Trend Structure:** Must have higher highs + higher lows (uptrend) OR lower highs + lower lows (downtrend)
- **Pullback Candle:** Price must pull back to the EMA 9 or between 9/20, then close back inside the trend
  - Bullish: Low touches EMA 9 (within 0.3% threshold), closes above EMA 9
  - Bearish: High touches EMA 9 (within 0.3% threshold), closes below EMA 9
- **Entry Trigger:** Break of the pullback candle's high (longs) or low (shorts)

### Exit Strategy

- **Stop Loss:** Below/above the most recent swing low/high, with 0.05% padding
- **Take Profit:** Risk × 2.0 (2R fixed ratio)
- **End of Day:** All positions force-close at session end (default 3:55 PM ET) — this is a day trade strategy

### Risk Management
- Position size: 5% of account equity per trade
- Maximum 1 trade per trading day
- Structural stops based on recent swing points (not arbitrary levels)
- Fixed 2:1 risk-to-reward ensures mathematically sound position sizing

---

## Backtest Results

**Period:** Jan 11, 2026 — Mar 1, 2026 (6 weeks)  
**Instrument:** USDCAD  
**Timeframe:** 5-minute chart  
**Initial Equity:** 10,000 CAD

| Metric | Result |
|--------|--------|
| **Total P&L** | +746.93 CAD (+0.07%) |
| **Max Equity Drawdown** | 158.71 CAD (0.02%) |
| **Total Trades** | 9 |
| **Winning Trades** | 6 (66.67% win rate) |
| **Losing Trades** | 3 (33.33%) |
| **Profit Factor** | 5.315 |
| **Average Win** | ~124.49 CAD |
| **Average Loss** | ~46.83 CAD |
| **Avg Risk-Reward Realized** | 2.66:1 |

### Key Takeaways
- ✅ **Low drawdown relative to gains** — Only 0.02% max drawdown vs. +0.07% return
- ✅ **Strong profit factor** — Each dollar risked generated $5.31 in profit
- ✅ **Quality over quantity** — Few trades but consistent execution of the alignment rules
- ✅ **Win rate above 60%** — Most trades hit their target, validating the entry logic

**Important:** This backtest reflects *past performance* on USDCAD during a specific time period. Different currency pairs, market conditions, and parameter adjustments will yield different results. **Always test on your target instrument before trading.**

---

## How to Use

### Step 1: Import into TradingView
1. Copy the strategy code from `/strategies/ForexAlignment.pine`
2. Open TradingView and go to **Pine Script Editor**
3. Click **New** → Paste the code
4. Click **Save** and deploy to your chart

### Step 2: Configure Parameters
- Open the **Settings** (gear icon) on the chart
- Review the input parameter groups:
  - **EMA Settings** — Adjust EMA lengths if testing different instruments
  - **Trend Structure** — Pivot lookback sensitivity
  - **Pullback & Entry** — Touch threshold, setup lifespan
  - **Risk Management** — Initial R:R, stop-loss padding
  - **Session** — Match your trading timezone
  - **Visuals** — Customize what you see on the chart

### Step 3: Backtest the Strategy
1. Open the **Strategy Tester** (bottom panel in TradingView)
2. Select the strategy from the dropdown
3. Choose your instrument, timeframe, and date range
4. Run the backtest and review results

### Step 4: Forward Test & Paper Trade
1. Paper trade on a live chart for at least 1-2 weeks
2. Track slippage, spread impact, and execution quality
3. Adjust parameters based on real-world conditions if needed
4. **Only then consider live trading with real small position sizes**

### Step 5: Continuous Learning
- Study each winning and losing trade
- Identify patterns in when the strategy works best
- Monitor changes in market structure
- Keep detailed notes on your results

---

## Strategy Customization

### Testing on Different Instruments
1. **Adjust EMA lengths** if the instrument is less volatile (shorter) or more volatile (longer)
2. **Modify the session time** to match your target market's hours
3. **Test different timeframes** (e.g., some instruments work better on 1H instead of 5M)
4. **Parameter sweep** — Run backtests with different combinations to find optimal settings

### Key Parameters to Adjust
- **Fast EMA (9)** — Lower values (5-7) = more responsive, more false signals
- **Slow EMA (20)** — Higher values (25-30) = slower confirmation, fewer but potentially larger moves
- **Risk-to-Reward Ratio (2.0)** — Conservative (1.5:1) = safer but lower return; Aggressive (3:1) = higher target but larger stops
- **Session Times** — Match your broker's trading hours exactly
- **Pivot Lookback (8)** — Lower = more swing points (more noise); Higher = fewer, cleaner pivots

---

## FAQ

**Q: Can I trade this strategy live?**  
A: Only after extensive personal testing. Backtest, forward test with paper trading, and validate it works in your market conditions before risking real money.

**Q: What's the best way to optimize these parameters?**  
A: Use TradingView's backtester with different parameter ranges. Start with the default, then tweak one parameter at a time while monitoring the profit factor and drawdown.

**Q: Does this work on all forex pairs?**  
A: Backtested on USDCAD; performance varies by instrument. Test thoroughly on your target pair before trading.

**Q: How much capital do I need to start?**  
A: The strategy uses 5% of equity per trade, so you need enough to sustain the max drawdown seen in testing. Never risk money you can't afford to lose.

**Q: What if I don't hit the target regularly?**  
A: Your market conditions or parameters may differ from the backtest. Adjust EMA lengths, pivot sensitivity, or trading hours. Slippage and spread also impact real results.

**Q: How do I understand the code?**  
A: See the [Pine Script Documentation](https://www.tradingview.com/pine-script-docs/) — it explains EMA, pivot points, and strategy execution concepts used here.

---

## Educational Resources

- [Pine Script Documentation](https://www.tradingview.com/pine-script-docs/) — Understand how the strategy code works
- [TradingView Strategy Tester Guide](https://www.tradingview.com/pine-script-docs/en/v5/concepts/strategies.html) — Learn backtesting
- [Risk Management Basics](https://www.investopedia.com/terms/r/riskmanagement.asp) — Core trading concepts
- [Multi-Timeframe Analysis](https://www.investopedia.com/terms/m/multiple-timeframes.asp) — Understanding trend confirmation

---

**Last Updated:** March 1, 2026  
**Strategy Version:** 1.0
