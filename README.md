Stock Price Trend Prediction (GRU Model + Technical Indicators)

This repository contains a complete end-to-end pipeline for stock market trend prediction using a GRU-based deep learning model.
The workflow includes:

Dataset preparation (combining multiple raw datasets + fetching last 5 years of data)

Feature engineering (technical indicators, returns, scaling)

Trend classification using cleaned labels

Model training + evaluation (Accuracy, Precision, Recall, F1)

Single-day and multi-day future prediction

Visualization of results for multiple companies



---

📂 Project Structure

📦 stock-trend-prediction
│
├── data/
│   ├── dataset1.csv
│   ├── dataset2.csv
│   ├── dataset3.csv
│   ├── final_dataset.csv      ← merged + cleaned master dataset
│
├── data_mine.ipynb            ← fetches extra 5-year historical stock data
├── mumbai_hacks.ipynb         ← main model training, evaluation, plotting
│
├── models/
│   └── GRU_<company>.keras    ← trained models saved per company
│
└── README.md                  ← this file


---

🧩 Workflow Overview

1️⃣ Raw Data

You start with three locally downloaded datasets (dataset1–3).
These contain initial OHLC values + company tickers.


---

2️⃣ Additional Data Fetching

Using data_mine.ipynb, the following happens:

Automatically fetches previous 5 years of daily stock data for selected companies.

Cleans date format, aligns columns, merges everything.

Concatenates with the 3 original datasets.

Outputs final_dataset.csv.


This CSV is the master dataset used for training.


---

3️⃣ Model Training + Prediction

All training happens in mumbai_hacks.ipynb, including:

✔ Data preprocessing

Per-company filtering

Scaling using MinMaxScaler

Creating 60-day sequences

Adding technical indicators

Creating noise-filtered labels

Train/val/test split


✔ GRU model

Two-layer GRU network with dropout + regularization

Early stopping

Trained separately for each company

Saved as:

models/GRU_<company>.keras


✔ Evaluation metrics

Accuracy

Precision

Recall

F1 Score


Printed per company + plotted.

✔ Predictions

Next-day or next-5-day trend prediction

Future close price prediction

Line plot comparing actual vs predicted close prices



---

🧠 What the Model Predicts

The final model can perform two tasks:

🔵 Regression

Predict future Close price

Plotted vs actual values


🟢 Classification

Predict market trend direction

Using noise-filtered label:

Positive trend if price ↑ more than +0.3%

Negative trend if price ↓ more than −0.3%

Neutral days ignored during training


Outputs: Accuracy, Precision, Recall, F1



---

📈 Key Features

GRU network optimized for time-series

Technical indicators (RSI, EMA, MACD, etc.)

Noise-filtered classification labels

Per-company saved models

Overfitting reduction (dropout, regularization, early stopping)

Supports adding unlimited number of companies



---

▶ How to Run

Step 1 — Install Dependencies

pip install numpy pandas matplotlib scikit-learn tensorflow ta

Step 2 — Run Data Mining Notebook

data_mine.ipynb

This generates final_dataset.csv.

Step 3 — Train + Predict

mumbai_hacks.ipynb

This will:

Train GRU models per company

Save trained models

Output metrics

Plot actual vs predicted close prices

Predict future trend and prices



---

🛠 Future Improvements

Multi-company joint model training (transfer learning)

Transformer-based price prediction

Hyperparameter tuning with KerasTuner

Real-time data streaming

Ensemble model (GRU)

🤝 Contributions

Kshitij Patel
Kavya Patel
Harsh Patel
Kanvi Makwana
