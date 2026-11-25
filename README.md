# 🌿 India Air Quality Monitoring Dashboard

![Power BI](https://img.shields.io/badge/Power%20BI-Analytics-F2C811?logo=powerbi&logoColor=black) ![DAX](https://img.shields.io/badge/DAX-Measures-blue) ![API](https://img.shields.io/badge/Data-REST%20API-green)

An interactive Power BI portfolio project exploring air pollution concentrations across Indian cities and monitoring stations using the CPCB dataset available through India's Open Government Data platform.

## 📸 Dashboard Preview

![India Air Quality Monitoring Dashboard](assets/dashboard.png)

## 🎯 Project Objectives

- Explore geographic differences in air pollution readings.
- Monitor PM2.5, PM10 and NO₂ concentrations.
- Compare cities, states and monitoring stations using interactive filters.
- Practice API integration, Power Query, DAX and dashboard design.

## 📊 KPI Snapshot

The following values are displayed in the dashboard screenshot, dated 25 November 2026, 17:00. They are not current live readings or independently validated statistics.

| KPI | Displayed value |
|---|---:|
| Monitoring stations | 576 |
| Cities | 296 |
| States / regions | 31 |
| Average PM2.5 | 117 µg/m³ |
| Average PM10 | 110.16 µg/m³ |
| Average NO₂ | 34.95 µg/m³ |
| High pollution stations | 412 |

The high-pollution indicator uses PM2.5 readings above 60 µg/m³ as a screening threshold, not an official AQI category.

## 🛠️ Tools and Technologies

- Microsoft Power BI Desktop — report design and visualization
- Power Query — API ingestion, data cleaning and transformation
- DAX — calculated measures and KPIs
- REST API / JSON — source data integration
- Geographic visualization and interactive slicers

## 📂 Data Source

- Provider: Central Pollution Control Board (CPCB)
- Portal: [Open Government Data Platform India](https://data.gov.in/resource/real-time-air-quality-index-various-locations)
- Resource ID: `3b01bcb8-0b14-4abf-b6f2-c1bfd384ba69`
- Fields: country, state, city, station, last_update, latitude, longitude, pollutant_id, pollutant_min, pollutant_max, pollutant_avg.

Example endpoint (replace the placeholder privately):

```text
https://api.data.gov.in/resource/3b01bcb8-0b14-4abf-b6f2-c1bfd384ba69?api-key=YOUR_API_KEY&format=json&offset=0&limit=10000
```

Never commit an API key to a public repository. Check API pagination and response limits before assuming all records have been retrieved.

## ⚙️ Workflow

1. Connect Power BI to the API using Get Data > Web.
2. Expand JSON records in Power Query.
3. Convert unavailable readings to null and assign appropriate data types.
4. Create DAX measures for distinct counts and pollutant-specific averages.
5. Build map, ranking, comparison and KPI visuals.
6. Add state, city, station and pollutant slicers.
7. Refresh the report to retrieve the latest available source readings.

## 🧮 Example DAX

```dax
Average PM2.5 =
CALCULATE(
    AVERAGE('3b01bcb8-0b14-4abf-b6f2-c1bfd384ba69'[Pollutant_Avg]),
    '3b01bcb8-0b14-4abf-b6f2-c1bfd384ba69'[Pollutant_ID] = "PM2.5"
)
```

## 🚧 Validation and Future Improvements

- Rank cities by a single selected pollutant's average concentration rather than summing different pollutants.
- Use unique station identifiers and state-based distinct station counts.
- Store historical snapshots to enable genuine time-series analysis.
- Use a single-pollutant average for the gauge; concentrations are not AQI scores.
- Configure and verify scheduled refresh separately; the screenshot does not establish continuous live streaming.

## 📁 Repository Setup

This documentation package includes the README and dashboard screenshot. Add your own `.pbix` report after removing credentials and validating the measures. Open the report in Power BI Desktop to interact with it.

## 👤 Author

**Rohit** — Data Analytics & Visualization

This is an independent learning and portfolio project, not an official government dashboard. Government branding and source data are attributed to their respective owners.
