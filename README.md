# SQL DATA CLEANING AND EXPLORATORY ANALYSIS(GLOBAL LAYOFFS)


## PROJECT OVERVIEW

This project involved a comprehensive end-to-end dataset using MYSQL. I took a raw, "dirty" dataset containing global tech layoffs(2020-2023) and performed extensive cleaning to ensure data integrity. Following the cleaning phase, I conducted an Exploratory Data Analysis(EDA) to uncover trends regarding which industries, companies, and periods were most affected by the economic shift.


## Phase 1: Data Cleaning

The goal was to transform the raw data into a reliable format for analysis.

Staging Environment: I created a layoffs_staging table to preserve the original raw data, followed by a layoffs_staging2 table for the final transformation.

Duplicate Removal: Used a CTE and ROW_NUMBER() partitioned across all columns to identify and delete exact duplicates.

Standardization: Trimmed whitespace and removed trailing punctuation(e.g., fixing "United States." to "United States").
                 Standardized industry names such as grouping "Crypto" labels into one consistent category.
                 Converted the date column from a string format to a proper SQL DATE type for time-series analysis.

Handling Nulls and Missing Values: Used a Self-Join to populate missing values. In the dataset, one entry for "Airbnb" had a category and another was blank, I mapped the correct data to the empty record.
 I dropped the helper row_num column used during cleaning to finalize the production table.


## Phase 2: Exploratory Data Analysis

With a clean dataset, I explored the numbers to find the "story" behind the layoffs.

Company Impact: I calculated the total layoffs per company using SUM(total_laid_off). This revealed the major players like Google and Amazon had the highest raw numbers.

Funding vs. Industry: I analyzed the total capital raised by each sector. By grouping the data by industry and sorting by total funding(ORDER BY 2 DESC), I found that the Media and Travel industries led the pack in terms of total investment.

Time-Series Trends: Extracted the month and year using SUBSTRING.
    
      Calculated a Rolling Total of layoffs by month to visualize the speed at which job losses accelerated.

Top 5 Yearly Rankings: Used a CTE AND DENSE_RANK() to identify the top 5 companies with the most layoffs for each year. I chose DENSE_RANK () over a standard RANK() to ensure that companies with identical layoffs counts received the same rank without skipping the next consecutive number in the sequence. By wrapping this in a CTE(Common Table Expression), I was able to perform a subquery like filter on the ranked results to isolate only the top 5 records per year.


SKILLS: Data Cleaning, Join Logic, CTEs(Common Table Expressions), Window Functions, String Manipulation.

TOOLS: MYSQL Workbench












