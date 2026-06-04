<h1 align="center">
  <br>
  <a href="https://www.palermo.edu"><img src="https://www.palermo.edu/images/header/logo@2x.png" alt="UP Logo" width="130"></a>
  <a name="Top"></a>
  <br>
  Machine Learning
</h1>

<p align="center">
  <img alt="GitHub commit activity" src="https://img.shields.io/github/commit-activity/t/Seiryu362/RandomForestClassifier-XGBoosting/main">
  <img alt="Python" src="https://img.shields.io/badge/python-3.10+-blue.svg">
  <img alt="License" src="https://img.shields.io/badge/license-MIT-green.svg">
</p>

# Digital Burnout & Productivity Classification

A final project for the Machine Learning course at Universidad de Palermo.
The goal is to classify productivity levels from digital behavior and lifestyle data using supervised learning models.

# Content
- [About](#About)
- [Dataset](#Dataset)
- [Models](#Models)
- [Results](#Results)
- [Requirements](#Requirements)
- [Usage](#Usage)
- [Contribution](#Contribution)
- [Contact](#Contact)

## About
This project applies a full supervised machine learning pipeline to a synthetic dataset on digital burnout and productivity analytics.

The target variable is `productivity_category` (Low / Medium / High), predicted from features related to digital behavior, screen usage, sleep, stress, focus habits, and workplace environment.

Key aspects covered:
- Exploratory Data Analysis (EDA) and feature correlation study
- Missing value imputation and categorical encoding
- Detection and removal of data leakage
- Proper train / validation / test split with stratification
- Model training, hyperparameter tuning, and evaluation
- Comparison of two ensemble models: Random Forest and XGBoost

## Dataset
**Digital Burnout & Productivity Analytics** — [Kaggle](https://www.kaggle.com/datasets/aiexplorer77/digital-burnout-and-productivity-analytics)

- 5,000,000 rows (50,000 sampled for local training)
- 34 features covering digital behavior, lifestyle, and workplace factors
- Synthetic dataset created for educational and ML purposes
- Target: `productivity_category` — Low, Medium, High

> **Note on dataset choice:** During EDA it was discovered that the original intended target `mental_state` had near-zero correlation with all features (max r = 0.21), making it unpredictable by design. The target was switched to `productivity_category`, which showed meaningful feature correlations and produced genuinely learnable models. This finding is discussed in the notebook.

## Models
Two ensemble tree-based classifiers were trained and compared:

| Model | Approach | Key Parameters |
|---|---|---|
| Random Forest | Parallel independent trees, majority vote | n_estimators=100, max_depth=10, min_samples_split=10 |
| XGBoost | Sequential boosting, corrects previous errors | n_estimators=200, learning_rate=0.1, max_depth=6 |

Hyperparameter tuning was performed using `GridSearchCV` with `StratifiedKFold(5)` on training data only. Test set was used exactly once for final evaluation.

## Results

| Model | Test Accuracy | Weighted F1 |
|---|---|---|
| Random Forest | 74.01% | 0.74 |
| XGBoost | 77.87% | 0.78 |

XGBoost outperformed Random Forest across all metrics. The largest improvement was on the Medium productivity class (F1: 0.63 → 0.70), consistent with XGBoost's sequential error correction mechanism targeting the hardest class boundary.

Baseline reference: a naive classifier predicting always "High" achieves 47.5% accuracy.

## Requirements
To run this project locally you will need:

- **Python 3.10+** — [Download here](https://www.python.org/downloads)
- **Jupyter Notebook** — via VS Code or standalone
- **Git** — [Download here](https://git-scm.com/downloads)
- A code editor — [Visual Studio Code](https://code.visualstudio.com) recommended

### Python Libraries
```bash
pip install pandas numpy matplotlib seaborn scikit-learn xgboost kagglehub python-dotenv
```

### Environment Variables
Create a `.env` file in the project root with your Kaggle credentials:
```
KAGGLE_USERNAME=your_username
KAGGLE_KEY=your_api_key
```
Get your Kaggle API key from your [Kaggle account settings](https://www.kaggle.com/settings).

This project has been tested on:
- **OS:** Windows 11
- **Python:** 3.11

## Usage
1. Clone the repository:
```bash
git clone https://github.com/Seiryu362/RandomForestClassifier-XGBoosting.git
```

2. Navigate to the project folder:
```bash
cd ml-burnout-productivity
```

3. Install dependencies:
```bash
pip install -r requirements.txt
```

4. Add your `.env` file with Kaggle credentials (see Requirements above)

5. Open the notebook:
```bash
jupyter notebook
```

6. Run all cells in order from top to bottom.

> The notebook will automatically download the dataset via `kagglehub`. On first run this may take a moment depending on your connection.

## Contribution
Thank you for your interest in this project.

This is primarily an educational project and not currently open to active contributions. You are welcome to explore the code and suggest improvements or ideas.

If you would like to contribute for learning purposes, feel free to fork the repository, make your changes, and submit a pull request. All contributions will be reviewed.

For detailed guidelines refer to [CONTRIBUTE.md](https://github.com/Seiryu362/RandomForestClassifier-XGBoosting/blob/main/CONTRIBUTE.md)

## Contact
For feedback or just to say hi, feel free to reach out.

See [CONTACT.md](https://github.com/Seiryu362/RandomForestClassifier-XGBoosting/blob/main/CONTACT.md)

[Back to Top](#Top)
