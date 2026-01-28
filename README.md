# Margin Leakage Analysis: End-to-End Data Analytics Project

## Project Overview

This is a complete data analytics workflow demonstrating:
- **Python** → Exploratory data analysis, hypothesis testing, quantifying business problems
- **SQL** → Data validation, query optimization, and findings corroboration
- **Tableau** → Executive storytelling and actionable dashboards

The goal isn't just to analyze data—it's to understand business impact, validate findings rigorously, and communicate insights to decision-makers.

---

## The Business Problem

A retail business reports 12.5% overall profit margin, which sounds healthy. But when we dig deeper:
- 18.7% of orders are losing money
- $566K in revenue is being lost to discounting
- Discounting strategy is backwards by geography: weak regions get heavy discounts, strong regions get light discounts

**The core question:** Where is the profitability leaking, and what decisions would recover it?

---

## Key Findings

### 1. Discounts Don't Drive Volume
- **Correlation(Discount, Quantity) = 0.009** (essentially zero)
- Discounting is NOT a volume lever in this business
- We're giving away margin without gaining anything in return

### 2. Discounts Hurt Profit Significantly
- **Correlation(Discount, Profit) = -0.219** (statistically significant)
- There's a clear breaking point: **orders with 20%+ discount average -$46 loss**
- Before 20%: still marginally profitable
- After 20%: systemic losses

### 3. Only One Product Can Absorb Aggressive Discounting
- **Copiers:** $1,616 baseline profit → $243 even at 20%+ discount 
- **Everything else:** Collapses beyond 15-20% discount 

### 4. Discounting Strategy is Backwards by Geography
- **Central Region:** 24% avg discount, $17.09/order profit
- **West Region:** 11% avg discount, $33.85/order profit
- Central is being discounted MORE THAN DOUBLE while already being less profitable

### 5. Damage is Concentrated
- Binders, Machines, Tables account for 52% of all discount damage
- Total: $298K out of $566K

---

## Project Structure

### Phase 1: Python Analysis (Exploratory → Quantification)

#### **01_exploratory_data_analysis.ipynb**
**Question:** Where is the problem?
- Establish baseline profitability (12.5% overall margin)
- Identify that 18.7% of orders lose money
- Verify that discounts correlate with losses
- Find the worst 10 and best 10 orders (62-80% vs 0-4% discount)
- **Output:** Clear evidence that discounting is the culprit

#### **02_discount_analysis.ipynb**
**Question:** How much damage is discounting doing?
- Quantify that discounts don't drive volume (correlation 0.009)
- Find the breaking point (20% discount)
- Calculate total damage: $566K in revenue lost
- Break down damage by sub-category, segment, and region
- Discover geographic paradox (Central 24%, West 11%)
- **Output:** Specific financial impact of discounting strategy

#### **03_profit_analysis.ipynb**
**Question:** Are these problems fixable, or are they structural?
- Analyze baseline profitability (0% discount orders only)
- Classify products by structural strength (Strong, Weak, Broken)
- Compare 0% vs 20%+ discount profit for each product
- Determine how much damage is discount-driven vs structural
- **Output:** Identification of which problems are fixable

#### **04_scenario_modeling.ipynb**
**Question:** What would change if we fixed the discount problem?
- Model: "What if we eliminated discounts on Binders/Machines?"
- Model: "What if we capped all discounts at 15%?"
- Model: "What if Central region adopted West's discount strategy?"
- Quantify profit recovery vs. volume risk
- **Output:** Actionable recommendations with financial impact

---

### Phase 2: SQL Validation (Confirm Python Findings)

#### **queries/01_baseline_profitability.sql**
Validates baseline profit by product/segment/region at 0% discount
- Confirms Python findings on which products are structurally strong
- Optimized query for large datasets

#### **queries/02_discount_impact.sql**
Calculates profit delta between 0% and 20%+ discount
- Validates the breaking point finding
- Shows damage by sub-category

#### **queries/03_regional_analysis.sql**
Compares discount strategy and profit by region
- Confirms Central vs West paradox
- Validates segment-level findings

#### **queries/04_scenario_validation.sql**
Tests scenario assumptions (elasticity, profit recovery)
- Validates scenario modeling from Python
- Calculates actual profit impact of proposed changes

---

