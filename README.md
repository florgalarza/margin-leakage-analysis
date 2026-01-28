# Margin Leakage Analysis

This is a business problem with a data-driven solution. The analysis shows exactly what to change and what the impact will be.

A retail business reports 12.5% profit margin—healthy on paper. But 18.7% of orders lose money, and $566K in revenue disappears to aggressive discounting. This project identifies exactly where the money is leaking and what to do about it.

## The Problem

- 18.7% of orders are unprofitable
- $566K lost to discounting strategy
- Discounting is backwards by region: weak regions get heavy discounts, strong regions get light discounts
- Example: Central region gets 24% average discount but only $17/order profit. West gets 11% discount and $33.85/order profit.

## Key Findings

| Finding | What It Means |
|---------|--------------|
| Discounts don't drive volume (correlation: 0.009) | We're giving away margin without gaining sales |
| Discounts hurt profit (correlation: -0.219) | Clear relationship: more discount = less profit |
| Breaking point at 20% discount | Orders exceed 0% lose money on average |
| Only Copiers absorb discounts well | Everything else collapses beyond 15-20% discount |
| Damage concentrated in 3 products | Binders, Machines, Tables = 52% of total loss |

## The Bottom Line

Most of the problem is fixable. It's not structural weakness—it's backwards discount strategy. Estimated recoverable profit: ~$227K/year.

## Project Structure

**01_eda.ipynb** — Where's the problem? (establishes baseline, identifies losses)

**02_discount_analysis.ipynb** — How bad is it? (quantifies damage by product/region, finds breaking point)

**03_profit_analysis.ipynb** — Can we fix it? (distinguishes structural problems from discount problems)

**04_scenario_modeling.ipynb**  — What if we change strategy? (models profit recovery scenarios)

## Key Numbers

- **$2.3M** in total sales
- **$286K** in total profit (12.5% margin)
- **$566K** lost to discounting
- **$227K** estimated recoverable through strategy change
- **20%** = the discount threshold (beyond this, orders go negative)
- **0.009** = correlation between discount and volume (essentially zero)

## Recommendations

1. **Stop discounting Binders and Machines** — These products are structurally strong at full price. Discounting destroys them.
2. **Cap all discounts at 15%** — Stay below the 20% breaking point where profitability collapses.
3. **Align Central region with West** — Reduce Central's 24% average discount to match West's 11%.
4. **Protect Copiers** — Only product that can absorb aggressive discounts. Keep it that way.

## How to Use

Read the notebooks in order (01 → 02 → 03 → 04). Each one answers a specific question and builds on the previous findings. All analysis is complete—you don't need to run code to see results.

## Data

Superstore dataset (Kaggle): ~10,000 transactions from 2014-2017 across 4 US regions, 3 customer segments, 17 product categories.

---
