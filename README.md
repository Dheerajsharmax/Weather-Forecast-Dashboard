# Weather-Forecast-Dashboard

<img width="1307" height="732" alt="image" src="https://github.com/user-attachments/assets/16694867-bfab-436c-91b6-1e3ec339c18e" />

# 🌦️ Weather Analytics Dashboard — Power BI
1. Project Overview

The Weather Analytics Dashboard is an interactive Power BI project developed using WeatherAPI to fetch real-time weather and forecast data.

The project integrates weather data through an API, transforms and structures the JSON response using Power Query, builds a relational data model in Power BI, and uses DAX measures to create dynamic KPIs and analytical visuals.

The dashboard provides a consolidated view of:

🌡️ Current temperature
🌤️ Current weather condition
💧 Humidity
💨 Wind speed
👁️ Visibility
☀️ UV Index
🌧️ Precipitation
🌡️ Atmospheric pressure
🌅 Sunrise & sunset
🌧️ Daily rain probability
📈 Temperature forecast
🌍 Multi-city weather comparison
🕐 Forecast information
2. Data Source
WeatherAPI

The dashboard uses WeatherAPI as the primary external data source.

# WeatherAPI

WeatherAPI provides weather information through REST API endpoints, which can return current weather as well as forecast information.

The Power BI project uses this API data as the foundation for the dashboard.

API Data Flow
WeatherAPI
     ↓
API Request
     ↓
JSON Response
     ↓
Power Query
     ↓
Data Transformation
     ↓
Power BI Data Model
     ↓
DAX Measures
     ↓
Dashboard
3. API Integration

The project demonstrates how an external REST API can be integrated into Power BI.

The API provides weather information based on the selected location.

For example, weather data can be requested for locations such as:

Bangalore
Bihar
Goa
Delhi
Haryana
Hyderabad
Mumbai
Noida

The API response contains structured weather information that is transformed in Power Query before being loaded into the Power BI model.

# 4. Power Query — Data Transformation

After retrieving the data from WeatherAPI, Power Query is used to prepare the API response for analysis.

The transformation process includes:

Data Extraction
Connecting Power BI to WeatherAPI
Retrieving API response
Expanding JSON records
Extracting nested weather fields
Data Cleaning
Removing unnecessary fields
Handling missing values
Standardizing location names
Correcting data types
Data Transformation
Converting date/time fields
Extracting forecast dates
Preparing day names
Structuring current weather data
Structuring daily forecast data
Structuring hourly forecast data
Final Tables

## The transformed API data is organized into:

Current_Data
Forecast_Data_Day
Forecast_Data_Hour
Location
# 5. Data Model

The project uses a relational model where the Location table acts as the central location dimension.

                       Location
                          │
             ┌────────────┼────────────┐
             │            │            │
             ▼            ▼            ▼
      Current_Data   Forecast_Data_Day   Forecast_Data_Hour
Relationships
From	To	Cardinality
Current_Data[location.name]	Location[location.name]	1 : 1
Forecast_Data_Day[location.name]	Location[location.name]	Many : 1
Forecast_Data_Hour[location.name]	Location[location.name]	Many : 1

All three relationships are active.
### 🎯 Main Objective

The primary objective of this project is to transform raw weather data into an **easy-to-understand analytical dashboard** that allows users to:

* Monitor current weather conditions
* Compare weather conditions across cities
* Analyze temperature trends
* Track rainfall probability
* View upcoming weather forecasts
* Monitor humidity, wind speed, visibility, UV index, precipitation, and pressure
* Analyze sunrise and sunset timings
* Provide a clean and interactive weather-monitoring experience

---

# 2. Tools & Technologies

| Tool                    | Purpose                                 |
| ----------------------- | --------------------------------------- |
| **Power BI Desktop**    | Dashboard development and visualization |
| **Power Query**         | Data transformation and preparation     |
| **DAX**                 | Measures, calculations and KPIs         |
| **Data Modeling**       | Relationships between tables            |
| **Weather Data/API**    | Source of weather information           |
| **Custom Icons/Images** | Weather visualization                   |
| **Power BI Visuals**    | Data presentation                       |

> The exact external weather API/source is not visible in the screenshots, so it should be added here once you confirm the source.

