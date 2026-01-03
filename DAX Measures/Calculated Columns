-- Calculated Column
-- Purpose: Extracts day name from date for day-wise attendance and WFH analysis
Day of the week =
FORMAT('Final Data'[Date], "ddd")


-- Calculated Column
-- Purpose: Assigns weighted value for Sick Leave (1 = SL, 0.5 = HSL)
SL Count =
SWITCH(
    TRUE(),
    'Final Data'[Attendence] = "SL", 1,
    'Final Data'[Attendence] = "HSL", 0.5,
    0
)


-- Calculated Column
-- Purpose: Assigns weighted value for Work From Home (1 = WFH, 0.5 = HWFH)
WFH Count =
SWITCH(
    TRUE(),
    'Final Data'[Attendence] = "WFH", 1,
    'Final Data'[Attendence] = "HWFH", 0.5,
    0
)


-- Measure
-- Purpose: Calculates total present days including office presence and WFH
Present Days =
VAR Presentdays =
    CALCULATE(
        COUNT('Final Data'[Attendence]),
        'Final Data'[Attendence] = "P"
    )
RETURN
Presentdays + [WFH Count]


-- Measure
-- Purpose: Calculates total working days excluding Weekly Offs and Holidays
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


-- Measure
-- Purpose: Calculates overall employee presence percentage
Presence % =
DIVIDE(
    [Present Days],
    [TotalWorkingDays],
    0
)


-- Measure
-- Purpose: Calculates proportion of WFH days out of total present days
WFH % =
DIVIDE(
    [WFH Count],
    [Present Days],
    0
)


-- Measure
-- Purpose: Calculates percentage of sick leave days out of total working days
SL % =
DIVIDE(
    [SL Count],
    [TotalWorkingDays],
    0
)
