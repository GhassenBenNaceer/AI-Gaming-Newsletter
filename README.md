# 🕹️ AI-Powered Gaming Newsletter Generator  
Automated scraping, summarization & newsletter creation using LLMs

This project is an **experimental pipeline** that scrapes gaming news, processes long-form articles, summarizes them using a large-context language model, and generates a polished newsletter.

The goal is to demonstrate an end-to-end workflow including scraping, text cleaning, summarization, and final newsletter construction.

> ⚠️ **Note:** This project is for experimental purposes. A production-ready system would require backend automation, frontend tools, scheduled jobs, and multi-source scraping.

---

## 🚀 Features

### ✔️ Web Scraping  
- Scrapes top gaming news from websites like **Gamespot**  
- Easily extendable to multiple sources (RSS feeds, blogs, news websites)

### ✔️ Long-Context LLM Summarization  
- Uses a **large-context transformer model** to summarize long articles  
- Smaller models were tested but insufficient due to long context length  
- Produces readable, structured summaries suitable for newsletters

### ✔️ Automated Newsletter Creation  
- Combines summarizations into a clean, curated newsletter  
- Uses prompt engineering to generate highlights, main stories, and quick news  
- Output ready for markdown, email templates, or CMS usage

### ✔️ Clean Notebook Workflow  
- Organized step-by-step  
- Easy to modify and expand into a backend pipeline

## 🧱 How It Works

### 1. Scraping  
The project uses Python libraries to fetch and parse articles:

- `requests` for HTTP requests  
- `BeautifulSoup4` for HTML extraction  
- Custom functions to extract titles, dates, paragraphs, and article content  

### 2. Cleaning & Content Extraction  
- Extracts readable text  
- Removes ads, irrelevant blocks, and formatting noise  
- Merges paragraphs into a clean article body  

### 3. Summarization  
A large HuggingFace model handles long inputs:

```python
model = AutoModelForSeq2SeqLM.from_pretrained(...)
tokenizer = AutoTokenizer.from_pretrained(...)
```
## 4. Newsletter Creation

Once all article summaries are generated, the pipeline constructs a final newsletter using a large language model and a structured prompt.

Key steps include:

- Merging all article summaries into a single text block  
- Feeding the combined content into an LLM with a carefully designed newsletter template  
- Generating sections such as:
  - **Featured Stories**
  - **Highlights**
  - **Quick News**
  - **Upcoming Releases**
- Producing clean Markdown output suitable for email, CMS, or GitHub pages

Example logic:

```python
articles_combined = "\n\n".join(article_summaries)

prompt = f"""
Create a polished gaming newsletter based on the summaries below...
```
## 📈 Roadmap (Future Improvements)

### 🔧 Backend Improvements
- Convert notebook logic into modular Python scripts
- Build a REST API using FastAPI or Flask
- Add background workers for scraping and summarization (Celery / RQ)
- Add persistent storage for articles and summaries (SQLite, PostgreSQL)

### 🖥️ Frontend Enhancements
- Create an admin dashboard to preview newsletters
- Add editing tools for manual adjustments
- Provide history view of past newsletters

### ⏱️ Automation & Scheduling
- Use cron jobs, Airflow, or Prefect for weekly automated runs
- Add automated email sending (SendGrid, AWS SES, Mailgun)
- Implement logging, error handling, and retry mechanisms

### 🌐 Data Source Expansion
- Add more gaming websites (IGN, Eurogamer, Polygon, Kotaku, etc.)
- Integrate RSS feeds for easy scaling
- Optional: scrape Reddit threads or YouTube metadata

### 🤖 Model & Summarization Improvements
- Experiment with smaller distilled models for faster inference
- Add chunking strategies for extremely long articles
- Evaluate summarization quality using automatic metrics

### 📨 Newsletter Output Enhancements
- Add HTML templates for email-ready newsletters
- Provide multiple format options (Markdown, HTML, PDF)
- Support A/B testing for newsletter variants


