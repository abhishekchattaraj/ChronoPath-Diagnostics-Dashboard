# 🏥 ChronoPath Diagnostics: Operational Performance & TAT Analysis

![Power BI](https://img.shields.io/badge/Power_BI-F2C811?style=for-the-badge&logo=powerbi&logoColor=black)
![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![Excel](https://img.shields.io/badge/Excel-217346?style=for-the-badge&logo=microsoft-excel&logoColor=white)

## 📊 Project Overview

**ChronoPath Diagnostics** is a comprehensive operational dashboard designed to analyze and optimize the **Turnaround Time (TAT)** for a network of medical diagnostic labs.

Managing patient expectations in healthcare relies heavily on speed and reliability. This project simulates a year of operational data (2025) for 20,000 diagnostic tests across 5 major zonal hubs in India. The dashboard identifies **bottlenecks**, tracks **SLA breaches**, and analyzes **logistical inefficiencies** (e.g., tests sent to the wrong processing center).

### 🎯 Key Objectives
* **Monitor Breach Rates:** Track failure rates against the 24-hour Standard of Service (SLA).
* **Identify Bottlenecks:** Pinpoint exactly *where* time is lost (Logistics vs. Lab Processing vs. Reporting).
* **Analyze Regional Efficiency:** Compare high-performing hubs (Chandigarh) against struggling ones (Kolkata).
* **Root Cause Analysis:** Determine if delays are caused by specific complex test types (e.g., COVID RT-PCR) or logistical routing errors.

---

## 🖼️ Dashboard Showcase

### 1. Welcome Page (Navigation)
*The landing page designed to set context and guide the user.*
<img src="Screenshots/Welcome Page.png" alt="Welcome Page" width="800">
* **Design Strategy:** Features a clean, high-contrast layout with a clear value proposition ("Operational Performance & TAT Analysis").
* **Navigation:** Clear call-to-action buttons allow stakeholders to jump immediately to the **Executive Summary** (High Level) or **Gap Analysis** (Deep Dive).

### 2. Executive Summary
*High-level view for senior stakeholders showing volume trends and regional performance.*
<img src="Screenshots/Executive Summary.png" alt="Executive Summary Dashboard" width="800">
* **Key Insight:** A clear "Monsoon Surge" (Jul-Sep) is visible, where increased test volumes correlate directly with a spike in SLA breaches.
* **Visuals:** KPI Cards, Trend Analysis (Bar & Line Combo), and Regional Performance rankings.
* **Feature:** Includes a "Detailed View" table at the bottom for granular record-level auditing.

### 3. Gap Analysis (Deep Dive)
*Operational drill-down to identify the "Why" behind the delays.*
<img src="Screenshots/Gap Analysis.png" alt="Gap Analysis Dashboard" width="800">
* **The "Quadrant" Logic:**
    * **Top-Left:** Overall status (Completion vs. Cancellation).
    * **Top-Right:** Logistics friction (Misallocated tests).
    * **Bottom-Left:** Process timeline (Stage-wise duration).
    * **Bottom-Right:** Product complexity (TAT by Test Type).
* **Key Insight:** Lab Processing (Stage 2) is the primary bottleneck, driven largely by complex COVID RT-PCR tests and MRI scans.

---

## 🛠️ Technical Architecture

### Data Generation (Python)
Instead of using generic dummy data, I wrote a custom **Python script** (`chromo_fact_table_generation.py`) to simulate realistic operational chaos. The script generates 20,000 records with built-in statistical "stories":
1.  **Seasonality Logic:** Programmed a volume spike in Q3 (Monsoon Season) to simulate viral outbreaks.
2.  **Center Personalities:**
    * *Chandigarh:* High efficiency, low breach rate (~13%).
    * *Kolkata:* Modeled as a logistical bottleneck with a ~25% breach rate.
3.  **Logistics Friction:** Randomly assigned "Actual Centers" different from "Processing Centers" to simulate routing errors, adding a time penalty to Stage 1.
4.  **Test Complexity:** Variable processing times based on test type (e.g., Blood tests are fast; MRIs vary significantly).

### Data Model (Star Schema)
The Power BI model is built on a robust Star Schema:
* **Fact Table:** `Fact_Test_Performance` (20,000 rows)
* **Dimension Tables:**
    * `Dim_Center` (Hub details)
    * `Dim_TestType` (SLA benchmarks, Categories)
    * `Dim_Status` (Workflow states)
    * `Dim_Date` (Standard Date Table)

---

## 🚀 How to Run This Project

### Prerequisites
* **Power BI Desktop** (to view the .pbix file)
* **Python 3.x** (optional, if you want to regenerate data)

### Steps
1.  **Clone the Repo:**
    ```bash
    git clone [https://github.com/yourusername/chronopath-diagnostics-dashboard.git](https://github.com/yourusername/chronopath-diagnostics-dashboard.git)
    ```
2.  **Generate Data (Optional):**
    Run the Python script to create a fresh dataset with new random variations.
    ```bash
    python chromo_fact_table_generation.py
    ```
    *This creates `Fact_Test_Performance_Final_v2.csv`.*
3.  **Open the Dashboard:**
    Double-click `ChronoPath_Dashboard.pbix` to explore the interactive visuals.

---

## 🧠 Design Decisions & "The Why"
* **Lollipop Chart (Page 3):** Chosen over a standard bar chart to reduce visual weight in the bottom-right corner and provide a modern aesthetic while highlighting the outlier data points (COVID tests).
* **Semantic Coloring:** Strictly adhered to a **Navy Blue (Neutral)** and **Coral Red (Alert)** palette. This guides the user's eye immediately to problem areas (Breaches, Delays, Misallocations).
* **Vertical Timeline:** On the Gap Analysis page, the "Stage Duration" chart is oriented horizontally to contrast with the vertical "Test Type" chart, creating a balanced grid layout.

---

## 📬 Contact
**Abhishek Chattaraj**
* [http://www.linkedin.com/in/abhishek-chattarajj]
* [https://www.datascienceportfol.io/abhishekchattarajj]

---
*Note: This project uses synthetic data generated for educational and portfolio purposes.*
