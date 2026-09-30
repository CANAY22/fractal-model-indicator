# Fractal Model Setup Guide

## Step-by-Step Installation

### Prerequisites
- TradingView account (free or paid)
- Access to Pine Editor
- Chart open on any symbol and timeframe

### Installation Steps

#### 1. Copy the Pine Script
- Open this repository
- Navigate to `fractal_model_professional.pine`
- Copy the entire code

#### 2. Add to TradingView
- Go to https://www.tradingview.com/chart/
- Open any chart
- Press `Alt + E` to open Pine Editor
- Click "New" script
- Paste the code
- Click "Save" (top-right)
- Name it: `Fractal Model Professional`
- Click "Add to Chart"

#### 3. Initial Configuration

The indicator will appear on your chart. In the settings:

**General Settings:**
- Higher Timeframe: `4H` (adjust based on your strategy)
- Bias: `Neutral` (show both bullish and bearish)
- Calculate On: `Close` (confirmed candles only)

**Display Options:**
- ✅ Show HTF Reference Levels
- ✅ Show Sweep Signals
- ✅ Show C2 Markers
- ✅ Show CISD Lines
- ✅ Show Projection Levels
- ✅ Show Labels
- ⬜ Enable Position Sizer (leave off for now)

#### 4. Review a Setup

1. Scroll left on the chart to find a completed reversal setup
2. Look for:
   - A red (bearish) or green (bullish) reference line from the HTF
   - A circle marker below/above (sweep signal)
   - A triangle marker (C2)
   - A dashed line (CISD)
3. Follow the sequence:
   - Sweep below/above HTF level ✓
   - Close back through the level ✓
   - C2 marked ✓
   - CISD confirmation ✓
   - Projections drawn ✓

#### 5. Enable Alerts (Optional)

1. Right-click the indicator name in the chart legend
2. Select "Create Alert"
3. Choose an alert condition:
   - "Bullish Fractal Confirmed" (strongest)
   - "Bearish Fractal Confirmed" (strongest)
   - "Bullish C2" (early signal)
   - "Bearish C2" (early signal)
4. Set notification: Popup, Email, Mobile Push, or Sound
5. Click "Create"

#### 6. Enable Position Sizer (Advanced)

Once comfortable with C2/CISD logic:

1. Open indicator settings
2. Enable "Enable Position Sizer"
3. Adjust "Risk %" and "Risk:Reward" to match your strategy
4. The indicator will now draw entry/stop/target boxes

## Common Settings Adjustments

### For Scalping (1m - 15m)
- Higher Timeframe: `15m` or `1h`
- Max Active Signals: `4-5`
- Bias: Your choice (bullish, bearish, or neutral)

### For Swing Trading (1h - 4h)
- Higher Timeframe: `4h` or `1d`
- Max Active Signals: `8-12`
- Bias: Neutral
- Enable Position Sizer: Yes

### For Day Trading (5m - 1h)
- Higher Timeframe: `1h` or `4h`
- Max Active Signals: `6-8`
- Bias: Your choice
- Calculate On: Close

### For Intraday (30m - 1h)
- Higher Timeframe: `4h`
- Max Active Signals: `8`
- Risk:Reward: `2.0` or `3.0`
- Enable Position Sizer: Yes

## Understanding the Colors

- **Green** = Bullish signals (sweep below, C2, CISD, projections)
- **Red** = Bearish signals (sweep above, C2, CISD, projections)
- **Dashed lines** = CISD confirmation levels
- **Solid lines** = HTF reference levels and projections

## Understanding the Shapes

- **Circle** = Sweep detected
- **Triangle (up)** = Bullish C2 candidate
- **Triangle (down)** = Bearish C2 candidate
- **Box** = Position sizer (entry/stop/target)

## Troubleshooting

### No signals appearing?
- Ensure HTF is set correctly (usually 4H works well)
- Check that sweep logic can detect price below HTF low or above HTF high
- Scroll left on chart to find historical setups
- Try a different symbol with more volatility

### Too many signals cluttering the chart?
- Increase "Max Active Signals" value
- Switch Bias to "Bullish" or "Bearish" (instead of Neutral)
- Adjust HTF to a higher timeframe (e.g., 1D instead of 4H)

### CISD line not appearing?
- Ensure "Show CISD Lines" is enabled
- Confirm C2 has been detected (triangle marker visible)
- Wait for the next candle to see the dashed CISD line

### Position Sizer box not showing?
- Enable "Enable Position Sizer" in settings
- Wait for a confirmed setup (C2 + CISD)
- Adjust Risk:Reward if the box seems incorrectly sized

## Next Steps

1. **Test on Historical Data**
   - Scroll through past charts
   - Note how many setups occur per week/month
   - Observe win/loss patterns

2. **Combine with Your Strategy**
   - Use fractal setups as confluent signals
   - Add support/resistance levels
   - Apply risk management rules

3. **Paper Trade**
   - Use TradingView's Paper Trading feature
   - Track setups and outcomes
   - Refine your entry/exit criteria

4. **Live Trading (When Ready)**
   - Start with small position sizes
   - Use the position sizer boxes as guides
   - Always use stop losses
   - Keep a trading journal

## Support & Customization

For issues or feature requests:
- Check the README.md for detailed documentation
- Review the Pine Script comments for logic explanation
- Fork this repository and modify as needed

## Disclaimer

This tool is for educational and analytical purposes only. It does not provide financial advice. Trading carries significant risk. Always test thoroughly and manage risk appropriately.
