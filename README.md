# World Life Expectancy  

## Data Cleaning & Exploratory Data Analysis

In this project, I worked on cleaning and analyzing global life expectancy data using SQL. The process involved:

- Identifying and removing duplicate entries.
- Filling missing values for life expectancy using neighboring year averages.
- Standardizing country status classifications (e.g., 'Developing' or 'Developed').
- Ensuring data integrity through grouping and conditional updates.
- This project highlights my skills in data cleaning, querying large datasets, and performing advanced SQL operations such as JOIN, ROW_NUMBER(), and conditional updates.

### Data Source

[world_life_expectancy.csv](https://github.com/janelleridge/SQL-Projects/blob/main/WorldLifeExpectancy.csv)

Cleaned Data: [WorldLifeExpectancy_Clean.csv](https://github.com/janelleridge/SQL-Projects/blob/main/WorldLifeExpectancy_Clean.csv) 

### Tool Used

- MySQL

### Data Cleaning

- Duplicate Removal: Identified and deleted redundant records using ROW_NUMBER() and GROUP BY.
- Handling Missing Values: Filled missing life expectancy values by calculating the average of neighboring years.
- Standardization: Updated inconsistent or missing country status labels (e.g., ‘Developing,’ ‘Developed’) through conditional joins.
- Null Checks: Ensured completeness by identifying and managing null entries in critical columns.

### Exploratory Data Analysis

- Overview of Life Expectancy Trends
- Life Expectancy Range and Growth by Country
- Average Life Expectancy by Year
- Correlation between GDP and Life Expectancy
- Impact of Country Status (Developed vs. Developing) on Life Expectancy
- BMI vs. Life Expectancy Analysis
- Rolling Adult Mortality Rates Over Time

### Data Analysis

Some interesting codes and features I worked with on this set: 

Trends over Time: Calculated the average life expectancy per year to observe trends: 

```sql
SELECT Year, ROUND(AVG(`Life expectancy`), 2)
FROM world_life_expectancy
GROUP BY Year
ORDER BY Year:
```

Life Expectancy Range: Analyzed min and max life expectancy per country to track improvement.
```sql
SELECT Country, 
       MIN(`Life expectancy`), 
       MAX(`Life expectancy`), 
       ROUND(MAX(`Life expectancy`) - MIN(`Life expectancy`), 1) AS Life_Increase_15_Years
FROM world_life_expectancy
WHERE `Life expectancy` <> 0
ORDER BY Country;
```

Comparative Analysis by Status: Compared average life expectancy between developed and developing countries.
```sql
SELECT Status, ROUND(AVG(`Life expectancy`), 1)
FROM world_life_expectancy
GROUP BY Status;
```

### Results/Findings

1. Positive Trends in Life Expectancy: The analysis reveals a general upward trend in life expectancy across many countries, indicating improvements in health outcomes and quality of life. This reflects global efforts toward better healthcare and living conditions.
2. Impact of Status on Life Expectancy: Distinctions between developed and developing countries show that status significantly influences life expectancy, reinforcing the need for policy changes that address these inequalities.
3. Economic Influences on Health: The correlation between GDP and life expectancy suggests that economic well-being plays a crucial role in health outcomes. Countries with higher GDP often enjoy better healthcare access and healthier populations.
4. Trends in Adult Mortality: The rolling totals of adult mortality provide insights into health trends over time, revealing fluctuations that may be influenced by social, economic, and healthcare advancements.

### Recommendations

- Data-Driven Health Interventions: Utilize data analytics to identify specific health trends and risk factors within different populations. Tailor public health interventions based on these insights, focusing on high-risk groups to maximize the effectiveness of health campaigns and resource allocation.
  
- Economic Development Strategies: Foster economic development programs that promote job creation and sustainable growth in lower-income regions. By improving GDP, countries can invest more in healthcare infrastructure, education, and public health campaigns, ultimately contributing to increased life expectancy and better health for their populations.
