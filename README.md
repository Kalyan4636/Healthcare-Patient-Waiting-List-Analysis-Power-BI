# 🏥 Healthcare Patient Waiting List Analysis | Power BI

An end-to-end **Power BI Healthcare Analytics project** focused on analyzing patient waiting lists across inpatient and outpatient services.

The project demonstrates the complete Power BI development lifecycle — from **business requirement gathering and data preparation to data modeling, DAX, dashboard design, interactivity, testing, and reporting**.

---

## 📊 Project Overview

Healthcare organizations need clear visibility into patient waiting lists to understand demand, identify trends, monitor specialties, and support operational decision-making.

This dashboard provides an interactive view of patient waiting-list data and enables users to analyze:

* Current patient waiting list
* Historical monthly trends
* Inpatient vs Outpatient waiting lists
* Specialty-level performance
* Age-profile distribution
* Waiting-time bands
* Average and Median waiting lists
* Top specialties by waiting list

**Data Scope:** 2018–2021

---

## 🎯 Business Objectives

The primary objectives of this project are:

1. Track the current status of the patient waiting list.
2. Analyze historical monthly waiting-list trends.
3. Compare Inpatient and Outpatient waiting lists.
4. Analyze waiting lists across medical specialties.
5. Understand patient age-profile distribution.
6. Analyze waiting-time bands.
7. Provide an interactive dashboard for detailed exploration.

---

## 🛠️ Tools & Technologies

| Tool               | Purpose                                 |
| ------------------ | --------------------------------------- |
| Power BI           | Dashboard development & visualization   |
| Power Query        | Data cleaning & transformation          |
| DAX                | KPI and analytical calculations         |
| Excel / CSV        | Source data                             |
| PowerPoint / Canva | Dashboard background & design           |
| GitHub             | Project documentation & version control |

---

## 🔄 Project Workflow

```text
Business Requirements
        ↓
Data Collection
        ↓
Data Cleaning & Transformation
        ↓
Data Modeling
        ↓
DAX Measures
        ↓
Dashboard Design
        ↓
Interactivity & Navigation
        ↓
Testing / UAT
        ↓
Power BI Deployment
        ↓
Refresh & Maintenance
```

---

# 📌 Dashboard Features

## 1️⃣ Executive Summary

The summary page provides a high-level overview of the patient waiting list.

### Key KPIs

* Current Total Wait List
* Average Waiting List
* Median Waiting List
* Previous Year Waiting List

### Interactive Analysis

Users can analyze the data using:

* Date slicers
* Case Type filters
* Specialty filters
* Average / Median toggle
* Interactive charts
* Tooltips
* Navigation buttons

---

## 2️⃣ Detailed Analysis

The detailed page enables users to investigate patient waiting lists at a granular level.

### Dimensions

* Archive Date
* Specialty
* Age Profile
* Time Band
* Case Type

### Metrics

* Total Waiting List
* Average Waiting List
* Median Waiting List

---

## 3️⃣ Tooltip Analysis

A dedicated tooltip page provides additional context when users hover over visualizations.

This improves dashboard usability without overcrowding the main report pages.

---

# 🧹 Data Transformation

Power Query was used to prepare the source data before creating the analytical model.

Key transformation steps include:

* Renaming columns
* Rearranging columns
* Creating missing columns
* Appending Inpatient and Outpatient datasets
* Replacing inconsistent values
* Trimming unnecessary spaces
* Standardizing categories
* Preparing data for modeling

The Inpatient and Outpatient datasets were standardized before being combined into the final analytical dataset.

---

# 🧩 Data Model

The project uses an analytical model connecting the main waiting-list dataset with a specialty mapping table.

```text
              Specialty Mapping
                     │
                     │
                     ▼
                 All_Data
                     │
          ┌──────────┼──────────┐
          │          │          │
     Case Type   Age Profile   Time Band
          │          │          │
          └──────────┼──────────┘
                     │
                Archive Date
```

The specialty mapping table allows specialties to be grouped and analyzed more effectively.

---

# 📐 DAX Measures

### Latest Month Wait List

```DAX
Latest Month Wait List =
CALCULATE(
    SUM(All_Data[Total]),
    All_Data[Archive_Date] = MAX(All_Data[Archive_Date])
) + 0
```

### Previous Year Latest Month Wait List

