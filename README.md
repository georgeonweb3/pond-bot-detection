# Pond Bot Detection Project

## Overview
This repository contains datasets, code, and results for detecting bots and Sybil users on the Pond platform. The goal is to improve fairness, authenticity, and trust by distinguishing genuine user activity from automated or malicious behavior.

---

## Problem Definition
Bot and Sybil accounts can manipulate rewards, submit fake bounties, and compromise the integrity of online platforms. This project focuses on detecting such accounts using data-driven methods, enabling platform operators to take proactive measures.

---

## Dataset

### 1. Raw Dataset
**File:** `data/synthetic_pond_dataset.xlsx`  
- Contains simulated submissions for 50 human users and 30 bot users.  
- Each submission includes:
  - `user_id` – unique identifier of the user
  - `submission_id` – unique identifier of the submission
  - `submission_time` – timestamp of submission
  - `bounty_id` – associated bounty
  - `submission_text` – content of submission
  - `device_fingerprint` – device identifier
  - `ip_country` – country of submission
  - `attachments_count` – number of attachments
  - `label` – `human` or `bot`  

### 2. Feature Dataset
**File:** `data/user_features.csv`  
- Contains processed features used for bot detection:
  - `num_submissions` – total submissions per user
  - `avg_time_between_submissions` – average gap between submissions
  - `unique_devices` – number of unique devices used
  - `trust_score` – likelihood of being human (0–1)
  - `label` – ground truth for evaluation

---

## Methodology
1. **Feature Extraction**
   - Counted submissions per user
   - Calculated average time between submissions
   - Counted unique devices used per user

2. **Model**
   - Trained an **XGBoost classifier** to predict bot vs human using the features above
   - Evaluation metrics included precision, recall, and F1-score

3. **Outputs**
   - `user_features.csv` contains both predictions and a trust score
   - Visualizations illustrate submission patterns and bot vs human behavior

---

## Results
- **Classification Report** shows high precision and recall for bot detection  
- Visualizations included in `/visuals` folder:
  - Number of users by label
  - Number of submissions per user
  - Average time between submissions  

---

## How to Run
1. Clone the repository:
```bash
git clone https://github.com/georgeonweb3/pond-bot-detection.git
cd pond-bot-detection