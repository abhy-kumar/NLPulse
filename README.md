# News Sentiment Analysis Dashboard

![img](https://iili.io/2qmnX8Q.png)
## 📊 Overview
A comprehensive Python application that performs real-time sentiment analysis on news headlines, storing the results in a SQLite database and generating interactive visualizations. The system employs multiple sentiment analysis models, including VADER, FinBERT, and RoBERTa, to provide nuanced sentiment scoring.

## 🌟 Key Features
- **Multi-Model Sentiment Analysis**: Combines VADER, FinBERT, and RoBERTa models for robust sentiment scoring
- **Real-time RSS Feed Processing**: Automatically fetches and analyzes news headlines
- **Interactive Visualizations**: Comprehensive dashboards using Plotly
- **Efficient Data Storage**: SQLite database with optimized indexing
- **Duplicate Detection**: Intelligent similarity-based duplicate removal
- **Comprehensive Analysis**: Including timeline views, sentiment distributions, and statistical breakdowns

### Custom Configuration
```python
from news_analysis import DatabaseManager, SentimentAnalyzer, DataVisualizer

# Initialize components
db = DatabaseManager('custom_database.db')
analyzer = SentimentAnalyzer()
visualizer = DataVisualizer()

# Run specific analyses
visualizer.create_visualizations('custom_database.db')
```

## 📊 Visualization Types

### Main Dashboard
- Daily Entry Counts
- Hourly Distribution
- Sentiment Timeline
- Summary Length Distribution
- Sentiment Distribution
- Weekly Patterns
- Sentiment Moving Average
- Headline Length vs Sentiment
- Time of Day Sentiment

### Headlines Analysis
- Recent Headlines Table
- Most Positive Headlines
- Most Negative Headlines
- Statistical Summaries

## 🗄️ Database Schema

### sentiment_scores Table
```sql
CREATE TABLE sentiment_scores (
    date TEXT,
    time TEXT,
    title TEXT,
    summary TEXT,
    score REAL
)
```

### Indexes
- `idx_date`: Optimizes date-based queries
- `idx_title`: Facilitates headline searches
- `idx_score`: Improves sentiment-based filtering

## 🔍 Duplicate Detection

The system includes sophisticated duplicate detection functionality:

### Features
- Text similarity comparison using SequenceMatcher
- Configurable similarity threshold
- Comparison of both titles and summaries
- Automatic removal of duplicate entries while preserving originals

### Configuration
```python
# Adjust similarity threshold (default: 0.85)
remove_duplicates(db_path='news_sentiment.db', similarity_threshold=0.90)
```

## 📈 Performance Optimization

### Database Optimization
- Write-Ahead Logging (WAL) mode
- Optimized cache settings
- Efficient indexing strategy
- Regular VACUUM operations

### Processing Optimization
- Thread pooling for parallel sentiment analysis
- LRU caching for frequently accessed data
- Batch processing capabilities
- GPU acceleration when available

## 🔧 Troubleshooting

### Common Issues

1. **Database Initialization Error**
```python
# Run database setup script
python setup_database.py
```

2. **CUDA/GPU Issues**
```python
# Force CPU-only mode
import os
os.environ['CUDA_VISIBLE_DEVICES'] = ''
```

3. **Memory Management**
- Adjust batch sizes for large datasets
- Enable garbage collection for long-running processes
- Monitor memory usage with logging

## 📝 Contributing

Contributions are welcome! Please feel free to submit a Pull Request. For major changes, please open an issue first to discuss what you would like to change.

### Guidelines
1. Fork the repository
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🙏 Acknowledgments

- NLTK team for VADER sentiment analysis
- Hugging Face for transformer models
- Plotly team for visualization capabilities
- Contributors and maintainers of all dependent libraries
