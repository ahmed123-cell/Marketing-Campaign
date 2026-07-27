# Marketing Campaign Effectiveness – A/B Testing & Analysis 🚀

## Project Overview

This project analyzes a real email marketing A/B test to answer a critical business question:

> **Did the email campaign actually drive more conversions, or was the observed difference due to chance or bias?**

We follow a structured analytical approach covering:

- Exploratory Data Analysis (EDA)
- Randomization / Balance checks
- Conversion Rate & Visit Rate analysis
- Revenue analysis
- Statistical Hypothesis Testing
- Bias & Confounding analysis

---

## Dataset

**Name:** Kevin Hillstrom – MineThatData Email Marketing Challenge  
**Source:** [Original Dataset](http://www.minethatdata.com/Kevin_Hillstrom_MineThatData_E-MailAnalytics_DataMiningChallenge_2008.03.20.csv)

### Description 

The dataset contains **64,000 customers** who made a purchase within the previous 12 months. Customers were randomly assigned to one of three groups:

| Group              | Description                          |
|--------------------|--------------------------------------|
| Mens E-Mail        | Received an email featuring men's products |
| Womens E-Mail      | Received an email featuring women's products |
| No E-Mail          | Control group (received nothing)     |

After the campaign, customer behavior was tracked for two weeks.

### Key Columns

| Column            | Description                                      |
|-------------------|--------------------------------------------------|
| `recency`         | Months since last purchase                       |
| `history`         | Total dollars spent in the past year             |
| `history_segment` | Binned version of history                        |
| `mens`            | 1 if customer bought men's products before       |
| `womens`          | 1 if customer bought women's products before     |
| `zip_code`        | Urban / Suburban / Rural                         |
| `newbie`          | 1 if new customer in the past 12 months          |
| `channel`         | Purchase channel (Phone, Web, Multichannel)      |
| `segment`         | Treatment group (Mens E-Mail / Womens E-Mail / No E-Mail) |
| `visit`           | 1 if customer visited the website                |
| `conversion`      | 1 if customer made a purchase                    |
| `spend`           | Amount spent during the 2-week period            |

---

## Analysis Roadmap

### 1. Exploratory Data Analysis (EDA)
- Distribution of treatment groups
- Summary statistics of key features
- Conversion and Visit rates overview

### 2. Randomization Check (Balance Analysis)
We verify whether the treatment was properly randomized by comparing feature distributions across groups using:
- Chi-Square tests (for categorical features)
- ANOVA / Kruskal-Wallis tests (for numerical features)

### 3. Conversion Rate Analysis
Calculate conversion rate for each treatment group and measure the absolute and relative lift compared to the control group.

### 4. Visit Rate Analysis
Measure website visit rates to understand if the email increased traffic even when it did not convert into purchases.

### 5. Revenue Analysis
- Mean Spend
- Median Spend
- Total Revenue  
(both overall and among converters only)

### 6. Statistical Hypothesis Testing
- Two-Proportion Z-Test (pairwise comparison of conversion rates)
- Chi-Square Test (overall association between treatment and conversion)

### 7. Bias & Confounding Analysis
Build a Logistic Regression model:
Conversion ~ Treatment + History + Recency + Newbie + Channel + Zip Code


If the treatment coefficient remains statistically significant after controlling for other variables, we gain stronger evidence that the email caused the increase in conversions.

### 8. Heterogeneous Treatment Effect (HTE)
Investigate whether the email effect differs across customer segments (e.g., High History vs Low History customers). This step is crucial before building formal Uplift models.

---

## Key Questions Answered

- Was the randomization successful?
- Did the email campaigns significantly increase conversion rates?
- Did the campaigns increase website visits?
- Did higher conversion come with higher (or lower) average revenue?
- Is the treatment effect consistent across different customer segments?

---

## Conclusion

This project demonstrates a complete, industry-standard approach to evaluating marketing campaign effectiveness — moving from basic A/B testing all the way to understanding heterogeneous treatment effects and uplift modeling.