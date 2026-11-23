# Bakery Inventory & Waste Analysis

## Project Overview

This project examines inventory production and waste in a bakery and grocery retail dataset containing **19,321 records** across three stores, covering the period from 1 January 2023 to 31 December 2024.

The analysis investigates how much recorded production remains unsold and identifies where unsold inventory is concentrated. It examines waste across products, product categories, perishability levels, stores and seasons to determine which factors are most closely associated with higher waste.

The project uses Python for exploratory data analysis (EDA), with a focus on translating inventory data into measurable business findings.

## Business Questions

The analysis addresses the following questions:

1. How much inventory goes unsold?
2. Which products generate the most waste?
3. Does perishability influence waste?
4. Are stores producing more than they sell?
5. Which stores manage inventory most efficiently?
6. Does seasonality influence product waste?
7. Does production efficiency vary by category?
8. How do product, shelf life, perishability, store and season relate to waste when examined together?

## Tools & Technologies

- Python: Data analysis and manipulation
- Pandas: Data aggregation and analysis
- NumPy: Numerical operations
- Matplotlib: Data visualisation
- Seaborn: Statistical visualisation
- Jupyter Notebook: Analysis and documentation

## Analytical Approach

### 1. Exploratory Data Analysis

The initial analysis examines the dataset's structure, dimensions, data types, missing values and duplicate records.

Inventory-related fields are selected for the analysis, including:

- `Units_Produced`
- `Units_Sold`
- `Unsold_Units`
- `Waste_Pct`
- `Shelf_Life_Days`
- `Product`
- `Category`
- `Perishability`
- `Store_ID`
- `Season`

Customer, pricing and payment fields are outside the scope of this project.

### 2. Bivariate Analysis

The analysis compares inventory waste across individual dimensions to identify where unsold inventory is concentrated.

The main comparisons include:

- Total production, sales and unsold units.
- Product-level waste rates and unsold quantities.
- Waste across perishability classifications.
- Store-level inventory performance.
- Category-level production efficiency.
- Seasonal waste patterns.

### 3. Multivariate Analysis

Multiple dimensions are examined together to investigate whether the patterns identified during bivariate analysis remain consistent.

Visualisations include:

- Scatter plot of shelf life against waste percentage, grouped by perishability.
- Heatmap of average waste percentage by store and category.
- Heatmap of average waste percentage by product and season.

## Key Findings

### Overall Inventory Performance

- 81,563 units were recorded as produced, of which 58,867 were sold and 22,696 remained unsold.
- Approximately 27.8% of recorded production remained unsold.
- The typical record had one unsold unit. Approximately 85% of unsold units were single-unit leftovers, suggesting that unsold inventory is widespread rather than concentrated in a small number of large overproduction events.

### Product & Category Performance

- Category is the strongest differentiator in pooled waste rates, ranging from 17.81% for Savoury Bakery to 39.13% for Cakes.
- Peanut Butter (45.66%), Jam (43.67%), Butterscotch Cake (43.58%), Honey (43.21%) and Pineapple Cake (43.00%) have the highest pooled product waste rates.
- Chocolate Cake has the largest absolute unsold quantity among the ten highest-waste products, with 623 unsold units.
- Indian Bakery accounts for the highest number of unsold units (5,485), reflecting its larger production volume.

### Perishability & Shelf Life

- Perishability shows no clear relationship with waste. Average record-level waste ranges from 32.99% to 37.13% across perishability classifications.
- Very High perishability items have the lowest average waste percentage, while Medium perishability items have the highest.
- Low perishability products account for the largest number of unsold units (8,595), largely because of their production volume.
- The scatter plot shows no visible relationship between shelf life and waste percentage. Products with longer shelf lives can still exhibit relatively high waste.

### Store Performance

- Pooled waste rates are relatively similar across all three stores:
  - ST01: 27.46%
  - ST03: 27.81%
  - ST02: 28.26%
- The difference between the highest and lowest store waste rates is only 0.8 percentage points.
- Category-level waste patterns are also consistent across stores, suggesting that product category matters more than store location in explaining the observed differences.

### Seasonal Patterns

- Seasonal pooled waste rates range from 27.17% in Monsoon to 28.65% in Summer.
- Product waste rankings remain relatively stable across seasons.
- No product varies by more than five percentage points across seasons, while 17 of the 35 products vary by two points or less.
- Product-level differences are substantially larger than seasonal differences.

## Metric Definitions

Two waste measures are used throughout the analysis. They should not be interpreted interchangeably.

**Pooled Waste Rate**

Calculated as:

`Total Unsold Units / Total Units Produced * 100`

This measure weights each record by production volume and is used for the headline inventory, product, category, store and seasonal comparisons where applicable.

**Average Record-Level Waste Percentage**

Calculated as the mean of the existing `Waste_Pct` values.

This measure gives every record equal weight, regardless of production volume. Consequently, it produces higher percentages than pooled waste rates in this dataset.

## Limitations

Several data and analytical limitations affect the interpretation of the findings:

- Every record contains at least one sold unit and one unsold unit. Consequently, the waste rates describe records with leftover inventory and should not automatically be interpreted as the bakery's overall waste rate.
- The dataset contains order-line records with `Order_ID`, `Quantity` and `Total_Bill`. It is unclear whether inventory fields represent individual order lines or production figures repeated across orders. This creates uncertainty around the reliability of aggregated production and waste totals.
- `Waste_Pct` is capped at 50% and takes discrete values, reflecting the influence of relatively small batch