---

# 3. Dataset Structure

The Power BI model contains multiple tables that separate **current weather information**, **daily forecasts**, **hourly forecasts**, and **location information**.

The major tables visible in the model are:

### 3.1 `Current_Data`

This table contains the **current weather information** for locations.

Typical information used by the dashboard includes:

* Location
* Current temperature
* Weather condition
* Humidity
* Wind speed
* Visibility
* UV Index
* Precipitation
* Atmospheric pressure
* Sunrise
* Sunset

This table is primarily responsible for the **current weather section** of the dashboard.

---

### 3.2 `Forecast_Data_Day`

This table contains **daily forecast information**.

It is used for:

* Upcoming daily weather cards
* Daily temperature forecast
* Rain probability
* Forecast comparison
* Future weather conditions

The dashboard uses the daily forecast to display weather for different days such as:

* Friday
* Saturday
* Sunday
* Monday
* Tuesday
* Wednesday
* Thursday

---

### 3.3 `Forecast_Data_Hour`

This table contains **hourly forecast data**.

It can be used for more granular analysis such as:

* Hourly temperature
* Hourly precipitation
* Hourly weather conditions
* Hourly wind conditions
* Hourly forecast trends

Although the current dashboard mainly focuses on daily information, the hourly table provides the foundation for deeper future analysis.

---

### 3.4 `Location`

The `Location` table acts as the **central location/dimension table**.

It contains location information such as:

* Location name
* City
* Geographic information

The location table allows the dashboard to connect weather information with specific cities.

---

# 4. Data Model

The project uses a relational data model with `Location` acting as the central lookup table.

The relationships shown in the Power BI model are:

### Relationship 1

`Current_Data[location.name]`

⬇️

`Location[location.name]`

**Cardinality:** 1 : 1
**Status:** Active

---

### Relationship 2

`Forecast_Data_Day[location.name]`

⬇️

`Location[location.name]`

**Cardinality:** Many : 1
**Status:** Active

---

### Relationship 3

`Forecast_Data_Hour[location.name]`

⬇️

`Location[location.name]`

**Cardinality:** Many : 1
**Status:** Active

---

### Model Structure

```text
                    Location
                       │
          ┌────────────┼────────────┐
          │            │            │
          ▼            ▼            ▼
   Current_Data   Forecast_Data_Day   Forecast_Data_Hour
```

This structure allows location-based filtering across current and forecast data.

---

# 5. Dashboard Design

The dashboard follows a **modern weather-app style design** using:

* Dark background
* Orange gradient panels
* Rounded cards
* Weather icons
* KPI cards
* Forecast cards
* Line chart
* Horizontal bar chart
* Location indicators

The design focuses on providing important information quickly rather than overwhelming the user with raw data.

---

# 6. Dashboard Sections

## 📍 A. Location & Last Updated

The top-left section displays:

**Location:** Bangalore

**Last Updated:** 04 Sep Friday

This provides users with immediate context about:

* Which location is currently being analyzed
* When the data was last refreshed

---

# 7. 🌡️ Current Weather

The main weather card displays:

### Bangalore

**Temperature:** 24.6°C

**Condition:** Overcast

This is the primary KPI of the dashboard.

The card also provides a quick comparison with other locations:

| Location  | Temperature |
| --------- | ----------: |
| Bangalore |      24.6°C |
| Bihar     |      28.2°C |
| Goa       |      26.3°C |

This allows users to quickly compare current temperatures across locations.

---

# 8. 🌤️ Weather Forecast Cards

The top section contains forecast cards for upcoming days.

The displayed days include:

* Friday
* Monday
* Saturday
* Sunday
* Thursday
* Tuesday
* Wednesday

Each card contains:

* Day
* Weather icon
* Forecast condition

This gives users an immediate visual understanding of the upcoming weather.

---

# 9. 📈 Temperature Forecast Trend

The line chart shows the **forecast temperature trend** across different days.

### Displayed values

| Day       | Temperature |
| --------- | ----------: |
| Saturday  |     26.70°C |
| Sunday    |     26.50°C |
| Monday    |     26.30°C |
| Tuesday   |     26.10°C |
| Friday    |     25.40°C |
| Wednesday |     25.40°C |
| Thursday  |     25.20°C |

