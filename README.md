# Shoe Price Tracker Infra (Python + FastAPI)

A small, production-style Python infrastructure for tracking shoe prices across multiple online stores.

This project is structured as a real-world service, not just a one-off script: it has scrapers, a normalization layer, a database, and an HTTP API that can be orchestrated by tools like Make.com, cron, or any workflow engine.

---

## Features

- 🧩 **Modular scraper design** – base scraper class + per-store implementations.
- 🧼 **Normalized data model** – unified `ShoeProduct` representation across stores.
- 💾 **Persistent storage** – SQLite database for price history.
- 🌐 **FastAPI service** – `/products` and `/products/{sku}` read endpoints.
- 🤖 **Automation-ready** – `/run-scraper` endpoint designed for Make.com or cron.
- 🧪 **Demo-friendly** – example scraper parses a local HTML file (no live scraping required).

---

## Architecture

**Components:**

- `src/scrapers/` – Scraper implementations
  - `BaseScraper` – abstract interface
  - `DemoStoreScraper` – parses `data/demo_store_sample.html`
- `src/models.py` – `ShoeProduct` dataclass used across the pipeline.
- `src/db.py` – SQLite initialization and insert helpers.
- `src/pipeline.py` – Orchestrates all scrapers and writes to DB.
- `src/api.py` – FastAPI app exposing:
  - `GET /ping`
  - `POST /run-scraper`
  - `GET /products`
  - `GET /products/{sku}`

All data is stored in `shoe_prices.db` at the project root.

---

## Tech Stack

- **Python 3.10+**
- **FastAPI** – API layer
- **Uvicorn** – ASGI server
- **SQLite** – simple, file-based storage
- **BeautifulSoup4** – HTML parsing

---

## Project Structure

```text
shoe-price-tracker/
├─ src/
│  ├─ __init__.py
│  ├─ models.py
│  ├─ db.py
│  ├─ pipeline.py
│  ├─ api.py
│  └─ scrapers/
│     ├─ __init__.py
│     ├─ base.py
│     └─ demo_store.py
├─ data/
│  └─ demo_store_sample.html
├─ requirements.txt
└─ README.md
