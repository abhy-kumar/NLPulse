## NLPulse: Sentiment Analysis for News Feeds

**NLPulse** is a Python program that analyzes the sentiment of news headlines and summaries from RSS feeds. It utilizes a combination of two powerful techniques:

* **NLTK VADER Sentiment Analysis:** This provides a baseline sentiment score based on a pre-built lexicon.
* **FinBERT Fine-tuned Sentiment Analysis:** This leverages a pre-trained deep learning model (FinBERT) specifically designed for financial news analysis, but also applicable to general news.

**Key Features:**

* **Combined Sentiment Score:** Merges the strengths of VADER and FinBERT for a more robust analysis.
* **Category-based Adjustments:** Tailors sentiment scores based on news category (finance or sports) to account for domain-specific language.
* **Custom Lexicon Integration:** Allows for further customization of sentiment analysis by including domain-specific terms.

**Installation:**

This program requires several Python libraries. You can install them using pip:

```bash
pip install feedparser TextBlob nltk transformers torch
```

**Usage:**

1. Save the code as `sentiReeder.py`.
2. Modify the `url` variable in the script to point to your desired RSS feed.
3. Run the script using:

```bash
python sentiReeder.py
```

The program will:

* Fetch news articles from the RSS feed.
* Analyze the sentiment of each news summary.
* Categorize the news as finance, sports, or general.
* Print the title, published date, summary, category, and sentiment score for each article.
* Calculate and display the average sentiment score for the entire feed.

**Example Output:**

```
---
Title: Rohit Sharma delights fan with 'birthday wish' on Mumbai street - Watch
Published: Wed, 09 Oct 2024 09:01:10 +0530
Summary: Rohit Sharma, India's Test and ODI captain, was spotted in Mumbai interacting warmly with fans while on a break. He delighted a fan by wishing her a happy birthday. Rohit, along with Virat Kohli and Ravindra Jadeja, retired from T20Is after India's T20 World Cup win. His approachable nature continues to captivate fans.
Category: sports
Sentiment Score: 6.34
---
Title: Women's T20 World Cup: Do Indian batters have a higher gear?
Published: Wed, 09 Oct 2024 08:14:50 +0530
Summary: The Indian women's cricket team faces Sri Lanka in the T20 World Cup with Harmanpreet Kaur fit to play. Despite a win over Pakistan, their performance has been inconsistent, particularly in batting. Key player Smriti Mandhana must lead against Sri Lanka’s spin-heavy attack to improve their net run rate and stay in contention.
Category: sports
Sentiment Score: 3.43
```

**Customization:**

* You can modify the `custom_lexicon` dictionary to add or adjust sentiment scores for specific words or phrases.
* Explore different RSS feeds by changing the `url` variable.

**Note:**

This program is for educational purposes and may require further development for production use. 
