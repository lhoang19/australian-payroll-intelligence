# Payroll Intelligence & Compliance Engine
An End-to-End Analytics Engineering Solution for Australian Payroll Remediation

# Business Problem Statement
In response to the Fair Work Legislation Amendment (Closing Loopholes) Act 2023, this project was developed to identify payroll non-compliance. Effective January 1, 2025, intentional underpayment of staff in Australia carries significant criminal penalties. This solution helps organisations identify "Required Amounts"—including wages, allowances, and leave entitlements—to ensure legal compliance and operational efficiency. The project 

# Data Engineering with MS-SQL
This project generated mock payroll-related datasets for a multi-industry Australian business. The data includes employee details, bonuses, allowances, time off in lieu, and history records, while maintaining data integrity and realistic relationships. To initiate the project, I was provided with 14 raw CSV files (see attachment). Given this volume of CSV files, I adopted the Medallion Architecture Transformation:

- Phase 1: Bronze (The Ingestion Layer): I established the LANDING schema for all 14 tables. At this stage, no transformations were performed; the raw structure, including inconsistent headers and string-based dates, was maintained to ensure a direct audit trail back to the source systems.
  
- Phase 2: Silver (The Integration & Cleansing Layer): I created the STAGING schema as outlined below. In the Silver layer, the 14 raw tables were joined and cleansed to form reliable business entities.

- Phase 3: Gold (The Curated Analytics Layer): The final Gold layer transforms the cleansed Silver data into the star schema depicted in the model. I established the MARTS schema for this purpose.

The detailed description of the Medallion Architecture Transformation is included in the attached SQL files.

# Power BI Integration & Semantic Modeling
Following the Gold-layer transformation in SQL Server, I developed a high-performance semantic model within Power BI to bridge the gap between raw data and executive decision-making.

- For Data Validation & Profiling: I conducted comprehensive data profiling across all fact and dimension tables to ensure referential integrity. This phase was critical for maintaining the high accuracy required for Australian payroll compliance and remediation reporting.


<img width="1909" height="872" alt="Screenshot 2026-04-18 163158" src="https://github.com/user-attachments/assets/0c60de70-0b71-4fa9-90f6-6c8f8ac542ab" />



- For Architectural Design: I implemented a Kimball-standard Star Schema. By establishing optimized one-to-many relationships between transactional facts and descriptive dimensions, I ensured low-latency report performance and robust time-intelligence capabilities.


<img width="947" height="796" alt="Screenshot 2026-04-18 154319" src="https://github.com/user-attachments/assets/9a993306-833c-4543-a874-3f1c57d63190" />

Semantic Model diagram illustrating the Star Schema on fact tables and dimensional tables




- For Visual Analytics: I developed an interactive dashboard suite comprising two specialised views: Payroll Remediation (risk-focused) and Employee Analysis (productivity-focused). To faciliate the interacitve dashboards, I also developed comprehensive DAX calculations in the Measures: Employmnet Count, Mandatory Payment, Overpayment Amount, Paid Amount, Total Allowance, Total Bonus, Total Overpayment, Total Overtime Hours, Total Underpayment, Total Undertime Hours, and Underpayment Amount. These measures acted as Key Performance Indicator (KPI) cards to demonstate overall payroll insights on employment. 

<img width="1266" height="706" alt="Screenshot 2026-04-18 163518" src="https://github.com/user-attachments/assets/eda7955b-986c-409d-8f11-077f2815ee15" />

Payroll Remediation Dashboard


<img width="1247" height="699" alt="Screenshot 2026-04-18 154244" src="https://github.com/user-attachments/assets/138ca8d6-f01a-445a-8887-f67bcb34b3b3" />

Employee Analysis Dashboard


# Strategic Business Insights
1. Governance: Contract & Compliance Alignment
I identified 23.81% of the workforce was associated with "Expired" contracts while maintaining "Active" employment status. This structural misalignment was identified as the primary catalyst for systemic payroll discrepancies. Standardising contract renewal workflows is a prerequisite for long-term compliance under the Closing Loopholes Act.

2.  Operational Risk: Workforce Burnout & Retention: Granular analysis of high-performing individuals (e.g., Andrea Collins) revealed a critical imbalance: 315 hours of overtime accrued against only 38 total leave hours. Reliance on excessive overtime indicates a potential burnout threshold. My analysis would provide leadership with the data needed to initiate proactive mental health interventions and resource-planning adjustments.

3. Financial Recovery: Identifying Operational Leakage. There was a total of $5.39M in overpayments, with significant spikes correlating to peak operational periods (December).The "Paid Amount" frequently deviates from the "Mandatory Payment" logic. By implementing the automated audit framework developed in this project, the organization could reclaim substantial capital and optimise its payroll logic to prevent future leakage.

# Recommendations
Based on the comprehensive analysis on the payroll and employment leave behaviours, I would recommend the further actions to ensure compliance with new payroll requirements: 
- Conducting a deep-dive audit into the "Mandatory Payment" logic for the specific cohorts affected to ensure that all Award-based allowances and superannuation contributions are included in the back-pay calculation.
- Analysing the overpayment spikes to determine if they are caused by incorrect "Public Holiday" multipliers or automated bonus triggers.
- Developing a "Recoupment Policy" for future overpayments that complies with Fair Work regulations regarding deductions.
- Create an automated workflow that notifies Department Heads 30, 60, and 90 days before a contract expires.
- Mandating "Forced Leave" or "TOIL" (Time Off In Lieu) clearing for employees exceeding a specific overtime-to-base-hour ratio to reduce the financial liability of accrued leave and protect employee well-being.
- Building a "What-If" parameter in Power BI that allows leadership to see the financial impact of potential Fair Work Commission annual wage increases (typically announced in June) across the entire workforce before they take effect.


