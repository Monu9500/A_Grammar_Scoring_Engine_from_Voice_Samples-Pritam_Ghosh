# Grammar Scoring Engine for Spoken Audio
An AI-powered system that automatically evaluates the grammatical quality of spoken English audio files and assigns a proficiency score (1-5).

# Overview
This project was developed to automate the assessment of spoken language grammar. The system takes raw audio files (.wav) as input, transcribes them into text, detects grammatical errors, and predicts a Mean Opinion Score (MOS) based on the density of errors.

This solution serves as a robust baseline for automated language testing, using state-of-the-art ASR (Automatic Speech Recognition) and NLP techniques.

# Needed Libraries
![Python](https://img.shields.io/badge/Python-3.8%2B-blue?style=for-the-badge&logo=python&logoColor=white)
![OpenAI Whisper](https://img.shields.io/badge/AI-OpenAI%20Whisper-green?style=for-the-badge&logo=openai&logoColor=white)
![Scikit-Learn](https://img.shields.io/badge/ML-Scikit--Learn-orange?style=for-the-badge&logo=scikit-learn&logoColor=white)
![Pandas](https://img.shields.io/badge/Data-Pandas-150458?style=for-the-badge&logo=pandas&logoColor=white)
![Jupyter](https://img.shields.io/badge/Notebook-Jupyter-F37626?style=for-the-badge&logo=jupyter&logoColor=white)

# Project Structure
The project is organized as follows:

Plaintext

Grammar_Scoring_Project/
│
├── dataset/                   
│   ├── audios/
│   │   ├── train/            
│   │   └── test/             
│   └── csvs/
│       ├── train.csv          
│       └── test.csv          
│
├── grammar_project.ipynb     
├── requirements.txt          
├── submission.csv             
└── README.md                 
# Methodology (How It Works)
The project implements a 3-Stage Pipeline to process audio and predict scores:

**Automatic Speech Recognition (ASR):**

**Tool:** OpenAI Whisper (Base Model)

**Process:** Converts raw .wav audio files into accurate text transcripts.

**Feature Engineering:**

**Tool:** LanguageTool Python

**Metric:** We calculate Error Density:

Error Density= 
Total Word Count
Total Grammar Mistakes
​
 
This normalizes the score so that longer audios aren't penalized unfairly.

**Predictive Modeling:**

**Model:** Linear Regression (scikit-learn)

**Logic:** The model learns the inverse relationship between Error Density and the Grammar Score (i.e., More errors = Lower score).

# Installation & Setup
Prerequisites
Python 3.8+

FFmpeg (Required for processing audio files)

**Windows:** winget install -e --id Gyan.FFmpeg

**Linux:** sudo apt install ffmpeg

**Mac:** brew install ffmpeg

Step 1: Install Dependencies
Open your terminal in the project folder and run:

## Bash

pip install -r requirements.txt
(Content of requirements.txt: openai-whisper, language-tool-python, pandas, scikit-learn, numpy, soundfile, librosa, ipykernel)

## How to Run the Project
**Prepare Data:** Ensure your dataset/ folder contains the train and test audio folders.

**Open Notebook:** Open grammar_project.ipynb in VS Code or Jupyter Lab.

**Run All Cells:** Execute the cells sequentially.

**Note:** The training process may take 15-20 minutes depending on your CPU/GPU, as Whisper transcribes 400+ audio files.

**Get Results:** Once finished, a file named submission.csv will be generated in the root directory containing the predicted scores for the test set.

# Evaluation & Results
**Metric:** Root Mean Squared Error (RMSE)

**Baseline Performance:** The model achieves an RMSE of approximately 0.85 on the validation set.

**Output Format:**

Code snippet

filename, label

audio_141,2.88

audio_114,3.12
...

# Future Improvements
Complexity Features: Add checks for vocabulary richness (Lexical Diversity) to better distinguish Score 5 (Advanced) from Score 3 (Intermediate).

Audio Features: Analyze pauses and hesitation (fluency) in addition to grammar.

# Author
Pritam Ghosh

Role: Final Year B.Tech Student

Institution: University of Engineering and Management
