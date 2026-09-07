# 🧠 Arabic Sentiment Analysis using Deep Learning

A Deep Learning project for **Arabic Sentiment Analysis**, where Arabic text is classified into three sentiment categories:

* 🔴 Negative
* 🟡 Neutral
* 🟢 Positive

The project implements and compares **5 different Deep Learning architectures** to evaluate their performance on Arabic text classification.

---

## 📌 Project Overview

Sentiment Analysis is an important Natural Language Processing (NLP) task that aims to understand the emotional sentiment behind text.

In this project, Arabic text goes through a complete NLP pipeline including:

* Arabic text cleaning
* Emoji sentiment handling
* Arabic character normalization
* Stopword removal
* Label encoding
* Train/Test splitting
* Handling class imbalance using Oversampling
* Tokenization
* Padding
* Training multiple Deep Learning models
* Model evaluation and comparison

The main goal is to compare different neural network architectures and analyze their performance on the same Arabic sentiment classification task.

---

## 🤖 Models

The following models were implemented and evaluated:

### 1️⃣ Simple RNN

A basic Recurrent Neural Network used as a baseline model for sequence learning.

```text
Embedding
    ↓
Simple RNN
    ↓
Dropout
    ↓
Dense
    ↓
Softmax
```

---

### 2️⃣ LSTM

Long Short-Term Memory networks are designed to better capture long-term dependencies in sequential data.

```text
Embedding
    ↓
LSTM
    ↓
Dropout
    ↓
Dense
    ↓
Softmax
```

---

### 3️⃣ GRU

Gated Recurrent Units provide a simpler alternative to LSTMs while maintaining the ability to learn long-term dependencies.

```text
Embedding
    ↓
GRU
    ↓
Dropout
    ↓
Dense
    ↓
Softmax
```

---

### 4️⃣ Bidirectional LSTM

The Bidirectional LSTM processes the text in both directions:

* Forward context
* Backward context

This helps the model capture more contextual information from the sentence.

```text
Embedding
    ↓
Bidirectional LSTM
    ↓
Dropout
    ↓
Dense
    ↓
Softmax
```

---

### 5️⃣ Transformer Encoder

A Transformer Encoder was built from scratch using:

* Multi-Head Attention
* Positional Encoding
* Feed Forward Network
* Residual Connections
* Layer Normalization

This architecture allows the model to capture relationships between words using the attention mechanism.

```text
Embedding + Positional Encoding
            ↓
      Multi-Head Attention
            ↓
        Add & Normalize
            ↓
    Feed Forward Network
            ↓
        Add & Normalize
            ↓
           Dense
            ↓
          Softmax
```

---

# 📂 Dataset

The dataset contains Arabic text with sentiment labels.

### Features

| Column      | Description     |
| ----------- | --------------- |
| `text`      | Arabic text     |
| `sentiment` | Sentiment label |

### Sentiment Classes

| Value | Label    |
| ----- | -------- |
| `-1`  | Negative |
| `0`   | Neutral  |
| `1`   | Positive |

---

# ⚙️ Data Preprocessing

Arabic text requires special preprocessing before being used in Deep Learning models.

The preprocessing pipeline includes:

### 🧹 Text Cleaning

* Removing URLs
* Removing unnecessary characters
* Removing numbers and non-Arabic characters

### 🔤 Arabic Normalization

Different Arabic characters are normalized to reduce vocabulary variations.

For example:

```text
أ → ا
إ → ا
آ → ا
ى → ي
```

### 📝 Removing Tashkeel

Arabic diacritics are removed to simplify the text representation.

### ➖ Removing Tatweel

```text
جميــــل → جميل
```

### 🔁 Reducing Character Repetition

Repeated characters are reduced to avoid unnecessary variations.

```text
جمييييييل → جميل
```

### 😊 Emoji Sentiment Mapping

Instead of removing emojis completely, common emojis are converted into Arabic words representing their sentiment.

For example:

