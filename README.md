# JPMorgan Chase Quantitative Research Job Simulation

This repository contains my completed work for the **JPMorgan Chase & Co. Quantitative Research Job Simulation** on Forage.  
The simulation involved four tasks covering **data analysis, pricing models and credit risk** - designed to mirror real challenges faced by quantitative researchers.

---

## 📌 Tasks Completed

### **Task 1: Investigate and Analyse Price Data**
- Downloaded monthly natural gas price data (Oct 2020 – Sep 2024).
- Analysed historical time series to estimate purchase prices on arbitrary dates.
- Built a forecasting function to extrapolate prices one year into the future.
- Visualised data to identify seasonal patterns and possible drivers of variation.

### **Task 2: Price a Commodity Storage Contract**
- Developed a prototype pricing model for natural gas storage contracts.
- Model inputs included:
  - Number of injections and withdrawals
  - Injection and withdrawal dates
  - Injection/withdrawal rates
  - Storage capacity limits
  - Storage costs
  - Transportation costs
- Function outputs the value of the contract under these conditions.
- Assumed no transport delay and zero interest rates.

### **Task 3: Credit Risk Analysis**
- Analysed borrower data (income, outstanding loans, prior defaults).
- Built models to predict **probability of default (PD)**.
- Calculated **expected loss (EL)** of the loan with a 10% recovery assumption.
- Explored multiple approaches (e.g. regression, random forests) and compared results.

### **Task 4: Bucket FICO Scores**
- Designed a **quantisation algorithm** to map continuous FICO scores into discrete ratings.
- Implemented a **dynamic programming** solution to find optimal bucket boundaries.
- Ratings were assigned so that **lower rating = better credit score**.
- Produced a reusable rating map to support future datasets.

---

## 🛠️ Technologies Used
- **Python**: NumPy, pandas, matplotlib, SciPy, scikit-learn
- **Jupyter Notebook**: development and visualisation

---

## 🚀 How to Run
1. Clone the repository:
   ```bash
   git clone https://github.com/<your-username>/<repo-name>.git
   cd <repo-name>
