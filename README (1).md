# MLR Analysis of Cereal Ratings

**Course:** STAT 481: Applied Regression | University of Illinois Chicago | Fall 2025  
**Author:** Bhavisha Ahuja

---

## Overview

Built a multiple linear regression model to predict Consumer Reports ratings for 76 breakfast cereals using nutritional data. Applied the full statistical modeling pipeline: descriptive analysis, assumption checking, multicollinearity testing, Box-Cox transformation exploration, and backward elimination variable selection.

**Key finding:** Just 3 variables — sodium, fiber, and sugars — explain 92%+ of the variance in cereal ratings. Higher fiber raises ratings; higher sugar and sodium lower them.

---

## Final Model

rating \= 61.08 − 0.0559(sodium) \+ 2.7525(fiber) − 2.1904(sugars)

Arrived at via backward elimination (α \= 0.10), removing weight → protein → vitamins → cups in sequence.

---

## Model Performance

| Model | R² | Notes |
| :---- | :---- | :---- |
| Full model (7 predictors) | \~0.93 | F \= 127.30, p \< 0.001 |
| **Final model (3 predictors)** | **\~0.92** | Simpler, equally interpretable |

The final model retains 92%+ of explanatory power with only 3 predictors — a meaningful reduction in complexity with no material loss in fit.

---

## Analysis Steps

**1\. Descriptive Statistics & EDA**

- Five-number summary, histograms, boxplots across all 7 predictors  
- Correlation matrix — rating strongly correlated with fiber (+), sugars (−), sodium (−)

**2\. Full Model Regression**

- Fit full MLR with 7 predictors  
- ANOVA table: F \= 127.30, p \< 0.001  
- Multicollinearity check: VIF values 1.2–2.0 (no concern)

**3\. Assumption Checks**

- Linearity & homoscedasticity: Residuals vs. fitted plot — no pattern; Breusch-Pagan p \= 0.246 ✅  
- Independence: Durbin-Watson \= 1.80 ✅  
- Normality: Shapiro-Wilk p \= 0.0003 — mild deviation; Box-Cox (λ \= −0.41) explored but didn't improve normality or change significant predictors; proceeded with original scale for interpretability

**4\. Variable Selection**

- Backward elimination at α \= 0.10  
- Removed: weight (x6), protein (x1), vitamins (x5), cups (x7)  
- Final model: sodium (x2), fiber (x3), sugars (x4)

**5\. Final Model Diagnostics**

- All assumptions (linearity, independence, constant variance) satisfied  
- Mild residual non-normality acknowledged but not corrected

---

## Dataset

77 breakfast cereals from Consumer Reports. 1 observation removed (missing values coded as −1), leaving 76 complete cases.

| Variable | Description |
| :---- | :---- |
| `protein` | Grams of protein per serving |
| `sodium` | Milligrams of sodium per serving |
| `fiber` | Grams of dietary fiber per serving |
| `sugars` | Grams of sugars per serving |
| `vitamins` | % of FDA recommended vitamins (0, 25, or 100\) |
| `weight` | Weight in ounces of one serving |
| `cups` | Number of cups in one serving |
| `rating` | Consumer Reports cereal rating (response) |

---

## Files

| File | Description |
| :---- | :---- |
| `CerealsRating.csv` | Dataset (CSV format) |
| `CerealsRating.xlsx` | Dataset (Excel format) |
| `Data_Analytics_Report.pdf` | Full statistical report with analysis, plots, and Python code appendix |

**Note:** Python code is included in the report appendix. No separate script file is available.

---

## Tech Stack

Python · pandas · NumPy · statsmodels · scipy · matplotlib · seaborn  
