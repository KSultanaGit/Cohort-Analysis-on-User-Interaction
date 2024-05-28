
# Cohort Analysis on User Interaction

INTRODUCTION

Cohort Analysis is a method used in analytics and business intelligence to group customers or users into cohorts based on shared characteristics or experiences within a defined time-span. These cohorts are then tracked over time to observe changes in behavior, usage, or other key metrics.

This project performs a comprehensive cohort analysis on user interaction data to understand user behavior over time, identify trends, and improve user retention strategies. 

STEPS IN COHORT ANALYSIS

1. The first step is to define the cohorts based on a specific characteristic or event. For example, in an e-commerce platform, cohorts could be defined based on the month of a user’s first purchase.
2. Gather relevant data for analysis.
3. Determine the time intervals you want to analyze.
4. Group users into cohorts based on the defined characteristic or event.
5. Choose the key performance metrics you want to analyze.
6. Calculate the chosen metrics for each cohort over the specified time periods.
7. Create visualizations to present your findings effectively.

Tech Stack

    Python: Main programming language
    Jupyter Notebook: Interactive development and analysis environment
    Pandas: Data manipulation and analysis
    Matplotlib: Data visualization
    Seaborn: Statistical data visualization

Files Included

    Cohort_Analysis.ipynb: Jupyter Notebook containing the cohort analysis.
    Cohort_Analysis_For_User_Interactions.ipynb: Extended analysis with detailed user interaction.
    Cohort_Analysis_PDF.pdf: PDF version of the analysis report.
    cohorts.csv: Dataset used for the analysis.
    plots: Directory containing all the generated plots.

OVERVIEW

The project involves analyzing user interaction data to create cohorts based on the first interaction date. The analysis tracks these cohorts' engagement with the product over time, identifying critical trends and behaviors that can inform strategies to improve user retention.

ABOUT THE DATASET

The provided dataset contains user interaction data, including metrics such as the number of new and returning users, and their engagement durations on Day 1 and Day 7. The data is structured with dates, allowing for time-series analysis. Key columns in the dataset are:
1. Date: The specific dates of user interactions.2. New Users: The count of new users for each date.3. Returning Users: The count of users returning on each date.4. Duration Day 1: The average duration (possibly in minutes or seconds) of user interaction on their first day.5. Duration Day 7: The average duration of user interaction on their seventh day.


Data Preparation

1. Check for datatypes of all the columns in the data
2. The Date column is in object (string) format. For effective analysis, especially in cohort analysis, we should convert this to a datetime format.
3. Check whether the dataset has any null or duplicate values or not.
4. To perform cohort analysis, we need to create a cohort week in this case for further analysis.


Descriptive Statistics Insights

1. New Users: The average number of new users is around 3,418 with a standard deviation of approximately 677. The minimum and maximum new users recorded are 1,929 and 4,790, respectively.
2. Returning Users: On average, there are about 1,353 returning users, with a standard deviation of around 247. The minimum and maximum are 784 and 1,766, respectively.
3. Duration Day 1: The average duration on the first day is about 208 seconds with a considerable spread (standard deviation is around 65).
4. Duration Day 7: The average 7-day duration is lower, around 136 seconds, with a larger standard deviation of about 97. The range is from 0 to 304.


DATA DISTRIBUTIONS AND TREND ANALYSIS
Plotting distributions of all variables using Pairplot
<img src="https://github.com/KSultanaGit/SalesAndTargetsAnalysis/blob/main/screenshots/1.png" alt="Screenshot 1" width="500" height="200" align="center">

Calculating Retention:

python

cohort_pivot = cohorts.pivot_table(index='CohortGroup',
                                  columns='CohortPeriod',
                                  values='TotalUsers')
cohort_size = cohort_pivot.iloc[:,0]
retention = cohort_pivot.divide(cohort_size, axis=0)
retention.round(3)*100

Plotting Cohort Analysis:

python

    plt.figure(figsize=(12, 8))
    plt.title('Cohorts: User Retention')
    sns.heatmap(data = retention,
                annot = True,
                fmt = '.0%',
                cmap = 'Blues')

Plots

    User Retention Heatmap:
    User Retention Heatmap
        Inference: This heatmap shows the retention rate of users for each cohort over time. It helps identify which cohorts have higher retention and which need improvement.

    Monthly User Retention:
    Monthly User Retention
        Inference: This plot illustrates the monthly retention rates, highlighting periods of increased or decreased user engagement.

    Cohort Size Over Time:
    Cohort Size Over Time
        Inference: This visualization displays the size of each cohort over time, indicating how user acquisition has changed.

Summary

The cohort analysis conducted in this project provides valuable insights into user behavior and retention trends. By segmenting users into cohorts , we can better understand how different groups of users engage with the product over time. These insights can inform strategies to improve user retention and overall engagement.
Contributor

    KSultanaGit: GitHub Profile ​

​
