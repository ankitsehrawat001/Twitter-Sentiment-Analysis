# Hate Speech Detector

A Streamlit application that classifies submitted English text as **Normal text** or **Hateful / harmful text**. It uses a trained Logistic Regression model and a fitted TF-IDF vectorizer.

## Features

- Text input on the home page and a separate prediction results page.
- Displays the predicted category and the submitted text.
- Cleans input using the same normalization used during model training: lowercasing, removing URLs and mentions, removing punctuation and numbers, and collapsing extra spaces.
- Limits input to 5,000 characters.

## Project files

| File | Purpose |
| --- | --- |
| `app.py` | Streamlit user interface and prediction flow |
| `hate_speech_model.pkl` | Trained Logistic Regression model |
| `tfidf_vectorizer.pkl` | Fitted TF-IDF vectorizer |
| `requirements.txt` | Python package dependencies |
| `Twitter_Sentiment_Analysis.ipynb` | Notebook containing the dataset preparation and model training workflow |

The model and vectorizer files must remain in the project root next to `app.py`.

## Setup on Windows

Open PowerShell in the project folder and create a virtual environment:

```powershell
py -3 -m venv .venv
```

Activate it:

```powershell
.\.venv\Scripts\Activate.ps1
```

If PowerShell blocks activation, allow it for the current terminal session and activate again:

```powershell
Set-ExecutionPolicy -Scope Process -ExecutionPolicy Bypass
.\.venv\Scripts\Activate.ps1
```

Install dependencies:

```powershell
python -m pip install --upgrade pip
python -m pip install -r requirements.txt
```

## Run the app

From the project folder, with the virtual environment active:

```powershell
streamlit run app.py
```

Streamlit will print a local URL (typically `http://localhost:8501`) to open in your browser. Enter text at the bottom of the home page and select **Analyze text** to view the prediction.

## Model and dataset

The notebook uses the [Hate Speech Detection Curated Dataset on Kaggle](https://www.kaggle.com/datasets/waalbannyantudre/hate-speech-detection-curated-dataset) and saves the trained model and vectorizer as pickle files. The application loads those saved files; it does not download the dataset or train the model when it starts.

`requirements.txt` pins scikit-learn to version `1.6.1`, matching the version used to serialize the model and vectorizer.

## Limitations

This is an automated text classification result, not a definitive judgment of intent or context. The model was trained for English text and may misclassify sarcasm, quotations, reclaimed language, or text outside its training data.
