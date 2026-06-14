<!-- GSD -->

# Portfolio — Architecture

## Context and Goals

Central landing page for Harshvardhan Kulkarni's data analytics portfolio. Aggregates multiple demo projects into a single browsable site with GitHub Pages hosting and a live Streamlit dashboard.

## Architecture

Multi-component repository combining static HTML pages, a Streamlit dashboard app, standalone analysis scripts, and sample data. Each component is independently deployable.

## Components

| Component | Files | Deployment |
|-----------|-------|------------|
| Portfolio site | `index.html` | GitHub Pages |
| Dashboard | `dashboard.py` | Streamlit Cloud |
| Analysis scripts | `1_customer_segmentation.py`, `2_sales_trend_analysis.py`, `3_data_cleaning_automation.py` | Local execution |
| Sample data | `sample_data.csv`, generated outputs | Bundled |
| Dev environment | `.devcontainer/devcontainer.json` | VS Code Dev Container |

## Data Flow

```
Portfolio site (index.html)
  → Links to project GitHub Pages sites
  → Links to Streamlit live dashboard
  → Links to GitHub repositories

Streamlit Dashboard (dashboard.py)
  → Synthetic data generation
  → KPI cards + Plotly charts
  → Live at https://harsh-data-analytics-portfolio.streamlit.app

Analysis Scripts
  → Independent Python scripts
  → Generate their own synthetic data
  → Produce visualizations and CSV exports
```

## Design Decisions

| Decision | Rationale |
|----------|-----------|
| GitHub Pages for portfolio | Free hosting, easy to maintain, no build tools needed |
| Streamlit for interactive demo | Live dashboard without backend infrastructure |
| Consolidated repo | Single place for all portfolio components |
| Synthetic data generation | Reproducible demos without real data dependencies |

## Trade-offs

- Scripts are duplicates of separate repo versions
- No automated sync between this repo and individual project repos
- GitHub Pages is static-only (no server-side processing)
- Dashboard data regenerates on every page load

## File Organization

```
portfolio/
├── index.html                    # Portfolio landing page
├── dashboard.py                  # Streamlit dashboard
├── 1_customer_segmentation.py    # Analysis script
├── 2_sales_trend_analysis.py     # Analysis script
├── 3_data_cleaning_automation.py # Analysis script
├── requirements.txt              # Streamlit Cloud deps
├── sample_data.csv               # Sample dataset
├── GITHUB_DEPLOY_GUIDE.md        # Deployment guide
├── .devcontainer/                # Dev container config
└── docs/
    ├── ARCHITECTURE.md
    ├── GETTING-STARTED.md
    ├── DEVELOPMENT.md
    ├── TESTING.md
    └── CONFIGURATION.md
```
