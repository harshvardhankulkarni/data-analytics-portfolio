<!-- GSD -->

# Data Analytics Portfolio

Central landing page for Harshvardhan Kulkarni's data analytics projects. Showcases Python-based analysis work through a GitHub Pages site, an interactive Streamlit dashboard, and standalone analysis scripts.

## What's Included

- **GitHub Pages site** (`index.html`) — dark-themed portfolio with 8 project cards linking to individual repos and live pages
- **Streamlit dashboard** (`dashboard.py`) — interactive sales analytics with KPI cards, Plotly charts, day-of-week and monthly breakdowns
- **3 analysis scripts** — customer segmentation (RFM), sales trend analysis (time series), data cleaning automation (pipeline)
- **Sample dataset** (`sample_data.csv`) — synthetic e-commerce orders for demonstrations
- **Output files** — `customer_segments_output.csv`, `sales_trend_output.csv`, `cleaned_data_output.csv` from each script

## Features

- Interactive dashboard deployed on Streamlit Cloud
- Static portfolio site hosted on GitHub Pages
- Self-contained analysis scripts that generate synthetic data (no external data sources needed)
- End-to-end data cleaning pipeline demonstrating 10-step data quality workflow
- RFM-based customer segmentation with visual segment analysis
- Sales trend decomposition with rolling averages and day-of-week patterns

## Tech Stack

| Layer | Technology |
|-------|-----------|
| Language | Python 3.11+ |
| Data | Pandas 2.2.0, NumPy 1.26.3 |
| Visualization | Matplotlib 3.8.3, Seaborn 0.13.2, Plotly 5.18.0 |
| Dashboard | Streamlit 1.31.0 |
| Hosting (static) | GitHub Pages |
| Hosting (dashboard) | Streamlit Cloud |
| Dev environment | Dev Container (VS Code / GitHub Codespaces) |

## Quick Start

```bash
# Install dependencies
pip install -r requirements.txt

# Run the dashboard
streamlit run dashboard.py

# Run individual analysis scripts
python 1_customer_segmentation.py
python 2_sales_trend_analysis.py
python 3_data_cleaning_automation.py
```

## Project Structure

```
portfolio/
  index.html                          # GitHub Pages landing page
  dashboard.py                        # Streamlit dashboard
  requirements.txt                    # Python dependencies
  sample_data.csv                     # Synthetic e-commerce dataset
  1_customer_segmentation.py          # RFM analysis
  2_sales_trend_analysis.py           # Time series analysis
  3_data_cleaning_automation.py       # Data cleaning pipeline
  GITHUB_DEPLOY_GUIDE.md              # Deployment instructions
  README.md                           # This file
  docs/
    ARCHITECTURE.md                   # Architecture and design decisions
    GETTING-STARTED.md                # Setup and usage guide
    DEVELOPMENT.md                    # Development workflow
    TESTING.md                        # Testing and validation
    CONFIGURATION.md                  # Configuration reference
  .devcontainer/
    devcontainer.json                 # Dev container config
    README.md                         # Dev container instructions
```

## Live Links

- **GitHub Pages site:** https://harshvardhankulkarni.github.io/data-analytics-portfolio/
- **Streamlit dashboard:** https://harsh-data-analytics-portfolio.streamlit.app
- **GitHub repository:** https://github.com/harshvardhankulkarni/data-analytics-portfolio

## Demo Note

All projects in this portfolio are **demo projects** built with synthetic datasets. They demonstrate analysis techniques, code quality, and data storytelling. Each project has its own standalone repository with full documentation (README, architecture docs, runbook).
