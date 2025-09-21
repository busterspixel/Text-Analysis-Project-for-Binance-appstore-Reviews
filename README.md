# Google Play Store Review Analysis: Sentiment & Topic Modeling

This project performs a comprehensive analysis of user reviews from a Google Play Store app(Binance). It processes raw text data to uncover key insights through sentiment analysis and topic modeling, and visualizes the results for easy interpretation.



## 📜 Project Overview

The goal of this project is to automate the process of understanding user feedback. By analyzing thousands of reviews, we can quickly identify:
* **Overall User Sentiment:** Are users generally positive, negative, or neutral about the app?
* **Key Themes & Topics:** What specific features, issues, or compliments are users frequently discussing?

This analysis pipeline is built using Python and popular data science libraries like Pandas, NLTK, TextBlob, and Scikit-learn.

## ✨ Features

* **Text Preprocessing**: Cleans and prepares raw review text by tokenizing, converting to lowercase, and removing special characters and stopwords.
* **Sentiment Analysis**: Utilizes `TextBlob` to calculate a sentiment polarity score for each review and categorizes them as **Positive**, **Negative**, or **Neutral**.
* **Topic Modeling**: Employs **TF-IDF** (Term Frequency-Inverse Document Frequency) and **NMF** (Non-negative Matrix Factorization) to discover latent topics within the reviews.
* **Data Visualization**: Generates clear and insightful visualizations:
    * A **pie chart** showing the distribution of sentiment.
    * **Bar charts** displaying the most important words for each topic.
    * **Word clouds** for a more intuitive view of topic keywords.

## 📦 Requirements

To run this project, you'll need Python 3 and the following libraries. You can install them using pip:

```bash
pip install pandas openpyxl nltk textblob scikit-learn matplotlib wordcloud
```

Additionally, the script requires NLTK data for tokenization and stopwords. The first time you run the script, it will download these necessary packages. You can also download them manually in a Python environment:

```python
import nltk
nltk.download('punkt')
nltk.download('stopwords')
```

## 📊 Workflow & Usage

The entire analysis is structured as a sequential pipeline. Follow the steps below to replicate the analysis.

### 1. Data Input

Place your raw data file (e.g., from a Google Play scraper) in the project directory. The script assumes it's an Excel file (`.xlsx`) and expects the user reviews to be in a column named `text`.

Update the `file_path` variable in the script to point to your dataset:
```python
# Replace 'your_file.xlsx' with the path to your Excel file.
file_path = "C:\\Users\\ASUS\\OneDrive\\Desktop\\dataset_google-play-scraper_2025-09-12_06-29-05-732.xlsx"
df = pd.read_excel(file_path)
```

### 2. Text Preprocessing

The initial part of the script cleans the `text` column. It performs the following operations and creates new columns in the DataFrame to store the intermediate results:
1.  **Drops empty rows**.
2.  **Tokenizes** the text (splits sentences into words).
3.  Converts text to **lowercase**.
4.  Removes **special characters** and punctuation.
5.  Removes common English **stopwords** (e.g., 'the', 'a', 'is').

### 3. Sentiment Analysis

Using the cleaned text, the script performs sentiment analysis with `TextBlob`:
1.  It calculates a **sentiment score** (polarity) for each review, ranging from -1 (very negative) to +1 (very positive).
2.  It categorizes each review as `Positive`, `Negative`, or `Neutral` based on the score.
3.  The results, including the scores and categories, are saved to a new Excel file named `sentiment_analysis_results.xlsx`.

### 4. Topic Modeling

The script then uses the cleaned text from `sentiment_analysis_results.xlsx` to identify 5 distinct topics:
1.  The text is converted into a numerical format using a **TF-IDF Vectorizer**.
2.  An **NMF model** is trained on the TF-IDF matrix to extract the topics.
3.  The top 10 most influential words for each topic are printed to the console.

### 5. Visualization

Finally, the script generates several plots to visualize the findings:
1.  **Sentiment Pie Chart**: A chart showing the percentage breakdown of positive, negative, and neutral reviews.
2.  **Topic Bar Charts**: A separate horizontal bar chart for each topic, illustrating the key words and their importance (weights).
3.  **Topic Word Clouds**: A word cloud for each topic, providing a visually engaging representation of the most prominent words.

All plots are displayed on the screen as the script runs.

## 📁 File Structure

```
.
├── your_dataset.xlsx              # Your initial input data file
├── sentiment_analysis_results.xlsx # Output file with sentiment scores and cleaned text
└── analysis_script.py             # Your main Python script containing the code
```

## ⚖️ License

This project is licensed under the MIT License. See the `LICENSE` file for more details.
