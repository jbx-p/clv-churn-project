# Customer CLV & Repeat-Purchase Analysis

Predicts 12-month customer lifetime value (BG/NBD + Gamma-Gamma) and first-purchase
repeat-buy probability on the Olist Brazilian E-Commerce dataset (93K+ customers),
revealing that customer *value* and customer *loyalty* are two distinct dimensions --
and translating that into a segmented business recommendation.

**Note on framing:** an initial churn-prediction approach was abandoned after
diagnosing that "days since last purchase" is confounded with customer tenure in a
mostly one-time-buyer marketplace (97% of customers). The project pivoted to
predicting repeat purchase from first-order signals instead -- see `outputs/business_memo.md`
for the full writeup, including two data leakage issues caught and corrected during development.

## Key results
- Repeat-purchase model: ROC-AUC 0.54 (XGBoost), delivery delay as strongest signal
- Found CLV tier and repeat-purchase rate are *inversely* related in the highest tier --
  Platinum customers are high-value but not more loyal; Bronze customers repeat-purchase
  nearly 3x more often despite lowest average value
- Segmented recommendation: upsell at first purchase for Platinum, basket-size incentives for Bronze

## Dataset
Download from Kaggle: https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce
Place the CSVs in `data/raw/` (not included in this repo due to license terms).

## Setup

## Structure
- `notebooks/01_data_cleaning` -- merge, clean, build transaction table
- `notebooks/02_rfm_and_clv` -- RFM features, predictive CLV (BG/NBD + Gamma-Gamma)
- `notebooks/03_repeat_purchase_model` -- repeat-purchase prediction, leakage fixes
- `notebooks/04_business_translation` -- segment analysis and findings
- `outputs/business_memo.md` -- 1-page business writeup