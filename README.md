# Thiranex Task 3 – Phishing Email Detection Model

A ready-to-run Scikit-learn project for detecting whether an email is **Phishing** or **Safe**.

## Features

- TF-IDF text features from email content
- URL-based features:
  - URL count
  - suspicious URL count
  - IP-address URL count
  - URL shortener count
  - `@` in URL count
  - HTTP vs HTTPS
  - average URL length
- Phishing keyword features
- Logistic Regression classifier
- Accuracy, precision, recall and F1-score
- Confusion matrix image
- Streamlit interface for testing a new email
- Saves the trained model as `models/phishing_model.joblib`

## Dataset

The project is configured to use the **Phishing validation emails dataset** from Zenodo:
https://zenodo.org/records/13474746

It contains 2,000 labeled emails with the labels **Safe Email** and **Phishing Email**.

The training script can download this dataset automatically. If downloading is not possible, it uses the included small `data/sample_emails.csv` so the project can still be demonstrated offline.

For your final Thiranex submission, use the full downloaded dataset and keep the generated `outputs/` files as evidence.

## 1. Install Python

Use Python 3.10 or newer.

## 2. Open the project in VS Code

Open this folder:

`phishing_email_detection_thiranex`

## 3. Create a virtual environment

Windows:

```powershell
python -m venv .venv
.venv\Scripts\activate
```

## 4. Install packages

```powershell
pip install -r requirements.txt
```

## 5. Train the model

Run:

```powershell
python train_model.py
```

The script will:
1. Download the Zenodo dataset if it is not already present.
2. Read and clean the data.
3. Split it into training and testing sets.
4. Extract TF-IDF and URL/security features.
5. Train Logistic Regression.
6. Print evaluation metrics.
7. Save the model.
8. Save the confusion matrix to `outputs/confusion_matrix.png`.
9. Save metrics to `outputs/metrics.txt`.

## 6. Run the web app

After training:

```powershell
streamlit run app.py
```

Then open the local Streamlit URL shown in the terminal.

Paste an email and click **Analyze Email**.

## Project structure

```text
phishing_email_detection_thiranex/
│
├── app.py
├── train_model.py
├── download_dataset.py
├── utils.py
├── requirements.txt
├── README.md
│
├── data/
│   └── sample_emails.csv
│
├── models/
│   └── phishing_model.joblib       # created after training
│
└── outputs/
    ├── confusion_matrix.png        # created after training
    └── metrics.txt                 # created after training
```

## Important

Do not claim a specific accuracy before you run the model. The actual accuracy depends on the dataset, split and model version. Use the accuracy printed by `train_model.py` in your submission.

## Thiranex presentation explanation

**Problem:** Phishing emails try to trick users into clicking malicious links or giving sensitive information.

**Solution:** The system uses machine learning to learn patterns from labeled phishing and legitimate emails. It analyzes email text and URL characteristics and predicts whether a new email is phishing or safe.

**Workflow:**

```text
Email Dataset
     ↓
Data Cleaning
     ↓
Text + URL Feature Extraction
     ↓
TF-IDF + Security Features
     ↓
Logistic Regression
     ↓
Prediction
     ↓
Phishing / Safe
     ↓
Accuracy + Confusion Matrix
```

## Technologies

- Python
- Pandas
- NumPy
- Scikit-learn
- Matplotlib
- Joblib
- Streamlit

## Dataset citation

Miltchev, R., Rangelov, D., & Genchev, E. (2024).
Phishing validation emails dataset.
Zenodo. DOI: 10.5281/zenodo.13474746
