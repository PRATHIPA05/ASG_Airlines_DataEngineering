ASG Airlines Data Engineering Case Study

Project Overview

This project builds an end-to-end data pipeline for ASG Airlines operational flight data.
It loads raw airline data, performs data quality checks, cleans and transforms the datasets, and prepares analytical data for Power BI reporting.
The project focuses on flight duration, route traffic, airline trends, and delay/anomaly analysis.

Technologies Used

- Python
- Pandas
- Jupyter Notebook
- Microsoft Power BI
- Excel
- draw.io

Project Structure

```text
ASG_Airlines_DataEngineering/
├── data/
│   └── raw/
│       └── UseCase - Airlines.xlsx
├── notebook/
│   └── data_profiling.ipynb
├── src/
├── output/
├── docs/
│   ├── architecture.md
│   └── ASG_Airlines_Architecture.drawio
├── ASG_Airlines_Dashboard.pbix
└── README.md
## Data Processing

The pipeline follows these main steps:

1. Load the four datasets from the Excel workbook.
2. Profile the datasets for missing values, duplicates, and invalid values.
3. Clean and standardize the data.
4. Transform flight duration into minutes.
5. Identify overnight flights and time anomalies.
6. Create analytical fields such as route.
7. Export cleaned datasets as CSV files.
8. Load the analytical datasets into Power BI.
9. Build interactive dashboards and KPI visualizations.
## Power BI Dashboard

The dashboard is organized into five pages:

- Airlines Overview
- Duration analysis
- Route Performance
- Airline Trends
- Delay & Anomaly Insights

The dashboard provides KPI cards, charts, tables, and airline slicers for interactive analysis.
## Data Quality

The pipeline performs data quality checks for:

- Missing values
- Duplicate records
- Invalid categorical values
- Invalid payment amounts
- Flight ID conflicts
- Passenger ID conflicts
- Inconsistent flight timestamps

Records with data-quality issues are flagged or standardized according to the defined cleaning rules.
## Key Results

- Total cleaned flight records: 1005
- Average flight duration: 164.62 minutes
- Overnight flights: 122
- Time anomalies: 1
- Unique flight IDs: 1004
- Unique routes: 30
- Highest flight traffic route: BOM → CCU
- Highest flight count by airline: IndiGo
## Architecture

The project architecture and data flow are documented in:

`docs/architecture.md`

An editable architecture diagram is available at:

`docs/ASG_Airlines_Architecture.drawio`
## How to Use

1. Place the raw Excel workbook in `data/raw/`.
2. Open `notebook/data_profiling.ipynb`.
3. Run the notebook cells to perform profiling, cleaning, transformation, and export.
4. Use the generated CSV files in the `output/` folder.
5. Open `ASG_Airlines_Dashboard.pbix` in Power BI to view the dashboard.
## Data Privacy

The source workbook contains passenger-related personal information.

Raw source data and passenger-level datasets containing PII are excluded from the GitHub repository.

Analytical outputs are used for reporting, while access to sensitive passenger information should be restricted to authorized users only.