### Phase 3: Tableau Visualization (Executive Communication)

#### **tableau/margin_leakage_dashboard.twbx**
Multi-sheet dashboard including:

**Sheet 1: Executive Summary**
- Key metrics: Total margin lost, breaking point, regional comparison
- Color-coded: Green (strong), Yellow (warning), Red (critical)

**Sheet 2: Discount Impact**
- Profit by discount level (barchart showing the cliff at 20%)
- Top 10 products losing money to discounting

**Sheet 3: Regional Deep Dive**
- Central vs West comparison (discount % vs profit/order)
- Why the paradox exists

**Sheet 4: Product Performance**
- Baseline (0%) vs Discounted (20%+)
- Which products can survive discounting

**Sheet 5: Scenario Outcomes**
- What-if analysis results
- Profit recovery potential vs volume risk

---

## Technology Stack

| Tool | Purpose | Skills Demonstrated |
|------|---------|---------------------|
| **Python** (Pandas, NumPy, SciPy, Matplotlib) | Exploratory analysis, statistics, hypothesis testing | Data analysis, SQL fundamentals, problem-solving |
| **SQL** | Data validation, query optimization, corroboration | Database querying, optimization, analytical thinking |
| **Tableau** | Dashboard creation, executive storytelling | Data visualization, business communication |
| **Git/GitHub** | Version control, project documentation | Collaboration, professional practices |

---

## Key Methodology Decisions

### What We Did Right
- **Focused on correlation, not causation** — We show that discounts correlate with losses, but we're careful not to claim causality
- **Avoided theoretical models** — No "what profit would be without discounts" calculations. We analyze real data only.
- **Stratified by discount level** — This lets us see patterns at different discount tiers (0%, 5%, 10%, 20%, etc.)
- **Quantified in dollars** — Not just percentages. The business cares about $566K, not "correlation = -0.219"

### What We Didn't Do
- **Price elasticity modeling** — Why? Because discounts don't move volume (correlation 0.009). No point modeling something that doesn't exist.
- **Reverse-engineering costs** — We can't determine cost structure from profit data alone. This analysis works with what we know.

---

## How to Use This Project

### For Learning
1. Read **01_exploratory_data_analysis.ipynb** to understand the problem
2. Study **02_discount_analysis.ipynb** to see quantification
3. Review **03_profit_analysis.ipynb** for classification logic
4. Check **04_scenario_modeling.ipynb** for decision-making

### For Validation
1. Run the **SQL queries** to confirm Python findings in a database
2. Compare outputs — Python results should match SQL results
3. This demonstrates rigor and understanding of both tools

### For Presentation
1. Use the **Tableau dashboard** for executive presentations
2. Reference Python/SQL findings for deep dives
3. Lead with business impact ($566K loss), support with data

---

## Key Findings Summary Table

| Question | Finding | Implication |
|----------|---------|------------|
| Do discounts move volume? | No (correlation: 0.009) | Discounting isn't a volume strategy |
| Do discounts hurt profit? | Yes (correlation: -0.219) | Discounting is destroying margin |
| What's the breaking point? | 20% discount | Beyond 20%, orders lose money |
| Which products can absorb discounts? | Only Copiers | Most products can't handle aggressive discounts |
| Where is damage concentrated? | 3 products, 52% of losses | Problem is concentrated, fixable |
| Is it discount or structure? | Mostly discount (fixable) | Can recover ~$227K by optimizing discounts |
| Geographic strategy? | Backwards (24% vs 11%) | Weak regions get heavy discounts |

---

## Data Dictionary

**Main Dataset:** `sample_superstore_processed.csv`

| Column | Definition |
|--------|-----------|
| `Order ID` | Unique order identifier |
| `Sales` | Revenue from order (after discount applied) |
| `Quantity` | Units sold |
| `Discount` | Discount percentage (0-0.80) |
| `Profit` | Net profit/loss (includes all costs) |
| `Category` | Product category (Furniture, Office Supplies, Technology) |
| `Sub-Category` | Specific product type (Binders, Machines, Copiers, etc.) |
| `Segment` | Customer segment (Consumer, Corporate, Home Office) |
| `Region` | US Region (Central, East, South, West) |
| `Ship Mode` | Shipping method |

