## Causal Inference Project Summary

### 1. **Career 2030 Training Program Evaluation**

**Objective**:  
Analyze the impact of ACME Manufacturing's **Career 2030** training program on employee promotion and retention.

**Methodology**:  
- **One-to-One Matching**: Matched treated and control employees based on covariates. Resulted in a treatment effect of **1.63** (p-value < 0.001) but suffered from imbalance in covariates like `disthome` and `testscore`.
- **Propensity Score Matching (PSM)**: Used propensity scores to balance treated and control groups. Produced a treatment effect of **2.43** (p-value < 0.001) but showed a broad distribution of propensity scores, indicating potential bias.
- **Inverse Probability of Treatment Weighting (IPTW)**: Weighted observations based on treatment probability. The treatment effect was **1.36** (p-value < 0.001), with some residual bias in covariates.
- **Instrumental Variable (IV)**: Utilized `disthome` as an instrumental variable. This method produced the most reliable estimate of **1.26** (p-value < 2.2e-16), given minimal assumption violations.

**Conclusion**:  
The **Career 2030 training program** had a statistically significant impact on employee promotions. The **IV method** was the most reliable for estimating the program's causal effect due to its robustness against confounding variables.

---

### 2. **Geo Matched Market Testing for Marketing Campaign**

**Objective**:  
Design a geo holdout experiment to evaluate the impact of a **Google Performance Max** marketing campaign across selected US markets.

**Methodology**:  
- **Market Selection**: A 4-week rolling window approach was used to identify a minimal, well-matched group of treatment markets from the given candidate markets.
- **R² and P-value Evaluation**: Multiple groups were tested using R² and p-values to ensure treatment and control groups were statistically well-matched.
- **Synthetic Control Method**: Applied to estimate the causal effect by constructing a synthetic control group that simulates the behavior of treated markets without the marketing campaign.
- **Population Causal Effect**: The results were extrapolated to estimate the overall impact of the campaign on national performance.

**Conclusion**:  
The **Google Performance Max campaign** demonstrated a positive causal impact on sales. The **synthetic control method** was instrumental in isolating the campaign's effect, and the findings support expanding the campaign to similar markets.

---

### Key Takeaways from Causal Inference Projects:
- **Causal inference methods**, such as **propensity score matching**, **inverse probability weighting**, and **instrumental variables**, can provide robust insights into the effectiveness of programs and campaigns.
- **Synthetic control methods** are effective for evaluating marketing impacts when randomized control trials are not feasible.
- Ensuring the **balance of treatment and control groups** through methods like R² and p-value checks is essential for reliable causal inference.
- Across both projects, the key to success was selecting the **right method** for addressing confounding and ensuring reliable, actionable insights.
