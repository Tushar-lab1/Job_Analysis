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
