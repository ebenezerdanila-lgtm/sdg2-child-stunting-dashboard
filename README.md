<div align="center">

<!-- HERO BADGE ROW -->
<img src="https://img.shields.io/badge/UN%20SDG%202-Zero%20Hunger-E5243B?style=for-the-badge&logo=united-nations&logoColor=white" alt="SDG 2"/>
<img src="https://img.shields.io/badge/Streamlit-Live%20Dashboard-FF4B4B?style=for-the-badge&logo=streamlit&logoColor=white" alt="Streamlit"/>
<img src="https://img.shields.io/badge/Python-3.9%2B-3776AB?style=for-the-badge&logo=python&logoColor=white" alt="Python"/>
<img src="https://img.shields.io/badge/OLS%20Model-R²%20%3D%200.795-22C55E?style=for-the-badge" alt="R²"/>
<img src="https://img.shields.io/badge/Data-2000–2022-FBBF24?style=for-the-badge" alt="Data Range"/>

<br/><br/>

# 🌍 SDG 2: Child Stunting & Food Security Dashboard

### *A data-journalism-grade analytical platform exposing the global forces behind child stunting*

<br/>

> **"149 million children are stunted right now — not because we lack the knowledge. Because we lack the urgency."**

<br/>

[![🚀 Launch Live Dashboard](https://img.shields.io/badge/🚀%20Launch%20Live%20Dashboard-sdg2--child--stunting--dashboard-FF4B4B?style=for-the-badge&logo=streamlit)](https://sdg2-child-stunting-dashboard-85ynyuyeajkeqcq8cwsypc.streamlit.app/)

<br/>

<sub>Submitted to **Paolo G. Hilado, MSc.** · Instructor, Analytics Techniques and Tools · Finals Alternative Learning Activity · AY 2025–2026</sub>

<sub>**Ebenezer C. Danila** · BSIS 3B — Business Analytics · West Visayas State University – CICT · Iloilo City, Philippines</sub>

</div>

---

## 📋 Table of Contents

- [The Crisis](#-the-crisis)
- [Mission & Purpose](#-mission--purpose)
- [Live Dashboard](#-live-dashboard)
- [Dashboard Sections](#️-dashboard-sections-at-a-glance)
- [World Map Feature](#️-world-map-section-5)
- [OLS Regression Model](#-ols-regression-model)
- [Key Findings](#-key-findings)
- [Tech Stack](#-tech-stack)
- [Data Sources](#-data-sources)
- [Project Structure](#-project-structure)
- [Getting Started Locally](#-getting-started-locally)
- [Literature & References](#-literature--references)
- [Author](#-author)

---

## 🚨 The Crisis

Child stunting — defined by the WHO as height-for-age more than two standard deviations below the median — is not merely a nutrition statistic. It is a **permanent developmental sentence**. A stunted child faces lifelong cognitive impairment, reduced earning potential, and higher mortality risk. The damage is irreversible after the first 1,000 days of life.

| Indicator | Current Scale |
|---|---|
| Children under 5 stunted globally | **149 million** |
| Children wasted & acutely hungry | **45 million** |
| Countries off-track for SDG 2 by 2030 | **Majority** |
| SDG 2 Zero Hunger deadline | **2030** |

Despite decades of global intervention, stunting remains heavily concentrated in **Sub-Saharan Africa** and **South/Southeast Asia** — regions where poverty, political instability, water insecurity, and limited female education intersect to create persistent traps of malnutrition.

**This dashboard exists to make that data impossible to ignore.**

---

## 🎯 Mission & Purpose

This project is both a **research output** and an **advocacy tool**, built around three core principles:

**1. Make the invisible visible.**
Global averages hide national crises. This dashboard breaks the aggregate — surfacing which countries are falling furthest behind, and why, year by year from 2000 to 2022.

**2. Ground urgency in evidence.**
Using OLS regression with HC3 robust standard errors, this project quantifies the exact statistical contribution of five structural drivers — from GDP to female education to political stability — on stunting rates across dozens of countries.

**3. Make data journalism accessible.**
Every visualization, from the animated D3.js world map to the real-time prediction sliders, is designed to be interpreted by policymakers, educators, researchers, and the general public — not just data scientists.

The project is structured around **UN SDG Indicators 2.1.2 and 2.2.1**, and serves as a direct academic contribution to understanding what Zero Hunger will actually require.

---

## 🚀 Live Dashboard

The dashboard is deployed on Streamlit Community Cloud and publicly accessible:

> ### 🔗 [https://sdg2-child-stunting-dashboard-85ynyuyeajkeqcq8cwsypc.streamlit.app/](https://sdg2-child-stunting-dashboard-85ynyuyeajkeqcq8cwsypc.streamlit.app/)

No installation required. Open the link and interact with all 9 sections — including the animated world map, regression model, and live prediction panel — directly in your browser.

---

## 🗂️ Dashboard Sections at a Glance

The dashboard is structured as a sequential analytical narrative — from context, to exploration, to modeling, to action.

| # | Section | What You'll Find |
|---|---|---|
| **1** | **Introduction** | The global scale of the crisis, SDG 2 framing, and the research question |
| **2** | **Dataset Overview** | Variable definitions, data provenance, country/year coverage, and missing data matrix |
| **3** | **Univariate Analysis** | Distribution plots and summary statistics for stunting rate and all five predictors |
| **4** | **Bivariate Analysis** | Correlation heatmap and paired scatter plots between stunting and each driver |
| **5** | **World Map** | D3.js/TopoJSON animated choropleth with year scrubber and "Worst 10" isolation mode |
| **6** | **Time Series** | Country-level trend lines tracing stunting and food security trajectories across 23 years |
| **7** | **OLS Regression Model** | Full coefficient table, model diagnostics (R², VIF, residuals, Q-Q), and interpretation |
| **8** | **Prediction Panel** | Real-time stunting rate estimator — adjust predictor sliders to simulate policy scenarios |
| **9** | **Conclusion** | Key findings, policy implications, study limitations, and call to action |

The sidebar provides a global control panel: a year slider (2000–2022) that drives all charts simultaneously, a live global average stunting rate display, and model metadata.

---

## 🗺️ World Map — Section 5

The world map is the dashboard's flagship visualization — built entirely from scratch using **D3.js v7** and **TopoJSON**, rendered inside a Streamlit HTML component (`st.components.v1.html`). It is not a Plotly or Folium map — every pixel is custom-authored SVG.

**Features:**

- **Animated year scrubber** — step through 2000–2022 with play/pause controls; the color scale updates live for each year
- **"Worst 10" isolation mode** — a toggle that highlights and labels the 10 highest-stunting countries for the selected year, fading out the rest
- **Editorial callout panels** — contextual data annotations appear alongside the map to anchor key statistics
- **Hover tooltips** — reveal country name, stunting rate (%), and year on mouse-over
- **Responsive sequential colormap** — anchored to the actual data range of each year, preventing color scale distortion from outliers

---

## 📊 OLS Regression Model

The regression model (Section 7) uses **Ordinary Least Squares with HC3 Robust Standard Errors** to quantify the structural drivers of child stunting across the dataset.

**Dependent variable:** Child stunting prevalence (%)

**Independent variables and their estimated effects:**

| Predictor | Coefficient | Standardized β | Direction |
|---|---|---|---|
| Undernourishment (%) | +0.5078 | **+0.5832** | ↑ Risk factor |
| Log(GDP per Capita) | −1.8885 | −0.4921 | ↓ Protective |
| Female Secondary Enrollment (%) | −0.1062 | −0.3814 | ↓ Protective |
| Safe Water Access (%) | −0.0887 | −0.2563 | ↓ Protective |
| Political Stability Index | −2.8677 | −0.1847 | ↓ Protective |

**Model fit:**

```
OLS with HC3 Robust Standard Errors
R²            = 0.795
Adjusted R²   = 0.794
Intercept     = 42.3708
```

The prediction panel (Section 8) uses the fitted equation to compute live stunting rate estimates as users adjust predictor sliders, paired with a confidence interval visualization for uncertainty communication.

---

## 📈 Key Findings

Analysis of cross-national panel data from 2000–2022 reveals the following patterns:

- **Undernourishment is the single strongest risk factor** for child stunting (β = +0.58), confirming its role as a direct upstream cause
- **Economic growth alone is insufficient** — high-stunting countries with GDP growth show improvement only when food security and water access improve simultaneously
- **Female secondary education** is a powerful structural lever (β = −0.38), consistent with evidence that maternal education is among the strongest predictors of child nutritional outcomes
- **Political instability** has an outsized effect (coefficient = −2.87 per unit of stability index), suggesting that conflict and governance breakdown are nutrition emergencies in themselves
- **Sub-Saharan Africa and South Asia** account for the majority of the global stunting burden — and the "Worst 10" map mode reveals this clustering has persisted across the entire 2000–2022 observation window
- **Global stunting rates have declined**, but the pace is insufficient to meet the SDG 2 target of eliminating hunger by 2030

---

## 🔧 Tech Stack

| Layer | Technology |
|---|---|
| **App framework** | [Streamlit](https://streamlit.io/) |
| **Data processing** | pandas, NumPy |
| **Statistics** | statsmodels (OLS, HC3), scipy |
| **Machine learning** | scikit-learn |
| **Standard charts** | Plotly Express / Plotly Graph Objects |
| **World map** | D3.js v7, TopoJSON — custom SVG via `st.components.v1.html` |
| **Styling** | Custom CSS injection — Inter + DM Mono fonts, dark cinematic theme |
| **Exploratory analysis** | Jupyter Notebook (`SDG2_ChildStunting_Regression.ipynb`) |
| **Deployment** | Streamlit Community Cloud |

---

## 📐 Data Sources

All datasets are publicly available and used strictly for academic research purposes.

| Source | Indicator | SDG Link |
|---|---|---|
| **WHO / UNICEF / World Bank Joint Malnutrition Estimates** | Child stunting prevalence (% under 5) | SDG 2.2.1 |
| **FAO FAOSTAT** | Dietary energy supply, food production indices | SDG 2.1.1 |
| **FAO FIES** | Prevalence of food insecurity (moderate or severe) | SDG 2.1.2 |
| **World Bank Open Data** | GDP per capita (current USD), population | — |
| **World Bank / WHO** | Access to safely managed drinking water (%) | SDG 6.1.1 |
| **World Bank / UNESCO** | Female secondary school enrollment (gross, %) | SDG 4.2 |
| **World Bank Governance Indicators** | Political Stability and Absence of Violence Index | — |

---

## 📁 Project Structure

```
sdg2-child-stunting-dashboard/
│
├── dashboard.py                         # Main Streamlit application (2,674 lines)
├── SDG2_ChildStunting_Regression.ipynb  # Exploratory analysis & model development
├── requirements.txt                     # Python dependencies
│
├── merged_panel_data.csv                # Pre-merged panel dataset (all countries, 2000–2022)
├── stunting_prevalence.csv              # Raw child stunting data
├── gdp_per_capita.csv                   # GDP per capita data
├── undernourishment.csv                 # Undernourishment prevalence
├── water_access.csv                     # Safe water access data
├── female_edu_enrollment.csv            # Female secondary enrollment
├── political_stability.csv              # World Bank political stability index
│
├── coefficient_plot.png                 # Standardized coefficients visualization
├── correlation_heatmap.png              # Correlation matrix
├── residual_plots.png                   # Regression residual diagnostics
├── linearity_assessment.png             # Linearity check plots
├── normality_assessment.png             # Normality assessment (Q-Q plot)
├── missing_matrix.png                   # Missing data matrix (missingno)
│
└── DEPLOYMENT_GUIDE.md                  # Deployment instructions for Streamlit Cloud
```

---

## 🚀 Getting Started Locally

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

> **Note on Python 3.14+:** If you are running Python 3.14, use unpinned version ranges in `requirements.txt` (e.g. `pandas>=2.2.3`) to ensure pip can resolve pre-built wheels. See `DEPLOYMENT_GUIDE.md` for details.

---

## 📚 Literature & References

The five predictor variables in the OLS model are each grounded in peer-reviewed literature:

| Predictor | Citation | Key Contribution |
|---|---|---|
| Log(GDP per Capita) | Haddad et al. (2003). *Reducing Child Malnutrition: How Far Does Income Growth Take Us?* World Bank Economic Review, 17(1). [DOI](https://doi.org/10.1093/wber/lhg012) | GDP growth reduces child undernutrition, but the relationship is nonlinear — hence the log transformation |
| Undernourishment (%) | FAO, IFAD, UNICEF, WFP & WHO (2023). *The State of Food Security and Nutrition in the World.* Rome: FAO. [DOI](https://doi.org/10.4060/cc3017en) | Undernourishment prevalence is the most direct upstream cause of child stunting |
| Safe Water Access (%) | Prüss-Ustün et al. (2019). *Burden of Disease from Inadequate Water, Sanitation and Hygiene.* Int. J. Hygiene & Environmental Health, 222(5). [DOI](https://doi.org/10.1016/j.ijheh.2019.05.004) | Contaminated water drives diarrheal disease, which is a primary pathway to stunting |
| Female Secondary Enrollment (%) | Ruel & Alderman (2013). *Nutrition-Sensitive Interventions and Programmes.* The Lancet, 382(9891). [DOI](https://doi.org/10.1016/S0140-6736(13)60843-0) | Maternal education is among the strongest structural predictors of child nutritional outcomes |
| Political Stability Index | Headey, D.D. (2013). *Developmental Drivers of Nutritional Change.* World Development, 42. [DOI](https://doi.org/10.1016/j.worlddev.2012.07.002) | Political instability severely disrupts food systems, supply chains, and child nutrition access |

---

## 👤 Author

**Ebenezer C. Danila**
3rd Year, BS Information Systems — Business Analytics Track
West Visayas State University – College of Information and Communications Technology (WVSU-CICT)
Section BSIS 3B · Iloilo City, Philippines

---

## 📄 Academic Context & License

This project was developed as a **Finals Alternative Learning Activity** for *Analytics Techniques and Tools*, submitted to **Paolo G. Hilado, MSc.**, Academic Year 2025–2026.

Data belongs to their respective organizations (FAO, WHO, UNICEF, World Bank). Code is released under the GPL-3.0 license and is open for educational use.

---

## 🙏 Acknowledgments

- **Paolo G. Hilado, MSc.** — Instructor, Analytics Techniques and Tools, WVSU-CICT
- **FAO, WHO, UNICEF, and World Bank** — for open-access global malnutrition and food security data
- **The Streamlit open-source community** — for a deployment platform that brings Python analytics to the world
- **D3.js and TopoJSON communities** — for the visualization primitives that power the world map

---

<div align="center">

<sub>SDG 2 — Zero Hunger · Child Stunting Global Analytics Dashboard · 2000–2022</sub><br/>
<sub>WVSU · CICT · BSIS 3B · 2026</sub>

</div>
