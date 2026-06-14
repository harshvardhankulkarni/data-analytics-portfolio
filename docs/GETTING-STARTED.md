<!-- GSD -->

# Getting Started

## Prerequisites

- Python 3.11 or later
- pip (Python package installer)
- A web browser
- Git (optional, for deploying your own copy)

## View the Portfolio

The fastest way to see the portfolio is to visit the live sites:

- **GitHub Pages:** https://harshvardhankulkarni.github.io/data-analytics-portfolio/
- **Streamlit Dashboard:** https://harsh-data-analytics-portfolio.streamlit.app

No setup required.

## Run the Dashboard Locally

```bash
# Clone the repository
git clone https://github.com/harshvardhankulkarni/data-analytics-portfolio.git
cd data-analytics-portfolio

# Install dependencies
pip install -r requirements.txt

# Launch Streamlit dashboard
streamlit run dashboard.py
```

The dashboard opens in your default browser at `http://localhost:8501`. It generates synthetic data on every run — no external files needed.

## Run Analysis Scripts Locally

Each script is self-contained and generates its own data:

```bash
# Customer segmentation (RFM analysis)
python 1_customer_segmentation.py

# Sales trend analysis (time series)
python 2_sales_trend_analysis.py

# Data cleaning automation (pipeline demo)
python 3_data_cleaning_automation.py
```

Each script prints results to the terminal, saves a PNG chart, and exports a CSV file to the repository root.

## Run in a Dev Container (VS Code / GitHub Codespaces)

This repository includes a `.devcontainer/devcontainer.json` configuration. When opened in VS Code with the Dev Containers extension (or in GitHub Codespaces), the environment is automatically set up with Python 3.11, all dependencies installed, and the Streamlit dashboard served on port 8501.

The post-attach command runs the dashboard automatically on container start.

## Deploy Your Own Copy

1. Fork or clone the repository
2. Create a GitHub repository named `data-analytics-portfolio`
3. Push the contents to the `main` branch
4. Enable GitHub Pages in repository Settings → Pages → Source: Deploy from `main` branch, root folder
5. Deploy the dashboard on Streamlit Cloud (share.streamlit.io) pointing to `dashboard.py`
6. Update the live URLs in `index.html` (nav links, dashboard CTA) to point to your own deployments

See `GITHUB_DEPLOY_GUIDE.md` in the repository root for detailed step-by-step instructions.
