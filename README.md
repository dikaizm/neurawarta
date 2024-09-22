# Neurawarta

**Neurawarta** is a data engineering pipeline designed to track daily trends in Indonesian news. The project involves web scraping, sentiment analysis, word cloud generation, and automated summaries using a generative AI model. The results are displayed on an interactive Streamlit dashboard.

## Table of Contents

- [Project Structure](#project-structure)
- [Features](#features)
- [Setup](#setup)
- [How to Run](#how-to-run)
- [Configuration](#configuration)
- [Dashboard](#dashboard)
- [Technologies Used](#technologies-used)

## Project Structure

```bash
neurawarta/
│
├── data/                           # Stores raw and processed data
│   ├── raw/                        # Raw scraped news data
│   ├── processed/                  # Preprocessed data for analysis
│   └── wordclouds/                 # Generated word cloud images
│
├── notebooks/                      # Jupyter Notebooks for EDA and experiments
│   └── sentiment_analysis.ipynb    # Experimenting with sentiment models
│
├── src/                            # Source code
│   ├── scraping/                   # Web scraping scripts
│   ├── sentiment_analysis/         # Sentiment analysis scripts
│   ├── wordcloud_generator/        # Word cloud generation scripts
│   ├── summary_generation/         # LLM-based summary generation
│   ├── pipeline/                   # Data pipeline orchestration
│   └── dashboard/                  # Streamlit dashboard
│       ├── app.py                  # Main Streamlit app
│       ├── plots.py                # Visualization functions
│       └── data_loader.py          # Data loading functions
│
├── config/                         # Configuration files
│   ├── scraper_config.yaml         # Scraper settings
│   ├── sentiment_config.yaml       # Sentiment model settings
│   └── api_keys.yaml               # API keys for LLM, etc.
│
├── logs/                           # Log files for pipeline runs
│   └── pipeline.log                # Daily logs
│
├── tests/                          # Unit and integration tests
├── requirements.txt                # Project dependencies
├── README.md                       # Project documentation
└── Dockerfile                      # Docker setup
```

## Features

- **Web Scraping**: Automatically scrapes news data from Indonesian news sources.
- **Sentiment Analysis**: Analyzes the sentiment of the news articles using a pre-trained or custom sentiment model.
- **Word Cloud Generation**: Creates word clouds to visualize trending terms.
- **Summarization**: Uses a generative AI model (LLM) to generate daily news summaries.
- **Streamlit Dashboard**: Interactive dashboard for visualizing trends, sentiment analysis, word clouds, and summaries.

## Setup

### Prerequisites

- Python 3.8+
- [Streamlit](https://docs.streamlit.io/library/get-started/installation)
- API access for LLM (e.g., OpenAI API)

### Clone the repository

```bash
git clone https://github.com/dikaizm/neurawarta.git
cd neurawarta
```

### Install dependencies

Install the required Python packages by running:

```bash
pip install -r requirements.txt
```

### Configure API Keys

Ensure that you add your API keys for any services (e.g., OpenAI, web scraping) in the `config/api_keys.yaml` file.

### Database Setup

Set up your database for storing scraped data (e.g., using PostgreSQL or MongoDB) and configure it in `config/scraper_config.yaml`.

## How to Run

### 1. Web Scraping

To scrape the latest news articles, run the scraping script:

```bash
python src/scraping/scraper.py
```

This will store the raw news data in the `data/raw/` folder or the configured database.

### 2. Sentiment Analysis

After scraping the news, run sentiment analysis on the data:

```bash
python src/sentiment_analysis/sentiment_model.py
```

This will save sentiment scores and processed data in the `data/processed/` folder.

### 3. Word Cloud Generation

Generate word clouds based on the processed data:

```bash
python src/wordcloud_generator/wordcloud_generator.py
```

The generated word cloud images will be saved in the `data/wordclouds/` folder.

### 4. LLM-based Summarization

To summarize the daily news trends using an LLM, run the following script:

```bash
python src/summary_generation/summary_api.py
```

This will generate daily summaries and store them for display on the dashboard.

## Configuration

All configurable settings (e.g., scraping targets, API keys, sentiment thresholds) are stored in the `config/` directory:

- `scraper_config.yaml`: Configuration for web scraping (target URLs, parsing rules).
- `sentiment_config.yaml`: Configuration for sentiment analysis (model type, language settings).
- `api_keys.yaml`: Store API keys for services like LLM, scraping, etc.

## Dashboard

To view the daily trends, word clouds, sentiment analysis, and news summaries, run the Streamlit dashboard:

```bash
streamlit run src/dashboard/app.py
```

The dashboard will be accessible in your web browser at `http://localhost:8501`.

## Technologies Used

- **Python**: Core language for scripting and pipeline management.
- **Streamlit**: Interactive dashboard for visualizing trends and insights.
- **BeautifulSoup / Scrapy**: Web scraping frameworks.
- **NLTK / spaCy**: Natural language processing for sentiment analysis.
- **OpenAI API**: Generative AI for text summarization.
- **WordCloud**: Python library for generating word clouds.
- **Docker**: Containerization for easy deployment.

## Future Work

- Implement more sophisticated topic modeling (e.g., LDA).
- Integrate real-time updates for the dashboard.
- Add more sources for news scraping.
