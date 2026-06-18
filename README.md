# Sentiment-analysis-model-comparison
# Sentiment-analysis-model-comparison

> Political Polarisation in Social Media in Spain: A Comparative Study of Sentiment Analysis Models using R
> **Master's Thesis Code Repository** — Miriam Lim Leal

---

## At a Glance

The objective of this project is to investigate whether architectural differences among computational models produce conflicting sentiment classifications when analysing political discourse across the ideological spectrum on social media. Using a dataset extracted from X (Twitter) containing posts from major Spanish political parties during the highly polarized 2020 COVID-19 pandemic era, the project models, processes, and evaluates sentiment extraction using a combination of traditional dictionary lexicons, fine-tuned transformer networks, and large language models (LLMs).

---

## Project Overview

| Component | Description |
|---|---|
| **Data Harvesting & Preprocessing** | Compiling, deduplicating, and cleansing a raw dataset of tweets from major Spanish political parties. Standardizes character sets, eliminates URLs, filters mentions, and normalizes whitespace. |
| **Linguistic & Emoji Integration** | Retains semantic emoji nuances across models. Dictionary pipelines use an embedded translation loop mapping emojis to Spanish strings via Emoji-SP. Transformer and LLM variants rely on deep token embeddings. |
| **Multiverse Sentiment Modelling** | Cross-architectural evaluations across three model types (see below). |
| **Inter-Model Reliability Analysis** | Standardized labels (Positive, Neutral, Negative) compared via Krippendorff's Alpha, tracking alignment and divergences. |

### Models Used

- 📖 **Lexicon-Based**: NRC Word-Emotion Association Lexicon via the `syuzhet` framework
- 🤖 **Transformer-Based**: RoBERTuito — optimized for Spanish social media syntax and slang
- 💬 **LLM**: Gemini 2.5 Flash Lite — asynchronous batch JSON API, temperature = 0.0

---

## 📦 Required Packages

### Data Loading and Manipulation
- `tidyverse` — text cleaning, filtering, and mutation pipelines
- `readxl` — reads the external Emoji-SP metadata database

### NLP and Text Processing
- `tidytext` — tidy text-mining pipelines
- `textdata` — access to lexicons and external text resources
- `stringi` — fast advanced regex corrections
- `syuzhet` — Spanish NRC sentiment scoring
- `udpipe` — tokenization, POS tagging, and lemmatization
- `emoji` — emoji lookups and character manipulation

### Python Integration
- `reticulate` — bridges R/Python, enabling PyTorch and Hugging Face models inside R

### API & Web Services
- `httr2` — HTTP client for parallelized Gemini API calls
- `jsonlite` — JSON builder and parser for API payloads

---

## ⚙️ Installation and Setup

### 1. R Packages

```r
install.packages(c("tidyverse", "tidytext", "textdata", "emoji", "readxl",
                   "stringi", "syuzhet", "udpipe", "reticulate", "httr2", "jsonlite"))
```

### 2. Python Virtual Environment

Ensure Python 3.10 is installed:

```bash
python3.10 --version
```

Navigate to the project directory and create a virtual environment:

```bash
cd /path/to/sentiment-analysis-polarisation
python3.10 -m venv venv
```

Activate it:
- **macOS/Linux**: `source venv/bin/activate`
- **Windows**: `venv\Scripts\activate`

Install dependencies:

```bash
pip install --upgrade pip
pip install transformers torch pysentimiento numpy h5py scipy
```

### 3. API Key Configuration

Open your R environment file with `usethis::edit_r_environ()` and add:
