# ⚠️ Error Handling & Data Cleaning

## Issue
Date columns contained non-date values such as:
- Holiday
- Off
- Weekly Off

## Approach
- Attempted to convert date column to Date type
- Power Query flagged non-date values as errors
- Automatically filtered out error rows

## Benefit
This method:
- Avoids hard-coded filters
- Automatically adapts to new months
- Keeps the ETL logic future-proof
