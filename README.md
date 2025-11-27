# Resource Allocation & Task Management Simulation (Power BI)

## 📌 Overview
This project simulates a realistic PMO / Project Coordinator environment, focusing on **resource planning**, **workload distribution**, and **project task tracking** across multiple concurrent projects.

I created a full end-to-end Power BI dashboard using a 3-sheet dataset (Resources, Projects, Tasks) that mirrors how PMOs manage work allocation, identify overload conditions, and track task progress.

The goal of this project is to demonstrate my ability to:
- Manage resources effectively  
- Track project-level and task-level progress  
- Identify under/over-utilization  
- Build interactive PMO dashboard reports  
- Use DAX and Power Query to build clean reporting models  

---

## 🎯 Key Objectives
- Visualize resource workload and weekly capacity.
- Track task progress (Not Started, In Progress, Completed).
- Identify overloaded resources through a capacity vs demand view.
- Monitor project-level health: progress %, tasks complete, timeline alignment.
- Provide a PMO-style simulation dashboard applicable to real project operations.

---

## 📂 Dataset Structure
The dataset (generated for simulation) contains **resources**, **projects**, and **tasks**.

### **1. Resources**
- Resource_ID  
- Resource_Name  
- Role  
- Department  
- Weekly_Capacity_Hours  

### **2. Projects**
- Project_ID  
- Project_Name  
- Start_Date  
- End_Date  
- Priority  

### **3. Tasks**
- Task_ID  
- Project_ID  
- Assigned_To  
- Start_Date  
- End_Date  
- Planned_Hours  
- Hours_Logged  
- Status (Not Started, In Progress, Completed)

Total size:
- **25 resources**
- **10 projects**
- **200 tasks**

---

## 🖥️ Dashboard Pages

### **Page 1 — Resource Load Overview**
- Total Resources  
- Total Tasks  
- Total Planned Hours  
- Utilization %  
- Department Workload Chart  
- Resource Workload Heatmap  
- Overload Table  

---

### **Page 2 — Project Progress & Task Tracking**
- Task Status KPIs (Completed, In Progress, Not Started)  
- Project Summary Table (progress %, priority, timeline)  
- Gantt-style Task Timeline  
- Task Status Distribution (donut chart)  
- Task Health Table (on-time vs delayed)  

---

### **Page 3 — Resource Capacity & Overload Analysis**
- Total Weekly Capacity  
- Total Planned Hours  
- Capacity Utilization %  
- Resource Overload Indicators  
- Workload Heatmap  
- Department Capacity Analysis Chart  

---

## 🛠️ Tools & Techniques
- **Microsoft Power BI Desktop**
- **Power Query** (data shaping)
- **DAX** (custom measures for KPIs, utilization, overload)
- **Excel** (dataset creation)
- Data modeling using relationships across three tables

---

## 🧮 Example DAX Measures

---DAX
Total Planned Hours = SUM(Tasks[Planned_Hours])

Total Logged Hours = SUM(Tasks[Hours_Logged])

Utilization % =
DIVIDE([Total Logged Hours], [Total Planned Hours], 0)

Completed Tasks =
CALCULATE(COUNTROWS(Tasks), Tasks[Status] = "Completed")

Planned Hours by Resource =
CALCULATE(SUM(Tasks[Planned_Hours]), ALLEXCEPT(Resources, Resources[Resource_ID]))

Overload Hours =
VAR Capacity = SELECTEDVALUE(Resources[Weekly_Capacity_Hours])
VAR Planned = [Planned Hours by Resource]
RETURN IF(Planned > Capacity, Planned - Capacity, 0)---

----

**✨ What This Project Demonstrates**

Understanding of PMO processes

Ability to handle multi-project scheduling

Strong analytical dashboarding skills

Real-world resource capacity planning methods

Professional BI reporting structure

PMO-level insights and practical simulation

-----



