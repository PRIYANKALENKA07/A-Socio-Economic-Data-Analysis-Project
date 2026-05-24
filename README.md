### A Socio-Economic Data Analysis Project | Odisha, India

This project presents a complete end-to-end data analysis of the 
Keonjhar District Household Survey 2026 — from raw KoBoToolbox 
export to a fully interactive Power BI dashboard. The goal is to 
provide actionable socio-economic insights for government planners, 
NGOs and policymakers to improve welfare scheme delivery across 
Keonjhar district, Odisha.

---

## 📌 Purpose of This Project

Keonjhar is one of the tribal-majority districts of Odisha with a 
significant ST population. Understanding the ground reality of 
households — their housing conditions, health access, education 
levels, income sources and women's welfare — is critical for 
targeted government intervention.

This dashboard answers 5 core questions:
- Where were households surveyed and what is the geographic reach?
- Who are these people — age, gender, caste and disability profile?
- Are they protected from illness and are children well nourished?
- Are children going to school and how do households earn?
- Are women and vulnerable groups included in welfare schemes?

---

## 📊 Dataset Overview

| Metric | Value |
|--------|-------|
| Total Households Surveyed | 67,307 |
| Total Individuals Covered | 2,38,471 |
| Total Blocks | 14 |
| Total Gram Panchayats | 174 |
| Total Villages | 662 |
| Average Household Size | 3.54 |
| Data Source | KoBoToolbox — Odia Household Survey |
| Raw File Format | 42 MB binary .xlsb |
| Survey Year | 2026 |

---

## 🛠️ Tools Used

| Tool | Purpose |
|------|---------|
| Python (pandas, pyxlsb) | Data cleaning and preprocessing |
| Power BI Desktop | Dashboard development |
| DAX | Measures and KPI calculations |
| GitHub | Version control and portfolio |

---

## 🧹 Data Cleaning — Python

The raw file was a 42 MB KoBoToolbox binary export (.xlsb) with 
202 columns and severe data quality issues. Power BI could not 
load it directly — it was taking 10+ minutes. Python cleaned the 
entire dataset in one automated script.

### What was cleaned:

| Issue | Action Taken |
|-------|-------------|
| 42 MB binary .xlsb format | Loaded with pyxlsb engine, exported to CSV |
| 15 completely empty columns | Dropped — no data in any row |
| KoBoToolbox system columns | Removed _id, _status, gps compound string |
| 43 multi-select sub-columns | Removed — parent column already had full answer |
| Date stored as Excel float (46113.259) | Converted to proper datetime (2026-04-01 06:14:07) |
| 52,818 cells with whitespace | Stripped — was causing duplicate entries in Power BI |
| Inconsistent column names | Standardised to lowercase_snake_case |
| Duplicate rows | Checked and removed |
| No JOIN key between sheets | Created household_index as relationship key |

### Result:
- Main sheet: 202 columns → 139 columns (no rows lost)
- Member sheet: 73 columns → 36 columns (no rows lost)
- Both exported as clean UTF-8 CSVs loading in under 5 seconds

---

## 📈 Dashboard Pages

### 🏠 Home — Navigation Page
A clickable overview page with section boxes that jump directly 
to each report page. Gives a quick summary of what the survey 
covers and how to navigate the dashboard.

---

### 📍 Page 1 — Overview & Geography
**Core Question: Where were households surveyed?**

**Visuals:** KPI cards, horizontal bar chart, treemap, 
block-level detail table

**Key Insights:**
- Hatadihi block has the highest survey coverage with 12,817 
  households
- Anandpur block has the lowest coverage with only 1,158 
  households
- 49.23% of all households belong to ST (Scheduled Tribe) category
- Youth (15-35 years) make up a large portion of the population 
  across all blocks

**Why this matters:**
Geographic coverage data helps planners identify underserved 
blocks and villages for follow-up surveys and targeted welfare 
scheme delivery.

---

### 👥 Page 2 — Demographics & Housing
**Core Question: Who are these people and how do they live?**

**Visuals:** KPI cards, stacked bar chart, donut charts, 
grouped bar chart

**Key Insights:**
- 49.22% ST population — highest welfare priority group
- Only 38.11% of households have access to a toilet
- 30.95% of households still live in Kutcha (mud/thatch) houses
- PMAY housing scheme has reached only 37.48% of households
- Electricity coverage varies widely — Anandpur leads at 70.82% 
  while Telkoi is at 59.50%
- LPG connection is lowest in Telkoi at 12.49%

