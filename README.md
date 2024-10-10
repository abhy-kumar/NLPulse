## NLPulse: News Sentiment Analysis with Multiple Models

This project, NLPulse, analyzes the sentiment of news articles using a combination of Natural Language Processing (NLP) techniques. It fetches news from a provided RSS feed, analyzes the sentiment of each article summary, and stores the results in a SQLite database.

**Key Features:**

* **Multiple Sentiment Models:** Leverages VADER, FinBERT, and RoBERTa models for a robust sentiment analysis.
* **Confidence-based Weighting:** Combines scores from each model based on their confidence level.
* **Keyword-based Post-processing:** Adjusts scores for specific keywords indicating high negativity or positivity.
* **Database Storage:** Stores sentiment results for future analysis (database file: `news_sentiment.db`).
* **Daily Average Score:** Calculates the average sentiment score for the current day.

**Requirements:**

* Python 3.x
* Required libraries:
    * `feedparser`
    * `nltk`
    * `requests`
    * `sqlite3`
    * `transformers`
    * `TextBlob` (optional, might be included in `nltk`)

**Installation:**

1. Install the required libraries using `pip`:

```bash
pip install feedparser nltk transformers torch TextBlob
```

**Usage:**

1. Modify the `url` variable in the script to point to your desired RSS feed.
2. Run the script:

```bash
python NLPulse.ipynb
```

**Output:**

* The script will print the title, published date, summary, and sentiment score for each analyzed article.
* It will also calculate and print the average sentiment score for the current day.
* The results will be stored in the `news_sentiment.db` database.

**Further Development:**

* Implement the `To do` sections within the script for additional functionalities like data analysis and visualization.
* Explore more advanced summarization techniques or sentiment analysis models.

**Disclaimer:**

This is a basic implementation and may require further tuning for specific use cases. 
