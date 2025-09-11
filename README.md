# Overview
Welcome to my analysis of the data job market, with a focus on trends and skills. This project, which was created to better understand the current landscape of the data industry, delves into the top job roles, geographical demand, and the most sought-after skills and their corresponding salaries.

The analysis is based on a dataset of job postings in 2023.

The data sourced from [Luke Barousse's Python Course](https://lukebarousse.com/python) which provides a foundation for my analysis, containing detailed information on job titles, salaries, locations, and essential skills. Through a series of Python scripts, I explore key questions such as the most demanded skills, job posting trends, and the intersection of demand and salary to identify optimal skills for data scientists.

# The Questions

1. How are job postings for the top three data roles trending over time?
2. What are the skills most in demand for the top 3 most popular data roles?
3. How well do jobs pay for top three Data roles?
4. What are the optimal skills for data scientist to learn? (High Demand AND High Paying)

# Data Cleaning & Preprocessing

The initial dataset was loaded into a pandas DataFrame and inspected for missing values and data types. I then performed the following cleaning and preprocessing steps to prepare the data for analysis:

- Date Conversion: The job_posted_date column was converted from an object to a datetime format to enable time-series analysis.

  ```python
  df['job_posted_date'] = pd.to_datetime(df['job_posted_date'])
  ```

- String-to-List/Dict Conversion: The job_skills and job_type_skills columns, which were stored as strings, were converted into actual lists and dictionaries using the ast.literal_eval function. This was a critical step for being able to "explode" the data and count individual skills later in the analysis.
  ```python
  df['job_skills'] = df['job_skills'].apply(lambda x: ast.literal_eval(x) if pd.notna(x) else x)
  df['job_type_skills'] = df['job_type_skills'].apply(lambda x: ast.literal_eval(x) if pd.notna(x) else x)


- Filtering for US Data: The analysis was focused on the job market in the United States, so the DataFrame was filtered to include only job postings where the job_country was 'United States'.
  ```python
  df_US = df[df['job_country'] == 'United States'].copy()
  ```
These steps were essential to ensure the data was in a usable format for the exploratory data analysis and to get accurate insights into the US data job market.

# Analysis

This section dives into the core of the project, exploring the key questions that define the current landscape of the US data job market in 2023.

## 1. Trending Job Posting in the US

This analysis examines the monthly volume of job postings for the top three data roles: Data Analyst, Data Engineer, and Data Scientist. The goal is to identify trends and patterns in demand for each role over the course of the year.

### Visualize Data
```python
sns.lineplot(data=posting_job_month_pivot,dashes=False, palette='tab10')
plt.show()
```

### Results