**Why this matters:**
Housing and amenity gaps directly indicate which blocks need 
priority attention for Swachh Bharat, PMAY, Ujjwala and 
electrification schemes.

---

### 🏥 Page 3 — Health & Nutrition
**Core Question: Are people protected from illness?**

**Visuals:** KPI cards, horizontal bar chart, bar charts 
for food frequency, drinking water source chart

**Key Insights:**
- 22,000+ household members are uninsured — not covered under 
  BSKY or PMJAY
- 718 SAM (Severely Malnourished) and 717 MAM (Moderately 
  Malnourished) children identified
- Only 39.83% of children are fully immunised — very low coverage
- NCD screening has reached only 10.67% of population
- Institutional delivery rate is critically low at 2.30%
- Handpump is the most common drinking water source — 
  piped water reach is limited

**Why this matters:**
Low immunisation, high malnutrition and poor health screening 
coverage highlight urgent gaps in healthcare delivery that need 
immediate government intervention.

---

### 📚 Page 4 — Education & Livelihoods
**Core Question: Are children learning and how do households earn?**

**Visuals:** KPI cards, dropout reasons bar chart, 
donut charts by gender, agriculture and migration cards

**Key Insights:**
- 52,000 children currently in school — but 2,000 dropouts recorded
- Dropout rate is 3.95% — Financial burden is the top reason
- Literacy rate is 81.49% — gender gap visible with females lower
- 24,000 children receiving scholarships but gaps remain
- Only 44% of trained youth got employment after skill training
- 59.18% of households depend on agriculture as primary livelihood
- Migrant workers make up 5.49% — mostly male

**Why this matters:**
Understanding dropout reasons helps design targeted scholarship 
and mid-day meal programmes. Low training-to-job conversion rate 
signals need to improve skill training quality and job linkage.

---

### 👩 Page 5 — Women & Social Protection
**Core Question: Are women and vulnerable groups included?**

**Visuals:** KPI cards, Subhadra gap bar chart, SHG 
grouped bar chart, digital access grouped bar chart

**Key Insights:**
- 1,19,000 total women covered in the survey
- Only 32.27% of women are SHG members — large gap in women's 
  collective participation
- Subhadra Yojana: 1,03,000 women eligible but only 55,000 are 
  beneficiaries — 48,000 women are missing out
- Aadhaar bank linkage is high but digital payment usage is low
- Smartphone access is significantly higher than actual digital 
  payment usage — suggesting digital literacy gap
- Keonjhar Sadar block leads in SHG membership

**Why this matters:**
The Subhadra gap of 48,000 women is the single most actionable 
insight in this dashboard — direct targeting can bring these 
women into the scheme immediately. SHG and digital literacy 
gaps inform women empowerment programme planning.

---

## 💡 Key Takeaways from the Entire Dashboard

1. **Health is the most critical gap** — low immunisation, 
   high malnutrition, 22K uninsured members need urgent attention
2. **Housing schemes are underpenetrated** — 30.95% Kutcha houses 
   and only 37.48% PMAY coverage despite high ST population
3. **Subhadra Yojana has a 48,000 women gap** — most actionable 
   finding for immediate government action
4. **Financial burden drives school dropouts** — scholarship 
   expansion can directly improve enrollment
5. **Digital divide exists** — people have smartphones but are 
   not using digital payments, pointing to literacy gap not 
   access gap

---

## 📁 Repository Structure

```
keonjhar-household-survey-dashboard/
│
├── clean_keonjhar_survey.py
├── Documentation.docx
├── README.md
│
└── screenshots/
    ├── 00_home_navigation.png
    ├── 01_overview_geography.png
    ├── 02_demographics_housing.png
    ├── 03_health_nutrition.png
    ├── 04_education_livelihoods.png
    └── 05_women_social_protection.png
```

## ⚠️ Data Privacy Note

The raw survey data and cleaned CSV files are NOT uploaded 
in this repository as they contain personal household 
information. Only the cleaning script, documentation and 
dashboard  are shared.

---
![Overview](https://github.com/PRIYANKALENKA07/A-Socio-Economic-Data-Analysis-Project/blob/main/Reports_Screenshot/R3.Demographics%20%26%20Housing.png)

---

## 👩‍💻 Author

**Priyanka Lenka**
Data Analyst | Python | Power BI | DAX
📧 priyankalenkabbs@gmail.com

---

*This project was completed as part of a data analyst assignment 
for the Keonjhar District Household Survey 2026, Odisha.*
