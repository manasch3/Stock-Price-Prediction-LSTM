# Stock Price Prediction using LSTM

A Deep Learning and Time Series Forecasting project that predicts future stock prices using Long Short-Term Memory (LSTM) neural networks. The project leverages historical market data from Yahoo Finance, applies sequence-based learning techniques, and forecasts future stock trends based on past price movements.

## Overview

Financial markets generate vast amounts of sequential data every day. Predicting stock prices is a challenging problem due to market volatility, external economic factors, and the dynamic nature of financial systems.

This project explores the use of Long Short-Term Memory (LSTM) networks, a specialized type of Recurrent Neural Network (RNN), to model temporal dependencies in stock market data. By learning patterns from historical closing prices, the model is able to forecast future stock values and identify underlying market trends.

The project demonstrates a complete deep learning workflow including data acquisition, preprocessing, feature scaling, sequence generation, model training, evaluation, forecasting, visualization, and model persistence.

## Objectives

The primary objectives of this project are:

- Predict future stock prices using historical market data.
- Implement a deep learning model using LSTM networks.
- Learn temporal patterns from sequential financial data.
- Evaluate forecasting performance using regression metrics.
- Visualize actual vs predicted stock prices.
- Build a reusable forecasting pipeline for multiple stock symbols.

## Dataset

Historical stock market data is collected directly from Yahoo Finance using the `yfinance` library.

### Dataset Characteristics

| Metric | Value |
|----------|----------|
| Data Source | Yahoo Finance |
| Stock Symbol | AAPL (Apple Inc.) |
| Historical Records | 1,761 |
| Training Samples | 1,360 |
| Testing Samples | 341 |
| Feature Used | Closing Price |
| Sequence Length | 60 Days |

### Data Attributes

The downloaded dataset contains:

- Open Price
- High Price
- Low Price
- Close Price
- Trading Volume

For forecasting, the model uses the **Closing Price** as the primary feature.

## Methodology

The project follows a complete time-series forecasting pipeline.

```text
Historical Stock Data
          ↓
Data Collection (Yahoo Finance)
          ↓
Feature Selection
          ↓
Data Scaling
          ↓
Sequence Generation
          ↓
LSTM Model Training
          ↓
Performance Evaluation
          ↓
Future Price Prediction
```

## Data Preprocessing

Before training the neural network, several preprocessing techniques are applied.

### Feature Selection

The closing stock price is extracted as the target variable because it represents the final market valuation for each trading day.

### Feature Scaling

Min-Max Scaling is used to normalize stock prices into the range:

```text
0 → 1
```

This improves neural network convergence and training stability.

### Sequence Generation

Instead of treating each stock price independently, the model learns from historical sequences.

Example:

```text
Previous 60 Days Prices
          ↓
Predict Next Day Price
```

This allows the network to capture temporal dependencies and market trends.

## Model Architecture

The forecasting model is built using a stacked LSTM architecture.

```text
Input Sequence
       ↓
LSTM Layer (50 Units)
       ↓
Dropout (0.2)
       ↓
LSTM Layer (50 Units)
       ↓
Dropout (0.2)
       ↓
Dense Layer (25 Units)
       ↓
Output Layer
```

### Regularization Techniques

To improve generalization and reduce overfitting, the following techniques are implemented:

- Dropout Layers
- Early Stopping
- Adaptive Learning Rate Scheduling (ReduceLROnPlateau)
- Validation Monitoring

These strategies help ensure robust performance on unseen data.

## Model Training

The model is trained using:

| Parameter | Value |
|----------|----------|
| Optimizer | Adam |
| Loss Function | Mean Squared Error |
| Metric | Mean Absolute Error |
| Epochs | 30 |
| Batch Size | 32 |

The training process automatically stops when validation performance stops improving, preventing unnecessary overfitting.

## Model Evaluation

Performance is evaluated using regression metrics commonly used in forecasting tasks.

### Evaluation Metrics

- Root Mean Squared Error (RMSE)
- Mean Absolute Percentage Error (MAPE)
- Actual vs Predicted Visualization

### Results

| Metric | Value |
|----------|----------|
| RMSE | 6.65 |
| MAPE | 2.77% |
| Historical Records | 1,761 |
| Training Samples | 1,360 |
| Testing Samples | 341 |

The low MAPE score indicates that the model predictions are, on average, only 2.77% away from the actual stock prices, demonstrating strong forecasting capability.

### Future Forecast

| Metric | Value |
|----------|----------|
| Predicted Next Day Closing Price | $247.71 |

## Visualization

Several visualizations are generated throughout the project:

- Historical Stock Price Trend
- Training vs Validation Loss
- Actual vs Predicted Prices
- Last 100 Days Prediction Performance

These visualizations provide insights into model behavior and forecasting accuracy.

## Repository Structure

```text
Stock-Price-Prediction-LSTM/
│
├── Stock_Price_Prediction.ipynb
├── stock_price_lstm_model.h5
├── scaler.pkl
├── actual_vs_predicted.png
├── README.md
└── requirements.txt
```

## Running the Project

### Clone the Repository

```bash
git clone https://github.com/manasch3/Stock-Price-Prediction-LSTM.git
cd Stock-Price-Prediction-LSTM
```

### Install Dependencies

```bash
pip install tensorflow yfinance pandas numpy matplotlib scikit-learn joblib
```

### Launch the Notebook

```bash
jupyter notebook Stock_Price_Prediction.ipynb
```

The notebook includes data collection, preprocessing, model training, forecasting, evaluation, visualization, and model persistence.

## Example Usage

Users can specify any supported stock symbol.

Examples:

```text
AAPL
TSLA
NVDA
MSFT
GOOGL
AMZN
```

The model automatically downloads historical market data and generates predictions.

## Key Findings

Several important observations emerged during experimentation:

- LSTM networks effectively capture long-term dependencies in stock price sequences.
- Time-series forecasting requires preserving temporal order unlike traditional machine learning tasks.
- Feature scaling significantly improves model training stability.
- Early Stopping and Dropout improve model generalization.
- The model achieved a MAPE of only **2.77%**, demonstrating strong predictive performance.
- Visualization of predicted and actual prices shows that the model successfully follows market trends.

The results demonstrate the effectiveness of deep learning approaches for financial forecasting and sequential data modeling.

## Skills Demonstrated

This project showcases practical experience in:

- Deep Learning
- Time Series Forecasting
- LSTM Networks
- TensorFlow / Keras
- Financial Data Analysis
- Data Preprocessing
- Feature Scaling
- Model Evaluation
- Data Visualization
- Model Persistence

## Future Improvements

Potential future enhancements include:

- Multi-feature forecasting using Open, High, Low, and Volume.
- Bidirectional LSTM architectures.
- GRU-based forecasting models.
- Hyperparameter optimization.
- Transformer-based time series models.
- Multi-stock portfolio forecasting.
- Real-time prediction dashboards using Streamlit.