### Key insight

The forecast indicates a **gradual decrease in temperature** over the displayed period.

The temperature moves from approximately:

**26.70°C → 25.20°C**

This chart makes it easy to identify future temperature movement rather than looking at individual forecast values.

---

# 10. 🌅 Sunrise & Sunset

The dashboard contains a dedicated section for astronomical timing.

Displayed values include:

### Sunrise

**06:08 AM**

### Sunset

**06:23 PM**

This provides useful contextual information for users planning outdoor activities or analyzing daylight conditions.

### Small documentation note

In the screenshot, the second label appears as **"Sunrise Time"**, but the value `06:23 PM` is clearly a **sunset time**. For the final dashboard, this should be renamed to:

**Sunset Time**

---

# 11. 💧 Weather KPI Cards

The dashboard contains several important weather KPIs.

## Humidity

**68**

Represents the current relative humidity.

---

## Wind Speed

**16.60**

Represents the current wind speed.

The unit should be displayed explicitly based on the source data, for example:

**16.60 km/h**

if that is the source/API unit.

---

## Visibility

**10**

Represents current visibility.

Again, the unit should be explicitly shown in the final dashboard, such as kilometers, depending on the source data.

---

## UV Index

**0**

Represents the current UV index.

---

## Precipitation

**0.00**

Indicates the current precipitation level.

---

## Atmospheric Pressure

**29.92**

Represents atmospheric pressure.

The unit should be explicitly displayed based on the source data.

---

# 12. 🌡️ Fahrenheit Temperature Card

The dashboard also displays temperature in Fahrenheit:

### **76.3°F**

This provides an alternative temperature representation alongside the Celsius value.

The Celsius and Fahrenheit measures visible in the model are:

* `Cur_temp_C`
* `Cur_temp_F`

This demonstrates the use of **DAX calculations/measures** for presenting temperature in different units.

---

# 13. 🌧️ Rain Probability Analysis

The right-side chart is titled:

### **Change of Rain Daily**

It displays the percentage distribution associated with daily rain conditions.

Displayed values include:

| Day       | Rain-related Percentage |
| --------- | ----------------------: |
| Monday    |                     93% |
| Wednesday |                     90% |
| Sunday    |                     86% |
| Saturday  |                     83% |
| Tuesday   |                     83% |
| Thursday  |                     41% |
| Friday    |                     39% |

### Key observation

Monday has the highest displayed rain probability at approximately **93%**, while Friday has the lowest at approximately **39%**.

The visual uses stacked bars to show the percentage composition.

---

# 14. 📊 DAX Measures

The model contains measures used to dynamically calculate dashboard values.

The visible measures include:

### `AQI`

Used to calculate/display the **Air Quality Index**.

---

### `Change of Rain`

Used to calculate the daily rain-related percentage displayed in the rain chart.

---

### `Cur_temp_C`

Used to return the current temperature in Celsius.

---

### `Cur_temp_F`

Used to return the current temperature in Fahrenheit.

This allows the dashboard to display:

```text
24.6°C
```

and

```text
76.3°F
```

---

### `Last_updated_Date`

Used to dynamically display the latest data refresh/update date.

For example:

```text
Last Updated: 04 Sep Friday
```

This is particularly useful in a weather dashboard because weather information is time-sensitive.

---

# 15. 📌 Key KPIs

The dashboard tracks the following major KPIs:

| KPI                 | Example Value |
| ------------------- | ------------: |
| Current Temperature |        24.6°C |
| Temperature °F      |        76.3°F |
| Humidity            |            68 |
| Wind Speed          |         16.60 |
| Visibility          |            10 |
| UV Index            |             0 |
| Precipitation       |          0.00 |
| Pressure            |         29.92 |
| Sunrise             |      06:08 AM |
| Sunset              |      06:23 PM |
| Rain Probability    |     Up to 93% |
| AQI                 |       Dynamic |

---

# 16. 🔄 Data Flow

The overall project workflow can be represented as:

```text
Weather Data Source
        ↓
Raw Weather Data
        ↓
Power Query
        ↓
Data Cleaning & Transformation
        ↓
Current_Data
Forecast_Data_Day
Forecast_Data_Hour
Location
        ↓
Data Model
        ↓
DAX Measures
        ↓
Power BI Visualizations
        ↓
Interactive Weather Dashboard
```

