Markdown

# Issue ID: plot_issue_001

## Problem
 - Lice range from 0-25 is incorrect considering the data suggests it should be in the range of 0-2

## Evidence
 - Colour bar on the right hand side of the figure shows colour values up to 25
 - Colour of the heatmap datapoints on the plot are the same colour with no variance suggesting the data is all the same which is false
 - Expected range based on data knowledge is ~0-2

## Hypothesis
Possible causes:
 - incorrect aggregation (mean instead of sum)
 - two data streams mixed up (northerly coordinates and avg sea lice)

## Fix (to investigate)
 - check df["lice_avg"].describe()
 - confirm original data definition
 - verify grouping logic

## Lesson 
Always validate value ranges before plotting spatial data.

# Pre-Plot Validation Check

## Step 1 — Summary statistics
Used df.describe() to check value distributions.

## Step 2 — Range validation
Checked for:
- lice_avg < 0 or unusually high values
- invalid coordinate ranges

## Step 3 — Distribution check
Histogram used to inspect skew/outliers in lice_avg.

## Step 4 — Spatial sanity check
Scatter plot used to verify coordinate structure.

## Key rule established
All spatial datasets must pass:
- numeric validity check
- range plausibility check
- distribution sanity check

before plotting heatmaps.