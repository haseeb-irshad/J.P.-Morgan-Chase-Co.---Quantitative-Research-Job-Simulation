# JPMorgan Chase Quantitative Research Job Simulation

I completed this job simulation on Forage in August 2025. It has four tasks set by JPMorgan Chase & Co.'s quantitative research team. These include modelling natural gas prices, pricing a gas storage contract, predicting the probability that a borrower defaults and grouping FICO credit scores into ratings. Each task has its own Jupyter notebook. Forage provided both datasets.

## Task 1: Investigate and Analyse Price Data
- The data is monthly natural gas prices from 31 October 2020 to 30 September 2024.
- I modelled the price as a linear trend plus a yearly sine wave and fitted the four parameters with SciPy's `curve_fit`.
- The fitted curve estimates the price on any date from 31 October 2020 and extrapolates one year beyond the data to 30 September 2025.

## Task 2: Price a Commodity Storage Contract
- The pricing function takes any number of injection and withdrawal dates and volumes and returns the value of the contract.
- Buying and selling prices come from the Task 1 curve.
- Withdrawals are taken from the earliest gas still in storage (first in, first out), so the storage and financing costs depend on how long each volume is stored.
- Costs per MMBtu are $0.01 to inject or withdraw, $0.10 to transport each way, $0.02 a month for storage and $0.015 a month for financing. Storage is capped at 10 million MMBtu. The storage and financing costs are example values from CME Group.
- Transport delays are ignored and interest rates are assumed to be zero.

## Task 3: Credit Risk Analysis
- The loan data covers 10,000 borrowers, with their credit lines, debt, income, years employed, FICO score and whether they defaulted.
- I trained logistic regression and a random forest on 80% of the borrowers, compared how well each ranked the other 20% by risk (ROC AUC) and refitted the better model on all of the data.
- The expected loss on a loan is the probability of default × (1 - recovery rate) × the amount outstanding, with a recovery rate of 10%.

## Task 4: Bucket FICO Scores
- The function splits FICO scores into a chosen number of buckets, each with its own default rate. It picks the boundaries that maximise the log-likelihood of the observed defaults and finds them with dynamic programming.
- Lower ratings mean better credit scores.
- The function works on any table with a FICO score column and a default column.

## Results
- **Price model.** The fitted curve follows the seasonal pattern in the data and estimates a price of $12.50 per MMBtu on 30 September 2025, one year beyond the data.
- **Storage contract.** Injecting 10,000 MMBtu each July from 2021 to 2023 and withdrawing it the following February gives an estimated value of approximately $35,000.
- **Credit risk.** A borrower with $1,000 outstanding, 5 credit lines, $500 total debt, an income of $50,000, 5 years in employment and a FICO score of 600 and an income of $50,000 has a 14.4% probability of default and an expected loss of $130.
- **FICO buckets.** With seven buckets, the boundaries are 520, 552, 580, 611, 649 and 719.

## Notes
- The notebooks were run in Google Colab and load the data from Google Drive, so the file paths need changing to run them elsewhere.
