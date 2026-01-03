## Calculated Columns
### Purpose: Extracts day name from date for day-wise attendance and WFH analysis
```DAX
Day of the week =
FORMAT('Final Data'[Date], "ddd")
```



### Purpose: Assigns weighted value for Sick Leave (1 = SL, 0.5 = HSL)
```DAX
SL Count =
SWITCH(
    TRUE(),
    'Final Data'[Attendence] = "SL", 1,
    'Final Data'[Attendence] = "HSL", 0.5,
    0
)
```



### Purpose: Assigns weighted value for Work From Home (1 = WFH, 0.5 = HWFH)
```DAX
WFH Count =
SWITCH(
    TRUE(),
    'Final Data'[Attendence] = "WFH", 1,
    'Final Data'[Attendence] = "HWFH", 0.5,
    0
)
```




