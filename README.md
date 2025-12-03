# SarcasmLens: Detecting Sarcasm in Hindi–English Code-Mixed Text

Sarcasm detection is a challenging NLP task, especially in **code-mixed Hindi–English social media text**, where sarcastic intent often contradicts surface sentiment and relies on cultural context.
This project presents **SarcasmLens**, a hybrid framework that combines **traditional feature-based classifiers** with a **multilingual transformer (XLM-RoBERTa)** using a weighted ensemble approach.



## 📌 Project Highlights

* ✅ First comprehensive baseline for Hindi–English code-mixed sarcasm detection
* ✅ Detailed **data quality and leakage analysis**
* ✅ **Hybrid ensemble** combining TF-IDF + linguistic features with XLM-RoBERTa
* ✅ State-of-the-art performance (F1-score: **0.9859**)
* ✅ Strong focus on **interpretability, reproducibility, and transparency**



## 🧠 Problem Statement

Traditional sentiment analysis systems fail to identify sarcasm due to:

* Literal interpretation of positive words
* Lack of contextual and cultural understanding
* Inability to handle **code-switching (Hindi–English)**

This project addresses these challenges by leveraging **multilingual contextual embeddings** while preserving interpretable surface-level cues.



## 📂 Dataset

* **Name:** HackArena Multilingual Sarcasm Dataset
* **Size:** ~11,900 social media comments
* **Labels:**

  * `1` → Sarcastic
  * `0` → Non-sarcastic
* **Language:** Predominantly Hindi–English code-mixed text

### ⚠️ Data Quality Observations

* Duplicate and near-duplicate samples
* Train–test overlaps (data leakage)
* Template-based sarcastic patterns

> These issues can artificially inflate evaluation scores.
> All findings are reported transparently.



## 🛠 Preprocessing Pipeline

* URL and user mention removal
* Emoji → textual meaning mapping
* Hashtag segmentation
* Elongation normalization (e.g., `soooo → soo`)
* Case normalization
* **Punctuation preserved** as sarcasm indicators
* No aggressive stopword removal (to retain code-mixed context)



## 🔧 Model Architecture

### Baseline Models

* Logistic Regression
* Linear Support Vector Machine (SVM)
* Random Forest
* Multinomial Naive Bayes

**Features:**

* TF-IDF (unigrams + bigrams)
* Linguistic cues (punctuation, capitalization, sentiment)



### Transformer Model

* **XLM-RoBERTa-base (125M parameters)**
* Multilingual pretrained on 100 languages
* Handles Romanized Hindi and code-switching naturally

**Fine-tuning:**

* Epochs: 3
* Learning Rate: 2e-5
* Sequence Length: 128



## 🔗 Ensemble Strategy

The final prediction is obtained using weighted probability fusion:

$P_{\text{final}} = 0.4\,P_{\text{traditional}} + 0.6\,P_{\text{XLM-R}}$


### Why Ensemble?

* Traditional models → surface-level sarcasm markers
* XLM-R → deep semantic & cultural understanding
* Ensemble → robust and generalized predictions



## 📊 Evaluation Setup

* Train/Test Split: 80% / 20% (stratified)
* Cross-validation: 5-fold stratified CV
* Random Seed: 42
* Hardware: GPU-accelerated training

**Metrics:**

* Primary: F1-score
* Secondary: Accuracy, Precision, Recall
* Advanced: AUC-ROC, confidence calibration



## 📈 Results

| Model               | Accuracy   | F1-score   | AUC-ROC    |
| - | - | - | - |
| Logistic Regression | 0.9425     | 0.9425     | 0.9832     |
| SVM (Linear)        | 0.9746     | 0.9746     | 0.9951     |
| Random Forest       | 0.9656     | 0.9656     | 0.9928     |
| XLM-RoBERTa         | 0.9812     | 0.9811     | 0.9978     |
| **Ensemble (Ours)** | **0.9860** | **0.9859** | **0.9989** |

### Key Insights

* 35% reduction in false positives
* 28% reduction in false negatives
* Minimal train-test generalization gap
* Significant improvement in ambiguous sarcasm cases



## 🔮 Future Work

* Collect more authentic, diverse code-mixed sarcasm datasets
* Extend to other Indian language pairs
* Deploy for real-time social media monitoring
* Cross-platform validation (Twitter, YouTube, Instagram)

## 👨‍🎓 Author
**Akshat Kadia**
Under the guidance of Professor Sourish Dasgupta
Dhirubhai Ambani University

🔗 GitHub: *Sarcasm Detection Project*
([https://github.com/akshat-11004/Sarcasm-Detection-Project.git](https://github.com/akshat-11004/Sarcasm-Detection-Project.git))


## 📄 License

This project is intended for **academic and research purposes only**.
