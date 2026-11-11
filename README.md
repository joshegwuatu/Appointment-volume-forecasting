# Appointment Volume Forecasting

This project uses the first operational dataset of Nexora Care to build a time-series forecasting model that predicts appointment volume at the clinic level. Using historical scheduling data, day-of-week effects, holiday calendars, and seasonal illness cycles, the model produces forward-looking estimates of demand over a rolling multi-week horizon.

## Project Overview

The goal is to improve forward planning for clinic operations by forecasting appointment demand. Because clinics operate with tight staffing and room capacity, even small changes in appointment volume can materially affect wait times, clinician workload, and scheduling efficiency. This project is designed to support administrators with earlier visibility into likely demand patterns.

## Exploratory Data Analysis (EDA)

The EDA work completed in [EDA/01-EDA.ipynb](EDA/01-EDA.ipynb) focused on understanding the appointment dataset, validating its quality, and checking whether the data was suitable for downstream forecasting.

### Data Loading and Initial Inspection

- Loaded the dataset from [data/AppointmentRecords.csv](data/AppointmentRecords.csv)
- Verified the table structure and reviewed the first rows
- Confirmed the dataset size and schema
- Inspected column-level metadata to understand the available fields and data types

### Data Quality Checks

The notebook performed a structured quality review covering the main data integrity issues:

- Duplicate rows and duplicate Appointment IDs
- Missing values by column
- Invalid or null date values in the appointment timestamp field
- Categorical variable review for values, frequency counts, and unique categories
- Checking for leading and trailing spaces in text fields
- Review of booking lead time values and negative lead-time cases

### Clinic and Identifier Validation

The dataset was reviewed for consistency across clinic identifiers:

- Verified the relationship between ClinicID and ClinicName
- Confirmed each clinic ID mapped consistently to a single clinic name
- Checked for missing clinic identifiers and missing clinic names
- No inconsistencies were found in these fields, so no cleaning was required

### Date and Time Validation

The appointment date field was validated for data quality and operational plausibility:

- Checked for missing appointment dates
- Confirmed all records contained valid appointment timestamps
- Reviewed the overall date range and the earliest/latest dates in the dataset
- Screened for future dates
- Assessing clinic-level gaps in appointment coverage by day of week

Findings from this review:

- The dataset spans 1 January 2024 through 31 December 2025
- No missing or future appointment dates were identified
- All records were retained for analysis
- Some clinics showed no appointments on Sundays, and one clinic started later than the others, which may reflect operating schedules rather than data quality problems

### Logical Consistency Checks

The EDA also validated relationships between fields that should align logically:

- Holiday flag vs. holiday name
- Seasonal flag vs. appointment month
- Appointment status distribution
- Booking lead-time range and plausibility

These checks were used to confirm that the data was internally consistent enough for modeling.

## Data Status

The dataset is now considered suitable for exploratory analysis and forecasting preparation. The notebook established a working understanding of the data structure, quality, and operational patterns before moving into modeling.

## Repository Structure

- [EDA/01-EDA.ipynb](EDA/01-EDA.ipynb): exploratory data analysis and validation work
- [data/AppointmentRecords.csv](data/AppointmentRecords.csv): appointment records used for analysis
- [README.md](README.md): project description and workflow summary

## Next Steps

Following the EDA, the project will move into:

1. Feature engineering for time-based and seasonal signals
2. Model selection for appointment volume forecasting
3. Validation and backtesting of forecasting performance
4. Final reporting and operational recommendations
