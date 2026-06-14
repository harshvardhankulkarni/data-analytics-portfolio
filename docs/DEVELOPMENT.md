<!-- GSD -->

# Development

## Project Structure

```
portfolio/
  index.html                      # GitHub Pages landing page (single file)
  dashboard.py                    # Streamlit app (single file)
  requirements.txt                # Pinned Python dependencies
  GITHUB_DEPLOY_GUIDE.md          # Deployment instructions
  README.md                       # This file
  docs/                           # GSD documentation
  .devcontainer/                  # Dev container config
  1_customer_segmentation.py      # Standalone analysis script
  2_sales_trend_analysis.py       # Standalone analysis script
  3_data_cleaning_automation.py   # Standalone analysis script
  sample_data.csv                 # Synthetic dataset (76 rows)
  *_output.csv                    # Generated export files (gitignored)
  *.png                           # Generated visualizations (gitignored)
```

## How to Modify index.html

The landing page is a single HTML file with embedded CSS in the `<style>` tag. No build tools or frameworks.

**Add a new project card:**

1. Copy an existing `.card` div block (lines 91-170 in `index.html`)
2. Update the card title, description, tags, and link href attributes
3. Maintain the existing card structure: `.card > .demo-label + h3 + .card-desc + tags + .card-footer`
4. Cards are laid out in a CSS Grid within `.projects` — no manual positioning needed

**Change styling:** All CSS custom properties are defined in `:root`. Modify variables like `--accent`, `--bg`, `--radius` to change the theme.

**Update navigation links:** Edit the `<nav>` section (line 69-74) to update GitHub profile or dashboard URLs.

## How to Update the Dashboard

The dashboard (`dashboard.py`) is a single Streamlit app (81 lines).

**Add a new KPI metric:** Add a new `st.columns` slot and call `colN.metric()`:
```python
col5, col6 = st.columns(2)
col5.metric('Label', value)
```

**Add a new chart:** Generate a Plotly figure and render with:
```python
fig = px.scatter(df, x='col1', y='col2')
st.plotly_chart(fig, use_container_width=True)
```

**Modify the synthetic data generator:** Edit the NumPy-based generation block (lines 16-24) to change data characteristics (period length, trend strength, noise level, seasonality parameters).

## How to Add New Analysis Scripts

1. Create a new file following the naming convention `N_description.py` (e.g., `4_churn_analysis.py`)
2. Use `np.random.seed(42)` for reproducible synthetic data
3. Print results to stdout
4. Save a PNG visualization with a descriptive filename
5. Export a CSV with a descriptive filename
6. No external file dependencies — scripts must be self-contained

## Sync Strategy: Consolidated vs Separate Repos

These scripts are **consolidated copies** of scripts from individual project repos (`customer-segmentation`, `sales-trend-analysis`, `data-cleaning-automation`). When updating a script:

1. Update in the individual project repo first (where it's the primary artifact)
2. Copy the updated version back into this consolidated repo
3. Keep both in sync — this repo is the portfolio showcase, individual repos are the canonical source

## GitHub Pages Deployment Workflow

GitHub Pages serves `index.html` directly from the `main` branch root:

1. Push changes to `main` on GitHub
2. Go to repository Settings → Pages and verify Source is set to "Deploy from branch: main, folder: / (root)"
3. Wait 1-2 minutes for the deployment to complete
4. Verify at https://harshvardhankulkarni.github.io/data-analytics-portfolio/

No build step, no CI configuration needed.

## Code Style

- **Python:** Follow PEP 8. Use descriptive variable names. Include module-level docstrings. Use `np.random.seed(42)` for reproducibility.
- **HTML/CSS:** Single-file approach. CSS custom properties for theming. No external libraries. Semantic HTML5 elements.
- **Comments:** Minimal — code should be self-documenting with clear naming and structure.
- **File naming:** `N_description.py` for scripts (numbered for ordering). All lowercase with underscores.
