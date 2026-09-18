# 🔗 API Data Extraction & Exploratory Analysis — JSONPlaceholder

![Python](https://img.shields.io/badge/Python-3.11-blue?logo=python)
![Pandas](https://img.shields.io/badge/Pandas-Data%20Analysis-150458?logo=pandas)
![Requests](https://img.shields.io/badge/Requests-API-orange)
![Status](https://img.shields.io/badge/Status-Completed-brightgreen)

## 🎯 Objective

Extract data from a public REST API, transform it into a structured table, and explore it to identify patterns (comment volume, text length, email domains).

## 📝 Description

This project connects to the public **JSONPlaceholder** API to download comments (`/comments`), converts the nested JSON response into a **pandas DataFrame**, and runs an exploratory analysis focused on:

- Comment volume per post (`postId`)
- Comment text length
- Email domain frequency (`email_domain`)

```
┌─────────────┐     requests      ┌──────────────┐     pandas      ┌───────────────┐
│  REST API   │ ───────────────▶ │  Raw JSON     │ ──────────────▶ │  Clean         │
│ (JSONPlace) │                   │  (nested)     │                  │  DataFrame/CSV │
└─────────────┘                   └──────────────┘                  └───────┬───────┘
                                                                              │
                                                                              ▼
                                                                    ┌───────────────┐
                                                                    │  Exploratory   │
                                                                    │  Analysis      │
                                                                    └───────────────┘
```

## 🛠️ Tools

| Tool | Purpose |
|---|---|
| **Python** | Core language for the project |
| **Requests** | Consuming the REST API |
| **Pandas** | JSON normalization, cleaning and analysis |
| **Jupyter Notebook** | Development and documentation of the workflow |

## 📊 Results

- **500 comments** were extracted, distributed across different posts (`postId`).
- An `email_domain` column was generated from each user's email address.
- **496 distinct domains** were identified, most with only one comment; the most frequent domains (`willis.org`, `lane.us`, `abigale.me`, `retha.me`) appear only **2 times each**.
- This shows a **high dispersion of domains**, with no meaningful concentration around any single provider.

**Top 5 domains by comment count:**

| Domain | Comments |
|---|---|
| willis.org | 2 |
| lane.us | 2 |
| abigale.me | 2 |
| retha.me | 2 |
| gardner.biz | 1 |

## ✅ Conclusions

- The API extraction pipeline is reproducible: any JSONPlaceholder endpoint can be queried using the same `fetch_json()` function.
- The dispersion of email domains confirms that the API's data is synthetic/random, useful for practicing extraction and transformation rather than reflecting real business patterns.
- The flow (API → JSON → DataFrame → CSV) serves as the foundation for larger-scale projects that combine multiple endpoints (`/posts`, `/users`, `/comments`).

## 📁 Repository Structure

```
├── data/
│   └── raw/              # Cache folder for downloaded JSON
├── comments.csv           # Exported data in CSV format
├── notebook.ipynb          # Notebook with the full workflow
└── README.md
```

## ▶️ How to Run

1. Clone the repository.
2. Install the dependencies:
   ```bash
   pip install requests pandas
   ```
3. Open the notebook and run the cells in order:
   ```bash
   jupyter notebook notebook.ipynb
   ```
4. The script will download the data, generate `comments.csv`, and display the email domain analysis.
