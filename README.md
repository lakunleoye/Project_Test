
# Overview
The UK has one of the biggest tech job markets in the world. In this project, I performed a detailed analysis  on the Data Analytics role in the UK market with a focus on the top-paying and in-demand skills in a bid to help Data Analysts find ideal job opportunities.

The dataset used for the project was sourced from "Luke Barousse's Python for Data Analytics Course (https://lukebarousse.com/python)". This data provided information on job titles, salaries, locations, and essential skills, and these form the basis of my analysis. I employed the use of Python scripts to explore and answer questions relating to the most demanded skills, salary trends, and the link between demand and salary in Data Analytics in the UK market.

# Research Questions
The project is centred around four key research questions.
1. What are the most popular skills for the top 3 data roles in the UK?
2. How are In-demand skills trending for Data Analysts in the UK?
3. How well do the Jobs and Skills pay for Data Analysts in the UK?
4. What are the most optimal skills to learn for Data Analysts in the UK?

# Tools used for the study
To provide an indepth and insightful analysis, I employed four key tools.
- **Python**:This is the cornerstone of the analysis as it allowed me to analyse the data and find critical insights.  I also incorporated relevant Python libraries including: **Pandas Library** was used for data analysis, 
**Matplotlib Library** was used to visualise data, and
**Seaborn Library** was used for advance visuals

- **Jupyter Notebooks**: This tool was used to run the Python scripts and also enabled me to easily include my notes and analysis.
- **Visual Studio Code**:  This is my preferred integrated development environment for executing Python scripts
- **Gits & GitHub**: These are essential for version control and sharing my Python code and analysis, ensuring collaboration with other developers. 

# Data Preparation and Cleanup
These are the steps that I used to prepare the data for analysis:
## Import and cleanup data
First, i import the necessary libraries and load the dataset. I then performed an initial data cleaning to ensure data accuracy and consistency.

# The Analysis
I used each Jupyter Notebook in this project to focus on investigating specific aspects of the UK's data job market. This was how I address each of my research questions.
## 1. What are the most popular skills for the top 3 data roles in the UK?

To find the most demanded skills for the top 3 most popular data roles(1) I filtered out those positions by which ones were the most popular and (2) got the top 5 skills for these top 3 roles. This query highlights the most popular job titles and their top skills, showing which skills focus on based on the role I am targetting.

View my notebook with detailed steps here: [2_Skill_Demand.ipynb](2_Skills_Count.ipynb)

### Visualise Data
```python 

fig, ax = plt.subplots(len(job_titles), 1)

for i, job_title in enumerate(job_titles):
    df_plot = df_skills_percent[df_skills_percent['job_title_short'] == job_title].head(5)
    sns.barplot(data=df_plot, y='job_skills', x='skills_percent',ax=ax[i], hue='skills_percent', palette='dark:r_r')
   

plt.show() 

``` 

### Result
![3_Capstone/Images/Skill_demand_top3_data_roles.png](3_Capstone\Images\Skill_demand_top3_data_roles.png)
*Bar plots visualising most demanded skills for top 3 data job titles in the UK

### Insights
In the UK, SQL is the the most sought after skills across the top 3 data roles. This is followed by Python. The level of request for each skill, however, vary for the individual roles. For example, Python featured prominently (69 %) for Data Scientists. This is in contrast with 20 % and 55 % for Data Analysts and Data Engineers. One notable information here is that Python is less essential for Data Analysts.

Second, If we go the top 3 most sought after skills for the individual roles, SQL, Excel, and Power BI are the most in-demand for Data Analysts. For Data Engineers and Data Scientists,SQL and Python are the topmost skills for both, with Azure completing the top 3 for the former and R for the latter.

Interestingly, Cloud computing skills (e.g. aws and azure) are rarely demanded for Data Analyst roles.

## 2. How are In-demand skills trending for Data Analysts in the UK?
To find how skills are trending in 2023 for Dta Analysts, I filtered data analyst positions and grouped the skills by the month of the job postings. This provided me the top 5 skills of data analysts by month, showing how popular skills were throughout 2023.
View my notebook with detailed steps here: [3_Skills_Trend.ipynb](3_Capstone\3_Skills_Trend.ipynb)


