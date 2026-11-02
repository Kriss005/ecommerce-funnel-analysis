# E-commerce Funnel Analysis: Where Do We Lose Buyers?

Analysis of 10,000 users moving from browsing to purchase. Only **10%** complete a purchase, and the biggest loss happens at the final step, between checkout and payment.

**Tool:** Microsoft Excel (PivotTable, formulas, funnel chart)

---

## Business Question

At which stage of the shopping journey do users drop off, and where should the business focus to improve conversion?

---

## Dataset

Event-level user activity data. Each row is one user action within a session.

| Column | Description |
|---|---|
| User ID / Session ID | Identifies the user and the session |
| Event Time | Time of the action |
| Event | Browse, Add to Cart, Checkout, or Purchase |
| Device | Desktop, Mobile, or Tablet |
| Region | North, South, East, or West |
| Channel | Organic, Email, Google Ads, Social Media |
| Product Category | Electronics, Sports, Fashion, Beauty |
| Revenue | Order value (only on Purchase events) |

**Data notes:**
- The Event Time column holds time values without dates, so this analysis compares users by event type rather than by order over time.
- Replace this line with the data source (for example, "synthetic practice dataset" or a link to the original dataset).

![Raw data preview](screenshots/01_raw_data.png)

---

## Method

1. **Counted unique users at each funnel stage.** I built a PivotTable using a **Distinct Count of User ID** by Event, so a user who triggers the same event more than once is only counted once.
2. **Calculated two conversion metrics for each stage:**
   - **Step conversion** = users at this stage ÷ users at the previous stage
   - **Overall conversion** = users at this stage ÷ users who browsed
3. **Visualized the results** in a funnel chart to show where users are lost.

![Funnel analysis](screenshots/02_funnel_analysis.png)

---

## Results

| Stage | Users | Step Conversion | Overall Conversion |
|---|---:|---:|---:|
| Browse | 10,000 | n/a | 100% |
| Add to Cart | 6,949 | 69% | 69% |
| Checkout | 3,456 | 50% | 35% |
| Purchase | 1,004 | 29% | 10% |

---

## Key Insights

1. **Only 10% of users who browse go on to buy.** Out of 10,000 users, 1,004 completed a purchase.
2. **The biggest leak is between Checkout and Purchase.** 71% of users who reached checkout (2,452 people) did not complete the purchase. This is the weakest step in the funnel at 29% step conversion.
3. **Cart abandonment is also high.** Half of the users who added an item to their cart never started checkout, which is 3,493 users lost at this step.
4. **Browse to Cart is the healthiest step.** 69% of browsers add something to their cart, which suggests product interest is not the main problem. The problem appears after that.
5. **The late-funnel steps offer the most upside.** The users lost at Cart and Checkout have already shown strong buying intent, so improving those steps is likely to pay off more than driving new traffic.

---

## Recommendations to Test

This data shows **where** users drop off, not **why**. The ideas below are hypotheses to test, for example with A/B tests, rather than confirmed causes.

- **Simplify checkout.** Fewer form fields, guest checkout, and showing the total cost (shipping, fees) early may reduce last-step abandonment.
- **Add payment options and trust signals**, such as secure payment badges and a clear return policy.
- **Run cart recovery campaigns.** Reminder emails or notifications to users who added items but did not check out.
- **Measure the impact** of each change as a change in step conversion at that stage.

---

## Limitations and Next Steps

- This analysis looks at the overall funnel only. The dataset also includes Device, Region, Channel, and Product Category, so a natural next step is to break the funnel down by these fields to find which segments convert best and worst (for example, mobile vs desktop, or email vs paid ads).
- Revenue per user and average order value are not analyzed here and could be added.

---

## Files

- `README.md`: this report
- `screenshots/`: images of the raw data and funnel analysis
- Excel workbook: add your `.xlsx` file here so others can open the pivot and formulas
