<!-- GSD -->

# Testing

## Automated Tests

This repository has **no automated test suite**. The analysis scripts are demo projects that generate synthetic data — there are no unit tests, integration tests, or CI pipelines configured.

## Manual Validation

Verify the portfolio works correctly by running these checks:

### 1. GitHub Pages Site

- Open https://harshvardhankulkarni.github.io/data-analytics-portfolio/
- Verify the page loads with the dark-themed design and animated background
- Check all 8 project cards render with correct title, description, tags, and buttons
- Test every "Repository" link — each should open the correct GitHub repo in a new tab
- Test every "Live Page" link — each should open the project's GitHub Pages site
- Verify the "Launch Dashboard" CTA button opens the Streamlit Cloud dashboard
- Check navigation links (GitHub, Dashboard) in the sticky navbar
- Confirm the footer displays name and location correctly
- Resize the browser window to verify responsive layout (mobile < 480px, tablet 640px+)
- Verify the stats section (8 projects, 8 pages live, Python, Plotly) displays correctly

### 2. Streamlit Dashboard

- Open https://harsh-data-analytics-portfolio.streamlit.app
- Verify the page title reads "Sales Analytics Dashboard"
- Check four KPI metric cards display (Total Revenue, Daily Average, Peak Day, Last 7 Days Avg)
- Scroll the sales trend chart — verify the line chart renders with three traces (daily, 7-day avg, 30-day avg)
- Hover over chart data points to verify Plotly interactivity
- Check the day-of-week bar chart (7 bars, Saturday should be highest)
- Check the monthly revenue bar chart
- Expand "View Raw Data" — verify the dataframe shows 50 rows with correct columns
- Test the "Download CSV" button — should download `sales_data.csv`

### 3. Analysis Scripts

Run each script locally and verify:

| Script | Console Output | Files Generated |
|--------|---------------|-----------------|
| `1_customer_segmentation.py` | Segment breakdown with customer counts, percentages, average spend, revenue driver identified | `1_customer_segments.png`, `customer_segments_output.csv` |
| `2_sales_trend_analysis.py` | Date range, total revenue, average daily, peak/lowest day + values, best/worst day-of-week, MoM change | `2_sales_trend_analysis.png`, `sales_trend_output.csv` |
| `3_data_cleaning_automation.py` | Before/after data quality report, issue counts, cleaning summary | `3_data_cleaning_report.png`, `cleaned_data_output.csv` |

Each script should complete without errors and exit cleanly with "Done."

### 4. Local Dashboard Run

```bash
streamlit run dashboard.py
```

- Verify the app starts on `http://localhost:8501`
- Confirm the experience matches the Streamlit Cloud deployment
- Test that no filesystem writes or external API calls occur (dashboard is fully self-contained)

### 5. Edge Cases

- Run scripts on a clean Python environment with only `requirements.txt` installed — verify no missing dependency errors
- Open `index.html` directly from the filesystem (file:// protocol) — CSS Grid layout should still render
- Disable JavaScript in the browser and reload the GitHub Pages site — all content should still render (no JS dependency)
