# 🎤 Age Estimation from Speech

A machine learning project that predicts a speaker’s age using acoustic, linguistic, and demographic features extracted from speech.

---

## 📌 Overview

This project investigates how speech characteristics can be used to estimate a speaker’s age. Two regression models were implemented and compared:

- K-Nearest Neighbors (KNN)
- Random Forest Regressor

The results show that **Random Forest outperforms KNN**, achieving better accuracy and generalization.

---

## 📊 Dataset

- **Total samples:** 3,624  
  - Development set: 2,933  
  - Evaluation set: 691  
- **Target:** Speaker age (continuous value)

### Features

#### Acoustic Features
- Mean, max, min pitch (Hz)
- Jitter, shimmer
- Energy
- Zero-crossing rate (ZCR)
- Spectral centroid
- Harmonic-to-noise ratio (HNR)
- Silence duration

#### Linguistic Features
- Number of words
- Number of characters
- Number of pauses
- Tempo (BPM)

#### Demographic Metadata
- Gender
- Ethnicity

---

## ⚙️ Preprocessing

- Removed irrelevant columns (`id`, `path`, `sampling_rate`)
- Fixed inconsistencies (e.g., typo in gender labels)
- Converted incorrect data types
- Train/test split: **80% / 20%**
- Normalized numerical features using **z-score normalization**
- Applied **one-hot encoding** to categorical variables

---

## 🤖 Models

### K-Nearest Neighbors (KNN)
- Tuned parameter: `k`
- Best configuration: `k = 30`
- Evaluation RMSE: **10.539**

### Random Forest Regressor
- Tuned parameters:
  - `n_estimators`
  - `max_depth`
  - `min_samples_split`
- Best configuration:
  - `n_estimators = 500`
  - `max_depth = 30`
  - `min_samples_split = 3`
- Evaluation RMSE: **10.215**

---

## 📈 Results

| Model           | RMSE (Evaluation Set) |
|----------------|----------------------|
| KNN            | 10.539               |
| Random Forest  | **10.215**           |

**Conclusion:** Random Forest provides better predictive performance and generalization.

---

## 🔍 Feature Importance (Random Forest)

**Most important:**
- Silence duration
- Spectral centroid

**Moderately important:**
- Jitter
- Number of pauses
- HNR

**Less important:**
- Gender
- Ethnicity

---

## 🚀 Usage

```bash
# Clone the repository
git clone https://github.com/your-username/age-estimation-speech.git

# Navigate into the project directory
cd age-estimation-speech

# Install dependencies
pip install -r requirements.txt

# Run training (example)
python train.py

# Run evaluation (example)
python evaluate.py
