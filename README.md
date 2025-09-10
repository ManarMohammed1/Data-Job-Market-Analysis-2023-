# Overview
Welcome to my analysis of the data job market, with a focus on trends and skills. This project, which was created to better understand the current landscape of the data industry, delves into the top job roles, geographical demand, and the most sought-after skills and their corresponding salaries.

The analysis is based on a dataset of job postings in 2023.

The data sourced from [Luke Barousse's Python Course](https://lukebarousse.com/python) which provides a foundation for my analysis, containing detailed information on job titles, salaries, locations, and essential skills. Through a series of Python scripts, I explore key questions such as the most demanded skills, job posting trends, and the intersection of demand and salary to identify optimal skills for data scientists.

# The Questions

1. What are the most popular job roles and which countries have the most job postings?

2. How are job postings for top roles trending over the year?

3. What are the most in-demand skills for each of these roles?

4. How do skills correlate with salary, and what are the most optimal skills for a Data Scientist to have?

# Data Cleaning & Preprocessing

The initial dataset was loaded into a pandas DataFrame and inspected for missing values and data types. I then performed the following cleaning and preprocessing steps to prepare the data for analysis:

- Date Conversion: The job_posted_date column was converted from an object to a datetime format to enable time-series analysis.

  ```python
  df['job_posted_date'] = pd.to_datetime(df['job_posted_date'])
  ```

- String-to-List/Dict Conversion: The job_skills and job_type_skills columns, which were stored as strings, were converted into actual lists and dictionaries using the ast.literal_eval function. This was a critical step for being able to "explode" the data and count individual skills later in the analysis.

- Filtering for US Data: The analysis was focused on the job market in the United States, so the DataFrame was filtered to include only job postings where the job_country was 'United States'.

These steps were essential to ensure the data was in a usable format for the exploratory data analysis and to get accurate insights into the US data job market.
