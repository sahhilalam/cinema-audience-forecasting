# 🎬 Cinema Audience Forecasting

A machine learning project focused on forecasting daily cinema audience attendance using historical attendance, ticket bookings, theatre information, and time-based features.

Developed as part of the Machine Learning Practice (MLP) coursework at IIT Madras, this project is based on the Kaggle Cinema Audience Forecasting Challenge.

## 📌 Problem Statement

The objective is to predict the number of people visiting cinemas on particular dates using historical booking records and related information.

This is a **time-series regression problem** because audience attendance depends on temporal patterns, historical booking behaviour, and other factors that can vary over time.

The main challenges include:

- Combining data from different booking systems
- Mapping theatre identifiers across datasets
- Capturing temporal trends and recurring patterns
- Constructing historical features without introducing data leakage
- Evaluating models using a time-aware validation strategy

- **Target Variable:** `audience_count`
- **Evaluation Metric:** Root Mean Squared Error (RMSE)

**Kaggle Competition:** [Cinema Audience Forecasting Challenge](https://www.kaggle.com/competitions/Cinema_Audience_Forecasting_challenge/overview)

## 📊 Dataset

The project uses eight competition files:

| Dataset | Description |
|---|---|
| `booknow_visits.csv` | Historical cinema audience counts |
| `booknow_booking.csv` | Online ticket booking records |
| `cinePOS_booking.csv` | Point-of-sale ticket booking records |
| `booknow_theaters.csv` | BookNow theatre information |
| `cinePOS_theaters.csv` | CinePOS theatre information |
| `movie_theater_id_relation.csv` | Mapping between theatre identifiers |
| `date_info.csv` | Calendar and day-of-week information |
| `sample_submission.csv` | Required prediction submission format |

The datasets are provided through Kaggle and are not included in this repository.

## 🔍 Exploratory Data Analysis

The exploratory data analysis investigates:

- Distribution and skewness of audience attendance.
- Changes in daily audience attendance over time.
- Weekly and day-of-week attendance patterns.
- Ticket booking patterns across different platforms.
- Audience attendance across theatre types and areas.
- Correlations between numerical features.

### Key Observations

- Audience attendance exhibits a right-skewed distribution.
- Attendance varies across days of the week, with higher attendance around weekends.
- Booking information provides useful signals for forecasting audience demand.
- Audience counts vary across theatre characteristics and locations.

## ⚙️ Feature Engineering

Several feature groups are constructed to capture temporal patterns, booking behaviour, and differences between theatres.

### 1. Calendar Features
- Day, month, and week-related features.
- Other date-derived features used in the forecasting workflow.

### 2. Booking Features
- Aggregated booking information from BookNow.
- Aggregated point-of-sale booking information from CinePOS.

### 3. Theatre Features
- Theatre-related characteristics.
- Area and location-related information.

### 4. Event Features
- Indicators for selected high-attendance dates and events.

### 5. Historical Features
- Lagged audience counts.
- Rolling means, standard deviations, minima, and maxima.
- Exponentially weighted historical statistics.

These features help the models capture recurring attendance patterns and changes in audience demand over time.

## 🤖 Model Development

Three regression models were initially evaluated using time-series cross-validation.

| Model | Mean Cross-Validation R² |
|---|---:|
| LightGBM | 0.496219 |
| Linear Regression | 0.495338 |
| Random Forest | 0.491969 |

Among these initial model comparisons, LightGBM achieved the highest mean cross-validation R².

### Hyperparameter Tuning

Random Forest was subsequently tuned using `RandomizedSearchCV` to explore different hyperparameter configurations.

The tuned Random Forest model was selected for generating predictions for the competition test dataset based on the score obtained during hyperparameter tuning.

This allowed the project to explore whether an optimized Random Forest configuration could provide better predictive performance than its initial configuration.

**Note:** The R² values above represent the initial cross-validation results. They are not Kaggle leaderboard scores, and the tuned Random Forest score is not reported here.

## 📈 Evaluation

The project uses cross-validation to assess model performance and compare regression approaches.

The primary competition evaluation metric is Root Mean Squared Error (RMSE).

- **R²:** Measures how well a model explains variation in the target variable.
- **RMSE:** Measures the magnitude of prediction errors, with larger errors receiving greater weight.

The initial model comparison favoured LightGBM based on mean cross-validation R², while the subsequent hyperparameter-tuning stage informed the selection of Random Forest for final prediction generation.

## 🛠️ Technologies Used

- **Python** — Core programming language.
- **Pandas** — Data manipulation and analysis.
- **NumPy** — Numerical computation.
- **Matplotlib** — Data visualization.
- **Seaborn** — Statistical visualization.
- **Scikit-learn** — Preprocessing, model evaluation, and hyperparameter tuning.
- **LightGBM** — Gradient boosting model.
- **Jupyter Notebook** — Interactive development and experimentation.

## 📁 Repository Structure

```text
Cinema-Audience-Forecasting/
├── README.md
├── 23f1002354-notebook-t32025.ipynb
└── requirements.txt
```

The notebook contains the data preparation, exploratory analysis, feature engineering, model development, evaluation, and prediction workflow.

## 🚀 Getting Started

### Prerequisites

- Python 3
- pip
- Jupyter Notebook

### 1. Clone the Repository

```bash
git clone https://github.com/YOUR_USERNAME/Cinema-Audience-Forecasting.git
cd Cinema-Audience-Forecasting
```

Replace `YOUR_USERNAME` with your GitHub username.

### 2. Install Dependencies

Install the dependencies listed in `requirements.txt`.

```bash
pip install -r requirements.txt
```

### 3. Download the Dataset

Download the competition datasets from the official Kaggle competition page:

[Download the Cinema Audience Forecasting Dataset](https://www.kaggle.com/competitions/Cinema_Audience_Forecasting_challenge/data)

Configure the dataset paths in the notebook to match your local environment.

The original competition datasets are not included in this repository.

### 4. Run the Notebook

```bash
jupyter notebook 23f1002354-notebook-t32025.ipynb
```

Execute the cells in order after configuring the dataset paths and installing the required dependencies.


## 📄 Dataset Disclaimer

The competition datasets are not included in this repository. Users should obtain the data directly from Kaggle and follow the applicable competition rules and dataset terms.