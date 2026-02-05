# AI-Powered Algorithmic Trading Bot (LSTM + NLP)
### *Predicting Stock Prices by fusing Technical Analysis with News Sentiment*

![Python](https://img.shields.io/badge/Python-3.10%2B-blue)
![TensorFlow](https://img.shields.io/badge/AI-TensorFlow%20LSTM-orange)
![NLP](https://img.shields.io/badge/NLP-VADER-green)
![Status](https://img.shields.io/badge/Status-Active-success)

---

##  Executive Summary
In modern quantitative finance, price data alone is often insufficient to predict market volatility. This project builds a **Dual-Signal Trading Engine** that predicts stock price movements by analyzing two distinct data streams:
1.  **Technical Data:** Historical OHLCV (Open, High, Low, Close, Volume) market data.
2.  **Unstructured Data:** Financial news headlines and market sentiment.

The system utilizes a **Long Short-Term Memory (LSTM)** neural network to identify non-linear patterns across time, while a **VADER Sentiment Analysis** engine quantifies the "fear and greed" of the market in real-time.

---

##  Technical Architecture

| Component | Tech Stack | Functionality |
| :--- | :--- | :--- |
| **Data Ingestion** | `Requests`, `BeautifulSoup` | Custom scraper designed to bypass "User-Agent" blocking and fetch live headlines from **Finviz**. |
| **NLP Engine** | `NLTK (VADER)` | Tokenizes text and calculates a "Compound Sentiment Score" (-1 to +1) for every headline. |
| **Data Processing** | `Pandas`, `NumPy` | Handles complex time-series merging, mixed date format parsing, and MultiIndex flattening. |
| **Deep Learning** | `TensorFlow`, `Keras` | **LSTM Network** (50 neurons) trained on sequential windows (Look-back methodology). |
| **Normalization** | `Scikit-Learn` | Implemented `MinMaxScaler` to normalize price ($200+) and sentiment (0-1) into a shared vector space. |

---

## Key Features

### 1. Robust News Scraper
* Includes a custom **User-Agent Header spoofing** mechanism to prevent `HTTP 403 Forbidden` errors.
* Automatically parses and standardizes mixed date formats (e.g., converting "Today" and "Feb-01-26" into a unified ISO timestamp).

### 2. Sentiment-Price Correlation
* Aggregates hundreds of daily headlines into a single **Daily Sentiment Signal**.
* Aligns sentiment spikes with market trading hours to detect "Pre-Market" or "After-Hours" news impacts.

### 3. LSTM Predictive Model
* Uses a sliding window approach (Sequence Generation) to feed the last $N$ days of data into the model.
* Outputs a specific predicted closing price (in USD) for the next trading day.

---

##  Visualizations

### The "Dual-Axis" Strategy Plot

<img width="1189" height="590" alt="image" src="https://github.com/user-attachments/assets/5aafafb6-2587-4e36-99de-99637927f7fe" />

---

## How to Run Locally

**1. Clone the Repository**
```bash
git clone [https://github.com/YourUsername/Sentiment-Trading-Bot.git](https://github.com/YourUsername/Sentiment-Trading-Bot.git)
cd Sentiment-Trading-Bot
