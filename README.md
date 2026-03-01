# 🥿 Shoe Price Tracker — Python + FastAPI + Make.com Orchestrated

A clean, production-style **Python microservice** for tracking shoe prices across multiple stores.  
This project showcases:

- modular scraper design  
- data normalization  
- persistence  
- API-first architecture  
- workflow automation with **Make.com**  
- and deployment-ready FastAPI service  

It’s built to demonstrate modern backend engineering and automation in a compact, portfolio-friendly form.

---

# ✨ Features

- 🧩 **Modular Scraper Layer**  
  Abstract `BaseScraper` + plug-in scrapers per domain (demo scraper included)

- 🧼 **Normalized Data Model**  
  Unified `ShoeProduct` object across all stores

- 💾 **SQLite Persistent Storage**  
  Tracks price history across runs

- 🌐 **FastAPI Service**  
  Endpoints for triggering scrapes and reading stored pricing data

- 🤖 **Make.com Automation**  
  Scheduler → POST → `/run-scraper` → logs / notifications

- 🧪 **Safe by Default**  
  Includes a sample HTML file (`demo_store_sample.html`) so you can demo without scraping live sites

- 🚀 **Deployable**  
  Free-tier friendly: Render, Railway, Koyeb, or any Linux VPS

---

# 🏗️ Architecture

[See separate file]

---

# 🧰 Tech Stack

### **Backend**
- Python 3.10+
- FastAPI
- Uvicorn
- BeautifulSoup4
- SQLite (file-based DB)
- Dataclasses

### **Automation & Orchestration**
- **Make.com**  
  - Scheduling  
  - Webhooks (HTTP triggers)  
  - Logging (Google Sheets / Airtable)  
  - Alerts (Slack / Telegram / Email)

### **Deployment (Optional)**
- Render (Free Tier)
- Railway
- Koyeb
- Fly.io
- Any VPS running Linux

---

# 📁 Project Structure

```text
shoe-price-tracker/
├─ src/
│  ├─ models.py
│  ├─ db.py
│  ├─ pipeline.py
│  ├─ api.py
│  └─ scrapers/
│     ├─ base.py
│     └─ demo_store.py
├─ data/
│  └─ demo_store_sample.html
├─ requirements.txt
└─ README.md
