# ASG Airlines Data Pipeline Architecture

## Pipeline Flow

Raw Excel File
↓
Python / Pandas
↓
Data Profiling & Quality Checks
↓
Data Cleaning & Transformation
↓
Clean Analytical CSVs
↓
Power BI Data Model
↓
Interactive Power BI Dashboard

## Data Flow

1. The raw airline Excel workbook is used as the source dataset.
2. Python and Pandas are used to load and profile the four datasets.
3. Data quality checks identify duplicates, missing values, invalid values, and time anomalies.
4. The datasets are cleaned and transformed for analytics.
5. Cleaned datasets are exported as CSV files.
6. The CSV files are loaded into Power BI.
7. Power BI relationships and visuals are used to create the final dashboard.
## Data Model

The Power BI model contains the following datasets:

- flight_id_reference — reference table for flight IDs
- flights_clean — cleaned flight-level data
- passenger_id_reference — reference table for passenger IDs
- passengers_clean — passenger data
- bookings_clean — booking data
- payments_clean — payment data

Key relationships:

- flight_id_reference → flights_clean
- flight_id_reference → bookings_clean
- passenger_id_reference → passengers_clean
- passenger_id_reference → bookings_clean
- bookings_clean → payments_clean
## Assumptions

- Exact duplicate flight records were removed.
- Missing or UNKNOWN airline values were standardized as `Unknown`.
- Missing or INVALID booking statuses were standardized as `Unknown`.
- Flight duration was taken from the provided duration field after converting it to minutes.
- Overnight flights were identified when the arrival date is later than the departure date.
- The flight record `SJ192` was flagged as a time anomaly because its arrival timestamp is earlier than its departure timestamp.
- The conflicting flight ID `6F250` was retained and flagged rather than arbitrarily removing one record.
- Passenger ID conflicts were retained and represented using a reference table.
- Missing or invalid payment amounts were converted to unknown numeric values rather than being guessed.
## Cleaning and Transformation Logic

### Flights
- Removed exact duplicate records.
- Standardized missing and UNKNOWN airline values.
- Converted flight duration into minutes.
- Created a route field using source and destination.
- Identified overnight flights using departure and arrival dates.
- Created a time anomaly flag for inconsistent timestamps.
- Created flags for conflicting flight IDs.

### Bookings
- Standardized missing and INVALID booking statuses as Unknown.
- Retained booking and seat information for analytics.
- Passenger and flight relationships were validated.

### Passengers
- Identified missing last names.
- Retained passenger records with data-quality issues instead of deleting them.
- Created a passenger ID reference table to identify conflicting passenger IDs.

### Payments
- Converted payment amounts to numeric values.
- Missing and INVALID amounts were treated as unknown.
- Payment methods were retained for analysis.
## Key Performance Indicators

The Power BI dashboard includes the following KPIs:

- Total Flights
- Average Flight Duration
- Overnight Flights
- Time Anomalies
- Anomaly Percentage
- Unique Flight IDs
- Unique Routes
- Flight Distribution by Airline
- Route-wise Flight Traffic
- Average Flight Duration by Airline

## Power BI Dashboard

The Power BI dashboard contains five pages:

1. Airlines Overview
   - Total flights
   - Average flight duration
   - Overnight flights
   - Time anomalies
   - Flight distribution by airline
   - Top routes
   - Airline slicer

2. Duration analysis
   - Unique flight IDs
   - Average duration
   - Overnight flights
   - Time anomalies
   - Average duration by airline
   - Route traffic

3. Route Performance
   - Top 10 routes by flight count
   - Average flight duration by route
   - Airline slicer

4. Airline Trends
   - Flight count by airline
   - Average flight duration by airline
   - Overnight flights by airline
   - Airline slicer

5. Delay & Anomaly Insights
   - Time anomaly count
   - Anomaly percentage
   - Details of the anomalous flight records
   - Airline slicer