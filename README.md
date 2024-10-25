## Note: Would really appreciate some help with increasing the performance of the duplication checker function. Right now that function single handedly slows down the program by a lot. 

## NLPulse

This Python-based project is designed to analyze sentiment from news articles fetched via RSS feeds, store the sentiment data in a SQLite database, and visualize the results using interactive dashboards. The project combines multiple natural language processing (NLP) models and libraries to ensure a robust sentiment analysis pipeline, providing an overview of sentiment trends across different days, times, and topics.

### Key Features

- **RSS News Fetching**: Pulls news articles from an RSS feed (default: Times of India Top Stories).
- **Sentiment Analysis**: Analyzes the sentiment of each news article using a combination of three sentiment analysis techniques:
  - **VADER**: A rule-based model for general sentiment analysis.
  - **FinBERT**: A transformer model designed specifically for financial sentiment analysis.
  - **RoBERTa**: A transformer model pre-trained on Twitter data, fine-tuned for sentiment.
- **Summarization**: Long news articles are summarized before sentiment analysis using the **BART** summarization model.
- **Data Storage**: Sentiment results, along with article metadata, are stored in an SQLite database for future analysis.
- **Visualizations**: A comprehensive dashboard is generated with multiple plots to visualize sentiment trends over time.

[img](https://iili.io/2fSF41f.png)

## Project Structure

- **Cell 1**: Contains the necessary imports and setup. Libraries like NLTK, transformers, and Plotly are used.
- **Cell 2**: Defines the `SentimentAnalyzer` class for performing sentiment analysis using multiple models and summarizing long texts.
- **Cell 3**: Implements the `DatabaseManager` class, which handles database operations such as storing, cleaning, and deduplicating news entries.
- **Cell 4**: Creates visualizations of the data using the `DataVisualizer` class, which generates an interactive dashboard.

## Requirements

Before running the code, ensure that the required libraries are installed:

```bash
!pip install feedparser TextBlob
!pip install nltk transformers torch wordcloud plotly
```

Libraries used:
- `feedparser`: For fetching and parsing RSS feeds.
- `nltk`: For natural language processing, including sentiment analysis using VADER.
- `transformers`: Hugging Face library for FinBERT, RoBERTa, and BART models.
- `torch`: For handling neural networks and models like BERT/Roberta.
- `wordcloud`: For generating word clouds.
- `plotly`: For creating interactive visualizations.
- `sqlite3`: Built-in Python library for managing a SQLite database.


## Operation Flow

1. **Fetching News**:
    - The program fetches news articles from the specified RSS feed (default: Times of India).
    - For each news article, the article's title and summary are retrieved along with the published date and time.

2. **Sentiment Analysis**:
    - Each article's summary is processed using three models:
      - **VADER**: General-purpose rule-based sentiment analysis model.
      - **FinBERT**: Transformer model fine-tuned for financial sentiment.
      - **RoBERTa**: Transformer model tuned for social media sentiment.
    - Each model generates a sentiment score between 0 and 10, which is combined into a weighted average score.

3. **Storing Results**:
    - The sentiment scores and article details (date, time, title, summary) are stored in a SQLite database.
    - A cleanup process is run on the database to remove redundant or incomplete entries.

4. **Visualization**:
    - Data is retrieved from the database, and an interactive dashboard is generated using Plotly.
    - Various plots display sentiment trends, daily distributions, hourly patterns, and topic-specific sentiment analysis.

## Database Structure

The SQLite database `news_sentiment.db` stores the following fields in the `sentiment_scores` table:

- `date`: The publication date of the news article (in `YYYY-MM-DD` format).
- `time`: The publication time (in `HH:MM:SS` format).
- `title`: The title of the news article.
- `summary`: A summarized version of the article, used for sentiment analysis.
- `score`: The sentiment score of the article (on a scale of 0 to 10).

## Visualizations

The dashboard generated includes several interactive plots:

### 1. **Sentiment Timeline**
   - A time-series line chart that shows the daily average sentiment score.
   - This plot helps in tracking overall sentiment trends over time.

### 2. **Daily Distribution**
   - A histogram displaying the distribution of sentiment scores.
   - It shows how often different sentiment scores (0 to 10) appear in the dataset.

### 3. **Sentiment by Day of Week**
   - A bar plot displaying the average sentiment score for each day of the week.
   - Helps identify trends like whether sentiment tends to be higher or lower on certain days (e.g., weekends vs. weekdays).

### 4. **Hourly Patterns**
   - A line chart showing sentiment scores by hour of the day.
   - Reveals whether sentiment tends to fluctuate based on the time articles are published.

### 5. **Word Cloud**
   - A word cloud generated from the summaries of all news articles.
   - Displays frequently occurring words, giving a quick sense of the most discussed topics.

### 6. **Topic Analysis**
   - A bar plot that shows the average sentiment score across different predefined topics (e.g., Politics, Economy, Health, Technology, Sports).
   - This analysis is based on the presence of specific keywords in the article summaries.

## How to Run

To run the program, simply execute the `main()` function, which will:

1. Fetch news articles from the RSS feed.
2. Analyze each article’s sentiment.
3. Store results in the SQLite database.
4. Clean the database of duplicates and incomplete records.
5. Generate and display an interactive dashboard for further analysis.

```python
if __name__ == "__main__":
    main()
```

## Customization

- **RSS Feed URL**: To change the source of news, replace the `NEWS_FEED_URL` variable with the desired RSS feed URL.
- **Database**: The name of the SQLite database is controlled by the `DATABASE_NAME` constant and can be modified as needed.
- **Visualization Customization**: Modify the `DataVisualizer` class to adjust plots, add new analyses, or include additional data sources.

## Future Enhancements

- **Advanced Topic Classification**: Implement machine learning models to classify news articles into topics more accurately.
- **Extended Sentiment Analysis**: Incorporate more advanced sentiment analysis techniques, including multilingual support.
- **Real-time Analysis**: Integrate real-time news feeds for continuous analysis and automatic updates.
