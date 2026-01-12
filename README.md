
# FinTech Project Delivery & Performance Dashboard  
**Power BI**

---

## Project Overview

This project analyzes project delivery performance within a FinTech organization managing multiple payment product developments across departments, countries, and experience levels.

The organization struggles with:
- Budget overruns  
- Schedule delays  
- Uneven workforce productivity  
- Delayed milestones  

The goal of this analysis is not just to report these issues, but to understand why they occur and where risks originate.

To achieve this, a three-page Power BI dashboard was designed, each page answering a distinct layer of the business problem:

1. **Overview** – Portfolio-level delivery health  
2. **Operational Efficiency** – Labor utilization, cost, and productivity  
3. **Milestone Performance** – Execution delays, risks, and root causes  

---

## Business Objective

To evaluate how effectively FinTech development projects are planned and executed by:

- Comparing planned vs actual budgets and timelines  
- Measuring employee and departmental efficiency  
- Identifying sources of delivery delays  
- Linking risks and root causes to execution outcomes  
- Surfacing early indicators of delivery failure  

The dashboard serves as a decision-support tool for project managers and stakeholders.

---

## Business Questions Addressed

### Project Delivery
1. How closely do planned budgets and timelines align with actual outcomes?  
2. What is the overall project completion rate?  
3. Which projects or risk categories experience the highest variance?  

### Operational Efficiency
4. Which employees and departments deliver work most efficiently?  
5. How do labor costs vary by experience level?  
6. How are planned and actual hours distributed across projects?  

### Milestone Performance
7. How many milestones are completed, delayed, or in progress?  
8. What is the average milestone delay?  
9. Which risks and root causes contribute most to delays?  

### Predictive Indicators
10. What early signals suggest future project overruns?

---

## Data Sources

### Projects Table
- Project ID, Product Name, Department  
- Planned vs Actual Start & End Dates  
- Planned vs Actual Budgets  
- Risk Level  
- Completion Percentage  

### Milestones Table
- Project ID  
- Milestone Name  
- Planned vs Actual Completion Dates  
- Milestone Status  
- Risk Level and Root Cause  

### Tasks / Hours Table
- Employee Name & Department  
- Project Assignment  
- Planned Hours vs Actual Hours  
- Experience Level  
- Hourly Rate  

---

##  Data Preparation & Modeling

### Data Cleaning
- Standardized date formats  
- Validated numeric fields (budgets, hours, rates)  
- Preserved nulls for ongoing work  
- Standardized status categories  

### Key Measures

**Budget Variance**
```DAX
Budget Variance =
SUM(Projects[Planned Budget]) -
SUM(Projects[Actual Budget])
```

**Schedule Variance**
```DAX
Schedule Variance =
SUM(Tasks[Planned Hours]) -
SUM(Tasks[Actual Hours])
```

**Employee Efficiency**
```DAX
Employee Efficiency =
DIVIDE(
    SUM(Tasks[Planned Hours]),
    SUM(Tasks[Actual Hours])
)
```

**Average Milestone Delay**
```DAX
Avg Milestone Delay =
AVERAGEX(
    Milestones,
    DATEDIFF(
        Milestones[Planned Completion Date],
        Milestones[Actual Completion Date],
        DAY
    )
)
```

### Data Model

- Projects → Milestones (Project ID, one-to-many)
- Projects → Tasks (Project, one-to-many)
- Slicer tables for Country, Risk Level, Status, Experience Level

---

## Dashboard Analysis

1.  **Overview — Project Delivery Health.**

<img width="700" height="385" alt="Image" src="https://github.com/user-attachments/assets/5d1601cc-c2fe-46a0-ae47-bcc8052c8f36" />

---

### Findings

- Most projects show negative budget and schedule variance
- 55% completion rate masks delivery risk
- High-risk projects drive most overruns

### Insights

- Projects are not delivering to plan
- Risk is identified but not actively managed

---

2. **Operational Efficiency — Labor & Cost**

<img width="689" height="383" alt="Image" src="https://github.com/user-attachments/assets/ecc4658a-3f02-4d36-862d-463c2285519c" />

---

### Findings

- Planned hours consistently exceed actual hours
- Employee efficiency varies significantly
- Higher labor cost does not guarantee higher productivity

### Insights

- Inefficiencies stem from planning and task allocation
- Cost alone is not a proxy for performance.

---

3. **Milestone Performance — Delays & Risk**

<img width="691" height="382" alt="Image" src="https://github.com/user-attachments/assets/6fbc5102-7fd9-4d3b-84e0-aaad1fef961a" />

---

### Findings

- 87 out of 288 milestones are delayed
- Average delay is  5 days late
- Regulatory approval and general availability drive most delays
- High-risk milestones experience longer delays

### Insights
- Delays are predictable and risk-linked
- Complex milestones lack adequate buffer

---

## Recommendations

- Use historical delivery data for realistic planning
- Actively monitor high-risk projects
- Allocate work based on efficiency, not seniority alone
- Add buffers for regulatory and dependency-heavy milestones
- Treat early variance as a leading risk indicator

---

## Conclusion

*This Power BI dashboard goes beyond reporting to diagnose why FinTech projects fail.*

By linking planning gaps, labor efficiency, and milestone risk, the analysis delivers actionable insights that improve delivery reliability, cost control, and execution performance across the project lifecycle.
