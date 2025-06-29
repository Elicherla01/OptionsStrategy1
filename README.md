# Dynamic SMA Supertrend Indicator - Documentation

**Author:** Ravindra Elicherla  
**Version:** Pine Script v6  
**Type:** Overlay Indicator  

## Overview

The Dynamic SMA Supertrend Indicator is a sophisticated trading tool that combines a timeframe-adaptive Simple Moving Average (SMA) with the Supertrend indicator to generate precise entry and exit signals for options trading strategies. The indicator is specifically designed to signal Bull Put Spreads and Bear Call Spreads with clean, non-repetitive signals.

## Key Features

### 1. **Dynamic SMA Calculation**
- Automatically adjusts SMA period based on the selected timeframe
- Formula: `SMA Period = 375 trading minutes ÷ Current Timeframe`
- Examples:
  - 1-minute chart: SMA = 375 periods
  - 3-minute chart: SMA = 125 periods
  - 5-minute chart: SMA = 75 periods
  - 15-minute chart: SMA = 25 periods

### 2. **Supertrend Integration**
- Uses ATR-based Supertrend indicator for trend direction
- Default settings: 14 ATR length, 4.0 multiplier
- Green line = Bullish trend, Red line = Bearish trend

### 3. **State Management**
- Prevents duplicate signals through intelligent state tracking
- Three states: FLAT (no position), LONG, SHORT
- Ensures proper signal sequence: Entry → Exit → Entry

## Signal Logic

### Entry Signals

#### **Bull Put Spread Signal (Green)**
- **Condition:** Price is above BOTH SMA and Supertrend
- **Strategy:** Sell put spreads in bullish market conditions
- **Visual:** Green label "Bull Put Spread" below the bar

#### **Bear Call Spread Signal (Red)**
- **Condition:** Price is below BOTH SMA and Supertrend
- **Strategy:** Sell call spreads in bearish market conditions
- **Visual:** Red label "Bear Call Spread" above the bar

### Exit Signals

#### **Exit Bull Put Spread (Red X)**
- **Condition:** Price drops below SMA (regardless of Supertrend)
- **Action:** Close bull put spread positions
- **Visual:** Red X with "EXIT Bull PS" below the bar

#### **Exit Bear Call Spread (Green X)**
- **Condition:** Price rises above SMA (regardless of Supertrend)
- **Action:** Close bear call spread positions
- **Visual:** Green X with "EXIT Bear CS" above the bar

## How to Use the Script

### Installation
1. Open TradingView and go to Pine Editor
2. Copy the complete script code
3. Paste it into a new Pine Editor window
4. Click "Add to Chart"

### Configuration

#### **Input Parameters**
- **Supertrend ATR Length:** Default 14 (range: 1-50)
  - Lower values = More sensitive signals
  - Higher values = Smoother, less frequent signals
  
- **Supertrend Multiplier:** Default 4.0 (range: 0.1-10.0)
  - Lower values = More signals, more noise
  - Higher values = Fewer signals, higher quality

### Reading the Chart

#### **Visual Elements**
1. **Blue Line:** Dynamic SMA
2. **Green/Red Line:** Supertrend (Green = Bullish, Red = Bearish)
3. **Information Table:** Shows current settings and position state

#### **Signal Interpretation**
- **Bull Put Spread:** Enter when both SMA and Supertrend are bullish
- **Bear Call Spread:** Enter when both SMA and Supertrend are bearish
- **Exits:** Based purely on SMA crossovers for quick response

### Trading Strategy

#### **For Bull Put Spreads**
1. Wait for "Bull Put Spread" signal
2. Sell put spread below current price
3. Monitor for "EXIT Bull PS" signal
4. Close position when exit signal appears

#### **For Bear Call Spreads**
1. Wait for "Bear Call Spread" signal
2. Sell call spread above current price
3. Monitor for "EXIT Bear CS" signal
4. Close position when exit signal appears

## Best Practices

### **Timeframe Selection**
- **1-5 minutes:** Day trading, scalping
- **15-30 minutes:** Swing trading
- **1 hour+:** Position trading

### **Market Conditions**
- Works best in trending markets
- Less effective in sideways/choppy markets
- Consider market volatility when setting position sizes

### **Risk Management**
- Always use stop losses
- Size positions appropriately
- Don't trade against major support/resistance levels
- Avoid trading during major news events

## Customization Options

### **Adjusting Sensitivity**
- **More Signals:** Reduce Supertrend multiplier to 2.0-3.0
- **Fewer Signals:** Increase Supertrend multiplier to 5.0-6.0
- **Faster Exits:** Consider using a shorter SMA for exits

### **Alternative Strategies**
The core logic can be adapted for:
- Traditional long/short equity trades
- Futures trading
- Forex trading
- Other options strategies

## Information Table Reference

The top-right table displays:
- **Timeframe:** Current chart timeframe
- **SMA Period:** Calculated dynamic SMA periods
- **Supertrend:** Current ATR length and multiplier settings
- **Exit %:** Reference percentage (currently 1%)
- **Position:** Current state (LONG/SHORT/FLAT)

## Troubleshooting

### **No Signals Appearing**
- Check if price is near both SMA and Supertrend lines
- Reduce Supertrend multiplier for more sensitivity
- Verify timeframe is appropriate for market volatility

### **Too Many Signals**
- Increase Supertrend multiplier
- Use higher timeframes
- Add additional filters (volume, RSI, etc.)

### **Late Exits**
- Consider using a faster SMA for exits
- Add additional exit conditions
- Monitor position size to reduce risk

## Disclaimer

This indicator is for educational and informational purposes only. It should not be considered as financial advice. Always:
- Test strategies on paper before live trading
- Understand options trading risks
- Consider consulting with a financial advisor
- Use proper risk management techniques

---

**Version History:**
- v1.0: Initial release with dynamic SMA and Supertrend integration
- Current: Options-focused labeling with state management
