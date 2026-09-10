# NLP Based Sentiment Analysis Using Naive Bayes and Transformers

## 📌 About the Project

This project focuses on **Sentiment Analysis**, an NLP technique used to identify the sentiment expressed in text. We implemented and compared two approaches: **Naive Bayes** as a traditional Machine Learning method and **Transformers** as a modern Deep Learning approach.

The project demonstrates how both methods can be used to classify text into sentiment categories and highlights the difference between traditional NLP techniques and context-aware Transformer models.

## 📝 Abstract

The project presents an NLP-based sentiment analysis system using **Naive Bayes and Transformer models**. The text data is first cleaned and preprocessed before being passed to the respective models.

For the traditional approach, **TF-IDF** is used to convert text into numerical features, which are then classified using **Naive Bayes**. The second approach uses a **Transformer model** to understand the contextual relationships between words and perform sentiment classification.

Both approaches are evaluated and compared using metrics such as **Accuracy, Precision, Recall, and F1-Score**. This comparison helps us understand the strengths and limitations of traditional Machine Learning and modern Transformer-based NLP techniques.

## 🔄 Workflow

## 🔄 Workflow

```text
                 Input Text
                     │
                     ▼
            Text Preprocessing
                     │
              ┌──────┴──────┐
              │             │
              ▼             ▼
           TF-IDF       Tokenization
              │             │
              ▼             ▼
        Naive Bayes    Transformer
              │             │
              └──────┬──────┘
                     ▼
           Sentiment Prediction
                     │
                     ▼
             Model Evaluation
```


## 🧠 Models Used

* **Naive Bayes** – Traditional and lightweight ML approach.
* **Transformer** – Context-aware Deep Learning approach.

## 🛠️ Technologies

* Python
* NLP
* Scikit-learn
* Pandas
* NumPy
* TF-IDF
* Naive Bayes
* Transformers

## 📊 Evaluation

The models are compared using:

* Accuracy
* Precision
* Recall
* F1-Score

## 🚀 Future Scope

* Add more sentiment classes such as **Neutral**.
* Experiment with different Transformer models.
* Deploy the system as a web application.
* Support multilingual sentiment analysis.

## 👥 Team

**NLP Based Sentiment Analysis Using Naive Bayes and Transformers**

Developed as an academic project to explore and compare traditional and modern NLP techniques.
