# Settings Reference - Fractal Model Indicator

## Complete Settings Breakdown

This document explains every setting in the Fractal Model indicator and how to adjust them for your trading style.

---

## GENERAL SETTINGS

### Higher Timeframe
**Default:** `4H`  
**Options:** Any timeframe (1m, 5m, 15m, 1h, 4h, 1d, 1w, etc.)

**What it does:**
- Sets the reference timeframe for HTF candles (red/green lines)
- The indicator pulls the high/low from this timeframe
- Price sweeps these levels, then reverses

**How to choose:**
- For scalping: 15m or 1h
- For day trading: 1h or 4h
- For swing trading: 4h or 1d
- Higher timeframe = fewer, cleaner setups
- Lower timeframe = more frequent setups (more noise)

---

### Bias
**Default:** `Neutral`  
**Options:** `Neutral`, `Bullish`, `Bearish`

**What it does:**
- Filters which direction of setups to show

**Options explained:**
- **Neutral:** Show both bullish (green) and bearish (red) signals
- **Bullish:** Show only bullish C2 and CISD (ignore bearish)
- **Bearish:** Show only bearish C2 and CISD (ignore bullish)

**When to use:**
- Use `Neutral` when learning or in choppy markets
- Use `Bullish` during uptrends to reduce false bearish signals
- Use `Bearish` during downtrends to reduce false bullish signals

---

### Calculate On
**Default:** `Close`  
**Options:** `Close`, `Open`

**What it does:**
- Determines whether the indicator uses confirmed closes or open prices

**Options explained:**
- **Close:** Uses the close of each candle (recommended)
  - Reduces live-chart flicker
  - More reliable (price confirmed)
  - Fewer false signals
- **Open:** Uses the open of each candle
  - More responsive to new candles
  - More chart updates (busier)
  - Can produce false signals on open

**Recommendation:** Leave on `Close` for stability.

---

### Risk %
**Default:** `1.0`  
**Range:** 0.1 - 100  
**Unit:** Percentage

**What it does:**
- Sets the risk percentage for position sizer calculations
- Only used if "Enable Position Sizer" is active

**Example:**
- If Risk % = 1.0 and account = $10,000
- Max loss per trade = $100
- Position size adjusted to match

**How to adjust:**
- Conservative traders: 0.5 - 1.0%
- Moderate traders: 1.0 - 2.0%
- Aggressive traders: 2.0 - 5.0%

---

### Risk:Reward
**Default:** `2.0`  
**Range:** 0.5 - 10.0

**What it does:**
- Sets the target/stop ratio for position sizer boxes
- Only used if "Enable Position Sizer" is active

**Example:**
- If Risk:Reward = 2.0 and stop loss = 50 pips
- Target profit = 100 pips
- Reward = 2x the risk

**Common values:**
- Conservative: 1.5 - 2.0
- Balanced: 2.0 - 3.0
- Aggressive: 3.0 - 5.0

---

### Max Active Signals
**Default:** `8`  
**Range:** 1 - 100

**What it does:**
- Limits the number of concurrent CISD lines on the chart
- Older signals are removed to keep chart clean

**How to adjust:**
- For clean charts: 4 - 6
- Standard: 8 - 10
- For detailed analysis: 15 - 20

---

## DISPLAY OPTIONS

### Show HTF Reference Levels
**Default:** `ON` ✅  
**Type:** Toggle

**What it does:**
- Shows red (high) and green (low) reference lines
- These are the levels that price sweeps

**When to disable:**
- Chart is too cluttered
- You want a cleaner view

---

### Show Sweep Signals
**Default:** `ON` ✅  
**Type:** Toggle

**What it does:**
- Shows small circles below (bullish) or above (bearish) when sweep is detected
- Marks the first part of the sequence

**When to disable:**
- Too many circles confusing the chart
- You only want to see confirmed setups (C2)

---

### Show C2 Markers
**Default:** `ON` ✅  
**Type:** Toggle

**What it does:**
- Shows triangles pointing up (bullish) or down (bearish)
- Marks the C2 reversal candidate (price closed back through HTF level)

**When to disable:**
- Only want confirmed setups (CISD)
- Chart is overcrowded

---

### Show CISD Lines
**Default:** `ON` ✅  
**Type:** Toggle

**What it does:**
- Shows dashed confirmation lines
- Price must close through these for confirmation

**When to enable:**
- You want to see all confirmation levels
- Helps identify when setups are confirmed

**When to disable:**
- Chart is too busy
- You only want to trade after visual confirmation

---

### Show Projection Levels
**Default:** `ON` ✅  
**Type:** Toggle

**What it does:**
- Shows target reference lines at 1x, 2x, 3x the setup range
- Acts as visual profit targets

**When to enable:**
- After setup is confirmed
- Planning entry and target

