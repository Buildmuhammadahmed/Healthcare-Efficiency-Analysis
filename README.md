
#  Healthcare Efficiency Analysis (Power BI)

https://github.com/user-attachments/assets/1e6545cb-2c6d-46a0-b0c8-1895e141c5cb



##  Project Overview
 **Client:** HealthStat (Fictitious Consulting Firm)/n 
 **Domain:** Healthcare Analytics / Hospital Efficiency/n
 **Tool:** Microsoft Power BI/n

This project involves analyzing a dataset of **26,000+ hospital discharges** from New York State to identify efficiency improvements for elective hip replacement surgeries. The goal was to help HealthStat's management understand the drivers of **Length of Stay (LOS)** and **Cost** across 151 hospitals.

##  Business Goals

The primary objective was to evaluate hospital performance based on the **Efficiency** domain of healthcare quality.

* **Identify Outliers:** Which hospitals have historically high costs or lengths of stay?
* **Root Cause Analysis:** What factors (severity, age, disposition) drive these inefficiencies? 
* **Benchmarking:** Compare individual facility performance against the state-wide average.

##  Data Source
The analysis utilizes a comprehensive, anonymized dataset of New York state-wide hospital discharges from the year 2016. The data structure consists of a single flat file containing 30 columns, where each row represents a distinct inpatient stay or discharge.


## Key Insights

Based on the analysis, the following factors were identified as the top influencers increasing LOS and Cost:

1. **Extreme Illness Severity:** Patients with "Extreme" severity significantly increase LOS.
2. **Discharge Disposition:** Patients discharged to **Skilled Nursing Homes** tend to have longer stays compared to those sent home.
3.**Geography:** Hospitals located in **New York City** showed higher average costs.
4.**Mortality Risk:** "Major" or "Extreme" risk of mortality is strongly correlated with higher inefficiencies.

---

## Technical Implementation

## Data Modeling
The data model is structured as a Star Schema to optimize performance and filtering capabilities:
* **Fact Table (hospital_discharges):** Contains the granular, transaction-level data for all 26,000+ discharges. It includes all foreign keys, outcome metrics (Cost, LOS), and descriptive attributes.
* **Dimension Table (surgical_program_volume_summary):** A summary table used to group and segment hospitals based on their surgical volume.
* **Relationships:**
  * **One-to-Many (1:*)** Relationship: Established between surgical_program_volume_summary (One) and hospital_discharges (Many).
  * **Cardinality:** The model ensures that filters applied to the program volume (e.g., "High Volume" vs. "Low Volume" programs) propagate down to the specific discharge records.
* **Measures Table (_Measures):** A dedicated, disconnected table used strictly to house all DAX calculations, keeping the field list clean and organized.

**Model View**
<img width="1112" height="1133" alt="image" src="https://github.com/user-attachments/assets/7f8f41f9-a463-48de-a336-2c2b919fa9bd" />

---
##  Dashboard Structure

The report consists of 4 navigational pages:

**Home:** 
<img width="1793" height="1005" alt="image" src="https://github.com/user-attachments/assets/c425989e-16c9-4fe1-b55a-33ea1e8a6f2c" />

**Hospital Profile:** A deep-dive page allowing stakeholders to drill into a specific facility's performance, contrasting their metrics against the state average using gauge charts.
<img width="1789" height="1007" alt="image" src="https://github.com/user-attachments/assets/6bceaee7-7115-41c2-b1e6-ca19cab7396d" />

**LOS Comparison:** Analysis of Length of Stay drivers, with   **Key Influencers** visual to explain variance.
<img width="1793" height="1007" alt="image" src="https://github.com/user-attachments/assets/9ddc8534-e49f-49e0-b659-8bbfbe4696d6" />

**Cost Comparison:** Analysis of cost with  Scatter plot  to identify expensive/inefficient outliers .
<img width="1792" height="1009" alt="image" src="https://github.com/user-attachments/assets/44d308a9-9aed-4fa4-98eb-928b0452329c" />

## Conclusion

This dashboard enables HealthStat stakeholders to quickly pinpoint inefficient hospitals and understand the "why" behind the data—whether it's driven by patient complexity (severity) or operational processes (discharge planning).
