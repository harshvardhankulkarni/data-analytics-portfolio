<!-- GSD -->

# Configuration

## Python Dependencies

Defined in `requirements.txt` at the repository root:

```
pandas==2.2.0
numpy==1.26.3
matplotlib==3.8.3
seaborn==0.13.2
plotly==5.18.0
streamlit==1.31.0
```

**Installation:**
```bash
pip install -r requirements.txt
```

**Notes:**
- Versions are pinned for reproducibility. Update pins after testing compatibility.
- `matplotlib` and `seaborn` are required by the standalone scripts but not by the Streamlit dashboard (which uses Plotly).
- `streamlit` is only needed for the dashboard — scripts can run without it.

## Dev Container

Defined in `.devcontainer/devcontainer.json`:

| Setting | Value |
|---------|-------|
| Base image | `mcr.microsoft.com/devcontainers/python:1-3.11-bookworm` |
| Python version | 3.11 (Debian Bookworm) |
| VS Code extensions | `ms-python.python`, `ms-python.vscode-pylance` |
| Auto-open files | `README.md`, `dashboard.py` |
| Post-create command | Installs `packages.txt` (if present), `requirements.txt`, and `streamlit` |
| Post-attach command | `streamlit run dashboard.py --server.enableCORS false --server.enableXsrfProtection false` |
| Forwarded port | 8501 (auto-opens in preview) |

GitHub Codespaces uses this configuration automatically when opening the repository.

## GitHub Pages Configuration

| Setting | Value |
|---------|-------|
| Source branch | `main` |
| Source folder | `/` (root) |
| Custom domain | None (uses default `harshvardhankulkarni.github.io/data-analytics-portfolio/`) |
| Enforce HTTPS | Enabled (default for GitHub Pages) |
| Build / deploy | Zero config — serves `index.html` directly from root |

**To enable in a forked copy:**
1. Repository Settings → Pages → Source: "Deploy from a branch"
2. Branch: `main`, folder: `/ (root)`
3. Save — site deploys in 1-2 minutes

## Streamlit Cloud Configuration

| Setting | Value |
|---------|-------|
| App source | GitHub repository |
| Repository | `harshvardhankulkarni/data-analytics-portfolio` |
| Branch | `main` |
| Main file path | `dashboard.py` |
| Python version | Auto-detected from runtime |
| Dependencies | Auto-installed from `requirements.txt` |

**Deploy URL:** https://harsh-data-analytics-portfolio.streamlit.app

## Analysis Script Parameters

All three scripts use the same pseudo-random seed for reproducibility:

```python
np.random.seed(42)
```

Changing this seed produces different synthetic data but preserves the same data quality characteristics.

### 1_customer_segmentation.py

| Parameter | Value | Description |
|-----------|-------|-------------|
| `n_customers` | 200 | Number of synthetic customers |
| `recency_days` | ~Exp(30), clipped [1, 180] | Days since last purchase |
| `frequency` | ~Poisson(5), clipped [1, 30] | Number of purchases |
| `monetary_value` | ~Exp(2000), clipped [100, 20000] | Total customer spend (INR) |
| `tenure_days` | Uniform [30, 730] | Customer relationship length |
| Segments | Champions (13-15), Loyal (10-12), Potential Loyalists (7-9), At Risk (5-6), Lost (3-4) | Based on RFM total score |

### 2_sales_trend_analysis.py

| Parameter | Value | Description |
|-----------|-------|-------------|
| `dates` | 180 days from 2024-01-01 | Period of analysis |
| `base_sales` | 50,000 INR | Baseline daily sales |
| `trend` | Linear 0 → 20,000 over 180 days | Upward trend component |
| `weekly_seasonality` | Sinusoidal, amplitude 0.3 | Weekly pattern multiplier |
| `weekend_boost` | [1.0, 1.0, 1.0, 1.1, 1.2, 1.5, 1.3] | Day-of-week multipliers (Mon-Sun) |
| `noise` | Normal(0, 5000) | Random variation |

### 3_data_cleaning_automation.py

| Parameter | Value | Description |
|-----------|-------|-------------|
| `n` | 150 | Number of synthetic records |
| Issue: duplicates | ~2 identical records introduced | Removed via `drop_duplicates()` |
| Issue: bad names | Whitespace, newlines, empty strings | Stripped, capitalized, nullified |
| Issue: bad emails | Missing `@`, missing domain, empty | Invalid emails set to None |
| Issue: city variants | 9 variants including typos and casing | Mapped to 5 canonical cities |
| Issue: null categories | NaN values | Defaulted to "Uncategorized" |
| Issue: negative spend | ~8% of records | Absolute value applied |
| Issue: invalid dates | Out-of-range months, non-date strings | Set to NaT (null) |
| Issue: active flag | 6 formats (Yes/No/Y/N/TRUE/FALSE) | Normalized to "Yes" / "No" |

## Output Files

| Script | Chart Output | CSV Output |
|--------|-------------|------------|
| `1_customer_segmentation.py` | `1_customer_segments.png` | `customer_segments_output.csv` |
| `2_sales_trend_analysis.py` | `2_sales_trend_analysis.png` | `sales_trend_output.csv` |
| `3_data_cleaning_automation.py` | `3_data_cleaning_report.png` | `cleaned_data_output.csv` |

All outputs are written to the repository root directory.
