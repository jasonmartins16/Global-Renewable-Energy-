# 🌿 Green Energy Pulse: Forecasting System

## 📌 Project Overview
The **Green Energy Pulse System** is a dynamic forecasting engine designed to track and predict the *"Greenness"* of a city's power grid in real-time.  
Unlike static environmental scores, this **Pulse** fluctuates hourly based on live weather data (Solar & Wind) and grid demand.

This project demonstrates how to transition from **Batch Processing** (analyzing historical data) to **Live Forecasting** (predicting the next 24 hours/Short term forecasting system) using advanced feature engineering and Gradient Boosting models.

---

## 🚀 Key Features
- **Real-Time Methodology**: Analyzes shortwave radiation and wind speed at 100m to calculate energy potential.
- **Cyclical Time Encoding**: Uses Trigonometric transformations (Sine/Cosine) to help the model understand 24-hour continuity.
- **Temporal Lag Features**: Incorporates momentum using previous hours (t-1, t-2) for improved short-term accuracy.
- **Global Scalability**: Uses geospatial data (Latitude/Longitude) to generalize across 10+ global cities.

---

## 📊 The "Pulse" Formula
The Green Score is calculated using the following weighted index:

```
Score_Pulse = (0.001 × Shortwave Radiation) + (0.0333 × Wind Speed_100m)
            
```

---

## 🛠️ Tech Stack & Workflow

### 1️⃣ Data Processing
- **Pandas & NumPy**: Time-series manipulation and feature creation
- **Feature Engineering**:
  - `hour_sin` / `hour_cos`: Maps time onto a 2D circular space
  - `lags`: Uses historical data as predictors

### 2️⃣ Machine Learning
- **Models**: XGBoost / Random Forest Regressor
- **Validation**: Time-Series Split  
  *(Train: Jan 05–11 → Forecast: Jan 12)*
- **Performance**:  
  - **R² Score: 0.9357** (High reliability for hourly forecasts)

### 3️⃣ Visualization
- **Matplotlib & Seaborn**:
  - Actual vs Predicted Green Energy Pulse
  - Cities analyzed: New York, Mumbai, Tokyo, Berlin, Lagos, Sao Paulo, London, Cairo, Sydney and Beijing

---

## 📈 Results & Analysis
The model highlights **Momentum (Lag Features)** and **Solar Cycles** as the strongest contributors to green energy availability.

Thanks to cyclical encoding, the system successfully captures:
- Evening energy dips (Duck Curve)
- Midday and night-time renewable surges

---

## 🔮 Future Roadmap
- **Recursive Multi-step Forecasting** (24–48 hour horizon)
- **Live API Integration** (OpenWeather, Solcast)
- **Deep Learning Models** (LSTM for long-range seasonal memory)

---

🌱 *Dataset: https://www.kaggle.com/datasets/nudratabbas/global-green-energy-pulse-real-time-renewable*
