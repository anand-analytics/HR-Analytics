# 📐 DAX Measures – HR Analytics: Employee Presence & Capacity Planning

This document contains all **DAX measures** used in the **HR Analytics: Employee Presence & Strategic Capacity Planning** Power BI project.  
Each measure is documented with its **business purpose** and **DAX logic**, making the calculations easy to understand without opening Power BI.

---

## 👥 Presence Metrics

### Present Days
**Purpose:**  
Calculates the total number of days an employee is considered present.  
This includes:
- Full office presence (`P`)
- Work From Home days (`WFH`), as employees are still working.

```DAX
Present Days =
VAR Presentdays =
    CALCULATE(
        COUNT('Final Data'[Attendence]),
        'Final Data'[Attendence] = "P"
    )
RETURN
Presentdays + [WFH Count]
```
### Total Working Days
**Purpose:**  
Calculates the total number of actual working days by excluding:

- Weekly Offs (WO)
- Holidays (HO)

```DAX
TotalWorkingDays =
VAR totaldays =
    COUNT('Final Data'[Attendence])
VAR nonworkdays =
    CALCULATE(
        COUNT('Final Data'[Attendence]),
        'Final Data'[Attendence] IN { "WO", "HO" }
    )
RETURN
totaldays - nonworkdays

```
### Presence %
**Purpose:**  
Measures the overall employee presence rate by comparing present days against total working days.

```DAX
Presence % =
DIVIDE(
    [Present Days],
    [TotalWorkingDays],
    0
)


```
---
##🏠 Work From Home (WFH) Metrics
### WFH Count
**Purpose:**  
Returns the total number of Work From Home days recorded in the dataset.

```DAX
WFH Count =
SUM('Final Data'[WFH Count])


```
### WFH %
**Purpose:**  
Calculates the proportion of WFH days out of total present days.

```DAX
WFH % =
DIVIDE(
    [WFH Count],
    [Present Days],
    0
)


```
---
## 🏥 Wellness & Sick Leave Metrics
### Sick Leave Count
**Purpose:**  
Calculates the total number of sick leave days taken by employees.
Used to monitor wellness trends and potential health risks.

```DAX
SL Count =
SUM('Final Data'[SL Count])


```
### Sick Leave %
**Purpose:**  
Measures the percentage of sick leave days relative to total working days.
Helps HR identify patterns such as seasonal illness or localized outbreaks.

```DAX
SL % =
DIVIDE(
    [SL Count],
    [TotalWorkingDays],
    0
)


```

