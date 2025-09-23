# gpa-quantile-modeling
Quantile regression analysis of student GPA performance across demographic, academic, and family features. Demonstrates OLS vs Quantile Regression inference and distributional heterogeneity.

## 📌 Project Overview
This project applies **quantile regression** to analyze high school student performance (GPA) using demographic, academic, and family background features. The motivation is to understand **which student characteristics most strongly influence GPA**—and how those effects differ across the **low (10%), middle (50%), and high (90%) quantiles** of the GPA distribution.  

Unlike OLS, which models only the mean, quantile regression reveals **distributional heterogeneity**, making it more robust in the presence of skewed GPA data and heteroskedastic residuals.

---

## 🎯 Research Question
> *Which student features (sex, age, study habits, attendance, family background, support programs, prior failures, etc.) are most significant to GPA performance, and how do these associations differ across the lower (10%), middle (50%), and upper (90%) parts of the GPA distribution?*

---

## 📊 Dataset
- **Source:** Portuguese secondary school dataset (649 students, 33 features)  
- **Structure:**  
  - 16 numerical variables (e.g., study time, prior failures, absences, parental education)  
  - 17 categorical variables (e.g., school attended, gender, support programs, guardian)  

A subset of variables used in this analysis:
- **Studytime** – Weekly study hours  
- **Failures** – Number of prior class failures  
- **Absences** – Number of school absences  
- **School** – Attended school (Gabriel Pereira or Mousinho da Silveira)  
- **Sex** – Student gender  
- **Schoolsup** – Extra educational support (yes/no)  
- **Higher** – Aspiration for higher education (yes/no)  
- **Fedu** – Father’s education level  

---

## 🧮 Methodology
1. **Exploratory Data Analysis (EDA)**
   - Identified skewed GPA distribution and weak-to-moderate correlations.
   - Detected OLS assumption violations (heteroskedasticity, non-normal residuals).

2. **OLS Baseline Model**
   - Estimated coefficients using `lm()` in R.  
   - Found important factors: study time, failures, absences, sex, school attended.  
   - Diagnostics: residuals non-normal, variance not constant → inference unreliable.

3. **Quantile Regression (QR)**
   - Estimated conditional quantiles at **τ = 0.10, 0.50, 0.90** using `rq()` from the **quantreg** package.  
   - Bootstrapped standard errors (R = 1000) for robustness against ties and non-uniqueness in the GPA values.  
   - Compared coefficient paths across quantiles.

---

## 🔑 Key Findings
- **Consistent Factors Across Quantiles:**
  - **Failures** strongly negative at all levels (largest single determinant).
  - **School support (schoolsup)** negatively associated, likely due to selection bias.
- **Bottom 10% (at-risk students):**
  - Strong penalty for attending Mousinho da Silveira (−0.46).  
  - Male students perform worse (−0.17).  
  - Higher education aspiration is protective (+0.31).  
- **Median (50%):**
  - Studytime becomes significant (+0.06 per level).  
  - Absences reduce GPA (−0.012 per absence).  
- **Top 10% (high achievers):**
  - Studytime has the largest effect (+0.10).  
  - Absences continue to reduce GPA (−0.013).  
  - Higher education aspiration remains strongly positive (+0.37).  
  - Gender gap disappears at the top.  

**Takeaway:**  
- **Low performers** are most affected by **school context and past failures**.  
- **Median performers** are sensitive to **attendance and moderate study effort**.  
- **Top performers** are distinguished by **intensive studytime and higher aspirations**.  

---

## 📂 Repository Contents
- `QR_4.pdf` — Full project report (with figures, derivations, and results).  
- `scripts/` — R scripts for OLS, QR models, and diagnostics.  
- `figures/` — Plots (residual density, Q-Q plot, coefficient paths).  
- `data/` — Dataset (if allowed to share; otherwise include retrieval instructions).  

---

## 🛠️ Tools & Skills Demonstrated
- **Statistical Modeling:** OLS, Quantile Regression, Diagnostics.  
- **Mathematical Foundations:** Loss functions, linear programming form of QR, heteroskedasticity handling.  
- **Software:** R (`quantreg`, `ggplot2`), LaTeX/R Markdown.  
- **Communication:** Structured technical writing with interpretation of results.  

---

## 🎓 Relevance to Graduate Study
This project demonstrates my ability to:
- Move beyond classical regression to **distribution-aware modeling**.  
- Apply **advanced statistical inference techniques** in real-world data contexts.  
- Use quantitative reasoning to identify **risk vs. success factors** in educational outcomes.  

These skills directly align with my goals for advanced study in **statistics, computational data science, and quantitative finance**, where robust inference under non-ideal data conditions is critical.

---

## 📎 References
- Koenker, R., & Bassett, G. (1978). *Regression Quantiles*. Econometrica, 46(1), 33–50.  
- R Package: `quantreg` by Roger Koenker.  

---

