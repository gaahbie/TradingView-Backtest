# TradingView Backtest Strategies

A collection of educational trading strategies for TradingView, developed and backtested to explore different market trading approaches.

## IMPORTANT DISCLAIMER

**This repository is for educational purposes only.** These strategies are shared to help traders understand different technical approaches and trading logic.

**This is NOT financial advice.** Past performance does not guarantee future results. Always backtest thoroughly and paper trade before using real capital. You are responsible for validating any strategy and managing your risk.

---

## Strategies

### 1. Forex Alignment
**Multi-timeframe trend continuation strategy for 5-minute forex charts**

- **Core Idea:** Identify trends across Daily → 1H → 5M timeframes, enter on pullbacks
- **Entry:** Break of pullback candle after EMA alignment confirmation
- **Exit:** Structural stop + 2:1 fixed risk-reward, EOD close
- **Backtest:** +746.93 CAD on USDCAD (66.67% win rate, 5.315 profit factor)

📖 **[Full Strategy Documentation →](docs/STRATEGY_FOREXALIGNMENT.md)**

---

## Quick Start

1. **Copy strategy code** from `/strategies/ForexAlignment.pine`
2. **Paste into TradingView** → Pine Script Editor
3. **Backtest** on your target instrument & timeframe
4. **Paper trade** for 1-2 weeks before considering real money
5. **Customize** parameters based on your results

See [Full Documentation](docs/STRATEGY_FOREXALIGNMENT.md) for detailed setup instructions.

---

## Repository Structure

```
TradingView-Backtest/
├── README.md                          # This file (overview)
├── LICENSE                            # License information
├── strategies/
│   └── ForexAlignment.pine            # Strategy code
└── docs/
    └── STRATEGY_FOREXALIGNMENT.md    # Detailed documentation & guide
```

---

## Key Resources

- [Full Forex Alignment Documentation](docs/STRATEGY_FOREXALIGNMENT.md)
- [Pine Script Documentation](https://www.tradingview.com/pine-script-docs/)
- [TradingView Strategy Tester Guide](https://www.tradingview.com/pine-script-docs/en/v5/concepts/strategies.html)
- [Risk Management Basics](https://www.investopedia.com/terms/r/riskmanagement.asp)

---

## License

This code is provided for educational purposes. See the LICENSE file for full details.

---

**Remember:** Your success depends on thorough testing, honest risk evaluation, and disciplined execution. Never risk money you can't afford to lose.
