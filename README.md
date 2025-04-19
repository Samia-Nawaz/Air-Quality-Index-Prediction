# Kalman Attention Bi-GRU for Air Quality Index (AQI) Forecasting

## 📌 Overview

This project proposes a novel regression framework for AQI forecasting by integrating:
- **Bi-Directional GRU (Bi-GRU)** for capturing temporal dependencies
- **Kalman Attention** for dynamic attention weighting based on uncertainty
- **Chi-Square Divergence** as a regularizer in the loss function

## 📊 Dataset

The model uses hourly pollutant data from the **U.S. EPA Air Quality System** (Denver–Aurora–Lakewood region, 2022–2024) including:
- Pollutants: `CO`, `NO₂`, `SO₂`, `O₃`, `PM₁₀`, `PM₂.₅`
- Target variable: `AQI`

You can download the dataset from: [EPA Air Quality System](http://www.epa.gov)

---

## 🧩 Modules

| File                      | Description |
|--------------------------|-------------|
| `data_preprocessing.py`  | Loads and imputes missing values with ARIMA, applies scaling |
| `kalman_filter.py`       | Implements 1D Kalman Filter for smoothing pollutant values |
| `kalman_attention.py`    | Custom attention mechanism integrating Kalman-based uncertainty |
| `bi_gru_kalman_model.py` | Kalman Attention-enhanced Bi-GRU regression network |
| `loss_chi_square.py`     | Custom loss combining MSE and Chi-Square Divergence |
| `train_model.py`         | Training pipeline with hyperparameters and sequence generation |
| `evaluate_visualize.py`  | Evaluation (MSE, MAE, R²) and visualization with scatter/line plots |

---

## 🧪 Training

```bash
python train_model.py
```

### Hyperparameters

| Parameter       | Value    |
|----------------|----------|
| Epochs         | 100      |
| Batch Size     | 32       |
| Hidden Units   | 128      |
| Learning Rate  | 0.001    |
| Dropout        | 0.3      |
| Chi² λ         | 0.2      |

---

## 📈 Evaluation Metrics

- **MAE** (Mean Absolute Error)
- **MSE** (Mean Squared Error)
- **R²** (Coefficient of Determination)

---

## 📉 Visualizations

- AQI trends (Hourly, Daily, Weekly, Monthly)
- Actual vs Predicted scatter plots
- Error distributions and attention weights (optional)
