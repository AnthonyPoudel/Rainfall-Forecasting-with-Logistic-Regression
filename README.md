🌟 Overview
This project builds a machine‑learning model to predict whether it will rain tomorrow in Australia using the WeatherAUS dataset. It demonstrates a complete end‑to‑end ML workflow:

Data loading and cleaning

Exploratory data analysis (EDA)

Feature engineering

Scaling and one‑hot encoding

Logistic Regression model training

Evaluation on train/validation/test splits

Saving processed datasets

Predicting on new user inputs

The notebook is ideal for anyone learning practical ML pipelines using Python and scikit‑learn.

📊 Dataset
Source: Kaggle – Weather Dataset (Rattle Package)  
Rows: ~145k
Target: RainTomorrow (Yes/No)

Key features include:

Temperature (MinTemp, MaxTemp)

Humidity

Pressure

Wind direction & speed

Rainfall

Cloud cover

Location & date

A time‑based split is used to avoid data leakage:

Train: data before 2015

Validation: 2015

Test: 2016 onward

🔍 Exploratory Data Analysis
The notebook includes visualizations such as:

Rainfall distribution

Temperature relationships

Humidity vs RainTomorrow

Location frequency

Year‑wise data availability

These insights guide feature selection and preprocessing decisions.

🛠️ Preprocessing Pipeline
🔧 Handling Missing Values
Numerical columns → mean imputation

Categorical columns → handled by OneHotEncoder

📏 Scaling
Applied MinMaxScaler to all numeric features

Ensures stable gradient updates for Logistic Regression

🎨 Encoding
Used OneHotEncoder (sparse_output=False)

Generated 100+ encoded features

Combined with scaled numeric features

🧹 Final Feature Set
numeric_cols

encoded_cols  
Total: 123 features

🤖 Model Training
Model used:
LogisticRegression(solver="liblinear")
Training is performed on:
X_train = train_inputs[numeric_cols + encoded_cols]
y_train = train_target
The model learns a weight for each feature and a bias term.

📈 Model Performance
Dataset	Accuracy
Train	~85.19%
Validation	~85.41%
Test	~84.22%
A normalized confusion matrix is included in the notebook to visualize prediction quality.

💾 Saving Processed Data
All processed datasets are saved as Parquet files for fast loading and preserved data types:

train_inputs.parquet
val_inputs.parquet
test_inputs.parquet
train_target.parquet
val_target.parquet
test_target.parquet
🔮 Predicting New Inputs
The notebook includes a helper function:

predictSingleInputs(singleInputs)
It:

Converts raw input into a DataFrame

Applies imputation, scaling, and encoding

Predicts Yes/No

Returns probability scores

🚀 Future Enhancements
Try tree‑based models (Random Forest, XGBoost, LightGBM)

Hyperparameter tuning

Address class imbalance

Deploy as a web app or API

Add SHAP or feature importance visualizations
