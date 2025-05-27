# 🌍 Global News Scraper using RSS and SQLite

This Python script fetches the latest headlines from major news RSS feeds across 20 countries, detects the language of each article, and stores the information in a local SQLite database (`news_articles.db`).

## 📦 Installation

1. **Install Python 3.6+** (if not already installed)

2. **Install Required Libraries**
   
   Open your terminal (or run in a Colab cell) and install the dependencies:

   ```bash
   pip install feedparser pandas langdetect
   ```

## ▶️ How to Run the Script

1. **Save the script** (e.g., `news_scraper.py`)

2. **Run it using:**

   ```bash
   python news_scraper.py
   ```

   This will:
   - Fetch RSS feeds from major news sources worldwide.
   - Extract and process article details.
   - Detect the language of each article summary.
   - Store everything in `news_articles.db`.

## 🗂️ Output

- **news_articles.db** – SQLite database containing:
  - `title` – News headline
  - `published` – Date/time published
  - `source` – News outlet name
  - `country` – Origin country
  - `summary` – Short summary of the article
  - `url` – Link to the full article
  - `language` – Detected language of the article summary

## 🧪 How to View the Data

To display the stored data in Python:

```python
import sqlite3
import pandas as pd

conn = sqlite3.connect("news_articles.db")
df = pd.read_sql_query("SELECT * FROM articles", conn)
print(df.head(10))  # Or use df.to_string() to print all
conn.close()
```

For prettier formatting, you can also install and use:

```bash
pip install tabulate
```

And display with:

```python
from tabulate import tabulate
print(tabulate(df.head(10), headers="keys", tablefmt="grid"))
```


## ✨ Future Improvements

- Schedule daily/weekly runs to build a long-term news archive.
- Add filtering by keywords or categories.
- Use full article scraping for in-depth analysis.
- Export to CSV, Excel, or Google Sheets.
- Integrate with Google Drive or cloud storage.

## 📄 License

MIT License – free to use, modify, and distribute.