```DAX
PY Latest Month Wait List =
CALCULATE(
    SUM(All_Data[Total]),
    All_Data[Archive_Date] =
        EDATE(MAX(All_Data[Archive_Date]), -12)
) + 0
```

### Median Wait List

```DAX
Median Wait List =
MEDIAN(All_Data[Total])
```

### Average Wait List

```DAX
Average Wait List =
AVERAGE(All_Data[Total])
```

### Average / Median Dynamic Measure

```DAX
Avg/Med Wait List =
SWITCH(
    VALUES('Calculation Method'[Calc Method]),
    "Average", [Average Wait List],
    "Median", [Median Wait List]
)
```

### Dynamic Dashboard Title

```DAX
Dynamic Title =
SWITCH(
    VALUES('Calculation Method'[Calc Method]),
    "Average",
        "Key Indicators - Patient Wait List (Average)",
    "Median",
        "Key Indicators - Patient Wait List (Median)"
)
```

---

# 📈 Key Insights

The dashboard enables stakeholders to investigate:

* Overall patient waiting-list volume
* Changes in waiting lists over time
* Differences between inpatient and outpatient services
* Specialty-level waiting-list patterns
* Patient age-profile distribution
* Waiting-time categories
* High-volume specialties
* Historical trends

> **Note:** Business conclusions should be drawn from the actual refreshed dataset and dashboard filters rather than assumed from the project structure alone.

---

# 📸 Dashboard Preview

Add your Power BI screenshots here.

### Executive Summary

![Executive Summary](Screenshots/Executive_Summary.png)

### Detailed Analysis

![Detailed Analysis](Screenshots/Detailed_View.png)

### Tooltip Analysis

![Tooltip Analysis](Screenshots/Tooltip_View.png)

---

# 📂 Repository Structure

```text
├── Dashboard
│   ├── Healthcare_Patient_Waiting_List.pbix
│   └── Dashboard_Preview.png
│
├── Data
│   ├── Inpatient
│   ├── Outpatient
│   └── Specialty_Mapping
│
├── Power_Query
│   └── Data_Transformation_Steps.md
│
├── DAX
│   └── Measures.md
│
├── Documentation
│   ├── Business_Requirements.md
│   ├── Data_Dictionary.md
│   └── Dashboard_Guide.md
│
└── Screenshots
    ├── Executive_Summary.png
    ├── Detailed_View.png
    └── Tooltip_View.png
```

---

# 💡 Skills Demonstrated

### Power BI

* Dashboard Development
* Data Modeling
* Interactive Visualization
* Drill-down Analysis
* Tooltips
* Navigation
* Slicers
* KPI Cards

### Power Query

* Data Cleaning
* Data Transformation
* Appending Queries
* Column Standardization
* Data Preparation

### DAX

* CALCULATE
* SUM
* AVERAGE
* MEDIAN
* SWITCH
* EDATE
* Dynamic Measures
* Dynamic Titles

### Analytics

* Healthcare Analytics
* Trend Analysis
* KPI Analysis
* Specialty Analysis
* Operational Reporting

---

# 🚀 End-to-End Development Process

This project follows a structured BI development approach:

**1. Requirement Gathering**
Understand stakeholders, business objectives, KPIs, scope, and reporting requirements.

**2. Data Collection**
Identify and connect to the required source datasets.

**3. Data Transformation**
Clean, standardize, and combine the source data using Power Query.

**4. Data Modeling**
Build relationships and prepare the analytical model.

**5. Visualization Blueprint**
Plan dashboard layout and required visuals.

**6. Dashboard Development**
Create KPIs, charts, slicers, tables, and interactive elements.

**7. Testing**
Validate calculations, filters, visuals, and user interactions.

**8. Deployment**
Publish and share the Power BI solution.

**9. Maintenance**
Establish a routine refresh and monitoring process.

---

# 👨‍💻 Author

**Aditya Kalyan**
Data Analyst | Data Analytics Trainer & Educator

🔗 LinkedIn: https://www.linkedin.com/in/adityaakalyan/

🔗 GitHub: https://github.com/Kalyan4636/

🔗 Portfolio: https://www.datascienceportfol.io/adityakalyanbscc

🔗 Website :  kalyanjha.lovable.app 

---

## ⭐ If you found this project useful

Feel free to **star ⭐ the repository** and explore the other Power BI and Data Analytics projects available on my GitHub.

---




