# Store Sales

## Competition Info

- competition link: https://www.kaggle.com/c/store-sales-time-series-forecasting

- actual time series competition
    - predicting 15 days of sales, per store / family category
    - given historical data for 3 years

- tried to fully submit by ourselves before looking at discussions / notebooks

## Own Findings

1. EDA
- decent eda, but missed many key ideas
- found that
    - weekday is very important (effects differ per family)
    - day of month important (15th and 31st higher due to paydays)
    - certain families spike at certain times of year

2. Modelling
- many rolling features
    - lagged sales per family/store combo
    - rolling sales per family/store combo
    - day of the week rolling
    - ratios to account for day of week, day of month effects
    - basic is-holiday column

3. Modelling technique - per 7d, 14d, 21d
- different models for predicting the first 7d, and each subsequent 7d

## What did we miss

1. Actually looking at the data

- seeing which values are missing
    - christmas missing
    - certain store/family combos completely missing

2. Leading and trailing zeros (big)
    - certain family/store combos ended with all zeros (category completely removed)
    - we were guessing this wrong (not completed zerod out)
    - leading zeros less relevant - just for data preprocessing

3. Holidays
- holidays had similar names, but for different regions (ex. independence day for each region)
    - preprocess to make the names the same
- merge in isHoliday by REGION (city, state, etc.) with stores, not just setting all stores to have a holiday based on date

Sources
- Our ideas were largely based on https://www.kaggle.com/code/chongzhenjie/ecuador-store-sales-global-forecasting-lightgbm (data exploration section)
- Many solutions seemed to use Darts for feature engineering + modelling, we struggled to replicate


## Final Models

We ended up doing basic LGBM on some simple rolling features
- trailing zeros helped
- not much advanced FE or thoughts