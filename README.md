# COVID-19 India Data Analysis

A SQL-based analysis of COVID-19 cases, testing, and vaccination data across Indian states and union territories using **Python, SQLite, SQL, and Pandas**.

## Project Overview

This project integrates three COVID-19 datasets into an in-memory SQLite database and uses SQL queries to analyze:

* State-level COVID-19 cases
* Case fatality rates
* Monthly new-case trends
* Testing positivity rates
* State-level vaccination activity

The analysis also includes data cleaning to handle inconsistent state names and appropriate treatment of cumulative time-series data.

## Datasets

The project uses three datasets:

* `covid_19_india.csv` — COVID-19 case, death, recovery, and cumulative case data
* `StatewiseTestingDetails.csv` — state-level COVID-19 testing data
* `covid_vaccine_statewise.csv` — state-level vaccination data

These datasets are loaded into three SQLite tables:

```text
cases
testing
vaccine
```

## Tech Stack

* **Python**
* **Pandas**
* **SQLite**
* **SQL**
* **Matplotlib**
* **Jupyter Notebook**

## Analysis Performed

### 1. Top 10 Most Affected States

Identifies the states with the highest cumulative confirmed COVID-19 cases and compares their deaths and recoveries.

### 2. Case Fatality Rate by State

Calculates the case fatality rate for states with more than 10,000 confirmed cases.

**Case Fatality Rate:**

```text
Deaths / Confirmed Cases × 100
```

### 3. Monthly New COVID-19 Cases

Derives monthly new cases from cumulative confirmed-case data using month-end values and the SQL `LAG()` window function.

This avoids incorrectly summing daily cumulative case counts.

### 4. State-Level Testing Positivity

Calculates state-level testing positivity using the latest available cumulative positive-test and total-sample figures.

**Testing Positivity Rate:**

```text
Positive Tests / Total Samples × 100
```

### 5. Total Vaccine Doses Administered

Ranks states by the total number of vaccine doses administered, excluding the India-level aggregate from the state comparison.

## Data Cleaning

The project handles inconsistencies in state names present in the source data, including variations such as:

* `Karanataka` → `Karnataka`
* `Himanchal Pradesh` → `Himachal Pradesh`
* `Maharashtra***` → `Maharashtra`

The cleaned state names are used for consistent state-level analysis.

## SQL Concepts Demonstrated

* `SELECT`
* `WHERE`
* `GROUP BY`
* `HAVING`
* `ORDER BY`
* Aggregate functions
* `CASE`
* `JOIN`
* Subqueries
* Common Table Expressions
* Window functions
* `LAG()`

## Visualizations

The notebook includes visualizations for:

* Top 10 states by confirmed COVID-19 cases
* Case fatality rate by state

## Key Skills Demonstrated

**SQL · SQLite · Python · Pandas · Data Cleaning · Data Analysis · Window Functions · Time-Series Analysis · Data Visualization**

## How to Run

### 1. Clone or download the repository

Ensure the project has the following structure:

```text
COVID-SQL-Analysis/
├── covid_sql_FINAL.ipynb
├── README.md
└── datasets/
    ├── covid_19_india.csv
    ├── StatewiseTestingDetails.csv
    └── covid_vaccine_statewise.csv
```

### 2. Install dependencies

```bash
pip install pandas matplotlib
```

### 3. Open the notebook

Open:

```text
covid_sql_FINAL.ipynb
```

in Jupyter Notebook, JupyterLab, or VS Code.

### 4. Run all cells

The notebook creates an in-memory SQLite database, loads the three datasets, executes the SQL analyses, and generates the visualizations.

## Data Note

The case and testing datasets contain cumulative measurements. Monthly trends and testing positivity are therefore calculated using appropriate cumulative-value handling rather than directly summing daily cumulative values.
