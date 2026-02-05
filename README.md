# The Analysis

## What are the most in demand skills for the top 3 most popular data roles

View my notebook with detailed steps here:
[2_Skill_Demand.ipynb](2_Skill_Demand.ipynb)

### Visualize Data

```python
fig , ax = plt.subplots(len(job_titles) , 1)
for i , job_title in enumerate(job_titles):
    df_plot = df_skills_perc[df_skills_perc.job_title_short == job_title].head(5)\
    sns.barplot(data=df_plot , x = 'skill_percent' , y ='job_skills' , ax = ax[i] ,hue='skill_count' , palette='dark:b_r')
    sns.set_theme(style='ticks')
plt.show()
```

### Result

![Visualization of Top skills for Data Nerds](images\skill_demand.png)

### Insights

- Python is a versatile skill, highly in demand across all three roles. 72% for Data Scientists and 65% for Data Enginners
- SQL is the most requested skill for Data analyst and Data Scientist, as it is present in more than half of the job postings
- DAta Enginners require more specialized skills like AWS , Azure , Spark compared to Data Analyst and Data Scientist

## How are in-demand skills trending for Data Analysts

View my notebook with detailed steps here:
[2_Skill_Demand.ipynb](3_Skill_Trend.ipynb)

### Visualize Data

```python
df_plot = df_da_us_perc.iloc[:, :5]


sns.set_theme(style='ticks')
sns.lineplot(data=df_plot, dashes=False, palette='tab10', legend=False)
sns.despine()


plt.xlabel('2023')
plt.ylabel('Likelihood in Job Posting')
plt.title('Trending job skills for data analytics')


for i in range(5):
plt.text(11.2, df_plot.iloc[-1, i], df_plot.columns[i])


plt.show()
```

### Result

![Visualization of Trending skills for Data Nerds](images\trending_skills.png)

### Insights

- SQL remains the most in-demand skill throughout the year, though it shows a gradual decline toward the end, indicating slight diversification in required skill sets.

- Excel stays consistently important but experiences a noticeable dip mid-to-late year before rebounding, suggesting seasonal or role-specific demand shifts.

- Python maintains a steady presence across months, highlighting its role as a core analytical skill rather than a seasonal requirement.

- Tableau (and other BI tools) show moderate but stable demand, reinforcing their importance for data visualization rather than primary analysis.

- Overall, the trends suggest that while foundational tools remain essential, employers increasingly value a balanced and adaptable data analytics skill set.

## How do salaries vary by top 6 roles in united states

View my notebook with detailed steps here:
[2_Skill_Demand.ipynb](4_Salary_Analysis.ipynb)

### Visualize Data

```python
sns.boxplot(data=df_us_top6 , x = 'salary_year_avg' , y = 'job_title_short' , order=job_order)
sns.set_theme(style='ticks')
plt.title('Salary Distribution in the United States')
plt.xlabel('Yearly Salary in USD')
plt.ylabel('')
plt.xlim(0 , 600000)
ticks_x = plt.FuncFormatter(lambda y , pos: f'${int(y/100)}K')
plt.gca().xaxis.set_major_formatter(ticks_x)
plt.show()
```

### Result

![Visualization of Salaries of top 6 data roles in United States](images\skill_analysis.png)

### Insights

- Senior roles consistently earn higher median salaries than their non-senior counterparts, confirming the strong salary premium associated with experience and leadership responsibilities.

- Data Scientists and Data Engineers show higher salary distributions compared to Data Analysts, reflecting the technical complexity and specialization required in these roles.

- Senior Data Scientists have the highest median salary among all roles, along with a wide spread, indicating both high earning potential and variability based on domain expertise and company size.

- Data Analyst roles have the lowest median salaries but also tighter distributions, suggesting more standardized compensation and lower variance across companies.

- The presence of high-end outliers across all roles (especially in engineering and scientist positions) suggests that top-paying opportunities exist, likely driven by niche skills, big tech companies, or high-cost locations.
