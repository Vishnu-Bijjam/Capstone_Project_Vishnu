# Capstone_Project_Vishnu
# Fake News Detection Using Machine Learning and Deep Learning
What Problem Did I Try to Solve?

1. Fake news detection refers to using machine learning algorithms to classify news articles as real or fake, addressing the widespread issue of misinformation on digital platforms
2. Reducing Manual Verification:The goal was to automate the news verification process, so fake news can be flagged quickly before it spreads — without depending only on human fact-checkers.


This repository contains code, analysis and a simple GUI for classifying U.S. political news headlines as *fake* or *real* using machine learning and deep learning methods.

Why Is This Project Important?
 Social Impact & Trust: Fake news can influence public opinion, disrupt democratic processes, and incite panic or violence, making reliable detection crucial to maintain societal trust and safety.
Industry Relevance: Social media platforms, news agencies, and cybersecurity firms require automated solutions to moderate content at scale and protect users from disinformation.

Who are the stakeholders or target audience?
Digital Platforms & Media Companies
General Public & Policymakers



## Table of Contents

- [Dataset](#dataset)  
- [Exploratory Data Analysis](#exploratory-data-analysis)  
- [Modeling](#modeling)  
- [Results](#results)  
- [Explainability](#explainability)  
- [GUI](#gui)    

---

## Dataset

- *Source*: Kaggle (https://www.kaggle.com/datasets/nitishjolly/news-detection-fake-or-real-dataset)
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
| *CNN (Conv1D)*        |  *98.7%* |
| LSTM                    |    51.0% |

- *CNN* achieved the highest accuracy on this dataset.  
- *LSTM* underperformed, likely due to limited sequence length and training epochs.

---

## Explainability

- *LIME*  
  - Local, per-sample feature attributions.  
  - Interactive HTML widget (probability bars, weight bars, highlighted text).  

---

## GUI

A simple *Tkinter* application wraps the trained CNN:

- Paste or type a headline/text.  
- Click *Classify* → shows *Fake/Real* with percentage.  
- Click *Explain (LIME)* → displays top token attributions.



