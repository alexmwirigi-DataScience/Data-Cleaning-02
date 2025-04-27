
 # Global Passenger Car Sales Data Cleaning (2019-2024)
### Project Overview
**This project focuses on cleaning and preparing a dataset containing global passenger car registrations and sales data for the years 2019 to 2024. The raw data, provided in a loosely structured CSV format (pc_sales_2024.csv), includes metadata, inconsistent formatting, and varying levels of aggregation (countries, regions, totals). The primary goal is to transform this raw data into a clean, structured, and analysis-ready format using Python and the pandas library.**

## Data Source
#### Filename: pc_sales_2024.csv

#### Source Type: CSV-like text data, derived from OICA (Organisation Internationale des Constructeurs d'Automobiles) reports or similar sources.

#### Content: New passenger car registrations and sales figures.

#### Granularity: Data for individual countries, sub-regional aggregates (e.g., EU27+EFTA+UK, USMCA), major regions (e.g., Europe, America), and global totals.

#### Time Period: Quarterly data for years 2019, 2020, 2021, 2022, 2023, and 2024.

#### Additional Metrics: Percentage change in sales for 2024 compared to 2023 and 2019.

## Project Goals
#### Load and Parse Data: Load the dataset correctly, handling initial metadata rows and identifying the true header.

#### Clean Structure: Remove non-data rows, such as blank separators, titles, and footnotes.

#### Standardize Columns: Rename columns to make them more descriptive and easier to work with.

#### Ensure Correct Data Types: Convert sales figures (strings with commas) to numeric types (integers or floats) and percentage changes (strings with '%') to numeric floats.

#### Clean Text Data: Handle inconsistencies in country/region names, such as extra whitespace and special characters.

#### Identify Data Hierarchy: Add a new column (Row_Type) to classify rows as individual countries, regional aggregates, or global totals.

#### Validate Data: Perform checks to ensure data consistency (e.g., no negative sales figures or calculation errors).

#### Handle Missing Data: Identify and address any missing data points (none found after initial cleanup).

#### Detect Duplicates: Ensure there are no duplicate entries.

#### Document Process: Provide a clear and detailed explanation of the cleaning steps and decisions made.

#### File Structure
 
.
├── pc_sales_2024.csv               # Raw input data file
├── pc_sales_cleaning.py            # Python script to perform data cleaning
├── pc_sales_cleaned.csv            # Cleaned data output (optional export)
└── README.md                       # Documentation file (this file)
#### Setup and Prerequisites
#### Python Requirements:
#### Python version: 3.7 or higher is recommended.

#### Required Libraries:

####pandas: For data manipulation and analysis.

#### numpy: For numerical operations (used implicitly by pandas).

## Installation:
#### Install necessary libraries using pip:
 
#### pip install pandas numpy
#### Usage Instructions
#### Place Data:

#### Ensure that the raw data file (pc_sales_2024.csv) is in the same directory as the script, or update the script to point to the correct file path.

#### Run Script:

#### Execute the Python cleaning script from your terminal:

 #### pc_sales_cleaning.py
#### Output:

####The script will process the data and display summaries of the cleaning steps.

####If configured, it will save the cleaned data to a new file (pc_sales_cleaned.csv).

#### Data Cleaning Process Summary
#### The pc_sales_cleaning.py script performs the following steps:

#### Loading:

#### Reads the CSV file, skipping metadata rows, and correctly identifies the header row.

#### Initial Cleanup:

#### Removes fully blank rows (used as separators) and eliminates footer notes.

#### Column Renaming:

#### Renames columns to make them more descriptive and easier to understand (e.g., Region_Country, Sales_2019, Change_2024_vs_2023_pct).

####Type Conversion:

#### Converts sales columns (e.g., Sales_YYYY) from string format (with commas) to numeric types (integer or float).

#### Converts percentage change columns (e.g., Change_2024_vs_2023_pct) from string format (with '%') to numeric float format.

#### Clean Text Data:

#### Strips extra whitespace and special characters from country and region names.

#### Missing Data Check:

#### Verifies that no missing values were introduced during the cleaning process (none found).

#### Outlier Review:

#### Reviews the descriptive statistics for sales data. No outliers were removed or capped, as the wide range in sales values is expected due to global market diversity.

#### Duplicate Removal:

#### Checks for and ensures the absence of duplicate rows or entries.

#### Feature Engineering:

#### Adds a new Row_Type column to classify each row as either a 'Country', 'Continent/Major Region', 'Sub-Regional Aggregate', 'Global/Total Aggregate', or 'Other Aggregate'.

#### Data Validation:

#### Performs spot checks on percentage changes, comparing them to sales figures to ensure consistency and no calculation errors.

#### Ensures there are no negative sales figures.

#### Documentation & Final Output:

#### Includes comments explaining each cleaning step.

#### Outputs the final cleaned DataFrame, ready for analysis or export.

#### Cleaned Data Structure
#### The final cleaned dataset has the following structure:


#### Column	Data Type	Description
#### Region_Country	object (str)	Name of the country, region, or aggregate group.
#### Sales_2019	float64/Int64	Sales/registrations for 2019.
#### Sales_2020	float64/Int64	Sales/registrations for 2020.
#### Sales_2021	float64/Int64	Sales/registrations for 2021.
#### Sales_2022	float64/Int64	Sales/registrations for 2022.
#### Sales_2023	float64/Int64	Sales/registrations for 2023.
#### Sales_2024	float64/Int64	Sales/registrations for 2024.
#### Change_2024_vs_2023_pct	float64	Percentage change in sales from 2023 to 2024.
#### Change_2024_vs_2019_pct	float64	Percentage change in sales from 2019 to 2024.
#### Row_Type	object (str)	Classification of the row (e.g., 'Country', 'Global').
#### Note: Sales columns might be represented as float64 or nullable Int64 depending on implementation.

#### Key Observations and Considerations
#### Data Hierarchy: The dataset contains different levels of aggregation. Use the Row_Type column to filter for specific data types #### (e.g., country-level analysis) and avoid double-counting.

#### Wide Data Range: Sales figures vary significantly between large markets (e.g., China, USA) and smaller countries, which is expected. Consider using log scale plots or normalization for visualizations.

#### Kazakhstan Data: A footnote indicated that Kazakhstan's data includes Light Commercial Vehicles (LCVs) and Heavy Commercial Vehicles (HCVs). This context should be considered during analysis.

#### Potential Future Work / Next Steps
#### Analysis & Visualization: Perform exploratory data analysis (EDA) to visualize trends over time, compare regional performance, and identify countries with significant growth or decline.

#### Data Enrichment: Merge the cleaned dataset with external data sources (e.g., GDP, population, electric vehicle adoption rates) for deeper insights.

#### Time Series Modeling: Forecast future sales based on historical trends, possibly after reshaping the data into a long format.

#### Export Clean Data: Save the final cleaned data to a CSV or Excel format for use in visualization tools (e.g., Tableau, Power BI).
