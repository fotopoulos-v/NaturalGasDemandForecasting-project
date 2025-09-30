# Natural Gas Consumption Demand Forecasting

[![Python](https://img.shields.io/badge/Python-3.9%2B-blue)](https://www.python.org/)  
[![TensorFlow](https://img.shields.io/badge/TensorFlow-2.12-orange)](https://www.tensorflow.org/)  
[![Jupyter Notebook](https://img.shields.io/badge/IDE-Jupyter%20Notebook-orange)](https://jupyter.org/)  
[![XGBoost](https://img.shields.io/badge/XGBoost-2.x-lightgrey)](https://xgboost.readthedocs.io/)  
[![Scikit-learn](https://img.shields.io/badge/Scikit--learn-1.x-blueviolet)](https://scikit-learn.org/) 
[![Matplotlib](https://img.shields.io/badge/Matplotlib-3.x-red)](https://matplotlib.org/)  
[![Plotly](https://img.shields.io/badge/Plotly-6.x-lightblue)](https://plotly.com/) 

## 📌 Project Overview
The goal of this project is to forecast natural gas demand in Greece for the **12-month period from August 2024 to July 2025**.  
Accurate forecasting is critical for energy planning, supply optimization, and cost reduction for industrial, residential, and commercial consumers.

The models use **historical consumption data** and **temperature data** as key variables to capture both seasonal patterns and external influences.

---

## 🛠 Approach

We compare a variety of time series forecasting methods, spanning **statistical**, **machine learning**, and **deep learning** approaches:

1. **SARIMA (Seasonal AutoRegressive Integrated Moving Average)**  
   A classical statistical model capturing trend, seasonality, and autocorrelation — serving as a baseline.

2. **XGBoost (Extreme Gradient Boosting)**  
   A tree-based ensemble learning method that uses lag features and temperature inputs.

3. **MLP (Multi-Layer Perceptron)**  
   A fully connected neural network capturing nonlinear relationships but lacking explicit temporal modeling.

4. **RNN (Recurrent Neural Network)**  
   Captures short-term sequential dependencies by passing information over time steps.

5. **LSTM (Long Short-Term Memory)**  
   An advanced RNN architecture handling long-term dependencies with gating mechanisms, avoiding vanishing gradients.

6. **GRU (Gated Recurrent Unit)**  
   A streamlined LSTM variant with fewer gates, offering faster computation while retaining strong sequential modeling.

7. **1D-CNN (One-Dimensional Convolutional Neural Network)**  
   Extracts local temporal patterns through convolutions along the time dimension.

---

## 📊 Data

- **Consumption Data:** Monthly historical natural gas consumption in Greece (Jan 2008 – Jul 2025).  
- **Weather Data:** Monthly average air temperatures from Meteostat API, aggregated from daily readings at a station near Athens, Greece.

---

## 📈 Results & Insights

### Model Comparison
| Model      | Strengths                                   | Weaknesses                                      |
|------------|---------------------------------------------|-------------------------------------------------|
| LSTM       | Best overall, captures long-term patterns | Computationally expensive                      |
| GRU        | Strong performance, faster than LSTM      | Slightly less accurate than LSTM               |
| SARIMA     | Stable baseline                            | Limited ability to incorporate external inputs |
| XGBoost    | Efficient training                         | Struggles with small datasets                  |
| RNN, CNN   | Captures sequential patterns               | Outperformed by LSTM/GRU, needs more data     |
| MLP        | Captures nonlinearities                    | No temporal awareness                           |

**Key insight:** LSTM performed best overall, with GRU close behind. Traditional SARIMA gave reliable results, while tree-based XGBoost struggled due to limited data.

---

### Forecast Accuracy Metrics
- **MAE (Mean Absolute Error):** Robust to outliers, interpretable average error magnitude.  
- **RMSE (Root Mean Squared Error):** Penalizes large deviations more heavily, useful for peak demand forecasting.  
> In energy forecasting, **RMSE is often prioritized** due to high costs from large errors during peak demand periods.

---

### Limitations
Models failed to accurately capture extreme peaks (e.g., January and February 2025) despite low temperatures, suggesting additional explanatory variables (e.g., policy changes, socioeconomic shifts) are required for better predictions.


