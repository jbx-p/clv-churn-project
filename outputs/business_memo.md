# Customer Value & Retention: Findings and Recommendations
**Olist E-Commerce Platform — Customer Analytics**

---

## Headline Finding

Customer value and customer loyalty are **two separate dimensions**, not one. Our highest-value customers (Platinum tier, R$442.8K in projected 12-month value) are *not* our most loyal — they earn their tier through large individual orders, not repeat behavior. Our most loyal customers (Bronze tier, 5.0% repeat-purchase rate — nearly 3x the platform average) are actually our lowest-spending segment. Treating "high value" and "high loyalty" as the same thing, as a standard CLV-based retention strategy would, misdirects spend toward customers who are already unlikely to leave in a meaningful behavioral sense, and away from the segment we could realistically grow.

## What We Did

We built a 12-month predictive CLV model (BG/NBD + Gamma-Gamma) across ~93,000 customers and a repeat-purchase prediction model using first-order signals (order value, product mix, payment method, delivery experience). The repeat-purchase model had limited standalone predictive power (ROC-AUC 0.54) — consistent with a marketplace where 97% of customers buy only once — but cross-tabulating predicted value against actual repeat behavior revealed the segmentation insight above, which the value model alone would have missed entirely.

## Segment Recommendations

| Tier | 12-Mo. Value | Repeat Rate | Read | Recommended Action |
|---|---|---|---|---|
| **Platinum** | R$442.8K (highest) | 3.4% | High-value, one-time-order-driven | Upsell/bundle offers **at first purchase** -- this is when their value is created |
| **Bronze** | R$140.2K (lowest) | 5.0% (highest) | Low-value, most loyal | Loyalty incentives to raise **basket size** on repeat visits |
| **Gold** | R$258.6K | 1.8% (lowest) | Mid-value, low loyalty | Low priority -- standard automated engagement only |
| **Silver** | R$192.7K | 1.8% (lowest) | Mid-value, low loyalty | Low priority -- standard automated engagement only |

**Rationale for deprioritizing Gold/Silver:** they show neither the value concentration of Platinum nor the loyalty behavior of Bronze -- dedicated retention spend here has the weakest expected return of any segment.

## Secondary Finding: Delivery Delay

Customers whose first order arrived late repeat-purchased at a modestly lower rate than those whose order arrived early (2.4% vs. 3.2%, population-level). This is directionally consistent with a known delivery-experience effect on this platform, but the association did not hold consistently once cut by CLV tier (small sample sizes in some cells, e.g. n=93 for "Platinum + very late," produced unreliable swings). We do not recommend acting on this segment-level yet.

**Recommended next step:** run a controlled test (e.g., proactive delay-notification messaging or a delivery-guarantee offer for Platinum customers) to establish whether delivery experience causally affects repeat purchase, rather than relying on this correlational finding.

## Estimated Impact

The Platinum segment alone represents R$442.8K in projected 12-month value across 23,194 customers (24.8% of the base). Shifting even a modest share of typically "value-tier" retention spend toward first-purchase upsell mechanics for this group -- rather than post-purchase retention offers this segment is statistically unlikely to need -- is the highest-leverage, lowest-risk change available from this analysis.

---
*Methodology, code, and full model diagnostics available in the accompanying GitHub repository.*
*Interactive dashboard: https://public.tableau.com/views/CustomerCLVLoyaltyDashboard/Dashboard1*