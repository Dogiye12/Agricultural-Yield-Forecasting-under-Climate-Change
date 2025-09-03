# 🌾 Agricultural Yield Forecasting under Climate Change

This repository demonstrates how **machine learning (ML)** can be applied to forecast **agricultural yields** under changing climate conditions.  
It uses **synthetic data** that captures temperature, precipitation, CO₂ concentration, soil quality, management practices, and remote sensing indices (NDVI, EVI, LST, Soil Moisture) to simulate yield responses to climate variability and change.

The pipeline integrates:
- Synthetic data generation (2000–2024, 40 regions)
- Feature engineering (climate, soil, management, remote-sensing proxies)
- Machine Learning models for forecasting
- Scenario analysis (+2 °C warming, −10% rainfall, +30 ppm CO₂)

---

## 🚀 Features
- Generates **synthetic dataset** of >1,000 samples across years and regions
- Trains:
  - **Random Forest Regressor**  
  - **Gradient Boosting Regressor**
- Evaluation metrics: MAE, RMSE, R² + parity plots
- Feature importance analysis
- Climate change scenario forecasting
- Exports results, models, and plots for analysis

---

## 📂 Project Structure
.
├── outputs_yield/
│ ├── agri_yield_synthetic.csv
│ ├── yield_rf.joblib
│ ├── yield_gbr.joblib
│ ├── parity_rf.png
│ ├── parity_gbr.png
│ ├── feature_importance_rf.png
│ ├── scenario_delta.csv
│ ├── scenario_hist_delta_t_ha.png
│ └── README_AgYieldDemo.txt
├── agricultural_yield_forecasting_under_climate_change.py
└── README.md

markdown
Copy code

---

## 📊 Dataset
The synthetic dataset includes:
- **Climate**: `temp_c`, `precip_mm`, `wind_ms`, `vpd_kpa`, `heatwave_days`, `co2_ppm`
- **Soil**: `soil_om_pct`, `soil_cation_meq`
- **Management**: `fert_kg_ha`, `irrigated`, `variety_score`
- **Remote Sensing Proxies**: `ndvi`, `evi`, `lst_c`, `soil_moisture`
- **Target**: `yield_t_ha` (crop yield in tons per hectare)

---

## 🧪 Methodology
1. **Data Generation**  
   Simulates 40 regions over 25 years (2000–2024), incorporating:
   - Long-term warming (+0.03 °C/year)
   - Rainfall variability
   - CO₂ fertilization effect
   - Soil fertility and irrigation
   - Remote-sensing indices linked to climate & management

2. **Model Training**  
   - RandomForestRegressor (baseline & feature importance)  
   - GradientBoostingRegressor (boosted ensemble)

3. **Evaluation**  
   - Metrics: MAE, RMSE, R²  
   - Plots: parity plots, feature importances  
   - Cross-validation with time-series splits

4. **Scenario Analysis**  
   - +2 °C warming  
   - −10% precipitation  
   - +30 ppm CO₂  
   Results saved in `scenario_delta.csv`

---

## ⚙️ Installation
```bash
git clone https://github.com/yourusername/Agricultural-Yield-Forecasting-under-Climate-Change.git
cd Agricultural-Yield-Forecasting-under-Climate-Change
pip install -r requirements.txt
requirements.txt

nginx
Copy code
numpy
pandas
scikit-learn
matplotlib
joblib
▶️ Usage
Run the demo script:

bash
Copy code
python agricultural_yield_forecasting_under_climate_change.py
This generates:

outputs_yield/agri_yield_synthetic.csv (synthetic dataset)

Trained models (yield_rf.joblib, yield_gbr.joblib)

Plots and scenario results

Quick Inference
python
Copy code
from joblib import load
import pandas as pd

df = pd.read_csv("outputs_yield/agri_yield_synthetic.csv")
X = df[['temp_c','precip_mm','wind_ms','vpd_kpa','heatwave_days','co2_ppm',
        'soil_om_pct','soil_cation_meq','fert_kg_ha','irrigated','variety_score',
        'ndvi','evi','lst_c','soil_moisture','lat','lon','elev_m']].values

# Load models
rf = load("outputs_yield/yield_rf.joblib")
gb = load("outputs_yield/yield_gbr.joblib")

# Predict yields
y_rf = rf.predict(X)
y_gb = gb.predict(X)
📈 Results (Synthetic Example)
Random Forest (test set):

MAE ≈ 0.35 t/ha

RMSE ≈ 0.55 t/ha

R² ≈ 0.85

Scenario (+2 °C, −10% rain, +30 ppm CO₂):

Average Δ yield ≈ −5%

Distribution exported in scenario_delta.csv

🌍 Applications
Climate-smart agriculture research

Crop yield forecasting

Climate risk and adaptation planning

Data-driven decision support for policymakers

📚 References
Lobell, D. B., et al. (2011). "Climate trends and global crop production." Science.

Asseng, S., et al. (2015). "Rising temperatures reduce global wheat production." Nature Climate Change.

Iizumi, T., & Ramankutty, N. (2016). "Changes in yield variability of major crops over the 20th century." Nature Plants.

📝 License
This project is released under the MIT License.

Author: Amos Meremu Dogiye
