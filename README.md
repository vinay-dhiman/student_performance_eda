# Student Performance & Academic Analytics using Python

Exploratory data analysis of the UCI Student Performance dataset to understand which factors are associated with final grades in Math and Portuguese.

## Objective

Help an educational institution understand what is associated with student academic performance, and turn the findings into practical recommendations.

## Dataset

- Source: [UCI Student Performance dataset](https://archive.ics.uci.edu/dataset/320/student+performance)
- Files: `student-mat.csv` (395 students, Math) and `student-por.csv` (649 students, Portuguese)
- 33 attributes per record: demographics, family background, study habits, lifestyle, absences and three grades (`G1`, `G2`, `G3`, scored 0-20)
- Target: `G3`, the final grade

## Questions Investigated

1. Distribution of final grades
2. Study time and performance
3. Attendance (absences) and grades
4. Parental education and performance
5. Family background and academic outcomes
6. Previous grades and final grades
7. Extracurricular activities and performance
8. Gender differences
9. Factors most strongly related to final grades
10. Unusually high or low performers

## Approach

- **Cleaning:** cast `G1`/`G2` from quoted strings to integers, check missing values, duplicates and constant columns, merge both subjects with a `subject` column, rename columns, add labels, grade bands and derived features
- **Descriptive statistics:** numeric and categorical summaries, by-subject comparison
- **Visuals:** histograms, KDE plots, box plots, bar plots, scatter/regression plots, heatmaps
- **Statistics:** Spearman correlation, Mann-Whitney U, Kruskal-Wallis, Cohen's d, eta squared
- **Outliers:** IQR rule, z-scores and residuals of final grade against `G2`

## Key Findings

- 78% of records pass (`G3` >= 10); the distribution is left-skewed with a spike of 53 zero grades
- `G2` correlates 0.91 with `G3`; past class failures are the strongest non-grade factor
- Study time helps up to 5-10 hours a week, then flattens
- Among active students, more absences go with lower grades (Spearman -0.24)
- Mother's education, urban address and internet access are associated with higher grades
- Boys lead in Math, girls lead in Portuguese
- Zero grades look like dropouts: falling grades beforehand and no recorded absences

## Repository Structure

```
student-performance-analytics/
├── student_performance_eda.ipynb
├── student-mat.csv
├── student-por.csv
├── report.docx
└── README.md
```

## How to Run

1. Install the requirements: `pip install numpy pandas matplotlib seaborn scipy jupyter`
2. Place both CSV files in the same folder as the notebook
3. Run: `jupyter notebook student_performance_eda.ipynb` and execute all cells

## Limitations

- Observational data: findings show association, not causation
- 382 students appear in both files, so records are enrolments rather than unique students
- Absences are not recorded for dropouts
- Data comes from two schools in Portugal and may not generalise
