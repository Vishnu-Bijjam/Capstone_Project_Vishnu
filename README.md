# Capstone_Project_Vishnu
# Fake News Detection Using Machine Learning
What Problem Did I Try to Solve?
![image](https://github.com/user-attachments/assets/892920a1-d305-448d-85f5-12837b30390c)

1. Fake news detection refers to using machine learning algorithms to classify news articles as real or fake, addressing the widespread issue of misinformation on digital platforms
2. Reducing Manual VerificationThe goal was to automate the news verification process, so fake news can be flagged quickly before it spreads — without depending only on human fact-checkers.
![image](https://github.com/user-attachments/assets/ca360d13-16fc-46a6-b4a2-ac1df0230c7a)


This repository contains code, analysis and a simple GUI for classifying U.S. political news headlines as *fake* or *real* using machine learning and deep learning methods.

## Table of Contents

- [Dataset](#dataset)  
- [Exploratory Data Analysis](#exploratory-data-analysis)  
- [Modeling](#modeling)  
- [Results](#results)  
- [Explainability](#explainability)  
- [GUI](#gui)  
- [Installation](#installation)  
- [Usage](#usage)  
- [License](#license)  

---

## Dataset

- *Source*: Kaggle  
- *File*: fake_and_real_news.csv  
- *Size*: ~10 000 headlines (balanced between “FAKE” and “REAL”)  
- *Columns*:  
  - Text — news headline or snippet  
  - label — “Fake” or “Real”

---

## Exploratory Data Analysis

1. *Label distribution*  
   - Balanced classes: ~5 000 fake, ~5 000 real.  
2. *Text length*  
   - Most headlines are under 100 tokens, with a long-tail of longer snippets.  
3. *Word clouds*  
   - Fake news: sensationalism and click-bait terms (e.g. “Trump”, “Media”, “Twitter”).  
   - Real news: neutral/reporting terms (e.g. “said”, “Reuters”, “Congress”).

---

## Modeling

We trained and compared several classifiers:

- *Logistic Regression* (TF–IDF)  
- *Support Vector Machine* (linear kernel, TF–IDF)  
- *Random Forest* (TF–IDF)  
- *Convolutional Neural Network* (Conv1D + GlobalMaxPooling)  
- *LSTM Network*

All models were evaluated on a 70/30 train/test split.

---

## Results

| Model                   | Accuracy |
|-------------------------|---------:|
| Logistic Regression     |    96.7% |
| SVM (linear)            |    97.3% |
| Random Forest           |    95.2% |
| *CNN (Conv1D)*        |  *98.7%* |
| LSTM                    |    51.0% |

- *CNN* achieved the highest accuracy on this dataset.  
- *LSTM* underperformed, likely due to limited sequence length and training epochs.

---

## Explainability

- *LIME*  
  - Local, per-sample feature attributions.  
  - Interactive HTML widget (probability bars, weight bars, highlighted text).  
- *SHAP*  
  - KernelExplainer for token-level contributions.  
  - Top-10 tokens displayed in the GUI.

---

## GUI

A simple *Tkinter* application wraps the trained CNN:

- Paste or type a headline/text.  
- Click *Classify* → shows *Fake/Real* with percentage.  
- Click *Explain (SHAP)* → displays top token attributions.



