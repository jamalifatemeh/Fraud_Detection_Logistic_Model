
# Fraud Detection using Logistic Regression

This project demonstrates how to detect fraudulent transactions using **Logistic Regression**. It leverages a dataset containing transaction details like duration and day of the week to predict whether a transaction is fraudulent.

---

## 📁 Dataset Description

The dataset includes:

- `transaction_id`: Unique ID for each transaction
- `duration`: Time duration of the transaction
- `day`: Day type (either "weekend" or "weekday")
- `fraud`: Whether the transaction is fraudulent (True/False)

Sample:

| transaction_id | duration | day     | fraud |
|----------------|----------|---------|-------|
| 28891          | 21.30    | weekend | False |
| 61629          | 22.93    | weekend | False |
| 53707          | 32.69    | weekday | False |

---

## 🧹 Data Cleaning & Feature Engineering

1. Checked for and handled missing values and duplicates.
2. Created new features:
   - `weekend`: One-hot encoded binary indicator (1 if weekend, 0 otherwise)
   - `fraud_true`: Converted boolean `fraud` to binary (1 for True, 0 for False)
   - `intercept`: Constant feature for logistic regression

---

## 🧠 Model: Logistic Regression

Used **statsmodels.Logit** to fit a logistic regression model:

```python
lm = sm.Logit(df['fraud_true'], df[['intercept', 'duration', 'weekend']])
```

### Final Logistic Regression Equation

To compute the probability of fraud:

\[
P(	ext{fraud}) = \frac{1}{1 + \exp(-(12.4174 + 1.4637 \times 	ext{duration} + 2.5465 \times 	ext{weekend}))}
\]

Example prediction for a 21.30s transaction on the weekend:

```python
import math
prob = 1 / (1 + math.exp(-(12.4174 + 1.4637 * 21.302600 + 2.5465 * 1)))
```

---

## 📊 Results

- Model used **duration** and **day of week** to predict probability of fraud.
- Allows real-time flagging of potentially fraudulent transactions.

---

## 🚀 How to Run

### 1. Clone the Repository

```bash
git clone https://github.com/yourusername/fraud-detection.git
cd fraud-detection
```

### 2. Install Dependencies

```bash
pip install pandas statsmodels
```

### 3. Run the Script

```bash
python fraud_detection.py
```

---

## 📂 File Structure

```
fraud-detection/
├── fraud_data.csv
├── fraud_detection.py
├── README.md
└── assets/
    └── [optional visualizations]
```

---

## 📌 Conclusion

This project walks through a complete pipeline for fraud detection using logistic regression:

- Cleaned data
- Engineered relevant features
- Built interpretable logistic model
- Predicted fraud probabilities

It's a simple but effective baseline for building more advanced fraud detection systems. 🔐💰

---

## 📄 License

MIT License.
