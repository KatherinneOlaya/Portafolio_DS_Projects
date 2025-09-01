# 📊 Real-Time Sentiment Analysis of iPhone 17 Tweetss

This project performs **real-time sentiment analysis** on tweets related to the iPhone 17 and Apple events, using **Natural Language Processing (NLP)** and **Transformer models**.

---

## 🎯 Project Objective

The main goal is to:
1. Collect recent tweets mentioning the *iPhone 17* and *Apple events*.
2. Preprocess and clean the text for analysis.
3. Apply a Transformer-based sentiment analysis model to classify tweet polarity (**positive, negative, neutral**).

---

## 🛠️ Technologies & Libraries Used

- **Python** – Main programming language.  
- **Google Colab** – Cloud-based development environment.  
- **Tweepy** – Interact with Twitter (X) API to collect tweets.  
- **Pandas** – Data manipulation and analysis.  
- **NLTK (Natural Language Toolkit)** – Tokenization, stopwords, and other NLP resources.  
- **spaCy** – Lemmatization and advanced text processing.  
- **demoji** – Emoji detection and handling.  
- **Transformers (Hugging Face)** – Pre-trained sentiment analysis model (`cardiffnlp/twitter-roberta-base-sentiment`).  
- **PyTorch** – Deep learning framework used by Transformer models.  
- **Scikit-learn** – ML utilities (not used in final pipeline but included).  
- **Seaborn & Matplotlib** – Data visualization (sentiment distribution).  
- **Joblib** – Model persistence (optional, implemented but not required).  
- **Tqdm** – Progress bar for batch operations.  

---

## 📝 Workflow

1. **Library Installation**  
   - Installed all required packages: `tweepy`, `transformers`, `torch`, `datasets`, `nltk`, `spacy`, `scikit-learn`, `demoji`.  

2. **Resource Download**  
   - Downloaded NLTK resources (`punkt`, `stopwords`, `wordnet`).  
   - Downloaded spaCy English model (`en_core_web_sm`).  

3. **Twitter API Configuration**  
   - Configured Tweepy client with a **Bearer Token**.  
   - Managed authentication errors and rate limits.  

4. **Data Collection**  
   - Collected recent English tweets mentioning *“iPhone 17”* or *“Apple Event”*.  
   - Saved raw tweets into `tweets_raw.csv`.  

5. **Data Loading & Exploration**  
   - Loaded CSV into Pandas DataFrame.  
   - Checked duplicates and null values.  

6. **Text Preprocessing** (`preprocess_text` function):  
   - Handled null values.  
   - Converted text to lowercase.  
   - Attempted emoji replacement (removed in final regex cleaning).  
   - Removed URLs, numbers, and special characters.  
   - Tokenized text.  
   - Removed stopwords.  
   - Lemmatized words using spaCy.  
   - Created a new column `processed_text` with clean tokenized text.  

7. **Sentiment Analysis with Transformers**  
   - Implemented a class `TransformerAnalysisSentiment` using Hugging Face model: `cardiffnlp/twitter-roberta-base-sentiment`.  
   - Added batch processing (`analyze_batch`) for efficiency.  
   - Function `sentiment_load_analysis` loads data, preprocesses, and applies model to return predictions (labels, scores, probabilities).  

8. **Results Processing & Visualization**  
   - Converted results into a Pandas DataFrame (`result_padnas`).  
   - Mapped raw labels (`LABEL_0`, `LABEL_1`, `LABEL_2`) to descriptive labels (`Negative`, `Neutral`, `Positive`).  
   - Visualized sentiment distribution with Seaborn countplots and score histograms.  
   - Displayed most positive and most negative tweets.  

---

## 🚀 Usage

1. Get a **valid Twitter API Bearer Token** and set it as an environment variable in your notebook.  
2. Run the notebook cells in order: install dependencies → collect tweets → preprocess → analyze sentiment.  
3. Final sentiment analysis results are stored in the Pandas DataFrame `result_padnas`.  
4. Use the included visualizations to explore sentiment trends.  

---

## 📂 Project Output

- `tweets_raw.csv` → Raw collected tweets.  
- `tweets_clean.csv` → Preprocessed, tokenized, lemmatized tweets.  
- `result_padnas` → DataFrame with sentiment predictions.  
- Visualizations: sentiment distribution plots and example tweets.  

---

## 📌 Future Improvements
- Deploy the pipeline as a **real-time dashboard**.  
- Add **topic modeling / clustering** to group opinions by themes (e.g., battery, camera, price).  
- Automate weekly **report generation** (PDF/HTML).  

---
