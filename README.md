Project Overview: The Green Energy Pulse System is a dynamic forecasting engine designed to track and predict the "Greenness" of a city's power grid in real-time. Unlike static environmental scores, this "Pulse" fluctuates hourly based on live weather data (Solar & Wind) and grid demand.This project demonstrates how to transition from Batch Processing (analyzing historical data) to Live Forecasting (predicting the next 24 hours/short term forecasting) using advanced feature engineering and Gradient Boosting models.

Key Features:
1. Real-Time Methodology: Analyzes shortwave radiation and wind speed at 100m to calculate energy potential.
2. Cyclical Time Encoding: Uses Trigonometric transformations (Sine/Cosine) to allow the model to understand the continuity of 24-hour cycles.
3. Temporal Lag Features: Incorporates "momentum" by feeding the model data from previous hours (t-1, t-2) to improve short-term accuracy.
4. Global Scalability: Includes geospatial data (Latitude/Longitude) to adapt to different climate zones across 10+ global cities.

The "Pulse" Formula: Through reverse-engineering of urban energy datasets, the system utilizes the following weighted index for the Green Score: Score_{Pulse} = (0.001 \times \text{Shortwave Radiation}) + (0.0333 \times \text{Wind Speed}_{100m})

Tech Stack & Workflow:
1. Data Processing: Pandas & NumPy: For time-series manipulation and cyclical feature generation. Feature Engineering: * hour_sin / hour_cos: Mapping time to a 2D circle lags: Using historical data as a predictor.
2. Machine LearningModel: XGBoost / Random Forest Regressor.Validation: Time-Series Split (Training on Jan 05-11, Forecasting for Jan 12).Performance: Achieved an R^2 Score of 0.9357, indicating high reliability for hourly forecasts.
3. Visualization: Matplotlib & Seaborn: Used to visualize the "Actual vs. Predicted" pulse for cities like New York, Mumbai, and Tokyo.

Results & Analysis: The system successfully identified that Momentum (Lags) and Solar Cycles are the primary drivers of the Green Energy Pulse. By using cyclical encoding, the model correctly predicts the "dip" in green energy during the evening (the "Duck Curve") and the "surge" during peak solar/wind hours.

Future Roadmap:
1. Recursive Multi-step Forecasting: Moving from 1-hour ahead to 48-hour ahead predictions.
2. API Integration: Connecting to OpenWeather or Solcast APIs for truly live "Live Feeds."
3. Deep Learning (LSTM): Exploring Recurrent Neural Networks for better long-range seasonal memory.

Dataset: https://www.kaggle.com/datasets/nudratabbas/global-green-energy-pulse-real-time-renewable
