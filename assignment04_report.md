# Assignment 04 Interpretation Memo

**Student Name:** [Your Name]
**Date:** [Submission Date]
**Assignment:** REIT Annual Returns and Predictors (Simple Linear Regression)

---

## 1. Regression Overview

You estimated **three** simple OLS regressions of REIT *annual* returns on different predictors:

| Model | Y Variable | X Variable | Interpretation Focus |
|-------|------------|------------|----------------------|
| 1 | ret (annual) | div12m_me | Dividend yield |
| 2 | ret (annual) | prime_rate | Interest rate sensitivity |
| 3 | ret (annual) | ffo_at_reit | FFO to assets (fundamental performance) |

For each model, summarize the key results in the sections below.
Model	Y Variable	X Variable	Interpretation Focus	Key Result
1	ret (annual)	div12m_me	Dividend yield	Negative slope (−0.0687), significant at 5%, but very low R² (0.002); higher dividend yield associated with slightly lower returns.
2	ret (annual)	prime_rate	Interest rate sensitivity	Negative slope (−0.914), highly significant, R² = 0.016; higher interest rates reduce REIT returns.
3	ret (annual)	ffo_at_reit	FFO to assets (fundamental performance)	Positive slope (0.5770), not significant, R² ≈ 0; more profitable REITs do not show higher returns in this sample.
---

## 2. Coefficient Comparison (All Three Regressions)

**Model 1: ret ~ div12m_me**
- Intercept (β₀): [0.1082] (SE: [0.006], p-value: [0.000])
- Slope (β₁): [-0.0687] (SE: [0.032], p-value: [0.035])
- R²: [0.002] | N: [2527]

**Model 2: ret ~ prime_rate**
- Intercept (β₀): [0.1998] (SE: [0.016], p-value: [0.000])
- Slope (β₁): [-0.0914] (SE: [0.003], p-value: [0.000])
- R²: [0.016] | N: [2527]

**Model 3: ret ~ ffo_at_reit**
- Intercept (β₀): [0.0973] (SE: [0.009], p-value: [0.000])
- Slope (β₁): [0.5770] (SE: [0.567], p-value: [0.309])
- R²: [0.000] | N: [2518]

*Note: Model 3 may have fewer observations if ffo_at_reit has missing values; statsmodels drops those rows.*

---

## 3. Slope Interpretation (Economic Units)

**Dividend Yield (div12m_me):**
- A 1 percentage point increase in dividend yield (12-month dividends / market equity) is associated with a [-0.0687] change in annual return.
- [Your interpretation: Is higher dividend yield associated with higher or lower returns? Why might this be?] Higher dividend yields are associated with slighlty lower returns in this sample.This could be because REITs with high dividend yields may be riskier, or the market prices in high yields as a signal of slower growth.

**Prime Loan Rate (prime_rate):**
- A 1 percentage point increase in the year-end prime rate is associated with a [-0.914] change in annual return.
- [Your interpretation: Does the evidence suggest REIT returns are sensitive to interest rates? In which direction?] Higher interest rates are associated with lower REIT returns. This makes sense because rising rates increase borrowing costs for REITs and make their dividend yields less attractive compared to other interest-bearing assets.

**FFO to Assets (ffo_at_reit):**
- A 1 unit increase in FFO/Assets (fundamental performance) is associated with a [0.5770] change in annual return.
- [Your interpretation: Do more profitable REITs (higher FFO/Assets) earn higher returns?] More profitable REITs (higher FFO/Assets) tend to earn higher returns, reflecting that better fundamental performance is rewarded by the market.

---

## 4. Statistical Significance

For each slope, at the 5% significance level:
- **div12m_me:** [Significsant] — [Dividend yield has a statistically significant negative relationship with REIT returns, though the effect is very small.]
- **prime_rate:** [Significant] — [The prime loan rate has a statistically significant negative relationship with REIT returns, indicating interest rates matter for REIT performance.]
- **ffo_at_reit:** [Not significant] — [FFO/Assets does not have a statistically significant effect on REIT returns in this sample.]

**Which predictor has the strongest statistical evidence of a relationship with annual returns?** [prime_rate, because it has the lowest p-value (0.000) and explains more variation in returns (R² = 0.016) than the other predictors.]

---

## 5. Model Fit (R-squared)

Compare R² across the three models: Model 1 (div12m_me): R² = 0.002 → Explains only 0.2% of the variation in REIT returns.
Model 2 (prime_rate): R² = 0.016 → Explains 1.6% of the variation, the highest among the three.
Model 3 (ffo_at_reit): R² = 0.000 → Explains essentially 0% of the variation.
- [Your interpretation: Prime loan rate explains the most variation in annual returns, but even its R² is very low. In general, all three R² values are extremely low, suggesting that dividend yield, interest rates, and FFO/Assets alone do not explain much of REIT returns. This implies that other factors—like market sentiment, leverage, property type, or macroeconomic conditions—likely drive REIT returns more strongly.]

---

## 6. Omitted Variables

By using only one predictor at a time, we might be omitting:
- [Leverage]: [Highly leveraged REITs may be more sensitive to interest rates and risk, affecting returns.]
- [Property Type]: [Different property types have different growth prospects and market risk exposures, which influence returns.]
- [Market sentimental/macroeconomic facotes]: [Broad economic conditions affect REIT cash flows and investor demand, impacting returns.]

**Potential bias:** If omitted variables are correlated with both the X variable and ret, our slope estimates may be biased. [If omitted variables are correlated with both the predictor (X) and REIT returns, our slope estimates may be biased.
For example, if highly leveraged REITs also tend to have high dividend yields, omitting leverage could overstate the negative effect of dividend yield on returns.]

---

## 7. Summary and Next Steps

**Key Takeaway:**
[Among the three single-predictor models, prime loan rate shows the strongest statistical relationship with REIT returns, consistent with the theory that higher interest rates reduce REIT performance. Dividend yield has a statistically significant but very small negative effect, while FFO/Assets is not significant. Overall, single-variable models explain very little variation in REIT returns, indicating that other factors are important.]

**What we would do next:**
- Extend to multiple regression (include two or more predictors)
- Test for heteroskedasticity and other OLS assumption violations
- Examine whether relationships vary by time period or REIT sector

---

## Reproducibility Checklist
- [ ] Script runs end-to-end without errors
- [ ] Regression output saved to `Results/regression_div12m_me.txt`, `regression_prime_rate.txt`, `regression_ffo_at_reit.txt`
- [ ] Scatter plots saved to `Results/scatter_div12m_me.png`, `scatter_prime_rate.png`, `scatter_ffo_at_reit.png`
- [ ] Report accurately reflects regression results
- [ ] All interpretations are in economic units (not just statistical jargon)
