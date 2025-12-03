# ADA Final Project – Evaluating Labor Induction and Cesarean Delivery in Rural Ghana

## Project Description

This project is my final assignment for Advanced Data Analysis (ADA)
The goal is to evaluate whether induction of labor at term is associated with cesarean section (CS) among low-risk pregnancies in a rural Ghanaian hospital.

Using 2020 maternity records, I conducted a retrospective cross-sectional analysis of term singleton deliveries. The primary research question is whether induction of labor is associated with the odds of CS after adjusting for maternal age, gestational age at delivery, gravidity, and history of previous cesarean section. A secondary objective was to assess whether maternal age modifies the association between induction and CS (induction × age interaction).

The final logistic regression model includes induction, age, gestational age, gravidity, previous CS, and an interaction term between induction and age. Model diagnostics include variance inflation factors, the Hosmer–Lemeshow goodness-of-fit test, and checks of linearity in the logit using grouped proportions.



## Code Description (Survey / Analysis Code)

**File:** `ADAprojectfinal.Rmd`  
This R Markdown file contains the full, annotated analysis pipeline:

- Data import from `matdata.xlsx`
- Variable recoding (mode of delivery, induction, previous CS, presentation, sex, age, GA, gravidity, etc.)
- Construction of the complete-case analytic sample (n ≈ 254)
- Descriptive statistics and initial summaries
- Logistic regression model:
  - `mode_bin ~ induction * age + GA + gravidity + previousCS`
- Extraction of odds ratios and 95% confidence intervals
- Model diagnostics:
  - Variance inflation factors (VIF)
  - Hosmer–Lemeshow goodness-of-fit test
  - Linearity checks via grouped proportions
- Generation of a sample size flow diagram using `DiagrammeR`

The code is commented throughout to explain each step, following the “coding to share” principles from class (e.g., clear object names, sectioning, and inline comments for key transformations and models).

To run the code, you will need the following R packages:

- `tidyverse`
- `readxl`
- `broom`
- `car`
- `ResourceSelection`
- `DiagrammeR`

---

## Dataset Description

**File:** `matdata.xlsx`  

This Excel file contains de-identified maternity records from a rural healthcare facility in Ghana for the year 2020. Each row represents a single delivery. Key variables used in the analysis include:

- `mode` – Mode of delivery (1 = vaginal, 2 = cesarean); recoded to `mode` (Vaginal/CS) and `mode_bin` (0 = vaginal, 1 = CS).
- `induction` – Induction status (1 = induced, 2 = not induced, 3 = not stated). “Not stated” is treated as missing in the analysis.
- `previousCS` – History of previous cesarean section (1 = yes, 2 = no).
- `age` – Maternal age in years.
- `GA` – Gestational age at delivery in weeks.
- `gravidity` – Number of pregnancies.
- `sex` – Sex of infant (1 = male, 2 = female).
- `presentation` – Fetal presentation (1 = cephalic, 2 = breech).
- Additional demographic and clinical variables (education, occupation, hemoglobin, birth weight, and reason for CS).

The analytic dataset is restricted to records with non-missing values for mode of delivery, induction status, previous CS, age, gestational age, and gravidity.