### Visualise Data
```   python 

from matplotlib.ticker import PercentFormatter

df_plot = df_DA_UK_percent.iloc[:, :5]
sns.lineplot(data=df_plot, dashes=False, legend='full', palette='tab10')

plt.gca().yaxis.set_major_formatter(PercentFormatter(decimals=0))

plt.show() 

 ```

 ### Results
 ![3_Capstone/Images/Data_Analysts_Skills_Trend](3_Capstone\Images\Data_Analysts_Skills_Trend.png)
 *Line plots visualising the trend of top skills for Data Analysts in the UK in 2023*


 ### Insight

 SQL maintained a top position throughout the year as the most in-demand skills for Data Analysts. However, the demand for the skill showed a steady fluctuation throughout, with  signicant upward spikes, first in May, and later in September, before a downward trend that span through till December.

 Second most in-demand skill throughout the year was Excel. The demand for this skill also fluctuated through the year with significant swings between July and December.

In the case of PowerBI, demand fluctuated around 30% in the early part of the year, trended upward in May and continued fluctuating at that level before decending to prior levels starting November to December.

The demand for Python and Tableau somehow tracked eachother and fluctuated around the 20 % level for most part of the year. However, there was a noticable divergence starting from August to December with the demand for Python skills ticking higher.


## 3. How well do the Jobs and Skills pay for Data Analysts in the UK?
To identify the highest-paying roles and skills, I filtered for only UK jobs and looked at their median salary.I then examined the salary distributions of common data jobs (Data Scientist, Data Engineer, and Data Analyst) to get an idea of which jobs are paid the most.

View my notebook with detailed steps here: [4_Salary_Analysis.ipynb](3_Capstone\4_Salary_Analysis.ipynb)

### Salary Analysis for Data Roles

### Visualise Data
```python 

sns.boxplot(data=df_UK_top6, x='salary_year_avg', y='job_title_short', order=job_order)
sns.set_theme(style='ticks')

ticks_x=plt.FuncFormatter(lambda y, pos: f'${int(y/1000)}K')

plt.gca().xaxis.set_major_formatter(ticks_x)
plt.show()

 ```

 ### Results
 ![3_Capstone/Images/Salary_Distribution](3_Capstone\Images\Salary_Distribution.png)
 *Box plots for visualising the salary distribution for the top 6 job titles*

### Insights
- There is a a wide variation in the earning potentials of the various job titles. While Data Scientists have the highest earning potentials, Data Analysts have the least.

- Generally, median salaries for the senior roles are higher than the junior roles showing the value that the industry place on advance skills and years of experience

- Interestingly, some junior level roles tend to earn higher salaries than senior level roles in the same discipline. This could be due to the junior level roles having specialist skills.

- Senior Data Engineers and Senoir Data Analysts have narrower range of salaries.  While Senior Data Analysts have fewer outliers demonstrating consistencies in salaries, Senior Data Engineers have considerable number of outliers at higher and lower ends of the spectrum, suggesting that exceptional skills and circumstances can affect compensation for this role.

- All the junior level roles have wider difference in salaries. Such variance in compensation could be related to the level of responsibilities, location, industry, or company size.

## Highest Paid and Most Demanded Skills for Data Analysts
Next, i narrowed my analysis and focused only on Data Analyst roles. I looked at the highest paid skills and the most demanded skills, and used two bar charts to showcase them.

### Visualise Data

``` Python

fig, ax = plt.subplots(2, 1)
sns.set_theme(style='ticks')

# Top 10 Highest Paid Skills for Data Analysts
sns.barplot(data=df_DA_top_pay, x='median', y=df_DA_top_pay.index, ax=ax[0], hue='median', palette='dark:r_r')

# Top 10 most In-demand Skills for Data Analysts
sns.barplot(data=df_DA_skills, x='median', y=df_DA_skills.index, ax=ax[1], hue='median', palette='light:r')

plt.show()

 ```

 ### Result
 ![Highest Paid and Most In-demand Skills for Data Analysts in the UK](3_Capstone\Images\Highest_Paid_and_Most_Demanded_Skills.png) *Bar plots visualising (1) Highest Paid Skills and (2) Most Demanded Skills for Data Analysts in the UK*


### Insights
As shown in the top graph, skills like 'Pandas', 'Pytorch' , and 'Tensorflow'  are associated with high salaries, sometimes upto $175K. 

The bottom graph shows that foundational skills like 'Excel', 'PowerBI', and 'SQL' are the most In-demand.