---

# 17. 🔧 Data Transformation

Power Query can be used in this project to perform tasks such as:

### Data Cleaning

* Removing unnecessary columns
* Handling null values
* Correcting data types
* Renaming columns
* Standardizing location names

### Data Preparation

* Converting date/time fields
* Extracting day names
* Preparing forecast dates
* Preparing location fields
* Formatting numerical weather indicators

### Data Modeling Preparation

The `location.name` field is standardized so that it can be used to connect:

```text
Current_Data
Forecast_Data_Day
Forecast_Data_Hour
```

with:

```text
Location
```

---

# 18. 🎨 Visualization Strategy

Different visualizations were selected based on the type of information being communicated.

| Visualization       | Purpose                         |
| ------------------- | ------------------------------- |
| KPI Cards           | Display current weather metrics |
| Weather Cards       | Show forecast conditions        |
| Line Chart          | Analyze temperature trends      |
| Bar Chart           | Analyze rain probability        |
| Icon-based Cards    | Improve weather readability     |
| Location Card       | Display selected city           |
| Sunrise/Sunset Card | Display daylight timings        |

The dashboard intentionally uses **visual hierarchy** so the most important information—current temperature and condition—is immediately visible.

---

# 19. 🧠 Analytical Insights

Based on the displayed dashboard data, several insights can be identified.

### Insight 1 — Current Weather

Bangalore is currently showing:

**24.6°C with Overcast conditions.**

---

### Insight 2 — Temperature Trend

Forecast temperature shows a gradual decline from:

**26.70°C → 25.20°C**

across the displayed forecast period.

---

### Insight 3 — Rain Probability

The highest displayed rain probability is:

**93% on Monday**

while the lowest is:

**39% on Friday.**

---

### Insight 4 — City Comparison

Among the displayed locations:

**Bihar — 28.2°C**

is warmer than:

**Goa — 26.3°C**

and:

**Bangalore — 24.6°C.**

---

### Insight 5 — Current Precipitation

The dashboard currently shows:

**0.00 precipitation**

for Bangalore.

---

# 20. 💡 Business/User Value

Although weather data is not traditionally considered a business dataset, this dashboard demonstrates several important **data analytics skills**.

It can help users make decisions related to:

* Travel planning
* Outdoor activities
* Agriculture
* Logistics
* Transportation
* Event planning
* Tourism
* Daily commuting
* Weather monitoring

For example, a logistics company could use similar analytics to understand weather conditions that may affect delivery operations.

---

# 21. 🚀 Interactive Features

The Power BI dashboard can be extended with interactive functionality such as:

### Location Selection

Users can select different cities such as:

* Bangalore
* Bihar
* Goa
* Delhi
* Haryana
* Hyderabad
* Mumbai
* Noida

The dashboard can then dynamically update weather information for the selected location.

---

### Forecast Filtering

Users can analyze:

* Current conditions
* Daily forecasts
* Hourly forecasts

depending on the selected date/location.

---

# 22. 📐 Recommended Improvements

There are a few improvements that would make this project even stronger.

### 1. Add AQI visualization

You already have an `AQI` measure.

Add an AQI card with categories such as:

```text
0–50       Good
51–100     Moderate
101–150    Unhealthy for Sensitive Groups
151–200    Unhealthy
201–300    Very Unhealthy
300+       Hazardous
```

---

### 2. Add units to KPIs

Instead of:

```text
Wind Speed
16.60
```

use:

```text
Wind Speed
16.60 km/h
```

Similarly, explicitly show units for:

* Visibility
* Pressure
* Precipitation
* Wind Speed

This makes the dashboard more professional.

---

### 3. Fix Sunrise/Sunset Label

Change:

```text
Sunrise Time
06:23 PM
```

to:

```text
Sunset Time
06:23 PM
```

---

### 4. Add hourly temperature chart

Since `Forecast_Data_Hour` already exists, you can create:

**24-Hour Temperature Forecast**

Example:

```text
12 PM → 24°C
1 PM  → 25°C
2 PM  → 26°C
3 PM  → 27°C
...
```

