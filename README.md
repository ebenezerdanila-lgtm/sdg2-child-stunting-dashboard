# 🌍 SDG 2 Child Stunting & Food Security Dashboard

> An interactive, data-journalism-grade analytical dashboard visualizing global trends in child stunting and food security, grounded in **UN SDG 2 (Zero Hunger)** indicators and powered by OLS regression modeling.

**Course:** Research Project — BSIS 3B, 2026  
**Institution:** West Visayas State University – College of Information and Communications Technology (WVSU-CICT)  
**Built with:** Python · Streamlit · Plotly · D3.js · TopoJSON · scikit-learn · pandas

---

## 📌 Overview

This dashboard presents an end-to-end analytical pipeline examining the relationship between **child stunting prevalence** (SDG Indicator 2.2.1) and key food security, agricultural, and socioeconomic indicators across multiple countries and years. It combines descriptive visualization, geospatial mapping, and inferential statistics into a cohesive, publication-grade interface.

The project was developed as an academic research output and is structured around the following analytical goals:

- Track global and country-level **child stunting trends** over time
- Visualize **food security indicators** (dietary energy supply, hunger prevalence, food insecurity scale)
- Identify and quantify **drivers of stunting** using Ordinary Least Squares (OLS) regression
- Provide an **interactive prediction tool** for estimating stunting rates from user-defined inputs

---

## 🗂️ Dashboard Sections

| Section | Description |
|---|---|
| **1. Introduction** | Project context, SDG 2 framing, and research objectives |
| **2. Dataset Overview** | Variable descriptions, data sources, and coverage summary |
| **3. Univariate Analysis** | Distribution plots and summary statistics for key indicators |
| **4. Bivariate Analysis** | Correlation matrix and scatter plots between stunting and predictors |
| **5. World Map** | Interactive D3/TopoJSON choropleth with animated year scrubber and "Worst 10" isolation mode |
| **6. Time Series** | Country-level trend lines for stunting and food security metrics |
| **7. OLS Regression Model** | Coefficient table, model diagnostics (R², residuals, VIF), and interpretation |
| **8. Prediction Panel** | Input sliders for real-time stunting rate estimation using the fitted model |
| **9. Conclusion** | Key findings, policy implications, and study limitations |

---

## 🗺️ World Map Feature (Section 5)

The world map is the flagship visualization of this dashboard, built from scratch using **D3.js v7** and **TopoJSON** rendered inside a Streamlit HTML component. Key features include:

- **Animated year scrubber** — step through annual data with play/pause controls
- **"Worst 10" isolation mode** — highlights and labels the 10 countries with the highest stunting rates for the selected year
- **Editorial callout panels** — contextual annotations appear alongside the map
- **Hover tooltips** — show country name, stunting rate, and year on hover
- **Responsive color scale** — sequential colormap anchored to actual data range per year

---

## 📊 Regression Model

The OLS model (Section 7) regresses **child stunting prevalence (%)** on a set of food security and development predictors. Key outputs include:

- Coefficients with standard errors and p-values
- Model fit metrics: R², Adjusted R², F-statistic
- Residual diagnostics: Q-Q plot, fitted vs. residuals
- Variance Inflation Factor (VIF) for multicollinearity assessment

The prediction panel (Section 8) uses the fitted model to generate live estimates as users adjust predictor sliders, with a confidence interval visualization.

---

## 🔧 Tech Stack

| Layer | Tools |
|---|---|
| App framework | [Streamlit](https://streamlit.io/) |
| Data processing | pandas, NumPy |
| Statistics & ML | scikit-learn, statsmodels, scipy |
| Standard charts | Plotly Express / Plotly Graph Objects |
| World map | D3.js v7, TopoJSON (rendered via `st.components.v1.html`) |
| Notebook analysis | Jupyter Notebook (`SDG2_ChildStunting_Regression.ipynb`) |

---

## 📁 Project Structure

```
sdg2-child-stunting-dashboard/
│
├── dashboard.py                        # Main Streamlit app
├── SDG2_ChildStunting_Regression.ipynb # Exploratory analysis & model development
├── data/
│   └── (dataset CSV files)
├── assets/
│   └── (static images, icons, etc.)
└── requirements.txt
```

---

## 🚀 Getting Started

### Prerequisites

- Python 3.9 or higher
- pip

### Installation

```bash
# 1. Clone the repository
git clone https://github.com/ebenezerdanila-lgtm/sdg2-child-stunting-dashboard.git
cd sdg2-child-stunting-dashboard

# 2. Install dependencies
pip install -r requirements.txt

# 3. Run the dashboard
streamlit run dashboard.py
```

The app will open in your browser at `http://localhost:8501`.

---

## 📦 Requirements

Key dependencies (see `requirements.txt` for full list):

```
streamlit
pandas
numpy
plotly
scikit-learn
statsmodels
scipy
```

---

## 📐 Data Sources

- **FAO FAOSTAT** — Dietary energy supply, food production indices
- **WHO / UNICEF / World Bank** — Child stunting prevalence (SDG 2.2.1)
- **FAO FIES** — Food Insecurity Experience Scale (SDG 2.1.2)
- **World Bank Open Data** — GDP per capita, population, agricultural indicators

> All datasets are publicly available and used strictly for academic research purposes.

---

## 📈 Sample Findings

- Countries in **Sub-Saharan Africa** and **South/Southeast Asia** consistently show the highest stunting rates
- **Dietary energy supply** and **access to safe water** are among the strongest negative predictors of stunting
- The OLS model achieves an **R² ≈ 0.950**, explaining ~95% of variance in stunting rates across the sample
- The "Worst 10" map mode reveals persistent clustering of high-stunting countries even as global averages improve

---

## 👤 Author

**Ebenezer C. Danila**  
3rd Year, BS Information Systems — Business Analytics Track  
WVSU-CICT, Section BSIS 3B  
📍 Iloilo City, Philippines

---

## 📄 License

This project is developed for academic purposes. Data used belongs to their respective organizations (FAO, WHO, World Bank). Code is open for educational use.

---

## 🙏 Acknowledgments

- Faculty advisers and panelists of WVSU-CICT BSIS 3B, 2026
- FAO, WHO, UNICEF, and World Bank for open-access global data
- The Streamlit and D3.js open-source communities
