
# A/B Test Analysis: Webpage Conversion Rates

This project presents an A/B testing analysis performed on webpage conversion data. The goal is to determine whether a **new landing page** increases user conversion compared to the **old landing page**.

## 🎯 Project Overview

An A/B experiment was conducted where users were randomly assigned to one of two groups:

- **Control Group**: Saw the old webpage.
- **Treatment Group**: Saw the new webpage.

The hypothesis was that the new design might improve conversions. This project includes **data cleaning**, **hypothesis testing**, and **bootstrapping** to evaluate this.

---

## 📁 Dataset Description

The dataset (`project9_ab_data.csv`) includes the following columns:

- `user_id`: Unique identifier for each user.
- `timestamp`: Timestamp of when the user visited the webpage.
- `group`: A/B group assignment — `control` or `treatment`.
- `landing_page`: The page the user actually saw — `old_page` or `new_page`.
- `converted`: Whether the user converted (1 = yes, 0 = no).

---

## 🧹 Data Cleaning

To ensure the integrity of the experiment:
- Removed mismatched rows where control group users saw the new page or treatment users saw the old page.
- Removed duplicate users (`user_id`) to ensure one observation per user.
- Checked and handled missing or inconsistent values.

---

## 📊 A/B Testing and Hypothesis Testing

### Hypotheses:

- **Null Hypothesis (H₀)**: The conversion rate of the new page is less than or equal to that of the old page.  
  *(p_new - p_old ≤ 0)*

- **Alternative Hypothesis (H₁)**: The new page has a higher conversion rate.  
  *(p_new - p_old > 0)*

### Analysis Steps:

1. Calculated conversion rates for `old_page` and `new_page`.
2. Measured the observed difference.
3. Performed bootstrapping (1000 iterations, 100,000 samples) to simulate the distribution of conversion rate differences.
4. Computed the **p-value** to check for statistical significance.
5. Compared results to a normal distribution approximation.

---

## 📈 Visualizations

- Histogram of bootstrapped differences between conversion rates.
- Highlighted observed difference and 95% confidence boundary.
- Comparison with normal distribution simulations.

---

## ✅ Conclusion

- The observed conversion rate of the **new page was higher** than the old.
- The **p-value was low**, indicating the difference is statistically significant.
- **We rejected the null hypothesis** and concluded that the new page leads to improved conversions.

---

## 🚀 How to Run

Make sure the dataset is available locally:

```bash
python ab_test_analysis.py
```

---

## 📂 File Structure

```
ab_test_project/
├── project9_ab_data.csv
├── ab_test_analysis.py
├── README.md
└── assets/
    └── [optional figures]
```

## 📄 License

MIT License.

---

Test, analyze, iterate. A/B testing makes perfect. 📈
