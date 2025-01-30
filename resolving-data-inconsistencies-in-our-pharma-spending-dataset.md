---
title: Resolving Data Inconsistencies in Our Pharma Spending Dataset
description: Discover how we identified and corrected discrepancies in our pharma spending dataset—particularly with Greece's 2021 PC_GDP—by refining our data filtering processes and script logic.
date: 2025-01-30
authors: [Anuar Ustayev]
---

## Introduction

We recently received feedback from one of our users regarding a discrepancy in our data: they noticed that Greece’s 2021 pharmaceutical spending as a percentage of GDP (`PC_GDP`) on our platform significantly differed from the value reported by the OECD (40.9 on our site vs. 2.5 on the OECD website). This prompted an investigation into our data processing pipeline, revealing issues related to new columns, quarterly data, and labeling changes. Below is an overview of the problem, how we addressed it, and a glimpse at the code changes implemented to correct the dataset.

## The Issue

- **User Complaint**:
  *“Greece 2021 PC_GDP on your website is 40.9, on OECD's website is 2.5. Thank you!”*
- **Diagnosis**:
  During the investigation, we discovered that our pipeline was inadvertently mixing annual and quarterly data. Additionally, some column names in the updated dataset had changed, leading to filtering issues. As a result, our final dataset incorrectly displayed larger values instead of the correct annual data.

## The Fixes

To resolve the issues and ensure our numbers match official data sources, we introduced the following changes:

1. **Filtering for Annual Data Only**
   - We restricted our processing to rows where the length of the date (`TIME`) column is exactly 4 digits (i.e., annual entries).
2. **Specifying Correct Columns**
   - We only keep rows with `Measure = "USD_CAP"`, `Indicator = "PHARMAEXP"`, and `Subject = "TOT"`.
3. **Refining the Scripts**
   - By reviewing each script in the pipeline, we updated them to output only the relevant columns while discarding superfluous quarterly data.

## Code Changes

Below is an excerpt from the `diff` file showing how we updated the scripts in our data processing pipeline:

```diff
diff --git a/scripts/process.py b/scripts/process.py
index a7daced..b22548b 100644
--- a/scripts/process.py
+++ b/scripts/process.py
@@ -14,31 +14,32 @@ def usd_per_cap():
     with open('archive/pharma-spending.csv', 'r') as inp, open('archive/usd-cap.csv', 'w', newline='') as out:
         reader = csv.reader(inp)
         writer = csv.writer(out)
-        writer.writerow(('LOCATION', 'MEASURE', 'TIME', 'Value', 'Flag Codes'))
+        writer.writerow(('LOCATION', 'MEASURE', 'TIME', 'Value'))
         next(reader)  # Skip header
-        writer.writerows([(row[1], row[4], row[6], row[7], row[8]) for row in reader if row[4] == "USD_CAP"])
+        # Write rows where USD_CAP and TIME is only annual (4 digits)
+        writer.writerows([(row[1], row[4], row[6], row[7]) for row in reader if row[4] == "USD_CAP" and len(row[6]) == 4 and row[3] == 'TOT' and row[2] == 'PHARMAEXP'])

 def percent_health_spending():
     with open('archive/pharma-spending.csv', 'r') as inp, open('archive/perc-health-spend.csv', 'w', newline='') as out:
         reader = csv.reader(inp)
         writer = csv.writer(out)
-        writer.writerow(('LOCATION', 'MEASURE', 'TIME', 'Value', 'Flag Codes'))
+        writer.writerow(('LOCATION', 'MEASURE', 'TIME', 'Value'))
         next(reader)  # Skip header
-        writer.writerows([(row[1], row[4], row[6], row[7], row[8]) for row in reader if row[4] == "PC_HEALTHXP"])
+        writer.writerows([(row[1], row[4], row[6], row[7]) for row in reader if row[4] == "PC_HEALTHXP" and len(row[6]) == 4 and row[3] == 'TOT' and row[2] == 'PHARMAEXP'])

 ...
```

### Key Highlights

1. **Filtering Out Quarterly Data**:
   Checking `len(row[6]) == 4` ensures that only annual data points are included.

2. **Dropping Unused Columns**:
   We no longer need the “Flag Codes” column, so it was removed to streamline the dataset.

3. **Consolidating Parameters**:
   Additional checks for `Subject = 'TOT'` and `Indicator = 'PHARMAEXP'` ensure only the intended rows are retained.

4. **Clean and Consistent Headers**:
   Updated header rows in the CSV outputs to match the new file structure and exclude fields that are no longer necessary.

## Outcome and Next Steps

With these changes in place:

- Our final dataset now reflects **only** the **annual** “USD_CAP,” “PC_HEALTHXP,” and “PC_GDP” metrics, as intended.
- The erroneous data that caused the inflated numbers for Greece (and potentially other locations) has been filtered out.
- We have also improved the code readability and maintainability by clarifying the logic around data selection.

Moving forward, we’ll continue to monitor feedback and regularly audit our data pipelines to catch any similar issues before they affect our published dataset.

## Conclusion

This fix underscores the importance of thorough data validation and user feedback in maintaining accurate public datasets. We appreciate the user who brought the discrepancy to our attention, helping us ensure that our platform remains a reliable source of information for healthcare and economic data.

If you have any questions or further feedback, feel free to reach out or submit an issue on our GitHub repository. Your input is invaluable to us!
