# Real-Time Sentiment Analysis Pipeline using Apache Kafka, Elasticsearch, Kibana and TextBlob

## Project Overview

This project implements a real-time data pipeline for sentiment analysis of Twitter data using Apache Kafka, Elasticsearch, Kibana and Python.

Tweets are streamed from a CSV dataset through Apache Kafka. A Python Consumer retrieves each tweet, performs sentiment analysis using TextBlob, enriches the data with prediction results, stores the processed documents in Elasticsearch, and finally visualizes them in Kibana.

The project demonstrates the implementation of a complete Data Engineering pipeline for real-time data processing and visualization.

---

## Architecture

```
Twitter Dataset (CSV)
        │
        ▼
Python Producer
        │
        ▼
Apache Kafka (tweets-topic)
        │
        ▼
Python Consumer
        │
        ▼
TextBlob Sentiment Analysis
        │
        ▼
Elasticsearch
        │
        ▼
Kibana Dashboard
```

---

## Technologies Used

- Python 3
- Apache Kafka
- Apache Zookeeper
- Elasticsearch
- Kibana
- Docker & Docker Compose
- Pandas
- TextBlob

---

## Project Structure

```
Project_Data_Engineering/
│
├── data/
│   └── twitter.csv
│
├── producer.py
├── consumer.py
├── docker-compose.yml
├── requirements.txt
└── README.md
```

---

## Features

- Stream tweets in real time using Kafka.
- Read data from a CSV dataset.
- Perform sentiment analysis with TextBlob.
- Compute tweet polarity.
- Compare predicted sentiment with dataset labels.
- Store processed tweets in Elasticsearch.
- Visualize results using Kibana dashboards.

---

## Dataset

The project uses a Twitter sentiment dataset containing:

- Tweet ID
- Tweet text
- Sentiment label

Example:

| id | tweet | label |
|----|-------|-------|
| 1 | I love this movie | 0 |
| 2 | This is terrible | 1 |

Label convention:

- **0 → Positive**
- **1 → Negative**

---

## Installation

Clone the repository

```bash
git clone https://github.com/your-username/Project_Data_Engineering.git
cd Project_Data_Engineering
```

Install Python dependencies

```bash
pip install -r requirements.txt
```

---

## Start Docker Services

```bash
docker compose up -d
```

This command starts:

- Apache Kafka
- Apache Zookeeper
- Elasticsearch
- Kibana

---

## Run the Producer

```bash
python producer.py
```

The Producer reads the dataset and publishes tweets to the Kafka topic.

---

## Run the Consumer

```bash
python consumer.py
```

The Consumer:

- Reads tweets from Kafka
- Performs sentiment analysis
- Computes polarity
- Stores results in Elasticsearch

---

## Elasticsearch Document Example

```json
{
    "id": 1,
    "tweet": "I love football",
    "true_sentiment": "Positive",
    "prediction": "Positive",
    "polarity": 0.62
}
```

---

## Kibana Dashboard

The Kibana dashboard allows users to:

- Explore indexed tweets
- Visualize sentiment distribution
- Compare TextBlob predictions with dataset labels
- Analyze sentiment statistics

Access Kibana:

```
http://localhost:5601
```

---

## Results

The project demonstrates a complete streaming workflow from data ingestion to visualization.

Experimental results show that TextBlob provides fast sentiment predictions but may differ from the original dataset labels due to:

- Informal language
- Hashtags
- Irony
- Social media abbreviations

---

## Future Improvements

- Replace TextBlob with BERT or RoBERTa
- Stream live tweets using the Twitter API
- Add Apache Spark Streaming or Apache Flink
- Build a real-time monitoring dashboard
- Deploy the project to the cloud

---

## Author

**Abdessalam Safadi**

Master's Student in Artificial Intelligence

Faculty of Sciences Ben M'Sik – Hassan II University of Casablanca

---

## License

This project is developed for educational and research purposes.
