## Project Summary: ACME Manufacturing - Career 2030 Training Program Evaluation

### Background
ACME Manufacturing, a large company with over 60,000 employees, introduced the **Career 2030** training program to enhance employee development. Initial data from a randomized cohort of employees who participated in the program a year ago has recently become available. The Chief People Officer of ACME has asked for an analysis of this dataset to understand the program's impact on **employee promotion** and **retention**.

### Problem
The goal of this proof-of-concept analysis is to demonstrate our group's competence in using **causal inference** techniques to monitor and evaluate employee programs. Despite the randomized nature of the trial, various external factors, such as manager interventions and employee motivation, may have influenced participation. These factors make it necessary to adjust for **confounding variables** when estimating the true causal effect of the training program on employee outcomes.

### Dataset Overview
The dataset contains **6,000 employee records**, with the following attributes:
- `empid`: Employee ID
- `promoted`: Whether the employee was promoted within a year
- `training`: Participation in the Career 2030 program
- `manager`: Employee's managerial status
- `raise`: Merit increase in the last review cycle
- `salary`: Salary bracket
- `children`: Number of children
- `mstatus`: Marital status
- `age`: Age at promotion
- `sex`: Gender
- `edu`: Years of education at promotion
- `vacation`: Vacation days prior to promotion
- `weight`, `height`: Physical attributes from the last exam
- `hrfriend`, `cxofriend`: Friends in HR or C-level roles
- `insurance`: Type of insurance
- `flexspend`: Flexible Spending Account program participation
- `retcont`: 401k retirement saving participation
- `race`: Race
- `disthome`: Distance from home to training facility
- `testscore`: Recruitment test score

### Causal Inference Methods Used
Given the presence of confounding factors, we applied multiple **causal inference** techniques to estimate the true effect of the training program:

1. **One-to-One Matching**: 
   - This method matches treated and control employees one-to-one based on observed covariates. It aims to reduce bias due to differences between treated and control groups.
   - **Result**: The treatment effect estimate was **1.63** with a p-value < 0.001, indicating statistical significance but potentially biased due to high imbalance in covariates such as `disthome` and `testscore`.

2. **Propensity Score Matching (PSM)**:
   - PSM matches individuals based on the likelihood of receiving treatment (i.e., participation in the training program) given observed covariates. It attempts to balance the treated and control groups.
   - **Result**: The estimated treatment effect was **2.43**, with a p-value < 0.001. Despite the significance, there was a broad distribution of the propensity scores, leading to potential imbalance.

3. **Inverse Probability of Treatment Weighting (IPTW)**:
   - IPTW weights observations based on the inverse probability of receiving the treatment, addressing confounding bias and improving causal inference.
   - **Result**: The estimated treatment effect was **1.36** with a p-value < 0.001. The standard mean difference (SMD) for `disthome` remained high, indicating residual bias.

4. **Instrumental Variable (IV)**:
   - This approach used an instrumental variable (`disthome`) to estimate causal effects in the presence of unobserved confounding. It assumes that the instrument affects training participation but not the promotion outcome directly.
   - **Result**: The estimated treatment effect was **1.26** with a p-value < 2.2e-16. Given the minimal violations of assumptions, the IV method was the most reliable in estimating the causal effect.

### Results and Insights
- **All models** demonstrated statistically significant treatment effects, with the **Instrumental Variable (IV) method** yielding the most reliable results due to its robustness to confounding.
- **One-to-one matching** and **IPTW** showed higher bias due to imbalanced covariates such as `disthome` and `testscore`.
- **Propensity Score Matching** produced a significant result but exhibited a wide distribution of propensity scores, raising concerns about imbalance.
- **Instrumental Variable Analysis** resulted in a lower effect estimate but was considered the most reliable method due to the consistency of the results and robustness to confounding.

### Conclusion and Recommendations
Based on the analysis, the **Career 2030 training program** has a positive and statistically significant effect on employee promotions. However, to further optimize the program:
- Consider **stratified interventions** for employees based on geographical proximity (`disthome`) and manager involvement, as these were key factors influencing participation.
- Future data collection should address potential biases introduced by employee motivations and manager interventions by documenting these factors explicitly.

