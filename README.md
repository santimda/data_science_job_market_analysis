# Data Science Job Market Analysis

Analysis of Data Science job postings, focusing on skills, salaries, and differences between the US and European markets.

## Overview

This project explores the Data Science job market using a large dataset of job postings. The analysis focuses on three main questions:

1. How do Data Science job postings differ between the US and Europe?
2. Which skills are most frequently requested?
3. Which skills are associated with higher reported salaries?

The analysis is performed in Python using pandas, NumPy, Matplotlib, Seaborn, and Hugging Face Datasets.

## Key Findings

- Python and SQL are by far the most frequently requested Data Science skills in both the US and European markets.
- The US has a higher reported salary distribution than the selected European markets, although salary reporting is substantially more common in the US.
- Skill requirements differ between the two markets, with some cloud technologies being relatively more prevalent in Europe and skills such as Tableau and Excel being more prevalent in US postings.
- Within Europe, reported median salaries vary substantially between countries.
- Some specialized cloud and data-engineering skills are associated with higher reported median salaries, while skills more commonly associated with Data Analyst roles tend to have lower reported median salaries.
- These salary associations should not be interpreted causally because the analysis does not control for seniority, industry, company, location, or other confounding variables.

## Dataset

The analysis uses the [Data Jobs dataset](https://huggingface.co/datasets/lukebarousse/data_jobs) collected and provided by Luke Barousse.

The dataset contains approximately 786,000 job postings and includes information about:

- Job titles and locations
- Job posting dates
- Work-from-home availability
- Degree requirements
- Health insurance
- Annual and hourly salaries
- Required skills
- Skill categories

A major limitation is that salary information is available for only a small fraction of the postings. Salary analyses therefore represent the subset of jobs for which salary information was reported.

## US vs Europe

The comparison examines job-posting characteristics, salary distributions, and skill requirements.

<p align="center">
   <img src="./figures/01_job_posting_characteristics.png" 
        alt="Job posting characteristics" 
        width="600">
</p>

### Main observations

- Work-from-home availability is more common in the US.
- In Europe it is more common to request a degree. 
- Health insurance is not a factor in Europe (consistent with a different health system).
- Salary information is reported for only a minority of job postings, remarkably less than 1% of all postings for Europe (!).
- US salaries are generally higher than European salaries in the reported salary data, although the distributions overlap substantially. In addition, the European market is not homogeneous: reported median salaries vary considerably between countries.

## Most Requested Skills

The following plot compares the most frequently requested skills in US Data Scientist job postings with their prevalence in European postings, where skill prevalence is calculated as the percentage of job postings mentioning a given skill.

The skills are ordered according to their prevalence in the US market.

<p align="center">
   <img src="./figures/02_top_skills_us_vs_europe.png" 
        alt="Top Data Science skills" 
        width="600">
</p>

### Main observations

- Python and SQL are, by a very large margin, the most frequently requested skills in both markets.
- Cloud technologies and data-related tools are also prominent requirements.
- In the US, requesting typical Data Analyst skills (such as Tableau and Excel) is more common than in the European market, while in Europe azure is more relevant. 

## Salaries

Salary distributions are compared using annual salary information reported in the job postings. All salaries are annual salaries in USD as provided by the dataset; no currency conversion was performed in this analysis.

<p align="center">
  <img src="./figures/03_salary_us_vs_europe.png" alt="US vs Europe salaries" width="600">
</p>

The salary distribution shows a higher reported salary level in the US market. Extreme US salary observations were excluded from the visualization to avoid compressing the main distribution.

Reported salaries should not be interpreted as representative of the complete job market because salary information is missing from most postings.

## European Salary Differences

The European market shows substantial variation in total number of job postings and the reported median salaries between countries.

<p align="center">
  <img src="./figures/04_counts_by_european_country.png" alt="European counts" width="600">
  <img src="./figures/05_salary_by_european_country.png" alt="European salaries" width="600">
</p>

The number of salary observations should be considered alongside the median salary for each country, since some countries have substantially fewer reported salaries than others.


## Skills and Salary

The final analysis examines the relationship between how frequently a skill is requested and the median salary associated with postings mentioning that skill.

<p align="center">
   <img src="./figures/06_skills_salary_europe.png" 
        alt="Skills and salaries" 
        width="600">
</p>

Only skills with a minimum number of job postings and salary observations are considered in order to reduce the influence of very small samples.

Higher median salaries are associated with postings requesting specific libraries (such as Airflow and Kafka) and cloud technologies (such as Snowflake, BigQuery, and AWS). Conversely, skills commonly found in Data Analyst roles, such as Power BI and Excel, are associated with lower reported median salaries.

Important caveat: the plot shows only the median salary for each skill and does not display the distribution of individual salaries underlying those medians (e.g. the 25th–75th percentile range). These distributions can be very broad, so apparent differences between skill-associated median salaries should be interpreted cautiously.

## Conclusions

The analysis suggests several broad patterns in the Data Science job market:

- **Python and SQL are fundamental skills** across both the US and European markets.
- **Cloud, data engineering, visualization, and machine-learning technologies** are also frequently requested, with some of these skills being associated with higher reported median salaries.
- The relative demand for individual skills differs between the two markets.
- **Reported US salaries are substantially higher** than reported European salaries, although salary reporting is incomplete (especially in the European market) and the markets are heterogeneous.
- Within Europe, **salary levels vary considerably by country**.
- Some skills associated with higher median salaries are less frequently requested, suggesting a **potential trade-off between skill prevalence and salary association**.
- Salary differences should not be interpreted causally: the analysis does not control for seniority, industry, company, location, or other confounding variables.

## Tools

- Python
- pandas
- NumPy
- Matplotlib
- Seaborn
- Hugging Face Datasets
- adjustText

## Repository Structure

```text
.
├── figures/
│   ├── 01_job_posting_characteristics.png
│   ├── 02_top_skills_us_vs_europe.png
│   ├── 03_salary_us_vs_europe.png
│   ├── 04_counts_by_european_country.png
│   ├── 05_salary_by_european_country.png
│   └── 06_skills_salary_europe.png
├── job-market_analysis.ipynb
├── README.md
└── .gitignore
```
     
