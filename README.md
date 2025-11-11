# 🌾 HackHub Code Canvas Dashboard  

### ⚡ Real-Time Global Agriculture & Sustainability Analytics Dashboard  
![Power BI](https://img.shields.io/badge/Made%20with-Power%20BI-yellow?style=for-the-badge&logo=powerbi)
![Status](https://img.shields.io/badge/Status-Completed-brightgreen?style=for-the-badge)
![License](https://img.shields.io/badge/License-MIT-blue?style=for-the-badge)

---

## 📘 Overview  

The **HackHub Code Canvas Dashboard** is a **Power BI-based analytical solution** built using the **FAOSTAT Global Food & Agriculture dataset**.  
It visualizes worldwide agricultural production, fertilizer usage, land utilization, and sustainability trends across countries.  

Designed for **hackathon-level performance**, the dashboard delivers high-impact insights through an **intuitive dark-themed layout**, combining **data-driven storytelling** and **aesthetic UI precision**.  

---

## 🎯 Key Objectives  

- Provide **interactive insights** into agricultural trends across countries and years.  
- Analyze the relationship between **fertilizer input efficiency** and **yield productivity**.  
- Compare **forest vs agricultural land utilization** to assess sustainability.  
- Highlight **export intensity** and **year-over-year production growth**.  
- Deliver a visually consistent, professional **Power BI dashboard** for global data exploration.  

---

## 🧠 Dataset Information  

**Source:** [Kaggle – Global Food & Agriculture Statistics](https://www.kaggle.com/datasets/unitednations/global-food-agriculture-statistics)  
**Publisher:** United Nations (FAOSTAT)  

**Files Used (5 CSVs):**  
- `fao_data_crops_data.csv`  
- `fao_data_fertilizers_data.csv`  
- `fao_data_forest_data.csv`  
- `fao_data_land_data.csv`  
- `fao_data_production_indices_data.csv`  

Each dataset was cleaned, merged, and transformed using **Power Query** in Power BI.

---

## ⚙️ Data Model  

| Table | Primary Columns | Description |
|--------|----------------|--------------|
| **Crops Data** | `country_or_area`, `item`, `year`, `value`, `area_harvested` | Production & yield data |
| **Fertilizer Data** | `country_or_area`, `year`, `value`, `agricultural_area` | Fertilizer input usage |
| **Forest Data** | `country_or_area`, `year`, `value` | Forest coverage (sustainability indicator) |
| **Land Data** | `country_or_area`, `year`, `value` | Total agricultural land usage |
| **Production Index** | `country_or_area`, `year`, `value` | Indexed measure of crop output |

**Relationships:**  
- `country_or_area` and `year` act as key relationships between tables (1-to-many).  
- Crops table is the **central fact table**, others are connected as dimension datasets.  

---

## 💡 Core DAX Measures  

| # | Measure | Formula |
|---|----------|----------|
| 1️⃣ | **Total Production** | `SUM('fao_data_crops_data'[value])` |
| 2️⃣ | **Average Yield** | `SUM('fao_data_crops_data'[value]) / SUM('fao_data_crops_data'[area_harvested])` |
| 3️⃣ | **Total Fertilizer Used** | `SUM('fao_data_fertilizers_data'[value])` |
| 4️⃣ | **Fertilizer per Hectare** | `SUM('fao_data_fertilizers_data'[value]) / SUM('fao_data_fertilizers_data'[agricultural_area])` |
| 5️⃣ | **Fertilizer Efficiency** | `SUM('fao_data_crops_data'[value]) / SUM('fao_data_fertilizers_data'[value])` |
| 6️⃣ | **Year-over-Year Growth (%)** | `(SUM('fao_data_crops_data'[value]) - CALCULATE(SUM('fao_data_crops_data'[value]), FILTER(ALL('fao_data_crops_data'), 'fao_data_crops_data'[year] = MAX('fao_data_crops_data'[year]) - 1))) / CALCULATE(SUM('fao_data_crops_data'[value]), FILTER(ALL('fao_data_crops_data'), 'fao_data_crops_data'[year] = MAX('fao_data_crops_data'[year]) - 1))` |
| 7️⃣ | **Export Intensity (%)** | `SUMX(FILTER('fao_data_crops_data','fao_data_crops_data'[element]="Export Quantity"),'fao_data_crops_data'[value]) / SUM('fao_data_crops_data'[value])` |
| 8️⃣ | **Total Agricultural Land** | `SUM('fao_data_land_data'[value])` |
| 9️⃣ | **Total Forest Area** | `SUM('fao_data_forest_data'[value])` |
| 🔟 | **Land Utilization (%)** | `SUM('fao_data_land_data'[value]) / (SUM('fao_data_land_data'[value]) + SUM('fao_data_forest_data'[value]))` |

---

## 📊 Dashboard Visuals Overview  

| Section | Visual Type | Key Metric / Insight |
|----------|--------------|-----------------------|
| **Global Production Map** | Filled Map | Shows country-wise crop production levels |
| **Yield Over Time** | Line Chart | Yearly yield trend across countries |
| **Fertilizer & Efficiency Scatter** | Scatter Chart | Relation between fertilizer input and yield |
| **Land Utilization Ratio** | Gauge Chart | Proportion of agricultural vs forest land |
| **Export Intensity** | Bar Chart | Highlights top exporting countries |
| **Forest & Sustainability Trend** | Area Chart | Displays global forest area decline/growth |
| **Agriculture KPIs** | KPI Cards | Production, Fertilizer, Land, Index |
| **Filters** | Slicers | Year, Country, Crop, Element, Category |

---

## 🎨 Theme & Design  

- **Theme Name:** AgriBlack Compact 🌑  
- **Primary Colors:**  
  - Green – `#4CAF50`  
  - Lime – `#CDDC39`  
  - Brown – `#6D4C41`  
  - Accent Gold – `#FFB300`  
- **Page Background:** `#0B0B0B`  
- **Panel Background:** `#111111`  
- **Font:** Segoe UI / Power BI Default  

---

## 🧩 Features  

✅ Clean data transformation via Power Query  
✅ 10 custom DAX measures  
✅ 1-to-many relationship model  
✅ Interactive slicers for year, country, and element  
✅ Fully optimized for dark-mode dashboards  
✅ Ideal for real-time presentation and hackathon judging  

---

## ⚡ How to Run  

1️⃣ Clone the repository  
```bash
git clone https://github.com/AdityaGaur19/HackHub-Code-Canvas-Dashboard.git
