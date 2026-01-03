# 👥 HR Analytics: Employee Presence & Strategic Capacity Planning

## 📌 Project Overview
This repository contains an **end-to-end Power BI project** designed to transform raw HR attendance data into **actionable business intelligence**.  
The solution enables HR and leadership teams to move away from manual Excel-based tracking toward a **dynamic, insight-driven system** that monitors employee presence, work-from-home (WFH) preferences, and wellness trends.

The project was developed to support **strategic workforce planning, operational efficiency, and cost optimization** in a hybrid work environment.

---

## 🎯 Business Requirements & Stakeholder Needs
Initiated by the HR Manager and Co-Founder of **:contentReference[oaicite:0]{index=0}**, the project addresses the following objectives:

- 📊 **Presence Monitoring**  
  Calculate weekly and monthly employee presence percentages to support software release and resource planning.

- 🏠 **Working Preference Analysis**  
  Identify trends in WFH usage, especially on specific days such as Mondays and Fridays.

- 🏥 **Wellness Tracking**  
  Monitor sick leave percentages to detect seasonal or localized health patterns and enable preventive actions.

- 💰 **Cost Optimization**  
  Use attendance trends to support a hybrid work model and optimize office space and rental costs.

---

## 🛠️ Tech Stack
- **BI Tool:** Power BI Desktop  
- **Data Source:** Multi-sheet Excel files (real-world randomized data for April, May, and June)  
- **ETL Layer:** Power Query Editor  
- **Data Modeling & KPIs:** DAX (Data Analysis Expressions)  

---

## 🔄 Data Engineering & Transformation (ETL Journey)
The dataset required advanced transformation due to its **non-standard structure**, where dates were stored as column headers.

Key ETL steps included:

- 🔁 **Dynamic Template Creation**  
  A parameterized Power Query function was created so the same transformation logic automatically applies to any new month added to the folder.

- 🔄 **Unpivoting Date Columns**  
  Date headers were unpivoted into a single column, enabling time-series analysis and proper aggregation.

- 🧹 **Automated Data Cleaning**  
  Non-date values such as *Holiday* and *Off* were handled dynamically by attempting type conversion to Date and filtering resulting errors.

- 🔑 **Attendance Code Handling**  
  The dataset included standardized codes:
  - `P` – Present  
  - `WFH` – Work From Home  
  - `SL` – Sick Leave  
  - `WO` – Weekly Off  

---

## 📐 Metrics & DAX Measures
Business KPIs were built using **advanced DAX logic** to quantify workforce behavior.

### Core Calculations:
- **Total Working Days**  
  Calculated by excluding Weekly Offs (WO) and Holidays (HO).

- **Weighted Presence**  
  Custom logic applied using `SWITCH`:
  - 1.0 → Full presence / WFH  
  - 0.5 → Half-day WFH or Sick Leave  

### Key KPIs:
- **Presence %**  
  `(Total Present Days ÷ Total Working Days)`

- **WFH %**  
  `(WFH Count ÷ Total Present Days)`  
  *(Shows WFH preference when employees are working)*

- **Sick Leave %**  
  `(Sick Leave Count ÷ Total Working Days)`

---

## 📊 Dashboard Features & Insights
The dashboard follows a **decision-first design**, placing critical KPIs where leadership attention naturally focuses.

### Key Features:
- 📌 **Executive KPI Cards**  
  Instant view of overall Presence %, WFH %, and Sick Leave %.

- 📈 **Trend Analysis**  
  Line and area charts showing attendance patterns over time, with weekends filtered out for clarity.

- 🔍 **Granular Drill-Down**  
  Interactive employee-level table with a detailed attendance matrix showing daily records.

- 🧠 **Behavioral Insights**  
  - Mondays & Tuesdays show the **highest office presence**
  - Fridays consistently show the **highest WFH preference** (often 15%+)

---

## 🚀 Strategic Impact & Future Scope (MVP)
This project serves as a **Minimum Viable Product (MVP)** with clear potential for enterprise-level expansion.

### Planned Enhancements:
- 📧 **Automated Alerts**  
  Email notifications when presence drops below defined thresholds (e.g., 70%).

- ☁️ **Cloud Integration**  
  Connect to SharePoint or Google Sheets for automatic refreshes.

- 🔐 **Row-Level Security (RLS)**  
  Managers see employee-level data; employees see only aggregated insights.

- 🏢 **Operational Optimization**  
  - Schedule team-building activities on **high-presence days (Mon/Tue)**
  - Plan maintenance on **low-occupancy days (Fridays)**
![Snapshot](https://github.com/anand-analytics/HR-Analytics/blob/main/Snapshot%20of%20Dashboard.png)

