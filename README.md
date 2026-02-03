# Parametric Climate Risk Modelling & Financial Pricing Calibration

### 📊 Project Overview
This project focuses on the design, calibration, and back-testing of a **Parametric Insurance Product** tailored for agricultural assets (Soybean) in Indore, India. By leveraging granular geospatial climate data (ERA5-Land), the model quantifies physical climate risk (excess rainfall) and translates it into a structured financial payout mechanism.

The objective was to engineer a data-driven insurance cover that balances **actuarial fairness** (Burn Cost Analysis) with **financial viability** (Target Premium Rate of 5%).

---

### 🎯 Key Objectives
* **Physical Risk Quantification:** Analyze 20 years of historical daily rainfall data (2005–2024) to identify extreme weather patterns affecting harvest periods.
* **Product Structuring:** Design a 3-slab parametric payout structure based on statistical percentiles rather than subjective assessment.
* **Actuarial Calibration:** Optimize trigger thresholds and payout magnitudes to strictly adhere to a **5% Pure Premium** target (₹2,500 per acre on a ₹50,000 Sum Insured).
* **Back-Testing:** Simulate the product's performance over historical epochs to assess payout frequency and "Basis Risk."

---

### 🛠️ Tech Stack & Data
* **Language:** Python 3.9+
* **Libraries:** `pandas` (Time-series analysis), `numpy` (Numerical computing), `matplotlib/seaborn` (Data visualization).
* **Data Source:** ERA5-Land Gridded Dataset (0.1° x 0.1° resolution).
* **Period:** October 1st – October 31st (Harvest Season), 2005–2024.
* **Tools:** Excel (for final ledger reporting and stakeholder presentation).

---

### ⚙️ Methodology

#### 1. Data Ingestion & Spatial Aggregation
Raw geospatial data (NetCDF/CSV) for the Indore block geometry was processed. Multiple grid points were spatially aggregated to derive a representative daily rainfall index for the region.

#### 2. Risk Indexing (Trigger Definition)
We defined "Excess Rainfall" using statistical thresholds derived from historical probability distributions:
* **Trigger 1 (Moderate Risk):** 80th Percentile event.
* **Trigger 2 (High Risk):** 90th Percentile event.
* **Trigger 3 (Catastrophic Risk):** 95th+ Percentile event.

#### 3. Pricing & Calibration (Burn Cost Analysis)
The core financial modeling involved an iterative calibration loop:
$$\text{Fair Premium} = \frac{\sum_{i=2005}^{2024} \text{Payout}_i}{N_{\text{years}}}$$
The triggers and payout amounts were adjusted iteratively until the *Average Payout* converged to the target premium of **₹2,500 (5%)**.

---

### 📂 Repository Structure

```

├── data/                   # Raw rainfall data and geometry files
├── notebooks/              # Jupyter notebooks for EDA and visualization
├── src/
│   ├── model.py            # Main script for threshold calculation and backtesting
│   └── utils.py            # Helper functions for data cleaning
├── results/                # Output Excel sheets and Back-testing logs
├── reports/                # PDF Report (Product Design Document)
└── README.md               # Project documentation

```

### 📈 Key Results
* **Optimized Premium Rate:** Achieved a historical burn rate of ~5.0%, aligning with commercial pricing targets.
* **Basis Risk Mitigation:** The tiered payout structure ensures that minor deviations in rainfall data do not result in "all-or-nothing" claim rejections, smoothing the volatility for the end-user.

### 🚀 How to Run
1.  Clone the repository:
    ```bash
    git clone [https://github.com/yourusername/parametric-climate-risk.git](https://github.com/sayandip30882636/Parametric-Climate-Risk-Modelling-Financial-Pricing-Calibration.git)
    ```
2.  Install dependencies:
    ```bash
    pip install pandas numpy matplotlib openpyxl
    ```
3.  Run the main modeling script:
    ```bash
    python src/model.py
    ```

---

### 📜 License
This project is open-source and available for educational and research purposes.

```
