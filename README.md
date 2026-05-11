# Nairobi Supply Chain EDA

Exploratory data analysis project for a Nairobi retail supply chain dataset. The analysis investigates stockout patterns, supplier reliability, regional availability, fulfillment performance, and data quality across 4,500 supply chain transactions.

## Project Overview

This project uses Python data analysis tools to answer practical supply chain questions:

- Which product categories experience the highest stockout rates?
- Which suppliers have the longest average lead times?
- How do stockouts change month over month?
- Which regions have the highest stockout counts?
- Which suppliers have the strongest fulfillment rates?

The main analysis is contained in [`Supply_two_eda.ipynb`](Supply_two_eda.ipynb), with the source data in [`Supply-Chain-Dataset.csv`](Supply-Chain-Dataset.csv).

## Key Findings

- The dataset contains 4,500 records across 2023 & 2024.
- Data quality is strong: no missing values, duplicate transaction IDs, invalid dates, or fulfillment anomalies were found.
- Overall stockout rate is 3.67%, with 165 stockout events.
- Dairy has the highest category stockout rate at 6.69%.
- Brookside Dairy has the longest average lead time at 11.82 days.
- Westlands has the highest number of stockout events, with 28 recorded stockouts.
- Supplier fulfillment rates are closely clustered, ranging from 92.37% to 92.90%.

## Repository Contents

| File | Description |
| --- | --- |
| `Supply-Chain-Dataset.csv` | Raw supply chain transaction dataset |
| `Supply_two_eda.ipynb` | Jupyter notebook containing cleaning, analysis, and visualizations |
| `REPORT.md` | Written project report with methodology, findings, and recommendations |
| `Wk 01 - Session Guide (3).pdf` | Supporting session guide used for the exercise |

## Dataset Fields

| Column | Description |
| --- | --- |
| `TransactionID` | Unique transaction identifier |
| `Date` | Transaction date |
| `Product_Name` | Product involved in the transaction |
| `Category` | Product category |
| `Supplier` | Supplier name |
| `Units_Ordered` | Number of units ordered |
| `Units_Received` | Number of units received |
| `Units_Sold` | Number of units sold |
| `Stock_On_Hand` | Available inventory after transaction |
| `Lead_Time_Days` | Supplier lead time in days |
| `Stockout_Flag` | Whether a stockout occurred |
| `Region` | Nairobi region or route |

## Setup

Create and activate a virtual environment:

```bash
python -m venv .venv
.venv\Scripts\activate
```

Install the required packages:

```bash
pip install pandas numpy matplotlib seaborn jupyter
```

## How to Run

Start Jupyter:

```bash
jupyter notebook
```

Open `Supply_two_eda.ipynb` and run the cells from top to bottom. The notebook loads the CSV, creates date features, checks data quality, answers the business questions, and generates visual dashboards.

## Analysis Workflow

1. Load analysis libraries and the supply chain dataset.
2. Parse dates and create time-based fields such as year, month, quarter, and day of week.
3. Assess data quality by checking missing values, duplicate transaction IDs, invalid dates, and fulfillment anomalies.
4. Calculate stockout rates, supplier lead times, fulfillment rates, and regional stockout patterns.
5. Visualize the findings using bar charts, a monthly trend chart, and a regional/category stockout heatmap.
6. Summarize business insights and limitations.

## Recommendations

- Prioritize stockout prevention for Dairy and high-risk products such as Brookside Milk 500ml and Potatoes 2kg.
- Review Brookside Dairy, Bakeries Ltd, and Chandaria Industries for lead time improvement opportunities.
- Monitor Westlands, Thika Road, and Mombasa Road more closely because they show the highest stockout counts.
- Add operational fields such as delivery cost, order status, supplier capacity, transport delays, and warehouse handling notes to support root-cause analysis.

## Limitations

The dataset shows what happened but does not fully explain why stockouts or delays occurred. It lacks supplier capacity, transport, payment, warehouse process, promotion, and customer demand context, so causal conclusions should be treated carefully.
