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
- **Prescriptive Optimization**: Implementing the Resilient Energy Window (REW) Algorithm that doesn't just find "green" energy, but seeks out the most stable and sustained periods for energy-intensive tasks.

---

## 📊 The "Pulse" Formula
The Green Score is calculated using the following weighted index:

```
Score_Pulse = (0.001 × Shortwave Radiation) + (0.0333 × Wind Speed_100m)
            
```

---

## The Three Core Constraints

###  Constraint 1: The Quality Threshold ($Pulse \geq \tau$)
The system enforces a "Hard Safety" check. A window is only considered if every hour within that block maintains a Green Energy Pulse score above a user-defined threshold ($\tau$). This prevents tasks from starting during a "clean" period and finishing during a "dirty" one.

### Constraint 2: The Stability Index ($\min \sigma^2$)
Energy-intensive tasks often require consistency. The model calculates the Variance ($\sigma^2$) of the green score within the window. By minimizing variance, the system avoids "flickering" energy sources (highly volatile wind or intermittent clouds) in favor of steady, reliable green power.

### Constraint 3: The Duration Factor ($\max T_{duration}$)
The model prioritizes consecutive availability. It identifies the longest contiguous blocks of high-quality energy, ensuring that multi-hour tasks (like EV charging or industrial manufacturing) can complete without interruption.

---

## The Ranking Formula
To balance these competing objectives, each identified window is assigned a Rank Score. This allows the system to prioritize a "slightly less green but very stable" window over a "very green but volatile" one.

```
Rank Score = (μ_window / (σ²_window + 0.01)) × T_duration

μ/Mean Score: Rewards higher overall green energy penetration.
σ²/Variance: Penalizes volatility (stability is the denominator).
$T$/Duration: Linearly scales the value of the window by its length.

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

By implementing this optimization layer, the system moves beyond observation into active load-shifting:
- Grid Resilience: Reduces peak-hour stress by moving heavy loads to periods of high renewable surplus.
- Operational Safety: Protects sensitive machinery by ensuring energy source stability throughout the task duration.
- Carbon Transparency: Provides users with a "Stability Index" (0.0 to 1.0) to quantify the reliability of the green energy they are consuming.
  
---

## 🔮 Future Roadmap
- **Recursive Multi-step Forecasting** (24–48 hour horizon)
- **Live API Integration** (OpenWeather, Solcast)
- **Deep Learning Models** (LSTM for long-range seasonal memory)

---

🌱 *Dataset: https://www.kaggle.com/datasets/nudratabbas/global-green-energy-pulse-real-time-renewable*
