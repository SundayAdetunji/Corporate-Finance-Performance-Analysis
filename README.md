# Corporate-Finance-Performance-Analysis

## Table of Contents
- [Project Overview](#project-overview)
- [Data Sources](#data-sources)
- [Tools](#tools)
- [Data Cleaning and Preparation](#data-cleaning-and-preparation)
- [Exploratory Data Analysis](#exploratory-data-analysis)
- [Data Analysis](#data-analysis)
- [Results and Findings](#results-and-findings)
- [Recommendations](#recommendations)
- [Limitations](#limitations)
- [References](#references)

---
### Project Overview
This project uses Microsoft Power BI to analyse the financial performance and profitability of publicly listed companies over the period 2007–2022. The objective is to provide insights into corporate profitability, operating income, cost efficiency, profit growth and financial stability through interactive dashboards and financial performance indicators. The analysis is designed to help management, board members and investment analysts identify financially strong and weak companies, assess profitability trends, evaluate operational efficiency and support informed investment decisions.

<img width="766" height="436" alt="WhatsApp Image 2026-11-10 at 21 34 21" src="https://github.com/user-attachments/assets/842b162f-6a90-4ecb-9a3c-5d38eff0cecb" />

### Data Sources
The primary data used for this analysisis the Financial_Statement.csv dataset obtained from Kaggle [Download Here](https://www.kaggle.com/datasets/murtazaaamir/financial-dataset).
The dataset contains 13 columns, 203,986 financial records across 4,713 publicly listed companies, covering reporting dates from 9 January 2007 to 14 May 2022.

### Tools
* Microsoft Excel/CSV: Initial dataset. 
* DAX (Data Analysis Expressions): Creation of financial measures and calculated columns.
* Power Query: Data extraction, transformation and cleaning.
* Microsoft Power BI Desktop: Data modelling, DAX calculations, financial analysis and dashboard development.

### Data Cleaning and Preparation

Data preparation was performed using Power Query in Power BI. The key activities involves the following:
- Imported the CSV dataset into Power BI.
- Renamed columns to improve readability and consistency.
- Standardised column names using a consistent naming convention.
- Converted the reporting date column into Date format.
- Converted company ticker identifiers into Text format.
- Converted financial fields into appropriate numeric data types.
- Inspected column quality, distribution and data profiling.
- Identified missing values across financial fields.
- Checked for duplicate records.
- Investigated repeated combinations of company ticker and reporting date.
- Retained legitimate negative financial values, including losses and negative expenses, rather than treating them as errors.
- Created additional date-related fields to support time-series analysis.

### Exploratory Data Analysis 

Exploratory analysis was carried out to understand the dataset’s structure, reporting periods, financial variables and company coverage. The analysis focused on the following:
* Number of companies represented in the dataset.
* Distribution of financial records across reporting years.
* Net profit and loss distribution.
* Operating income patterns.
* Operating expense distribution.
* Net profit growth and operating income growth.
* Missing values in financial variables.
* Repeated company and reporting-date combinations.
* Extreme financial values and potential outliers.

### Data Analysis
Financial analysis was performed using DAX measures and calculated columns in Power BI. The key performance indicators includes the following:
* Total Net Profit.
* Average Net Profit per Company.
* Average Operating Income per Company.
* Percentage of Loss-Making Companies.
* Average Profit Growth Rate.
* Average Net Operating Profit.
* Average Total Profit.
* Average Operating Expenses.
* Average Profit Volatility.

The dashboard was designed around the following six major analytical areas:

i. Net Profit Trend Over Time

ii. Top Performing Companies

iii. Profit Distribution and Risk Analysis

iv. Operating Expenses vs Net Profit

v. Growth vs Profitability Matrix

vi. Profit Volatility Analysis
  
Some of the key calculations are as follows:
- ``Total Net Profit =
SUM('Corporate_Financials'[Net_Profit])``
- ``Average Net Profit per Company =
AVERAGEX(
    VALUES('Corporate_Financials'[Ticker]),
    CALCULATE(
        AVERAGE('Corporate_Financials'[Net_Profit])
    )
)``
- ``Average Operating Income per Company =
AVERAGEX(
    VALUES('Corporate_Financials'[Ticker]),
    CALCULATE(
        AVERAGE('Corporate_Financials'[Operating_Income])
    )
)``
- ``Loss-Making Companies =
COUNTROWS(
    FILTER(
        VALUES('Corporate_Financials'[Ticker]),
        CALCULATE(
            AVERAGE('Corporate_Financials'[Net_Profit])
        ) < 0
    )
)``
- ``Profitability Status =
SWITCH(
    TRUE(),
    ISBLANK('Corporate_Financials'[Net_Profit]), "Unknown",
    'Corporate_Financials'[Net_Profit] > 0, "Profitable",
    'Corporate_Financials'[Net_Profit] < 0, "Loss-Making",
    "Break-Even"
)``

### Results and Findings

The results of the analysis are summarised as follows:

- The companies recorded a combined total net profit of 107.96 trillion across the reporting period, demonstrating the substantial scale of reported corporate profitability represented in the dataset.
- The average net profit per company was 436.67 million, providing a benchmark for comparing the profitability of individual companies.
- The average operating income per company was approximately 4.75 billion, highlighting the significant operating income generated across the companies analysed.
- The average profit growth rate stood at 47.57, indicating positive reported profit growth overall, although individual company performance varied.
- A total of 430 companies were classified as loss-making, highlighting the need to investigate businesses experiencing profitability challenges and identify the factors contributing to their losses.
- The Net Profit Trend Over Time chart shows an overall upward movement in reported profitability, with noticeable increases in certain reporting periods, indicating periods of stronger financial performance.
- The Top 10 Companies by Average Net Profit chart highlights significant differences in profitability across companies, demonstrating that a relatively small group of companies accounts for a substantial share of the strongest reported average profits.
- The Operating Expenses vs Net Profit analysis reveals varying relationships between operating costs and profitability, providing opportunities to identify companies where expense management may require improvement.
- The Company Growth vs Profitability matrix highlights differences in company performance, helping distinguish businesses with stronger growth and profitability from those requiring closer financial assessment.
- The Profit Volatility analysis identifies companies with substantial variations in reported net profit, highlighting potential financial instability and the importance of monitoring earnings consistency.
- Overall, the dashboard provides an interactive framework for evaluating corporate profitability, operating efficiency, growth performance and financial risk, supporting more informed management and investment decisions.

### Recommendations

Based on the analysis, the following recommendations are proposed:

- Strengthen profitability monitoring to identify deteriorating financial performance.
- Investigate loss-making companies and implement measures for profitability
- Improve cost efficiency by identifying companies with disproportionately high operating expenses relative to operating income.
- Monitor profit growth by assessing whether companies are achieving sustainable growth rather than relying on isolated periods of strong performance.
- Assess financial stability by identifying companies with inconsistent financial results.

### Limitations

The following limitations were observed:

* The dataset covers reporting dates from 2007 to 2022 and does not provide information beyond this period.
* The dataset does not explicitly identify the currency in the supplied file.
* The reporting frequency and whether individual figures are annual, quarterly, interim or cumulative require further validation.
* Some companies have multiple records associated with the same reporting date.
* Missing values exist in several financial fields.
* Extreme financial values and growth rates may influence averages and volatility calculations.
* The dataset does not include all information required for a complete investment assessment, such as cash flow, debt levels, market valuation, dividends and industry benchmarks.
* Profitability alone does not establish whether a company is a suitable investment.

Consequently, the dashboard should be considered a financial performance and screening tool rather than a standalone investment recommendation system.

### References
