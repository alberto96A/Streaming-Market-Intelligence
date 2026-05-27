# Streaming Market Intelligence Pipeline (2015-2026)
### Data Engineering, Analytics & NLP Sentiment Modeling

## 📊 Project Overview
This project builds a data pipeline to analyze the content strategies of five streaming platforms: Netflix, Amazon Prime, Disney+, HBO Max, and Apple TV+. It consolidates over 22,000 historical records, addresses web scraping constraints for future data, and analyzes title sentiment using Natural Language Processing (NLP).

## 💡 Key Findings
* **Content Mix Strategy:** Apple TV+ focuses heavily on episodic content, with TV Shows making up over 87% of its 2026 catalog. This model targets long-term subscriber engagement and stable Monthly Recurring Revenue (MRR) to reduce churn. In contrast, Netflix maintains a 50/50 balance between movies and series to appeal to a broader audience.
* **Title Sentiment Analysis:** Using NLP (`TextBlob`), the analysis shows that Disney+ leads in content naming positivity, matching its family-friendly branding. HBO Max and Apple TV+ score lower, reflecting their focus on mature dramas and thrillers.

---

## 🔍 Data Engineering: Handling Scraping Limits
A key challenge during the project was handling data quality issues:
1. **The Issue:** The initial web scraper (`BeautifulSoup`) capped the 2026 data for all platforms at exactly 131-132 titles.
2. **The Cause:** The target website used dynamic lazy-loading and pagination limits, blocking the basic scraper from reading the full catalog.
3. **The Solution:** To get accurate data, I replaced the scraper results by connecting directly to the **TMDB REST API**. I implemented a loop that automatically requests all available pages to retrieve the complete catalog volume.

---

## 🛠️ Tech Stack & Data Architecture
* **Data Processing & Analytics:** Python, Pandas, Matplotlib
* **Database:** SQLite3 (Relational storage, data normalization)
* **Web Scraping & APIs:** BeautifulSoup4, Requests (TMDB API connection)
* **Natural Language Processing:** TextBlob (Sentiment polarity scoring)

### Repository Structure
```text
├── data/                    # Legacy CSV datasets [Local Only]
├── main.ipynb               # Jupyter Notebook with full pipeline and code
├── .gitignore               # Excludes database and raw data files
└── README.md                # Project documentation


How to Run the Project
1. Clone the repository: [https://github.com/tu-usuario/cancellations-streaming-service.git](https://github.com/tu-usuario/cancellations-streaming-service.git)
2. Install dependencies: pip install pandas textblob matplotlib requests beautifulsoup4
python -m textblob.download_corpora
3. Run main.ipynb sequentially. The pipeline automatically creates the local SQLite database (streaming_project.db) during execution.
