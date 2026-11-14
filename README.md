# Phase 3 Clinical Trials: Industry vs Non-Industry Funding - Hypothesis Testing on Termination Rates and Trial Size

*Last updated: November 2026*

---

## Summary

This project tests two questions about Phase 3 clinical trials registered on ClinicalTrials.gov from 2010 onwards. First, whether Industry-funded trials have a different termination rate from non-Industry (Other) trials. Second, whether completed Industry-funded trials differ in average enrollment size from non-Industry trials.

Industry-funded Phase 3 trials had a lower termination rate than non-Industry trials (difference statistically significant, p < 0.001). Among completed trials, there was no statistically significant difference in average enrollment size (p = 0.221). The analysis is observational and cannot show what caused the difference in termination rates.

---

## Background

Phase 3 clinical trials are large-scale studies that test whether a medical intervention is safe and effective enough for regulatory approval. Termination of a Phase 3 trial can mean lost scientific opportunity and substantial financial cost for sponsors.

Funding source may influence trial design, recruitment, monitoring, and decisions to stop early. This project compares trials funded by industry with those funded by other sources (mainly academic, government, and non-profit organisations).

---

## Research Questions

1. Is there a statistically significant difference in the termination rate of Phase 3 trials between Industry-funded and non-Industry (Other) trials?
2. Among *completed* Phase 3 trials, is there a statistically significant difference in average enrollment size between Industry-funded and non-Industry trials?

---

## Dataset

| Item              | Detail                                      |
|-------------------|---------------------------------------------|
| Source            | ClinicalTrials.gov                          |
| Study phase       | Phase 3 only                                |
| Time period       | Start year ≥ 2010                           |
| Key variables     | Study Status, Funder Type, Enrollment       |
| Funder groups     | INDUSTRY vs OTHER                           |
| Sample (H1)       | All Phase 3 trials from 2010                |
| Sample (H2)       | Completed Phase 3 trials from 2010          |

---

## Methodology

1. **Data cleaning and filtering** in Python (pandas): restricted to Phase 3 trials with start year ≥ 2010 and Funder Type of either INDUSTRY or OTHER.
2. **Hypothesis 1 – Termination rates**  
   Compared the proportion of terminated trials between the two funder groups using a two-proportion test.
3. **Hypothesis 2 – Enrollment size**  
   Compared mean enrollment of *completed* trials between the two groups using Welch’s two-sample t-test (`equal_var=False`). Eleven missing enrollment values were dropped.
4. Significance level: α = 0.05.

---

## Results

### Hypothesis 1 – Termination Rate

| Group     | Result                          |
|-----------|---------------------------------|
| Industry  | 12.59          |
| Other     | 14.48         |
| p-value   |  0.0006                         |
| Decision  | Reject the null hypothesis      |

There is a statistically significant difference in termination rates. Industry-funded Phase 3 trials were less likely to be terminated.

### Hypothesis 2 – Enrollment Size (Completed Trials)

| Statistic     | Value     |
|---------------|-----------|
| t-statistic   | −1.22     |
| p-value       | 0.221     |
| Decision      | Fail to reject the null hypothesis |

There is not enough evidence to conclude that average enrollment size differs between Industry and non-Industry completed Phase 3 trials.

---

## What the results show

- Industry-funded Phase 3 trials had a meaningfully lower termination rate than non-Industry trials.
- Once a trial reached completion, average size (enrollment) did not differ significantly by funder type.
- The analysis is descriptive and comparative. It does not explain *why* Industry trials were less likely to be terminated.

---

## Conclusion

Phase 3 trials funded by industry showed a lower termination rate than those funded by other sources. Among trials that completed, average enrollment size was statistically indistinguishable between the two groups. The findings describe observed differences; they do not establish causation.

---

## Recommendations

- **Researchers:** Investigate possible reasons for the lower termination rate in Industry trials (e.g., different disease areas, adaptive designs, financial incentives, or monitoring intensity).
- **Further analysis:** Stratify by therapeutic area, primary endpoint type, and whether the trial was stopped for efficacy, safety, or futility.
- **Transparency:** Report both absolute numbers and rates, and publish the exact filtering criteria used.

---

## Limitations

- The data come from ClinicalTrials.gov registrations and may contain incomplete or inconsistently reported fields.
- “OTHER” funder type is heterogeneous (academic, government, non-profit, etc.).
- Missing enrollment values were dropped; the impact is small but not zero.
- Observational design — differences may be explained by unmeasured factors (disease area, trial complexity, regulatory environment, etc.).
- Results apply only to Phase 3 trials that started in 2010 or later and were registered on ClinicalTrials.gov.

---

## Tools

Python (pandas, NumPy, SciPy, statsmodels), Jupyter Notebook, Git and GitHub.

---

## Data Source

ClinicalTrials.gov – https://clinicaltrials.gov/

---

*Author: Emmanuel Bitrus*