This would make better use of your hourly dataset.

---

### 5. Add Weather Alerts

A very useful addition would be a dynamic alert system:

```text
⚠️ Heavy Rain Expected
```

or

```text
☀️ High UV Alert
```

or

```text
💨 Strong Wind Alert
```

based on thresholds.

---

# 23. ⭐ Skills Demonstrated

This project demonstrates several important Power BI/Data Analyst skills:

### Power BI

* Dashboard development
* Data modeling
* Relationships
* KPI design
* Visual selection
* Dashboard UI/UX
* Interactive reporting

### Power Query

* Data transformation
* Data cleaning
* Data type management
* Data preparation

### DAX

* Measures
* Dynamic KPIs
* Temperature conversion
* Date calculations
* Percentage calculations

### Data Analytics

* Trend analysis
* Comparative analysis
* Forecast analysis
* KPI monitoring
* Data storytelling

---

# 24. 🗂️ Project Architecture

```text
                    WEATHER ANALYTICS PROJECT
                              │
             ┌────────────────┴────────────────┐
             │                                 │
       DATA SOURCES                       POWER BI
             │                                 │
             ▼                                 ▼
      Weather Data/API                 Power Query
             │                                 │
             ├──────────────┐                  ▼
             │              │             Data Model
             ▼              ▼                  │
       Current Data     Forecast Data          │
                            │                  │
                     ┌──────┴──────┐           │
                     │             │           │
                     ▼             ▼           │
                  Daily         Hourly         │
                     │             │           │
                     └──────┬──────┘           │
                            │                  │
                            ▼                  ▼
                         Location        DAX Measures
                                              │
                                              ▼
                                       Dashboard
```

---

# 25. 📋 Project Summary

**Project Name:** Weather Analytics Dashboard

**Platform:** Microsoft Power BI

**Domain:** Weather Analytics / Forecasting

**Data Type:** Current + Daily Forecast + Hourly Forecast

**Primary Location:** Bangalore

**Key Analytical Areas:**

* Current weather
* Temperature
* Humidity
* Wind
* Visibility
* UV
* Precipitation
* Atmospheric pressure
* Rain probability
* Daily forecast
* Hourly forecast
* Sunrise & sunset
* AQI

---

# 26. 🎤 Interview Explanation

If an interviewer asks:

### **"Tell me about your Power BI project."**

You can explain it like this:

> **"I developed a Weather Analytics Dashboard in Power BI to analyze current weather conditions and forecast data across multiple locations. I structured the data into Current Data, Daily Forecast, Hourly Forecast, and Location tables and created relationships between them using location as the common dimension.**
>
> **I used Power Query for data preparation and DAX measures for dynamic KPIs such as current temperature in Celsius and Fahrenheit, rain probability, AQI, and last updated date.**
>
> **For visualization, I created KPI cards for humidity, wind speed, visibility, UV index, precipitation and pressure, along with forecast cards, a temperature trend line chart, and a rain probability chart.**
>
> **The main goal was to convert raw weather information into an interactive dashboard that allows users to quickly understand current conditions, compare locations, and analyze upcoming weather trends."**

---

# 27. 🏆 Portfolio Description

### Short Version

**Weather Analytics Dashboard | Power BI**

Built an interactive Weather Analytics Dashboard using Power BI to monitor current weather conditions and forecast trends across multiple locations. The dashboard integrates current, daily, and hourly weather data and uses Power Query, data modeling, and DAX to create dynamic KPIs and visual insights.

**Key features include:**

* 🌡️ Current temperature in °C & °F
* 🌧️ Rain probability analysis
* 📈 Temperature forecast trends
* 💧 Humidity & precipitation
* 💨 Wind speed
* 👁️ Visibility
* ☀️ UV Index
* 🌅 Sunrise & Sunset
* 🌍 Multi-location comparison
* 📊 AQI analysis

**Tools:** Power BI | Power Query | DAX | Data Modeling | Weather Data/API

---

## 🔥 Overall Project Assessment

This is a **solid portfolio project for a fresher Data Analyst profile** because it demonstrates more than simply putting charts on a Power BI canvas.

The strongest parts are the combination of:

**Data → Transformation → Data Model → DAX → Visualization → Insights
