# Margin Leakage Analysis: Where Does Profitability Disappear?

## The Real Problem

You ever look at a retail operation and see: "Our products have 75% margin" but the actual profit is half that? That gap isn't an accounting mystery. It's leakage. Discounts that seemed small add up. Shipping costs more than expected. Some product categories kill margins silently.
This project investigates where exactly that leakage happens—not with guesses, but with actual numbers. I looked at a real retailer's data and asked: if we're losing 30% of our potential margin, which 5 decisions are eating it? And what would change if we fixed the top 3?
The point isn't just analysis. It's showing how to think about profitability like someone who runs the business, not just analyzes spreadsheets.

---

## What I actually looked for

**The core questions:**

1. **Where is the money going?** Break down the gap between what we should make and what we actually make. Assign a dollar amount to each leak.
2. **Are discounts worth it?** If we discount 15%, do we actually sell 15% more volume? Or are we just giving away margin to customers who'd buy anyway?
3. **Is faster shipping worth the cost?** Same-Day shipping sounds premium, but does it make us money or just cost more?
4. **Which customer types are actually profitable?** Some segments might look good by volume but destroy margin once you factor in discounts and logistics.
5. **What's worth changing?** If we fixed the biggest leak, what would we gain? What would we lose?

## How I Measured It

**The Math**
**What we should make** (if we sold everything at list price)**:**
-Take list price, subtract what it costs to make it, divide by list price
-This is theoretical margin

**What we actually make:**
-Take actual profit, divide by actual sales
-This is realized margin

**The gap** = leakage. Now break it down:
**1. Discounting leakage**
-Add up all the discounts we gave. How much did we leave on the table?
-If we discount 20% but only get 3% more volume, that's bad math

**2. Shipping leakage (as a proxy)**
-Compare profit margins for Same-Day vs Standard shipping
-Important note: We can't prove Same-Day causes lower margins. Premium customers might just self-select Same-Day. But we can see the correlation.

**3. Product mix leakage**
-Some categories have high volume but negative margins
-Some have great margins but low volume
-The mix you actually sell might destroy profitability

**4. Customer segment leakage**
-Do some customer types (Consumer, Corporate, Home Office) have systematically lower margins after accounting for discounts?
-Are we subsidizing unprofitable segments?

**5. Everything else**
-Returned items, pricing errors, operational waste—stuff that doesn't fit neatly above

## The Investigation
Questions I'll Answer:

**1. What's the leakage breakdown?**
-In dollars and percentage, how much does each factor cost us?
-If discounting costs us $500k, that matters. If it's $50k, it's noise.

**2. On discounts specifically:**
-Which product categories get heavy discounts?
-When we discount, do we actually move volume? How much?
-Are there categories where we could raise prices and still sell everything?

**3. On shipping:**
-What's the actual profit margin for Same-Day vs Standard?
-Do Same-Day customers just happen to be higher-margin (selection effect) or does offering Same-Day actually hurt us?

**4. On customer segments:**
-Which segment is most profitable after we account for all costs?
-Any segments that are outright unprofitable and should maybe be exited?

**5. On recovery:**
-If we reduced the biggest leak by 20%, what happens to profit?
-What would it cost us in volume?
-Is it worth it?

## The Data
Source: Superstore Sales dataset from Kaggle
Link: https://www.kaggle.com/datasets/rohitsahoo/sales-forecasting
What's in it:

~10,000 transactions from a US retailer
Years 2014-2017
4 regions, 3 customer segments, 17 product subcategories
Fields include: sales amount, quantity, discount %, actual profit, shipping method, and more

Important: This is a teaching dataset (Tableau public). The goal is to show the method, not make real business recommendations. But the method is real—this is how you'd investigate margin issues at any company.

## What You'll Get (What I Built)

**1. Baseline Analysis**
-What does the margin look like overall? By category? By segment?
-Where do we see profit, and where do we see losses?
-Quick snapshot of which products/regions/customers are the problem children

**2. The Leakage Breakdown**
-A clear waterfall: "Here's our theoretical margin, here's our real margin, here's what ate the difference"
-Heatmap showing leakage by category and segment
-Dollar impact of each leak source

**3. Deep Dive on Discounts**
-Which categories get discounted most?
-Do discounts correlate with higher volume? (not proof of causation, but useful signal)
-Where is discounting clearly irrational?

**4. Shipping Economics**
-Margin by shipping method
-Who picks what, and do they correlate with profitability?
-Honest assessment of what we can and can't conclude

**5. Customer Segment P&L**
-Profit per transaction by segment
-Average discount given to each segment
-How much volume each segment drives

**6. Scenarios**
-"What if we cut discounts by 5%? What profit would we gain?"
-"What volume would we have to lose to make that worth it?"
-Trade-off analysis in real dollars


## What This ISN'T

We're not claiming causation where we don't have it. If Same-Day shipping looks unprofitable, that might be because premium customers pick Same-Day, not because Same-Day actually costs us money. I'll flag that.
We're not including costs we can't measure. No overhead allocation, no customer acquisition cost, no retained earnings analysis. This is transaction-level profit only.
We're not predicting the future. This is history. We can't say "if you implement this, profit will go up 20%." We can say "in past data, this pattern cost us X."
We're not accounting for loyalty. A cheap discount that brings back a repeat customer is worth more than the transaction shows. But we can't measure repeat rates here.
We're not saying all unprofitable segments should die. Sometimes you keep a low-margin business unit for strategic reasons. But you should know you're doing it, and know the cost.

## How I Built It

SQL: Extracted data, calculated margins, built aggregations
Python: Cleaned data, ran statistical analysis, built visualizations
Tools: Pandas, NumPy, Matplotlib, Seaborn
Version Control: Everything on GitHub so you can see the work