```text
😀 → سعيد
😍 → رائع
😡 → غاضب
😭 → حزين
```

This helps preserve useful sentiment information.

### 🚫 Stopwords Removal

Common Arabic stopwords are removed using NLTK.

---

# ⚖️ Handling Class Imbalance

The dataset contains different numbers of samples for each sentiment class.

To handle this problem, **Oversampling** is applied only to the training data.

> The oversampling process is performed after the Train/Test split to avoid data leakage.

The test set remains unchanged so that the final evaluation represents the real data distribution.

---

# 🔢 Tokenization and Padding

The cleaned Arabic text is converted into sequences of integers using TensorFlow's Tokenizer.

```python
VOCAB_SIZE = 20000
```

An `<OOV>` token is used to handle unknown words.

After tokenization, sequences are padded to the same length.

The maximum sequence length is determined using the **95th percentile of the text word count**, which helps avoid choosing an unnecessarily large sequence length.

---

# 🏋️ Training Configuration

The models are trained using:

* **Embedding Dimension:** 128
* **Optimizer:** Adam
* **Loss Function:** Categorical Crossentropy
* **Output Activation:** Softmax
* **Batch Size:** 64
* **Random State:** 42

---

# 📊 Evaluation

Each model is evaluated using multiple metrics:

* Accuracy
* Precision
* Recall
* F1-Score
* Confusion Matrix

Training history is also visualized to monitor:

* Training Accuracy
* Validation Accuracy
* Training Loss
* Validation Loss

---

# 📈 Final Model Comparison

After training all five models, their performance is compared side by side.

The project compares:

```text
Simple RNN
LSTM
GRU
Bidirectional LSTM
Transformer
```

The comparison helps identify which architecture performs best for the Arabic sentiment classification task.

A combined visualization of the **Confusion Matrices** is also generated for all models.

---

# 🛠️ Technologies Used

* Python
* TensorFlow / Keras
* NumPy
* Pandas
* Scikit-learn
* Matplotlib
* Seaborn
* NLTK
* PyArabic

---

# 📦 Installation

Clone the repository:

```bash
git clone https://github.com/YOUR_USERNAME/Arabic-Sentiment-Analysis-Deep-Learning.git
```

Navigate to the project directory:

```bash
cd Arabic-Sentiment-Analysis-Deep-Learning
```

Install the required libraries:

```bash
pip install tensorflow pandas numpy matplotlib seaborn scikit-learn nltk pyarabic openpyxl
```

---

# 🚀 Usage

1. Place the dataset in the project directory.
2. Make sure the dataset path is correctly configured:

```python
DATA_PATH = "Arabic Sentiment Analysis .xlsx"
```

3. Open the notebook:

```bash
jupyter notebook sentiment_analysis_arabic_deep_learning_.ipynb
```

4. Run all cells.

---

# 📁 Project Structure

```text
Arabic-Sentiment-Analysis-Deep-Learning/
│
├── sentiment_analysis_arabic_deep_learning_.ipynb
│
├── Arabic Sentiment Analysis .xlsx
│
├── README.md
│
└── requirements.txt
```

---

# 🎯 Key Takeaways

This project demonstrates a complete Deep Learning workflow for Arabic NLP:

```text
Raw Arabic Text
       ↓
Text Cleaning
       ↓
Arabic Normalization
       ↓
Emoji Processing
       ↓
Stopword Removal
       ↓
Train/Test Split
       ↓
Oversampling
       ↓
Tokenization
       ↓
Padding
       ↓
Deep Learning Models
       ↓
Evaluation
       ↓
Model Comparison
```

The project also provides a practical comparison between traditional recurrent architectures such as **RNN, LSTM, and GRU**, a **Bidirectional LSTM**, and a **Transformer-based architecture** for Arabic text classification.

---

## 👨‍💻 Author

**Ahmed Maged**

Machine Learning Engineer | Deep Learning & NLP Enthusiast

⭐ If you found this project useful, consider giving the repository a star!