**When to disable:**
- Pre-confirmation (too much visual noise)
- Use position sizer instead

---

### Show Labels
**Default:** `ON` ✅  
**Type:** Toggle

**What it does:**
- Adds text annotations ("Bull C2", "Confirmed", etc.)
- Helps identify setups quickly

**When to disable:**
- Text is overlapping on crowded charts
- You prefer a minimal visual interface

---

### Enable Position Sizer
**Default:** `OFF` ⬜  
**Type:** Toggle

**What it does:**
- Draws colored boxes showing entry, stop, and target
- Uses Risk % and Risk:Reward settings

**Bullish boxes (green):**
- Entry: CISD level
- Stop: HTF low
- Target: Entry + (Risk:Reward × risk)

**Bearish boxes (red):**
- Entry: CISD level
- Stop: HTF high
- Target: Entry - (Risk:Reward × risk)

**When to enable:**
- After learning the C2/CISD logic
- Planning actual trades
- Need visual risk/reward geometry

---

## EXAMPLE SETUPS

### Bullish Setup Sequence
```
1. Price trades below prior HTF low (green reference line)
   → Sweep detected (green circle)

2. Candle closes back above the HTF low
   → C2 marked (green triangle)
   → CISD line drawn (dashed green)

3. Price closes above CISD
   → Setup confirmed ("Confirmed" label)
   → Projection lines drawn (light green)
   → Position sizer box drawn (if enabled)
   → Alert fires (if enabled)
```

### Bearish Setup Sequence
```
1. Price trades above prior HTF high (red reference line)
   → Sweep detected (red circle)

2. Candle closes back below the HTF high
   → C2 marked (red triangle)
   → CISD line drawn (dashed red)

3. Price closes below CISD
   → Setup confirmed ("Confirmed" label)
   → Projection lines drawn (light red)
   → Position sizer box drawn (if enabled)
   → Alert fires (if enabled)
```

---

## RECOMMENDED CONFIGURATIONS

### Scalping (1m - 15m charts)
```
Higher Timeframe: 15m
Bias: Neutral
Calculate On: Close
Show HTF Levels: ON
Show Sweeps: ON
Show C2: ON
Show CISD: ON
Show Projections: OFF (enable later)
Position Sizer: OFF
Max Active Signals: 5
```

### Day Trading (5m - 1h charts)
```
Higher Timeframe: 1h
Bias: Neutral or trending direction
Calculate On: Close
Show HTF Levels: ON
Show Sweeps: ON
Show C2: ON
Show CISD: ON
Show Projections: ON
Position Sizer: ON
Risk:Reward: 2.0
Max Active Signals: 8
```

### Swing Trading (1h - 4h charts)
```
Higher Timeframe: 4h
Bias: Neutral
Calculate On: Close
Show HTF Levels: ON
Show Sweeps: ON
Show C2: ON
Show CISD: ON
Show Projections: ON
Position Sizer: ON
Risk % : 1.0
Risk:Reward: 3.0
Max Active Signals: 12
```

### Longer-term (4h - 1d charts)
```
Higher Timeframe: 1d
Bias: Neutral
Calculate On: Close
Show HTF Levels: ON
Show Sweeps: ON
Show C2: ON
Show CISD: ON
Show Projections: ON
Position Sizer: ON
Risk % : 0.5
Risk:Reward: 2.5 - 3.0
Max Active Signals: 10
```

---

## TIPS & TRICKS

1. **Start Minimal**
   - Begin with defaults
   - Disable features one at a time
   - Enable only what you need

2. **Adjust HTF Last**
   - Logic works best with 4H default
   - Only change if you have a specific reason

3. **Use Bias During Trends**
   - In uptrend: set Bias to Bullish
   - In downtrend: set Bias to Bearish
   - Reduces false signals

4. **Position Sizer for Planning**
   - Don't trade the box size automatically
   - Use it as a visual guide
   - Adjust based on your rules

5. **Combine with Your Strategy**
   - Fractal setups are ONE signal
   - Add support/resistance
   - Add trend filters
   - Apply risk management

---

## Troubleshooting Common Issues

| Issue | Solution |
|-------|----------|
| Too many signals | Increase HTF, set Bias, increase Max Active Signals |
| Too few signals | Decrease HTF, try Neutral bias |
| CISD not showing | Ensure C2 exists, wait for next candle |
| Projections missing | Enable "Show Projection Levels", confirm setup first |
| Chart too cluttered | Disable sweeps, labels, or projections |
| Position sizer box wrong | Check Risk %, Risk:Reward, and CISD level |
| Alerts not firing | Check alert condition selected, enable notifications |

---

## More Info

For detailed logic and code explanation, see `README.md`.  
For installation steps, see `SETUP_GUIDE.md`.
