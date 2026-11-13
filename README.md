# HR Employee Attrition Dashboard (Advanced Excel)

An interactive Excel dashboard that analyses employee attrition for 999 employees. It uses an Excel Table, calculated fields, PivotTables, PivotCharts and slicers to show who leaves, and flags a high-risk group of current staff.

**File:** `Advanced_excel_Dashboard.xlsx`

## Key Findings

| Metric | Value |
|---|---|
| Employees | 999 |
| Employees who left | 186 (**18.6% attrition**) |
| Avg monthly income, all employees | $6,616.90 |
| Avg monthly income, leavers vs stayers | $4,901 vs $7,009 |

- **Overtime is the strongest signal.** 33.9% of overtime workers left, against 12.1% of non-overtime workers (about 2.8x).
- **Job role varies widely.** Sales Representative has the highest attrition (40.0%), then Laboratory Technician (31.0%) and Research Scientist (20.5%). Research Director is lowest (5.6%), followed by Manager (7.7%) and Manufacturing Director (8.7%).
- **Age matters.** Under-25s leave most (46.4%), and attrition falls to 9.5% for ages 45-54.
- **High-risk flag works as a screen.** 56 employees are flagged, and 50.0% of them left, against 16.8% of everyone else.

## Workbook Structure

| Sheet | Contents |
|---|---|
| `Data Dictionary` | Definitions for the 40 source and calculated columns |
| `Data` | `EmployeeData` table, 999 rows x 41 columns |
| `Analyze` | Three PivotTables feeding the charts and KPIs |
| `DashBoard` | Two charts and four slicers |

### Calculated fields

| Field | Logic |
|---|---|
| `Attrition_Count_Column` | `=IF(Attrition="Yes", 1, 0)`, so a sum gives leavers and an average gives attrition rate |
| `High_Risk_Flag` | `"High Risk"` if Over Time = Yes **and** Monthly Income < 5,000 **and** Job Satisfaction ≤ 2, otherwise `"Normal"` |
| `CF_age band` | Age grouped into Under 25, 25-34, 35-44, 45-54, Over 55 |
| `CF_attrition label` | Current Employees / Ex-Employees |
| `CF_current Employee` | 1/0 flag for currently employed |

### Dashboard

- **Charts:** *Attrition Rate by Job Role* and *Turnover Rate: Overtime vs. Regular Hours*.
- **Slicers:** Age Band, Department, Over Time, High Risk Flag.
- **Pivot logic:** attrition rate = average of `Attrition_Count_Column`. The overtime split uses "% of row total".

## Skills Demonstrated

Excel Tables and structured data, calculated columns, nested `IF`/`AND` logic, PivotTables with "Show Values As", PivotCharts, slicers, and dashboard layout.

## Usage

1. Open in desktop Excel (slicers need Excel 2013 or later).
2. Use the slicers on `DashBoard` to filter.
3. After editing `Data`, use Data → Refresh All to update the pivots.

## Limitations

- Slicers are connected to the Job Role PivotTable (`PivotTable4`). The overtime chart and the KPI pivot do not respond to them. To fix, use Slicer → Report Connections.
- The `High_Risk_Flag` thresholds (income under 5,000, satisfaction of 2 or less) are hand-set, not fitted to the data. This is a screening rule, not a predictive model.
- Results are descriptive. They show association, not cause.
- The chart title "Attritition Rate" on the job role chart is misspelled; fix before publishing.
- The dictionary describes the dataset as "HR Employee Attrition"; it looks like the public IBM HR sample. If so, credit the source.

**Author:** Faria Hassan, BBA (Finance), North South University
