# RECWn: Pakistani Air Quality Crisis 2025-2026

## 1. Report: Executive Summary

This project presents a comprehensive machine learning framework for predicting PM2.5 concentration levels across 10 major Pakistani cities during the critical winter pollution season (November 2025 – February 2026). Analyzing **21,840 hourly observations** spanning 91 days, the study demonstrates exceptional predictive accuracy while uncovering critical environmental insights about Pakistan's worsening air quality crisis.

**Key Findings:**

- **Faisalabad** emerged as the most polluted city (155.7 μg/m³ average PM2.5), exceeding WHO safe limits by **4.4×**
- **40%** of all observations fall under the "Unhealthy" AQI category
- Peak pollution occurs during **early morning hours (6–8 AM)**, correlating with morning rush hour and temperature inversions
- Strong negative correlation (**r = -0.33**) between wind speed and PM2.5 confirms wind's pollution-dispersal effect

---

## 2. Evaluation: Methodology & Performance

### 2.1 Data Foundation
- **Source**: Open-Meteo API
- **Coverage**: 10 major Pakistani cities (Lahore, Karachi, Islamabad, Rawalpindi, Faisalabad, Multan, Peshawar, Quetta, Rahim Yar Khan, Sialkot)
- **Features**: 26 original columns + 13 engineered features (total: 39)
- **Data Quality**: 100% complete (zero missing values)

### 2.2 Feature Engineering Strategy
Advanced feature engineering created:
- **Lag Features**: 1h, 3h, 6h, 24h historical PM2.5 values
- **Rolling Statistics**: 3h, 6h, 24h moving averages
- **Cyclical Encoding**: Hour and month encoded using sine/cosine transformations
- **Interaction Features**: Temperature-humidity product, wind speed-direction components

### 2.3 Model Performance
**Baseline XGBoost Model Achieved:**
- **R² Score**: 0.9991 (exceptional fit)
- **RMSE**: 1.62 μg/m³ (minimal prediction error)
- **MAPE**: 1.17% (high precision)

**Advanced Architecture:** Transformer-BiLSTM hybrid with multi-horizon forecasting (6h, 12h, 24h)

### 2.4 Critical Correlations Discovered

| **Relationship** | **Correlation (r)** | **Interpretation** |
|:-----------------|:-------------------:|:--------------------|
| PM2.5 ↔ PM10 | +0.97 | Strong co-emission sources |
| PM2.5 ↔ SO2 | +0.59 | Industrial combustion link |
| PM2.5 ↔ NO2 | +0.52 | Vehicle emission link |
| PM2.5 ↔ Wind Speed | -0.33 | Wind dispersion effect |
| PM2.5 ↔ Humidity | +0.33 | Hygroscopic growth of particles |

---

## 3. Conclusion: Key Insights & Implications

### 3.1 Pollution Hotspots
**Top 5 Most Polluted Cities:**
1. **Faisalabad**: 155.7 μg/m³ (industrial hub)
2. **Multan**: 136.8 μg/m³
3. **Lahore**: 126.8 μg/m³
4. **Rawalpindi**: 92.3 μg/m³
5. **Rahim Yar Khan**: 87.5 μg/m³

### 3.2 Temporal Patterns
- **Peak Hours**: 6–8 AM (morning inversion + rush hour)
- **Lowest Levels**: 3–5 PM (afternoon dispersion)
- **Weekend Effect**: Marginal difference (suggests continuous emissions)
- **Seasonal Trend**: Winter smog significantly elevated

### 3.3 Air Quality Distribution
- **Unhealthy**: 40.1%
- **Moderate**: 22.3%
- **Unhealthy for Sensitive Groups**: 19.2%
- **Very Unhealthy**: 12.0%
- **Good**: 3.5%
- **Hazardous**: 2.9%

### 3.4 Model Interpretability
- **Top Feature**: `pm2_5_rolling_3h` (80.6% importance)
- Confirms that recent pollution levels are strongest predictors
- Weather variables provide critical modulating effects

---

## 4. Way Forward: Recommendations & Future Work

### 4.1 Policy & Public Health Recommendations

**Immediate Actions:**
1. **Targeted Alerts**: Implement early warning system for Faisalabad, Multan, and Lahore during 6–8 AM peak hours
2. **Emission Controls**: Strengthen industrial regulations in Faisalabad (correlation with SO₂ suggests industrial sources)
3. **Traffic Management**: Consider congestion pricing or odd-even schemes during morning rush hours
4. **Public Health Advisories**: Issue real-time AQI-based health recommendations

**Infrastructure Needs:**
- Expand monitoring network beyond 10 cities
- Deploy low-cost sensors in high-risk neighborhoods
- Integrate weather forecasting with pollution prediction

### 4.2 Technical Enhancements

**Model Improvements:**
- Incorporate satellite aerosol optical depth (AOD) data
- Add regional transport modeling (HYSPLIT trajectories)
- Implement ensemble methods combining XGBoost, LightGBM, and deep learning
- Develop spatio-temporal graph neural networks for inter-city pollution transport

**Deployment Roadmap:**
1. **Phase 1**: API deployment for real-time predictions (3 months)
2. **Phase 2**: Mobile app integration with personalized health alerts (6 months)
3. **Phase 3**: Policy dashboard for urban planners (9 months)
4. **Phase 4**: Integration with smart city IoT infrastructure (12 months)

### 4.3 Future Research Directions

1. **Source Apportionment**: Use model SHAP values to quantify contribution of traffic vs. industry
2. **Health Impact Assessment**: Link predictions to hospital admission data
3. **Climate Change Projections**: Extend model to 2030–2050 scenarios
4. **Economic Impact Analysis**: Quantify productivity losses from poor air quality

---

## 5. Project Impact

| **Metric** | **Achievement** |
|:-----------|:----------------|
| Cities Analyzed | 10 major urban centers |
| Data Completeness | 100% |
| Prediction Accuracy | 99.9% (R²) |
| Feature Engineering | 13 new predictive features |
| Worst-City PM2.5 | 4.4× WHO limit |
| Population at Risk | ~100 million (estimated) |

This project establishes a **deployment-ready system** providing actionable insights for environmental policy, public health alerts, and emission control strategies across Pakistani urban centers. The combination of exceptional predictive accuracy and comprehensive exploratory analysis makes it a valuable tool for both immediate public health protection and long-term urban planning.

---

**Contributors:**
- **Part 1 (EDA & Baseline)**: Hammad zahid
- **Part 2 (Advanced Deep Learning)**: hammadansari7

*“Environmental Impact | Health Alert System | Smart City Integration”*
