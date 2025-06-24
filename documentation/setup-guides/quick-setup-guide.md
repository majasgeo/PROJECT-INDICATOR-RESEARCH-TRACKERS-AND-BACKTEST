# Quick Setup Guide - Divergence Research System

**Getting your research trackers up and running in 5 steps**

---

## 🚀 Prerequisites

Before starting, ensure you have:
- ✅ **TradingView account** με Pine Script access
- ✅ **"Divergence for Many Indicators v5 with 4BB"** indicator loaded
- ✅ **Basic understanding** των divergence concepts
- ✅ **BTC/USD or preferred chart** open σε 1-hour timeframe

---

## 📋 Step-by-Step Setup

### **Step 1: Prepare Your Main Indicator**

1. **Open your existing "Divergence for Many Indicators v5 with 4BB"**
2. **Verify it's working** - you should see:
   - 4 sets of Bollinger Bands
   - Divergence lines and labels
   - RSI-based signals

3. **Note the exact settings** you're using:
   - Pivot period (usually 5)
   - Bollinger Bands parameters
   - Which divergence types are enabled

### **Step 2: Add Research Trackers**

Choose ONE of the following based on your research focus:

#### **Option A: Performance Tracking**
For general signal performance monitoring:
```
1. Copy code from: pine-scripts/trackers/performance-tracker-part1.pine
2. Add as new indicator below your main chart
3. Connect inputs to your main indicator outputs
```

#### **Option B: Fibonacci Inverse Research**
For testing the inverse theory:
```
1. Copy code from: pine-scripts/research/fibonacci-inverse-tracker.pine
2. Add as new indicator in separate pane
3. Configure Fibonacci level (start με 1.0)
```

#### **Option C: Behavior Research**
For pure behavior analysis:
```
1. Copy code from: pine-scripts/research/behavior-research-tracker.pine
2. Add as new indicator in separate pane
3. Set tracking period (recommend 50 bars)
```

### **Step 3: Connect the Inputs**

**Critical Step:** Link your tracker to the main indicator

1. **In your tracker settings**, find the "CONNECTION TO MAIN INDICATOR" section
2. **For each input**, select the corresponding output από your main indicator:

```
Bullish Regular Signal → [Your main indicator] "Bullish Regular"
Bearish Regular Signal → [Your main indicator] "Bearish Regular"  
RSI Value → [Your main indicator] "RSI Value"
BB1 Upper → [Your main indicator] "BB1 Upper"
BB1 Lower → [Your main indicator] "BB1 Lower"
```

**⚠️ Important:** If you don't see these options in the dropdown, your main indicator needs modification to expose data (see Advanced Setup).

### **Step 4: Configure Settings**

**Recommended starting settings:**

#### **Performance Tracker:**
- Tracking Period: 200 bars
- Target Distance: 2.5% (BB1), 5.0% (BB2)
- Max Active Signals: 10

#### **Fibonacci Inverse:**
- Fibonacci Level: 1.0 (test others later)
- Tracking Period: 50 bars
- RSI Thresholds: Bull 65, Bear 35

#### **Behavior Research:**
- Tracking Period: 50 bars
- Minimum Move: 2.0%
- RSI Extremes: 70/30

### **Step 5: Verify Operation**

**Check that everything works:**

1. **Look for the research table** στο chart (usually top-right)
2. **Wait for a divergence signal** από your main indicator
3. **Verify the tracker detects it** (new entry in table)
4. **Monitor for a few hours** to see data collection

**Success indicators:**
- ✅ Table shows "Total Signals: 1" (or more)
- ✅ No error messages στο Pine Script console
- ✅ Tracker responds to new divergence signals

---

## ⚙️ Advanced Setup (If Basic Connection Fails)

If the tracker can't read signals από your main indicator, you need to add data exposure:

### **Main Indicator Modification:**

Add these lines στο **end** of your main indicator code:

```pine
// Data exposure για research trackers
plot(pos_reg_div_detected ? 1 : 0, title="Bullish Regular", display=display.data_window)
plot(neg_reg_div_detected ? 1 : 0, title="Bearish Regular", display=display.data_window)
plot(rsi, title="RSI Value", display=display.data_window)  
plot(upper1, title="BB1 Upper", display=display.data_window)
plot(lower1, title="BB1 Lower", display=display.data_window)
plot(upper2, title="BB2 Upper", display=display.data_window)
plot(lower2, title="BB2 Lower", display=display.data_window)
```

**Note:** Replace variable names (pos_reg_div_detected, rsi, upper1, etc.) με the actual variable names από your indicator.

---

## 🎯 What to Expect

### **First 24 Hours:**
- 1-3 divergence signals (depending on market activity)
- Basic table data population
- Initial performance tracking

### **First Week:**
- 5-15 signals collected
- Pattern recognition starting
- Early statistical trends

### **First Month:**
- 20-50 signals (statistical significance)
- Clear behavior patterns
- Actionable insights για strategy refinement

---

## 📊 Reading the Results

### **Performance Tracker Table:**
```
PERFECT TRACKER STATS    VALUE    STATUS
Total Signals               25    
Active Signals               3    
Win Rate                  68.2%   ✅ GOOD
Avg PnL                   +2.4%   ✅ POSITIVE
```

### **Research Tables:**
```
DIVERGENCE BEHAVIOR RESEARCH
                    BULLISH DIV    BEARISH DIV
Total Signals            15            12
Normal Behavior       10 (66.7%)    8 (66.7%)
Reverse Behavior       3 (20.0%)    2 (16.7%)
```

---

## 🚨 Troubleshooting

### **Common Issues:**

**"No signals detected"**
- ✅ Check main indicator is producing divergences
- ✅ Verify input connections are correct
- ✅ Ensure both indicators are on same timeframe

**"Tracker not updating"**
- ✅ Refresh browser/TradingView
- ✅ Check for Pine Script errors στο console
- ✅ Verify data exposure από main indicator

**"Strange results"**
- ✅ Check tracking period settings (too short/long)
- ✅ Verify minimum move percentage
- ✅ Ensure proper signal classification

### **Getting Help:**
- Check documentation/setup-guides/ για detailed troubleshooting
- Review raw-conversations/ για implementation context
- Create GitHub issue με specific error details

---

## 🎉 Success Checklist

Before proceeding με serious research:

- [ ] **Tracker connects** to main indicator successfully
- [ ] **Data collection** working (increasing signal counts)
- [ ] **No consistent errors** στο Pine Script console  
- [ ] **Results look reasonable** (not 0% or 100% rates)
- [ ] **Alert system** functioning (optional)

**Once setup is complete:** Start collecting data for 2-4 weeks before drawing any conclusions about performance patterns!

---

**Setup Time:** ~15-30 minutes  
**Skill Level:** Intermediate (basic Pine Script knowledge helpful)  
**Support:** Available στο documentation/ folder

**Ready to start your divergence research journey!** 🚀
