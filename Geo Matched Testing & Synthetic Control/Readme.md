
## Project Summary: ACME Manufacturing - Geo Matched Market Testing

### Background
ACME Manufacturing, a direct seller of household goods across the US, is evaluating the effectiveness of its marketing campaigns. After the success of the Career 2030 Impact Project, ACME's Chief Marketing Officer (CMO) has asked your analytics consulting group to participate in a "bake-off" with five other vendors. Your task is to design a **geo holdout experiment** to assess the impact of a **Google Performance Max** marketing campaign over four weeks across selected US markets.

### Problem
The main goal is to demonstrate your capability to **analyze marketing data** and provide **actionable insights** for optimizing future campaigns. The dataset consists of **two years of weekly order data** across all 50 states and Washington, DC, with an expected order value of $200 and a gross profit margin of approximately 30%. The challenge is to design a **four-week experiment** to measure the marketing impact while ensuring that the selected treatment markets do not overlap with other ongoing marketing activities. The client has provided nine candidate treatment markets, but **these cannot be used as control markets**.

### Dataset Overview
The dataset contains **104 weeks of order data** across the 51 markets (50 US states + Washington, DC), with the following key characteristics:
- **Order Value**: $200
- **Gross Profit Margin**: 30%

### Causal Inference Methods Used

To design the experiment and estimate the causal effect of the marketing campaign, we implemented several techniques:

1. **Market Selection**:
   - We removed one state from the candidate markets to prevent potential data leakage.
   - We adopted a **4-week rolling window** approach to identify the smallest group of treatment markets that would be most suitable for testing the effect of the campaign.

2. **Model Fit with R² and P-value**:
   - We evaluated different combinations of treatment and control groups using **R²** (coefficient of determination) and **p-value** to ensure the final group selection minimized differences between treatment and control groups.
   - This ensured that the **control markets** were well-matched to the treatment markets in terms of order volume, trends, and other key metrics.

3. **Synthetic Control Method**:
   - Once the treatment group was identified, we applied the **Synthetic Control Method** to estimate the causal effect of the Google Performance Max campaign.
   - This method constructs a synthetic control group by weighting non-treatment markets to simulate what would have happened in the absence of the campaign in the treated markets. 

4. **Population-Level Causal Effect**:
   - The causal effect derived from the synthetic control method was extrapolated to calculate the **population-level causal effect**, providing insight into the overall impact of the marketing campaign on ACME's national performance.

### Results and Insights

- **Market Selection**: The rolling window approach identified a small, well-matched group of treatment markets from the provided candidates.
- **R² and P-value**: The final selection of treatment and control groups showed a high R² value and low p-value, indicating a good fit and statistical significance for matching purposes.
- **Causal Effect**: The synthetic control method revealed the **causal effect** of the Google Performance Max campaign, providing strong evidence of its effectiveness in increasing order volumes in the treatment markets.
- **Population Causal Effect**: Extrapolating the findings showed a positive impact of the campaign on national sales performance, offering actionable insights for scaling future campaigns.

### Conclusion and Recommendations
The **Google Performance Max marketing campaign** had a positive and measurable impact on order volumes in the selected treatment markets. Based on these findings, we recommend:
1. **Scaling the campaign** to additional markets based on the treatment results.
2. **Refining the targeting strategy** for future campaigns, focusing on markets with similar characteristics to the identified treatment group.
3. **Implementing geo holdout experiments** as a continuous evaluation mechanism for future marketing activities, ensuring that ongoing campaigns are evaluated rigorously for their impact on sales.
