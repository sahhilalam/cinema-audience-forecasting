# 🎬 Cinema Audience Forecasting

A machine learning project focused on forecasting daily cinema audience
attendance using historical attendance, ticket bookings, theatre
information, and time-based features.

This project was developed as part of the Machine Learning Practice (MLP)
coursework at IIT Madras and is based on a Kaggle competition.

## 📌 Problem Statement

The objective is to predict the number of people attending a cinema
for a given theatre and show date.

Accurate audience forecasting can help cinema operators improve
operational planning, staffing, and resource allocation.

**Target Variable:** `audience_count`

**Evaluation Metric:** Root Mean Squared Error (RMSE)

**Kaggle Competition:**  
[Cinema Audience Forecasting Challenge](https://www.kaggle.com/competitions/Cinema_Audience_Forecasting_challenge/overview)

## 📊 Dataset

The project uses eight competition files:

| Dataset | Purpose |
|---|---|
| `booknow_visits.csv` | Historical cinema audience counts |
| `booknow_booking.csv` | Online ticket booking records |
| `cinePOS_booking.csv` | Point-of-sale ticket booking records |
| `booknow_theaters.csv` | BookNow theatre information |
| `cinePOS_theaters.csv` | CinePOS theatre information |
| `movie_theater_id_relation.csv` | Mapping between theatre identifiers |
| `date_info.csv` | Calendar and day-of-week information |
| `sample_submission.csv` | Required prediction submission format |

The datasets are available through the Kaggle competition and are not
included in this repository.

## 🔍 Exploratory Data Analysis

The exploratory analysis investigates:

- Distribution and skewness of audience attendance.
- Changes in average daily attendance over time.
- Weekly and day-of-week attendance patterns.
- Ticket bookings across different platforms.
- Audience attendance across theatre types and areas.
- Correlations between numerical features.

### Key Observations

- Audience attendance has a right-skewed distribution.
- Attendance exhibits a strong weekly seasonal pattern, with higher
  attendance around weekends.
- Ticket booking information has a positive relationship with audience
  attendance.
- Audience counts vary across theatre types and areas.

## ⚙️ Feature Engineering

The project incorporates several types of features:

- **Calendar features:** Day, month, week, and other date-derived features.
- **Booking features:** Aggregated ticket bookings from BookNow and CinePOS.
- **Theatre features:** Theatre type, area, and location-related information.
- **Event features:** Indicators for selected high-attendance dates and events.
- **Historical features:** Lagged audience counts for previous days.
- **Rolling statistics:** Rolling means, standard deviations, minima,
  and maxima calculated from historical audience counts.
- **Exponentially weighted features:** Features derived from historical
  attendance patterns using exponentially weighted statistics.

Historical features are designed to capture recurring attendance patterns
and changes in audience demand over time.

## 🤖 Model Development

The following regression models were evaluated:

| Model | Mean Cross-Validation R² |
|---|---:|
| LightGBM | 0.496219 |
| Linear Regression | 0.495338 |
| Random Forest | 0.491969 |

The models were compared using time-series cross-validation.

LightGBM achieved the highest mean cross-validation R² among these
three models in the recorded experiments.

A Random Forest Regressor with tuned hyperparameters was subsequently
used to generate predictions for the competition test dataset.

**Note:** The reported R² values are cross-validation results, not
Kaggle leaderboard scores.

## 🛠️ Technologies Used

- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Scikit-learn
- LightGBM
- Jupyter Notebook

## 📁 Repository Structure

```text
Cinema-Audience-Forecasting/
├── README.md
├── 23f1002354-notebook-t32025.ipynb
└── .gitignore
```

Additional files may be included as the project evolves.

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

Install the libraries listed in `requirements.txt` after it has been
added to the repository.

### 3. Download the Dataset

Download the competition datasets from:

https://www.kaggle.com/competitions/Cinema_Audience_Forecasting_challenge/data

Update the dataset paths in the notebook to match your local environment.

### 4. Run the Notebook

```bash
jupyter notebook 23f1002354-notebook-t32025.ipynb
```

Run the cells in order after configuring the dataset paths.

## 📈 Results and Limitations

The recorded cross-validation experiments show that LightGBM achieved
the highest mean R² among the three compared models.

The final competition submission was generated using a tuned Random
Forest Regressor.

A verified Kaggle leaderboard score has not been documented here.

## 🙏 Acknowledgements

- Kaggle for providing the Cinema Audience Forecasting Challenge.
- IIT Madras for the Machine Learning Practice coursework.

## 📄 Dataset Disclaimer

The competition datasets are not included in this repository.
Users should obtain the data directly from Kaggle and follow the
applicable competition rules and dataset terms.