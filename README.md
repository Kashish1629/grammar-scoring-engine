# Speech-Based Grammar Scoring Engine 

## Problem Statement 

Spoken English assessment is traditionally manual, subjective, and time-consuming.
This project explores how speech recognition and NLP techniques can be combined to automatically evaluate the grammatical quality of spoken responses.

The goal is to build an end-to-end system that predicts a continuous grammar score (0–5) from raw speech audio.

## Dataset 

This project uses English speech recordings from the Mozilla Common Voice dataset.

The dataset provides real-world voice samples, making the system more robust and practical for real assessment scenarios.

## System Overview 

Given an input audio file (.wav), the system:

Transcribes speech using OpenAI Whisper

Extracts advanced linguistic quality features

Trains an XGBoost regression model

Predicts a continuous grammar score between 0 and 5

## System Pipeline 

Audio → Transcription → Linguistic Feature Extraction → ML Model → Score Prediction

1) Speech Recognition

Audio files are transcribed using Whisper to convert speech into text.
This step transforms raw speech into structured textual data suitable for linguistic analysis.

2) Feature Engineering

Instead of relying on simple word counts, the system extracts advanced linguistic indicators such as:

Grammar error density

Lexical diversity

Sentence length metrics

Pause density (fluency proxy using transcription segments)

Readability score (Flesch Reading Ease)

Repetition ratio

These features collectively capture:

Structural correctness

Vocabulary richness

Sentence formation quality

Speech fluency patterns

3) Model Training

An XGBoost Regressor is trained on structured linguistic features.

Validation Strategy

80–20 train-validation split

Evaluation using Mean Squared Error (MSE)

Root Mean Squared Error (RMSE) for interpretability

Validation RMSE: ~1.09

This indicates the model predicts grammar scores within approximately ±1 point on average.

## Output Example 

| Filename        | Predicted Score |
|----------------|----------------|
| audio_706.wav  | 3.046294       |
| audio_800.wav  | 3.638973       |
| audio_68.wav   | 3.611071       |
| audio_1267.wav | 3.798203       |
| audio_683.wav  | 2.404651       |

## Future Improvements 

Incorporating transformer-based sentence embeddings

Adding pronunciation and speech-rate metrics

Fine-tuning Whisper for accent-specific robustness

Exploring LightGBM or CatBoost for comparison

Developing an end-to-end neural scoring architecture

## Technologies Used 

Python

Whisper (Speech-to-Text)

LanguageTool (Grammar checking)

TextStat (Readability metrics)

XGBoost

Scikit-learn

Librosa

## How to Run 

Install dependencies:

pip install -r requirements.txt

Open the notebook:

Grammar_Scoring_Engine.ipynb

## Run all cells to 

Transcribe audio

Extract features

Train the model

Generate predictions

Repository Structure :

Grammar_Scoring_Engine.ipynb
submission.csv
README.md
