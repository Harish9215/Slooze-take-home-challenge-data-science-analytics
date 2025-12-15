# Slooze-take-home-challenge-data-science-analytics

## 📖 Project Overview
This project delivers a comprehensive data science solution for **Slooze**, a multi-location wine and spirits retailer. The objective was to transition from spreadsheet-based tracking to a robust, **data-driven inventory optimization system**.

Using historical transaction data (Sales, Purchases, Inventory, and Invoices), this analysis identifies inefficiencies in the supply chain, forecasts future demand, and recommends optimized procurement strategies to minimize costs and prevent stockouts.

## 💾 Dataset
**Note:** The dataset used for this analysis is hosted on Kaggle.
👉 **[Download the Dataset Here](https://www.kaggle.com/datasets/sloozecareers/slooze-challenge/data)**

Please download the files and place them in a folder named `slooze_challenge/` (or `data/`) in the same directory as the notebook.
## 🎯 Key Business Objectives
1.  **Demand Forecasting:** Predict future sales trends to automate replenishment and reduce stockouts.
2.  **Inventory Classification:** Prioritize management focus using Multi-Dimensional **ABC Analysis**.
3.  **Process Optimization:** Determine **Economic Order Quantities (EOQ)** and identify **Just-In-Time (JIT)** candidates to free up working capital.
4.  **Vendor Risk Management:** Analyze supplier lead-time variability to refine safety stock policies.

---

## 🛠️ Methodology & Approach

### 1. Data Integration & Cleaning
* **Unified Master Dataset:** Merged disparate data sources (Sales, Purchases, Beginning/Ending Inventory) to create a single source of truth.
* **Feature Engineering:** Calculated critical metrics such as *Lead Time* (Invoice Date - PO Date), *Gross Margin*, and *Demand Volatility (CV)*.
* **Data Quality:** Addressed missing "Receive Dates" by deriving fulfillment cycles from Invoice timestamps.

### 2. Advanced Analytics
* **Time Series Forecasting (SARIMA):**
    * Identified clear **weekly seasonality** in sales data.
    * Implemented a SARIMA model (Order: 1,1,1 | Seasonal: 1,1,1,7) to forecast demand 30 days out for top-performing SKUs.
* **Strategic ABC Analysis:**
    * Classified inventory not just by revenue, but by **Consumption Value** (Cost × Volume).
    * *Result:* Identified the "Vital Few" (A-Items) that drive 80% of costs but represent only a fraction of total SKUs.
* **Interactive EOQ Simulation:**
    * Built a dynamic tool to calculate the optimal order size that minimizes the sum of *Ordering* and *Holding* costs.
    * Filtered for **JIT Candidates**: High-volume items with low volatility ($CV < 0.5$).

### 3. Supply Chain Risk
* **Vendor Performance:** Analyzed order-to-invoice variability to identify suppliers that require higher safety stock buffers due to inconsistent delivery times.

---

## 📊 Key Insights & Visualizations

### 📉 Demand Forecasting
* **Weekly Patterns:** Sales show distinct weekly cycles (higher on weekends), which simple monthly averages miss.
* **Action:** Automated replenishment orders should be timed to arrive *before* the Friday peak.

### 📦 Strategic Inventory Matrix
* **High Cost / Low Volume:** Identified products that tie up significant capital with low turnover (Risk of Obsolescence).
* **Low Cost / High Volume:** Identified "Fast Movers" ideal for automated bulk reordering.

### 🚚 Vendor Reliability
* Analysis revealed significant lead-time variance among top vendors.
* **Recommendation:** Renegotiate SLAs with high-variance vendors or increase safety stock specifically for their products.

---

## 💻 Tech Stack
* **Language:** Python
* **Data Processing:** Pandas, NumPy
* **Visualization:** Matplotlib, Seaborn
* **Modeling:** Statsmodels (SARIMA, Seasonal Decompose)
* **Interactive Tools:** IPyWidgets (for EOQ cost simulation)

## 🚀 How to Run

### 1. Clone the Repository

Clone this repository using the following command:

```bash
git clone https://github.com/yourusername/slooze-inventory-analytics.git
```
### 2. Download the Data: Download the CSV files from Kaggle and unzip them into a folder named https://www.kaggle.com/datasets/sloozecareers/slooze-challenge/data

### 3. Install Requirements
Install the required Python packages using pip:
```
pip install pandas numpy matplotlib seaborn statsmodels ipywidgets
```

### 4. Launch the Notebook:
jupyter notebook Slooze_Challenge_Analysis.ipynb
