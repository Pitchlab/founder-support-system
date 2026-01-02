# Get Year And Quarter Command

You are tasked with determining the year and quarter to run admin tassks for. 
Typically, admin tasks are done on the PRECEDING quarter. 

## Usage

```
/get-year-and-quarter
```

Example: `/get-year-and-quarter`

## Process

### Step 1: Determine PRECEDING Quarter (The One That Just Ended)

**CRITICAL**: VAT invoices are for the PRECEDING quarter (the one that just ended), NOT the current quarter!

Always use bash to get the current date and calculate the PRECEDING quarter:

```bash
# Get current year and month
date +"%Y %m"
```

Then determine PRECEDING quarter based on current month:
- Current Months 1-3 (Jan-Mar): Download Q4 of PREVIOUS YEAR
- Current Months 4-6 (Apr-Jun): Download Q1 of CURRENT YEAR
- Current Months 7-9 (Jul-Sep): Download Q2 of CURRENT YEAR
- Current Months 10-12 (Oct-Dec): Download Q3 of CURRENT YEAR

**Examples:**
- If current date is October 2025 (month 10), download Q3 2025 (July-September)
- If current date is January 2025 (month 1), download Q4 2024 (October-December)
- If current date is April 2025 (month 4), download Q1 2025 (January-March)

### Step 2: Output the Year and the Quarter

Output the Year and the Quarter

**Example:**
- Year is 2025 and quarter is Q3: Output `Administration for 2025, Q3`.