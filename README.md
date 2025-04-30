# Sparx Assessment Analysis

This report contains my approach and answers to the Sparx data analysis task. The accompanying notebook (`working/sparx_analysis.ipynb`) contains all code and visualisations used to derive the insights below.

---

## Question 1: How many distinct students do we have both assessment and activity data for?

I extracted the unique `student_id`s from both datasets and computed their intersection.

**Answer**: 1394 students have both assessment and activity data.

---

## Question 2: For students who completed at least two assessments, what was the mean progress they made from one test to the next?

I defined progress as the difference in percentage scores between consecutive assessments. I excluded students with fewer than two assessments or missing marks.

**Answer**: Mean progress between tests was **-3.17%**, indicating a slight average decline.

---

## Question 3: Plot/visualise this ‘progress’ distribution

A histogram and KDE plot were used to visualise progress between assessments. Most students had a small change, but the distribution skewed slightly negative.

---

## Question 4: On average, how did students perform in the second test compared to the first?

I extracted the first and second test scores per student and ran a paired t-test:

- **Average change**: -4.88%
- **p-value**: < 0.0001

**Conclusion**: The result is statistically significant, suggesting performance declined between the first and second test on average.

---

## Question 5: How can we improve confidence in this result?

We could control for test difficulty, the time gap between assessments, and topic overlap. This would reduce bias from test sequencing and allow better comparison.

---

## Exploratory Question: Can we say “Using Sparx improves students’ exam performance”?

I measured the number of Sparx homework questions completed per student and compared it to their average assessment scores. The analysis revealed:

- **Correlation**: 0.26 (positive)
- **p-value**: < 0.0001

**Conclusion**: There is a statistically significant positive relationship between Sparx activity and performance. While this suggests that using Sparx may be beneficial, the data is observational — so we cannot confirm causation.

---

## Stretch Question: How can modelling help personalise homework without assessment data?

Even without formal assessment scores, we can use Sparx activity data to estimate student mastery and personalise homework. I propose a topic-level proficiency model using features such as:

- Number of prior correct attempts
- Time to first correct answer
- Video time
- Answer pattern summaries (e.g. `C`, `W`, `V`)

This model (e.g. Bayesian Knowledge Tracing or gradient boosting) could infer a student’s current skill level and recommend personalised homework based on weak topics.

---

## Files Included

- `working/sparx_analysis.ipynb`: All code and plots
- `README.md`: All answers
- Raw data: `task_qla_df.csv`, `task_tia_df.feather`
