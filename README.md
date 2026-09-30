# Fractal Model Indicator

A professional TradingView Pine Script indicator for identifying multi-timeframe reversal sequences using fractal analysis.

## Overview

The **Fractal Model** is a visual-analysis tool that detects and tracks higher-timeframe reversal setups. It does **not** place orders or guarantee trade outcomes — it is a charting reference system.

### The Logic

```
Higher-timeframe level → sweep → close back through level → C2 → CISD → projections / trade plan
```

## Key Features

### Bullish Sequence
1. Price trades **below** a prior higher-timeframe low
2. The active candle closes **back above** that low
3. Script identifies the reversal candle as a **bullish C2** candidate
4. A later close above the calculated **CISD** level confirms the move
5. Optional liquidity lines, projections, and position-sizing boxes frame the upside objective

### Bearish Sequence
1. Price trades **above** a prior higher-timeframe high
2. The active candle closes **back below** that high
3. Script identifies the reversal candle as a **bearish C2** candidate
4. A later close below the calculated **CISD** level confirms the move
5. Optional liquidity lines, projections, and position-sizing boxes frame the downside objective

## What the Script Draws

### Higher-Timeframe (HTF) Reference Levels
- Red line: prior HTF high
- Green line: prior HTF low
- Acts as the sweep target and reversal reference

### Sweep and C2 Marking
- **Sweep signal**: small circle below (bullish) or above (bearish) the candle
- **C2 marker**: triangle pointing up (bullish) or down (bearish)
- Marks the reversal candidate immediately after price closes back through the HTF level

### CISD Line
- Dashed line (green for bullish, red for bearish)
- Represents the confirmation boundary
- Price must close through this level before the setup is considered confirmed

### Projection Levels
- Range-based targets calculated from the setup
- Default multipliers: 1.0x, 2.0x, 3.0x the setup range
- Serve as visual reference levels, not predicted prices

### Position Sizer (Optional)
- Entry zone box
- Stop-loss (HTF level)
- Target (based on risk/reward ratio)
- Useful for visualizing trade geometry

## Settings Guide

### General Settings

| Setting | Default | Purpose |
|---------|---------|----------|
| Higher Timeframe | 4H | HTF candles to reference |
| Bias | Neutral | Filter for bullish, bearish, or both |
| Calculate On | Close | Use confirmed candles (reduces live updates) |
| Risk % | 1.0 | For position sizer sizing |
| Risk:Reward | 2.0 | Target/stop ratio for position sizer |
| Max Active Signals | 8 | Limit concurrent signals on chart |

### Display Options

| Option | Default | Effect |
|--------|---------|--------|
| Show HTF Reference Levels | On | Plot higher-timeframe high/low |
| Show Sweep Signals | On | Mark sweep detection |
| Show C2 Markers | On | Label C2 candidates |
| Show CISD Lines | On | Plot confirmation boundary |
| Show Projection Levels | On | Draw target reference lines |
| Show Labels | On | Add text annotations |
| Enable Position Sizer | Off | Draw entry/stop/target boxes |

## How to Use

### 1. Add to TradingView
- Open Pine Editor (Alt+E)
- Create a new script
- Copy the full `fractal_model_professional.pine` code
- Save and apply to chart

### 2. Start with Default Settings
- Set **Bias** to Neutral
- Keep **Higher Timeframe** on Automatic or 4H
- Enable **Show Sweeps**, **Show CISD**, **Show Projections**
- Leave **Position Sizer** off initially

### 3. Review Completed Setups
- Wait for a complete bullish or bearish sequence
- Note the sweep, C2, and CISD confirmation
- Review how projections align with price action
- Before relying on the model in a trading workflow, test across symbols and timeframes

### 4. Optional: Enable Projections and Position Sizer
- Once comfortable with the C2/CISD logic
- Turn on projections to see target reference levels
- Enable position sizer to see risk/reward geometry

## Important Notes

- **This is a visual-analysis tool**, not an automated trading system
- **No orders** are placed by this script
- **No guaranteed outcomes** — test and validate before live use
- Adjust the higher timeframe based on your trading style (1H, 4H, 1D, etc.)
- Use alerts to get notified of setups without watching the chart constantly
- Combine with your own price action, support/resistance, and risk management rules

## Customization

### Adjust Projection Multipliers
Edit the lines:
```pine
bullProj1 = bullCISD + bullRange * 1.0
bullProj2 = bullCISD + bullRange * 2.0
bullProj3 = bullCISD + bullRange * 3.0
```

### Change Colors
Modify the `color.new()` calls in plot sections:
```pine
plot(showHTFLevels ? htfLastHigh : na, title="HTF High", color=color.new(color.red, 0), ...)
```

### Adjust Risk/Reward Default
Change the `input.float()` line:
```pine
rrRatio = input.float(2.0, "Risk:Reward", minval=0.5, step=0.1)
```

## Alerts

The script provides four built-in alert conditions:
1. **Bullish Fractal Confirmed** — bullish CISD confirmation
2. **Bearish Fractal Confirmed** — bearish CISD confirmation
3. **Bullish C2** — bullish C2 detected (pre-confirmation)
4. **Bearish C2** — bearish C2 detected (pre-confirmation)

To enable:
- Right-click the indicator
- Select "Create Alert"
- Choose one or more conditions
- Set notification method (popup, sound, email, etc.)

## Version History

- **v1.0** (2026-09-30): Initial release
  - HTF reference levels
  - Sweep and C2 detection
  - CISD confirmation
  - Projection levels
  - Position sizer
  - Bias filtering
  - Alert conditions

## Disclaimer

This indicator is provided as-is for educational and analytical purposes. It does not constitute financial advice. Trading futures, forex, stocks, or other instruments carries risk. Test thoroughly on historical data and in a demo environment before live use. Past performance does not guarantee future results.

## License

MIT License — feel free to modify, fork, and distribute.
