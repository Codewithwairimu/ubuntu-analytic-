# Nairobi Supply Chain EDA Report

## Executive Summary

This report summarizes an exploratory data analysis of a Nairobi supply chain dataset containing 4,500 transaction records from 2023-01-01 to 2024-12-31. The project focused on data quality, stockout risk, supplier performance, regional availability, and fulfillment reliability.

The dataset is clean and suitable for exploratory analysis. No missing values, duplicate transaction IDs, invalid dates, or cases where `Units_Received` exceeded `Units_Ordered` were found. The overall stockout rate is 3.67%, representing 165 stockout events.

The main operational risks are concentrated in specific categories, products, suppliers, and regions. Dairy has the highest category stockout rate, Brookside Dairy has the longest average lead time, and Westlands has the highest stockout count.

## Objectives

The analysis aimed to answer five business questions:

1. Which product categories have the highest stockout rates?
2. Which suppliers have the longest average lead times?
3. How do stockouts change over time?
4. Which regions experience the most stockouts?
5. Which suppliers have the best or weakest fulfillment rates?

## Data Description

The source dataset is `Supply-Chain-Dataset.csv`.

| Metric | Value |
| --- | ---: |
| Records | 4,500 |
| Columns | 12 |
| Date range | 2023-01-01 to 2024-12-31 |
| Total units ordered | 1,247,417 |
| Total units received | 1,155,321 |
| Total units sold | 647,060 |
| Average lead time | 11.54 days |
| Average stock on hand | 162.98 units |
| Stockout events | 165 |
| Overall stockout rate | 3.67% |

The dataset includes transaction IDs, dates, products, categories, suppliers, ordered and received units, sold units, stock on hand, lead time, stockout status, and region.

## Methodology

The analysis was completed in the Jupyter notebook `Supply_two_eda.ipynb` using Python, pandas, NumPy, Matplotlib, and Seaborn.

The workflow included:

- Loading the CSV data into a pandas DataFrame.
- Parsing the `Date` field with day-first formatting.
- Creating time-based features: year, month, quarter, and day of week.
- Checking data quality across missing values, duplicates, invalid dates, and logical fulfillment errors.
- Aggregating stockout rates by category and region.
- Aggregating average lead time and fulfillment rate by supplier.
- Visualizing patterns with bar charts, line charts, and a heatmap.

## Data Quality Findings

| Check | Result |
| --- | ---: |
| Missing values | 0 |
| Duplicate transaction IDs | 0 |
| Invalid parsed dates | 0 |
| Rows where received units exceed ordered units | 0 |
| Data quality score | 100.0% |

The dataset is internally consistent for the checks performed. This makes it reliable for descriptive analysis, although it still lacks several operational fields needed for root-cause analysis.

## Business Findings

### Stockout Risk by Category

Dairy has the highest stockout rate at 6.69%, followed by Baby at 4.90%, Noodles at 4.67%, Produce at 4.53%, and Bakery at 4.21%.

| Category | Stockout Rate |
| --- | ---: |
| Dairy | 6.69% |
| Baby | 4.90% |
| Noodles | 4.67% |
| Produce | 4.53% |
| Bakery | 4.21% |

This suggests that stockout prevention should focus first on chilled dairy items and other fast-moving household essentials.

### High-Risk Products

The products with the highest stockout rates include:

| Product | Records | Stockouts | Stockout Rate |
| --- | ---: | ---: | ---: |
| Potatoes 2kg | 308 | 22 | 7.14% |
| Brookside Milk 500ml | 284 | 19 | 6.69% |
| Pampers Size 4 | 286 | 14 | 4.90% |
| Indomie Noodles | 300 | 14 | 4.67% |
| Bread 400g | 309 | 13 | 4.21% |

Potatoes 2kg and Brookside Milk 500ml stand out as the strongest product-level stockout risks.

### Supplier Lead Time

Average lead times are relatively close across suppliers, but Brookside Dairy has the longest lead time at 11.82 days.

| Supplier | Average Lead Time | Fulfillment Rate |
| --- | ---: | ---: |
| Brookside Dairy | 11.82 days | 92.47% |
| Bakeries Ltd | 11.78 days | 92.53% |
| Chandaria Industries | 11.78 days | 92.84% |
| Export Trading Group | 11.67 days | 92.37% |
| KWAL | 11.61 days | 92.90% |

Lead time differences are not extreme, but small delays can still affect availability for categories with short shelf lives or high demand volatility.

### Regional Stockouts

Westlands has the highest number of stockout events, followed by Thika Road and Mombasa Road.

| Region | Records | Stockouts | Stockout Rate |
| --- | ---: | ---: | ---: |
| Westlands | 624 | 28 | 4.49% |
| Thika Road | 647 | 26 | 4.02% |
| Mombasa Road | 635 | 25 | 3.94% |
| Kiambu | 625 | 22 | 3.52% |
| Ngong Road | 666 | 23 | 3.45% |
| Karen | 636 | 21 | 3.30% |
| Eastleigh | 667 | 20 | 3.00% |

Westlands should be reviewed first for replenishment planning, demand forecasting, and delivery timing.

### Monthly Stockout Pattern

The highest monthly stockout count occurred in 2023-08, with 13 stockout events. Other high-stockout months include 2024-10, 2024-02, and 2023-10.

This pattern suggests that monthly monitoring can help identify seasonal or planning-related pressure points, but more demand and operations data is needed to explain the causes.

## Recommendations

1. Prioritize Dairy stockout prevention.
   Dairy has the highest category stockout rate, and Brookside Milk 500ml is one of the highest-risk products. Review safety stock, ordering frequency, and supplier delivery reliability for dairy items.

2. Investigate Potatoes 2kg replenishment.
   Potatoes 2kg has the highest product-level stockout rate at 7.14%. Produce availability may be sensitive to demand swings, supplier harvest cycles, or transport timing.

3. Review Brookside Dairy lead time.
   Brookside Dairy has the longest average lead time and is connected to a high-risk category. A supplier review could identify whether delivery schedules, order cutoffs, or minimum order quantities are contributing to stockouts.

4. Strengthen monitoring in Westlands.
   Westlands has both the highest stockout count and the highest regional stockout rate. This region should receive closer inventory monitoring and replenishment checks.

5. Add operational root-cause fields.
   Future datasets should include delivery status, supplier capacity, transport delays, warehouse delays, order placement date, expected delivery date, actual delivery date, promotions, pricing, and demand forecasts.

## Limitations

The analysis is descriptive, not causal. The data can identify where stockouts and delays are concentrated, but it cannot fully explain why they occurred. For example, it does not include supplier capacity, vehicle availability, route conditions, payment delays, warehouse processing time, promotions, or customer demand drivers.

The analysis also treats each transaction record equally. A future version could weight stockout severity by lost sales, product margin, demand volume, or customer impact.

## Conclusion

The supply chain dataset is clean and useful for exploratory analysis. Overall stockout levels are moderate, but risk is concentrated in specific products, categories, suppliers, and regions. The strongest action areas are Dairy, Potatoes 2kg, Brookside Dairy lead times, and Westlands regional availability.

With additional operational fields, this project could move from descriptive EDA into root-cause analysis, forecasting, and inventory optimization.