These suggest that Data Analysts that wants to maximise their potential must develop a diverse skillset that include both high-paying specialised skills and fequently demanded foundational skills.

## 4. What is the most optimal skills to learn for Data Analysts in the UK?

Here, I grouped the skills to determine their median salaries and likelihood of being in job posting. I then visualise the median salary  against the percent of skill demand to determine the most optimal skills and if certain technologies are more prevalent.

View my notebook with detailed steps here: [5_Optimal_Skills.ipynb](3_Capstone\5_Optimal_Skills.ipynb)

### visualise Data?
```python

from adjustText import adjust_text
import matplotlib.pyplot as plt

plt.scatter(df_DA_skills_high_demand ['skills_percent'], df_DA_skills_high_demand['median_salary'])

plt.show()

```
### Results
![3_Capstone/Images/Most_Optimal_Skills_for_Data_Analysts](3_Capstone\Images\Most_Optimal_Skills_for_Data_Analysts.png) *Scatter plot showing the most optimal(high-paying and high-demand) skills for Data Analysts in the UK*

### Insights
From the plot, Programming skills (coloured Blue) formed two clusters: the top-right (Python and SQL) and the middle-left (sas, r, and go). The graph suggests that Data Analysts with programming skills in the top-right might benefit from higher demand and higher salary offer.

For the Analyst-tools (coloured orange), the are three clusters: top-left(Looker, PowerBI, and Tableau), middle-right(Excel), and bottom-left (Word and Outlook). The graph suggests that the demand for Excel is prevalent in job postings, suggesting that the tool is versatile. However, the salary attached to the skill is in the middle of the range. While Data Analysts with Excel skill will benefit from the highest demand, they might be able to attract higher salary benefit by acquiring at least one of the visualisation skills in the top-left clustter. 

The only Cloud technology skills(coloured Green) that featured in the scattered plot, Azure, is associated with one of the highest salaries- an indication of the high value placed on the expertise for analysing and processing Big Data.

# What I Learned
The project helped deepen my understanding of the data analyst job market in the UK, and also enhanced my Python skills especially in the area of data manipulation and visualisation. Specifically, I learned
- **Advanced Python Usage**: My use of various libraries like Pandas for data manipulation, Seaborn and matplotlib for data visualisation enhance my ability for perfoming data analysis tasks efficiently.
- **Data Cleaning Importance**: Throrough data  cleaning and preparation are crucial can before any analysis can be conducted as this would ensure accurate  insights are gleaned from the data.
-**Strategic Skill Analysis**:
The project emphasied the importance of alligning one's skills with market demand. Understanding the relationship between skill demand, salry, and job availability allows for more strategic career planning in the tech industry.



# Insights
this project provided several general insights into the data job market for analysts:

- **Skill Demand and Salary Correlation**:There is a correlation between the demand for certain skills and the type of salaries they command. Advanced skills like Python and SQL are often associated with higher salaries in the UK market.
- **Market Trends**: The are changing trends in skill demand - an indication of dynamic nature of the job market. Keeping up with these trends is essential for career growth in data analytics.

- **Economic Value of Skills**: An understanding of high-demand and high-paying skills can help data analysts to ptioritise learning for maximum economic returns.

# Challenges
These are the challlenges I faced in the project
- **Data Inconsistencies**: A thorough and carefully considered techniques were required to handle inconsistent dta entries to ensure the integrity of the analysis.
- **Complex Data Visualisation**: The design of effective visual that provide clear and compelling insights that represent the complex datasets used in the project was challenging.

- **Balancing Breadth and Depth**: Deciding the depth to go with each analysis while maintaining a broad landscape required constant balancing to avoid dwelling on unimportant details.

# Conclusion
Analysis of the Data Analytics job market in the UK has provided valuable insights into the key factors driving the industry. By examining job titles, salary trends, and the essential skills required, it is clear that certain technical proficiencies and tools are in high demand, directly influencing salary potential. Python and SQL, for instance, consistently emerge as critical skills that can significantly enhance a Data Analyst’s career prospects. Furthermore, there is a notable correlation between the demand for specific skills and higher salary brackets, underlining the importance of staying current with industry trends. This analysis serves as a useful guide for Data Analysts seeking to identify the most lucrative and in-demand roles in the UK job market, and equips them with the knowledge to tailor their skillset accordingly. As the demand for data-driven insights continues to rise, those who refine their expertise in the areas identified will be well-positioned to succeed in this competitive field.







