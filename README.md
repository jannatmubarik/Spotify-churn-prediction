# Spotify User Churn Prediction

Predicting Spotify user churn using LASSO, Random Forest, Neural Networks, and K-Means clustering on a synthetic dataset of ~10,000 users. Identifies key behavioral churn drivers — skip rate, listening time, offline engagement, and subscription type, and delivers data-driven retention strategies for Free/Student and Premium/Family user segments. Best model (LASSO) achieves AUC of 0.889 and ~80% accuracy.

---

##  Project Overview

User churn is one of the most critical challenges for subscription-based platforms like Spotify. This project analyzes a synthetic Spotify user dataset to:

- Identify users at high risk of churning
- Understand the demographic and behavioral factors driving churn
- Segment users into meaningful groups for targeted retention strategies
- Recommend data-driven interventions to reduce churn rate

---

## Repository Structure

```
spotify-churn-prediction/
├── README.md
├── data/
│   └── spotify_churn_dataset.csv       # Synthetic Spotify user dataset (Kaggle)
└── code/
    └── spotify_churn_analysis.R        # Full analysis: EDA, modeling, clustering
```

---

## 📊 Dataset

- **Source:** Kaggle (2025 synthetic Spotify dataset)
- **Size:** ~10,000 users
- **Key Features:**
  - Demographics: `age`, `gender`, `country`
  - Subscription: `subscription_type`, `device_type`, `ads_listened_per_week`
  - Engagement: `listening_time`, `skip_rate`, `songs_played_per_day`, `offline_listening`
  - Target: `churn` (binary)

> Data is synthetically generated and reflects general trends rather than precise real-world outcomes.

---

## Key Findings

| Metric | Value |
|--------|-------|
| Overall Churn Rate | 53.88% |
| Free Tier Churn | 72.6% |
| Premium Tier Churn | 29.6% |
| Best Model (LASSO) AUC | 0.889 |
| Best Model Accuracy | ~80% |

**Top Churn Predictors:** skip rate, listening time, offline listening, subscription type (Free), age

---

## Models Developed

| Model | Notes |
|-------|-------|
| Null Model | Baseline |
| Logistic Regression | Key predictors: age, skip rate, offline listening |
| Logistic Regression + Interactions | Slight overfit (AIC 4986 vs 4794) |
| LASSO Logistic Regression | **Best model** — AUC 0.889, Accuracy 80% |
| Classification Tree | 78% accuracy, 21.6% misclassification |
| Random Forest | Low OOB error, strong generalization |
| Neural Network | Captured non-linear patterns, lower interpretability |

All models evaluated via **10-fold cross-validation** using AUC, RMSE, Log-loss, and Accuracy.

---

## User Segments (K-Means Clustering)

**Cluster 1 — Free/Student Users**  
Price-sensitive, high skip rates, low offline engagement, high churn (~80%). Recommended strategy: Premium trial offers, curated playlist refreshes, recommendation algorithm improvements.

**Cluster 2 — Premium/Family Users**  
High-value, steady engagement, lower churn (~30%). Churn is situational (subscription fatigue, payment cycles). Recommended strategy: loyalty incentives, pause options, value reinforcement messaging.

---

## Business Recommendations

- **Flag high-risk users** (predicted churn probability > 0.7) for automated retention campaigns
- **Offer time-limited Premium trials** to Cluster 1 users to drive free-to-paid conversion
- **Reduce skip rates** by improving playlist recommendations (Daily Mix, Discover Weekly)
- **Promote offline listening** features — strong negative predictor of churn
- **Regional targeting** — India and Germany show higher churn; web-only users in Sweden and India are elevated risk
- **Monitor payment cycle stability** for Premium users as an early churn signal

---

## How to Run

1. Clone the repository:
   ```bash
   git clone https://github.com/yourusername/spotify-churn-prediction.git
   ```
2. Open `code/spotify_churn_analysis.R` in RStudio
3. Install required packages:
   ```r
   install.packages(c("tidyverse", "caret", "glmnet", "randomForest", "rpart", "neuralnet", "pROC", "cluster"))
   ```
4. Run the script end-to-end or section by section

---

## Results Summary

LASSO logistic regression was selected as the best model due to its combination of high predictive performance (AUC = 0.889) and interpretability — critical for Spotify's marketing and strategy teams to understand *why* a user might churn, not just *if* they will.

---

## License

This project was completed as part of an academic course. Dataset is sourced from Kaggle under its respective license.
