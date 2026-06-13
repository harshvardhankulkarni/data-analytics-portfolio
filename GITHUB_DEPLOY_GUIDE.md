# Portfolio Showcase Guide

This guide shows you how to push your portfolio to GitHub, post on LinkedIn, deploy your dashboard, and run your Python scripts. Follow the steps in order.

---

## Part 1: Push to GitHub

### Step 1.1: Create a GitHub repository

1. Go to github.com and sign in.
2. Click the green "New" button or go to github.com/new.
3. Repository name: `data-analytics-portfolio`
4. Description: "Python data analysis portfolio customer segmentation sales trends data cleaning"
5. Set to Public.
6. Do not initialize with README (you will push local files).
7. Click "Create repository."

### Step 1.2: Upload your files

Open PowerShell on your computer. Run these commands one by one.

```
cd C:\Users\PilzIndia\Documents\Personal Info\portfolio
git init
git add .
git commit -m "Initial portfolio: 3 analysis scripts + dashboard + dataset"
git branch -M main
git remote add origin https://github.com/YOUR_USERNAME/data-analytics-portfolio.git
git push -u origin main
```

Replace YOUR_USERNAME with your actual GitHub username.

If git is not installed, download it from git-scm.com and run the installer. Restart PowerShell after installation.

### Step 1.3: Verify

Open `https://github.com/YOUR_USERNAME/data-analytics-portfolio` in a browser. You should see all files listed.

---

## Part 2: Run Python Scripts on Your Machine

### Step 2.1: Install Python

If you do not have Python installed:

1. Go to python.org/downloads.
2. Download Python 3.11 or 3.12.
3. Run the installer.
4. Check "Add Python to PATH" during installation.

### Step 2.2: Install required packages

Open PowerShell and run:

```
pip install pandas matplotlib seaborn numpy streamlit plotly
```

### Step 2.3: Run each analysis

Run these commands one at a time from the portfolio folder:

```
cd C:\Users\PilzIndia\Documents\Personal Info\portfolio
python 1_customer_segmentation.py
python 2_sales_trend_analysis.py
python 3_data_cleaning_automation.py
```

Each script will:
- Print results to your terminal.
- Save a PNG chart in the same folder.
- Export a cleaned CSV.

Run the dashboard:

```
streamlit run dashboard.py
```

Your browser opens automatically. The dashboard updates when you change filters.

---

## Part 3: Deploy Dashboard to Streamlit Cloud (Free)

### Step 3.1: Push to GitHub first

Complete Part 1 before this step. The dashboard must be on GitHub.

### Step 3.2: Create a requirements.txt

Create a new file called `requirements.txt` in the portfolio folder with this content:

```
pandas==2.2.0
numpy==1.26.3
plotly==5.18.0
streamlit==1.31.0
```

Push this file to GitHub:

```
git add requirements.txt
git commit -m "Add requirements for Streamlit Cloud"
git push
```

### Step 3.3: Deploy on Streamlit Cloud

1. Go to share.streamlit.io.
2. Sign in with your GitHub account.
3. Click "New app."
4. Select the repository `data-analytics-portfolio`.
5. Branch: `main`.
6. Main file path: `dashboard.py`.
7. Click "Deploy."

Your dashboard is live in 2-3 minutes. Share the URL. It looks like:
`https://YOUR_USERNAME-data-analytics-portfolio-dashboard.streamlit.app`

---

## Part 4: LinkedIn Post (Manual)

Open LinkedIn. Create a new post. Use this exact text.

---

Headline: I spent 180 days analyzing sales data. Here is what I found.

Body:

I built a Python pipeline to analyze 180 days of synthetic sales data. Three scripts, one dashboard, one dataset.

What the analysis revealed:

Revenue peaks on Saturdays. 1.5x higher than Monday and Tuesday. Customers buy more on weekends. Schedule your marketing pushes on Tuesday and Wednesday to smooth the curve.

Customer segments are not equal. 11% of customers are Champions. They drive 28% of revenue. A loyalty program targeting this group yields the highest ROI.

Data quality matters. My cleaning script found 12% bad emails, 8% invalid dates, and 5% negative spend values. Every CRM has these issues. Fixing them is a 30-minute task that pays immediate dividends.

I built everything in Python. Pandas for data work. Matplotlib and Plotly for charts. Streamlit for the dashboard.

The full portfolio is on GitHub. Link in comments.

Want a clean view of your business data? DM me. I build analysis pipelines for small businesses. Flat fee. 48-hour delivery.

#DataAnalytics #Python #SmallBusiness #Pune

---

### Step 4.1: Attach images

Download these images from your portfolio folder:
- 1_customer_segments.png
- 2_sales_trend_analysis.png
- 3_data_cleaning_report.png

Upload 1-2 of them to your LinkedIn post. Do not upload all three. Pick the best one.

### Step 4.2: Pin the GitHub link

Add a comment to your own post with the link to your GitHub repository.

---

## Part 5: Maintain and Update

Run these scripts once a month to keep your portfolio fresh. Replace the synthetic data with your own analysis for maximum impact.

Update the dashboard URL in your LinkedIn bio.

Add new scripts over time. Good candidates:
- A/B test analysis
- Churn prediction model
- Web scraping pipeline
- Automated reporting script

---

## File Reference

| File | Purpose |
|------|---------|
| sample_data.csv | Synthetic e-commerce dataset |
| 1_customer_segmentation.py | RFM analysis with segments |
| 2_sales_trend_analysis.py | Time series with trend detection |
| 3_data_cleaning_automation.py | End-to-end data cleaning |
| dashboard.py | Interactive Streamlit dashboard |
| requirements.txt | Dependencies for deployment |
