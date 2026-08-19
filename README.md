# Solar Plant Yield Prediction & SCADA Anomaly Detection

**Author:** Siddharth Aggarwal

## The Business Problem
Solar power plants suffer from hidden revenue leakage due to thermal derating and silent inverter failures. Standard SCADA monitoring often relies on manual audits to catch hardware drops. This project automates that process by predicting expected power yield and instantly flagging hardware anomalies when conversion efficiency breaks down under high temperatures.

## Architecture & Tech Stack
*   **Database:** Local PostgreSQL server handling raw generation and weather sensor time-series data.
*   **Data Pipeline:** Python (`sqlalchemy`, `pandas`) executing SQL joins to bridge database schemas and extract analytical features.
*   **Yield Forecasting (Machine Learning):** `XGBoost` regression.
*   **Fault Detection:** Scikit-Learn `IsolationForest`.

## Key Results
1.  **Thermal Lag Optimization:** Built a model that mathematically accounts for panel heat retention. The XGBoost pipeline outperformed standard Linear Regression, dropping the Root Mean Square Error (RMSE) by over 94 points.
2.  **Automated Fault Isolation:** Processed 33,266 active daylight sensor readings and isolated exactly 333 instances of silent hardware failure, where DC-to-AC conversion efficiency dropped to zero strictly between 40°C and 60°C. 

## Visual Proof
The left chart proves the forecasting accuracy of the XGBoost model. The right chart highlights the exact moments of thermal overload, identifying the 333 localized hardware faults that trigger immediate maintenance alerts.

<img width="1653" height="611" alt="Image" src="https://github.com/user-attachments/assets/37558404-fbf1-4b07-a547-8138c000808b" />
