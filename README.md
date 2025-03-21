# Power BI Hospital Emergency Room Dashboard - Project Documentation

This Power BI project presents an Emergency Room Dashboard analyzing patient visits, admission details, wait times, satisfaction scores, and demographic distribution. It provides both Monthly View, Consolidated View, and Patient Details View for deeper analysis.

**1.Data Collection & Import:**
    - **Imported data from Excel Workbook (Hospital ER_Data) using Get Data → Excel workbook option.**
    - **Connected data source and loaded it into Power BI.**

**2.Data Cleaning & Preprocessing:**
Performed data cleaning tasks in Power Query Editor:
- **Removed unwanted columns (if any irrelevant fields existed).**
- **Renamed columns for consistency (like Patient Id, Patient Name, Patient Gender, etc.).**
- **Replaced or filled missing values (e.g., “Declined to Identify” used for missing race data).**
- **Converted data types (like Date columns formatted properly).**
- **Filtered out records with null or inconsistent data (if any).**
- **Ensured proper formatting of numerical fields (Wait Time in minutes, Age as Whole Number, etc.).**

**3.Data Modeling:**
- **Defined relationships within the dataset.**
- **Ensured one-to-many relationships (for example, Patient ID as unique identifier).**
- **No need for complex multiple tables, a single table structure was normalized.**
- **Configured Date hierarchy to allow Year-Month slicing.**
- **Created Calculated Columns:**
    - **Age Group Column: Binned patient ages into ranges (e.g., 0-9, 10-19, etc.).**
    - **Wait Time Category: Categorized patients based on wait time (Within 30 mins / Target Missed).**

**4.DAX Measures & Calculated Columns:**
Used DAX functions for:
- **Average Wait Time:**
  - **Avg_Wait_Time = AVERAGE('Hospital ER_Data'[Patient Waittime])**
- **Patient Satisfaction Score:**
  - **Avg_Satisfaction = AVERAGE('Hospital ER_Data'[Patient Satisfaction])**
- **% Patients Seen Within 30 Mins:**
  - **Seen_Within_30Mins = DIVIDE(**
    - **COUNTROWS(FILTER('Hospital ER_Data', 'Hospital ER_Data'[Patient Waittime] <= 30)),**
    - **COUNTROWS('Hospital ER_Data'),**
    - **0**
    - **)**
- **Gender Distribution, Race Count, Referral Department Count using COUNTROWS and FILTER functions.**
<br>

**5.Data Visualization:**
Created three primary views:

- **Monthly View:**
- **KPIs:**
    - **Total Patients**
    - **Average Wait Time**
    - **Satisfaction Score**
    - **Number of Referrals**
- **Trends:**
    - **Line charts showing daily trends.**
- **Bar Charts:**
    - **Age Group distribution, Department referrals, Gender, Race.**
- **Donut Charts:**
    - **Admission Status, Patients seen within 30 mins.**
- **Heatmap:**
  - **Patients by Day & Hour (identifying peak hours & days).**

**6.Consolidated View:**
- **Similar to Monthly View but covers cumulative data over selected period.**
- **Used Date Slicer to filter date range.**
- **Aggregated numbers (Total Patients: 9216, Wait Time, Satisfaction Score).**

**7.Patient Details View:**
- **Detailed table:**
   - **Patient ID, Name, Gender, Age, Admission Date, Race, Wait Time, Referral Department, Admission Status.**
- **Scrollable, filterable table for granular analysis.**

Dashboard Interaction <a href="https://github.com/Moinkhan123456/Hospital-Analysis/blob/main/Screenshot%20(12).png">View Dashboard of Monthly View</a>
<br>
Dashboard Interaction <a href="https://github.com/Moinkhan123456/Hospital-Analysis/blob/main/Screenshot%20(13).png">View Dashboard of Consolidate View</a>
<br>
Dashboard Interaction <a href="https://github.com/Moinkhan123456/Hospital-Analysis/blob/main/Screenshot%20(14).png">View Dashboard of Patient Details</a>
<br>
Analysis and create a dashboard report.
