# 🚦 Road Accident Analysis — Power BI Dashboard

![Power BI](https://img.shields.io/badge/Power%20BI-F2C811?style=flat&logo=powerbi&logoColor=black)
![DAX](https://img.shields.io/badge/DAX-Time%20Intelligence-blue)
![Domain](https://img.shields.io/badge/Domain-Public%20Safety-red)

A single-page **road accident analytics dashboard** built in Power BI that analyses UK road casualty data across vehicle types, road types, light conditions, and geographic locations. The report enables year-over-year performance tracking and helps transport authorities and safety planners identify high-risk patterns — filtered interactively by road surface and weather conditions.

---

## 📈 Key Metrics — Current Year vs Previous Year

| Metric | Value | YoY Change |
|---|---|---|
| Total Casualties | 158.0K | ▼ 10.6% |
| Total Accidents | 117.0K | ▼ 10.4% |
| Fatal Casualties | 1.3K | ▼ 34.5% |
| Serious Casualties | 22.65K | ▼ 14.6% |
| Slight Casualties | 132.9K | ▼ 9.4% |

---

## 📊 Visuals & Analysis

### KPI Cards with YoY Comparison
Five headline KPI cards — Total Casualties, Total Accidents, Fatal, Serious, and Slight — each showing current year totals alongside percentage change vs the prior year using TOTALYTD and SAMEPERIODLASTYEAR DAX measures.

### CY vs PY Monthly Casualty Trend
Dual-layer area chart overlaying current year and previous year monthly casualty counts, enabling visual identification of seasonal patterns and improvement periods across all 12 months.

### Casualties by Vehicle Type
Icon-annotated breakdown: Car (125,650) · Bike (12,741) · Van (12,772) · Bus (5,335) · Agricultural (323) · Other (1,166)

### Casualties by Road Type
Single carriageway (248K) · Dual carriageway (54K) · Roundabout (22K) · One way street (6K) · Slip road (5K)

### Casualties by Urban / Rural
Urban 62.36% (209K) vs Rural 37.64% (126K)

### Casualties by Light Condition
Daylight 76.16% (255K) vs Dark 23.84% (80K)

### Casualties by Location — Geospatial Map
Bing Maps dot-plot of accident hotspots across the UK, with visible clustering around urban centres in England.

---

## ⚙️ DAX Measures

```dax
-- Current Year Casualties
CY Casualties = TOTALYTD(SUM(Data[Number_of_Casualties]), 'Calender'[Date].[Date])

-- Previous Year Casualties
Previous Year Casualties = CALCULATE(SUM(Data[Number_of_Casualties]), SAMEPERIODLASTYEAR('Calender'[Date]))

-- Year-over-Year %
YoY Casualties = ([CY Casualties] - [Previous Year Casualties]) / [Previous Year Casualties]

-- Current Year Accidents
CY Accident = TOTALYTD(COUNT(Data[Accident_Index]), 'Calender'[Date])

-- Calendar Table
Calender = CALENDAR(MIN(Data[Accident Date]), MAX(Data[Accident Date]))
```

**Calculated Columns:** Year · MonthNo · Month · QuarterNo · Quarter · Day

**Data Groups:** Vehicle Type · Light Conditions · Weather Conditions · Road Surface Conditions

---

## 🛠 Tools & Skills

- **Power BI Desktop** — data modelling, report design, interactive filters
- **DAX** — TOTALYTD, SAMEPERIODLASTYEAR, CALCULATE, CALENDAR for time intelligence
- **Geospatial Mapping** — Bing Maps integration for location-level accident plotting
- **Interactive Slicers** — Road Surface and Weather Conditions filters across all visuals

---

## 💡 Key Insights

- Overall casualties fell **10.6% YoY** — fatalities saw the sharpest decline at 34.5%
- **Cars** account for 79% of all vehicle-related casualties (125,650)
- **Single carriageways** are the most dangerous road type with 248K casualties
- **Urban areas** account for 62.36% of casualties
- **76% of accidents** occur in daylight — traffic volume, not lighting, is the primary risk factor
- Accident hotspots cluster around **Greater London, the Midlands, and the M1/M6 corridor**

---

## 📂 Files

├── [Road_Accident.pbix](https://github.com/abhisheknirmal02-lab/Road-Accident-Analysis/blob/main/Road%20Accident.pbix)    # Power BI report file
├── [Road_Accident_Dax.xlsx](https://github.com/abhisheknirmal02-lab/Road-Accident-Analysis/blob/main/Road%20Accident%20Dax.xlsx)   # DAX measures reference sheet
├── [Dashboard preview]((https://github.com/abhisheknirmal02-lab/Road-Accident-Analysis/blob/main/Road%20accident.png))



## 🚀 How to Use

1. Clone or download this repository
2. Open `Road_Accident.pbix` in Power BI Desktop
3. Connect to your data source or use the included CSV
4. Use the **Road Surface** and **Weather Conditions** slicers to explore conditional breakdowns
5. Refer to `Road_Accident_Dax.xlsx` for all DAX measure definitions and calculated columns

---

*Built as a portfolio project demonstrating time-intelligence DAX, geospatial visualisation, and public safety analytics in Power BI. ⭐ Star this repo if you find it useful!*
