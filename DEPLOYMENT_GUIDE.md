# SDG 2: Child Stunting Dashboard — Setup & Deployment Guide
# Analytics Techniques and Tools | WVSU-CICT BSIS 3B

## ─── STEP 1: DOWNLOAD YOUR DATA (Do this first) ───────────────────────────

You need 5 CSV files from World Bank Open Data and 1 from FAO.
Save all files in the SAME folder as dashboard.py and the .ipynb notebook.

### File 1 — Stunting Prevalence (Y)
Source: https://data.worldbank.org/indicator/SH.STA.STNT.ME.ZS
Filename: stunting_prevalence.csv
Steps:
  1. Go to the URL above
  2. Click DOWNLOAD → CSV
  3. Extract and rename the main data file to: stunting_prevalence.csv

### File 2 — GDP per Capita (X1)
Source: https://data.worldbank.org/indicator/NY.GDP.PCAP.KD
Filename: gdp_per_capita.csv

### File 3 — Undernourishment Prevalence (X2)
Source: https://data.worldbank.org/indicator/SN.ITK.DEFC.ZS
Filename: undernourishment.csv

### File 4 — Safe Water Access (X3)
Source: https://data.worldbank.org/indicator/SH.H2O.SMDW.ZS
Filename: water_access.csv

### File 5 — Female Secondary Education (X4)
Source: https://data.worldbank.org/indicator/SE.SEC.ENRR.FE
Filename: female_edu_enrollment.csv

### File 6 — Political Stability (X5)
Source: https://databank.worldbank.org/source/worldwide-governance-indicators
Indicator: Political Stability and Absence of Violence/Terrorism: Estimate (PV.EST)
Filename: political_stability.csv

### Optional — Pre-merged file for Dashboard
After running the Jupyter Notebook, export df_merged to:
  df_merged.to_csv("merged_panel_data.csv", index=False)
Place this file in the same folder as dashboard.py.
The dashboard will auto-load it. Without it, it uses built-in demo data.


## ─── STEP 2: SET UP PYTHON ENVIRONMENT ────────────────────────────────────

### Option A: pip (recommended for most students)
```bash
# Open Command Prompt or Terminal in your project folder
pip install -r requirements.txt
```

### Option B: conda
```bash
conda create -n sdg2 python=3.11 -y
conda activate sdg2
pip install -r requirements.txt
```


## ─── STEP 3: RUN THE JUPYTER NOTEBOOK ─────────────────────────────────────

```bash
jupyter notebook
```
1. Open: SDG2_Child_Stunting_Regression.ipynb
2. Run all cells: Kernel → Restart & Run All
3. At the end of Section 2.4, export the merged data:
   df_merged.to_csv("merged_panel_data.csv", index=False)
4. Note the regression coefficients output from Section 5.1
5. Update the COEF dict at the top of dashboard.py with actual values


## ─── STEP 4: RUN THE DASHBOARD LOCALLY ─────────────────────────────────────

```bash
# Make sure you are in the folder containing dashboard.py
streamlit run dashboard.py
```

The dashboard will open at: http://localhost:8501
Test all year slider values (2000–2022) to confirm dynamic updates.


## ─── STEP 5: PUSH TO GITHUB ────────────────────────────────────────────────

```bash
# Initialize git repository (first time only)
git init
git add .
git commit -m "Initial commit — SDG2 Child Stunting Dashboard"

# Create repo on GitHub.com (name it: sdg2-child-stunting-dashboard)
# Then connect and push:
git remote add origin https://github.com/YOUR_USERNAME/sdg2-child-stunting-dashboard.git
git branch -M main
git push -u origin main
```

Your GitHub repo should contain:
  ✅ dashboard.py
  ✅ requirements.txt
  ✅ merged_panel_data.csv
  ✅ SDG2_Child_Stunting_Regression.ipynb
  ✅ All individual CSV source files


## ─── STEP 6: DEPLOY ON STREAMLIT COMMUNITY CLOUD ──────────────────────────

1. Go to: https://share.streamlit.io/
2. Sign in with your GitHub account
3. Click "New app"
4. Select:
   - Repository: YOUR_USERNAME/sdg2-child-stunting-dashboard
   - Branch: main
   - Main file path: dashboard.py
5. Click "Deploy!"

Wait ~2 minutes. Your app URL will be:
https://YOUR_USERNAME-sdg2-child-stunting-dashboard-dashboard-XXXX.streamlit.app/

6. Copy this URL and paste it into Section 6 of your Jupyter Notebook:
   ## 🌐 Live Dashboard: https://YOUR-URL.streamlit.app


## ─── STEP 7: ZIP FOR SUBMISSION ────────────────────────────────────────────

Create a ZIP file containing:
  📁 SDG2_Child_Stunting/
    ├── SDG2_Child_Stunting_Regression.ipynb   ← Jupyter Notebook
    ├── dashboard.py                            ← Streamlit Dashboard
    ├── requirements.txt                        ← Dependencies
    ├── merged_panel_data.csv                  ← Merged dataset
    ├── stunting_prevalence.csv                ← Source dataset 1
    ├── gdp_per_capita.csv                     ← Source dataset 2
    ├── undernourishment.csv                   ← Source dataset 3
    ├── water_access.csv                       ← Source dataset 4
    ├── female_edu_enrollment.csv              ← Source dataset 5
    └── political_stability.csv               ← Source dataset 6


## ─── TROUBLESHOOTING ────────────────────────────────────────────────────────

Problem: "FileNotFoundError: merged_panel_data.csv"
Fix: The dashboard will use built-in demo data automatically.
     To use real data, export it from the notebook first.

Problem: "ModuleNotFoundError: No module named 'missingno'"
Fix: pip install missingno

Problem: Streamlit app crashes on deploy
Fix: Ensure requirements.txt is in the root of your GitHub repo.
     The file must be named exactly: requirements.txt

Problem: World Bank CSV has extra header rows
Fix: The load_wb_wide() function uses skiprows=4 to skip the WB metadata.
     If your download has a different format, adjust skiprows accordingly.

Problem: Choropleth map shows blank countries
Fix: Ensure country_code column uses ISO 3-letter codes (e.g., PHL, IND, NGA).
     World Bank CSVs use this format by default.


## ─── UPDATE REGRESSION COEFFICIENTS ────────────────────────────────────────

After running your notebook with real data, update the COEF dictionary
at the top of dashboard.py (around line 35) with actual values:

COEF = {
    "const":            YOUR_B0,
    "log_gdp":          YOUR_B1,
    "undernourishment": YOUR_B2,
    "water":            YOUR_B3,
    "female_edu":       YOUR_B4,
    "pol_stability":    YOUR_B5,
}

Also update R_SQUARED, ADJ_R_SQUARED, and F_STATISTIC.