**Important Note:** Profit already includes all costs (COGS, shipping, operational). We cannot reverse-engineer individual cost components.

---

## Files Structure

```
margin-leakage-analysis/
│
├── 📊 PYTHON ANALYSIS
│   ├── 01_exploratory_data_analysis.ipynb
│   ├── 02_discount_analysis.ipynb
│   ├── 03_profit_analysis.ipynb
│   └── 04_scenario_modeling.ipynb
│
├── 🗄️ SQL VALIDATION
│   ├── queries/01_baseline_profitability.sql
│   ├── queries/02_discount_impact.sql
│   ├── queries/03_regional_analysis.sql
│   └── queries/04_scenario_validation.sql
│
├── 📈 TABLEAU VISUALIZATION
│   ├── tableau/margin_leakage_dashboard.twbx
│   └── tableau/executive_summary.pdf (screenshot)
│
├── 📋 DOCUMENTATION
│   ├── README.md (this file)
│   └── METHODOLOGY.md (detailed explanation)
│
└── 📊 DATA
    ├── sample_superstore_processed.csv
    └── data/raw_sample_superstore.csv (if applicable)
```

---

## Business Impact & Recommendations

### Financial Opportunity
- **Current loss to discounting:** $566K annually
- **Recoverable through discount optimization:** ~$227K (estimated)
- **Risk:** Potential volume loss if discounts eliminated too aggressively

### Recommended Actions
1. **Eliminate discounts on Binders and Machines** — These are structural weak points
2. **Cap all discounts at 15%** — Stay below the 20% breaking point
3. **Align Central region strategy with West** — Reduce from 24% to 11% avg discount
4. **Protect Copiers from discounting pressure** — Only product with strong baseline

*Full financial modeling in 04_scenario_modeling.ipynb*


## Questions This Project Answers

- ✅ How much money is being lost to discounting?
- ✅ Do discounts actually move volume?
- ✅ What's the breaking point for discount profitability?
- ✅ Which products can absorb discounts, and which can't?
- ✅ Is the problem uniform across the business, or concentrated?
- ✅ Is it a discount problem or a structural problem?
- ✅ How much could we recover by changing discount strategy?
- ✅ Which region/product/segment should we focus on first?

---

## How to Run This Analysis

### Prerequisites
- Python 3.11+ (Pandas, NumPy, SciPy, Matplotlib, Seaborn)
- SQL database 
- Tableau Public or Tableau Desktop

### Steps
1. Clone the repo: `git clone https://github.com/florgalarza/margin-leakage-analysis.git`
2. Run Python notebooks in order (01 → 02 → 03 → 04)
3. Use SQL queries to validate findings in your database
4. Import data into Tableau and build dashboards

### No Setup Required for Review
All notebooks include complete outputs. You can view findings without running code.

---

## Data Source

**Dataset:** Superstore Sales (Kaggle) https://www.kaggle.com/datasets/vivek468/superstore-dataset-final
- **Coverage:** 2014-2017, ~10,000 transactions
- **Geography:** 4 US regions
- **Segments:** Consumer, Corporate, Home Office
- **Products:** 17 sub-categories across 3 main categories
- **Educational use:** Sample data for methodology demonstration

---

## What Makes This Project Different

Most margin analysis stops at "we're losing money." This project asks **why** and **what would change.**

- **Doesn't assume causation** — We show correlation, not fake theory
- **Focuses on actionable insights** — Not just "here's a cool chart"
- **Demonstrates full data workflow** — Python for discovery, SQL for validation, Tableau for communication
- **Business-focused** — Every finding connects to a decision
- **Quantified in dollars** — Not just percentages

---

## License

MIT License - See LICENSE file for details

---

## Next Steps / Future Work

- Add predictive modeling (forecasting impact of discount changes)
- Incorporate customer segmentation (are certain customer types more elastic?)
- A/B testing framework (test discount changes by region/product)
- Real-time monitoring dashboard (track discount strategy effectiveness)

---

## Contact & Questions

For questions about methodology, findings, or code:
- Review the individual notebooks (detailed comments throughout)
- Check the SQL queries (optimized and commented)
- Refer to Tableau dashboard for visual explanation

---

**This project demonstrates that data analysis isn't just about finding patterns—it's about understanding business impact and making decisions with confidence.**
