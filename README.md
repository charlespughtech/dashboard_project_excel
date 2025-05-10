# Excel Bike Sales Dashboard Project

# dashboard_project_excel

---

Excel dashboard project, cleaning, analysing and visualising bike sales data.

---

## Author

**Charles Pugh**

Google-certified Data Analyst

Email: [charlespughtech@gmail.com](mailto:charlespughtech@gmail.com)

LinkedIn: [https://www.linkedin.com/in/charlespughtech/](https://www.linkedin.com/in/charlespughtech/)

Date: March 10, 2025

---

## Table of Contents

1. [Dataset](#dataset)
2. [Requirements](#requirements)
3. [Project Structure](#project-structure)
4. [Data Cleaning](#data-cleaning)
5. [Data Analysis](#data-analysis)
6. [Data Visualisation](#data-visualisation)
7. [Usage](#usage)
8. [Contact](#contact)

---

## Dataset

The dataset used in this project is included in the `excel_dashboard_project.xlsx` file under the "bike_buyers" sheet. The original dataset can be found at:

- **Source URL**: [https://github.com/AlexTheAnalyst/Excel-Tutorial/blob/main/Excel%20Project%20Dataset.xlsx](https://github.com/AlexTheAnalyst/Excel-Tutorial/blob/main/Excel%20Project%20Dataset.xlsx)

For this project, the data is stored in the "bike_buyers" sheet of `excel_dashboard_project.xlsx`.

---

## Requirements

- Microsoft Excel 2016 or later
- Access to the `excel_dashboard_project.xlsx` file

---

## Project Structure

```bash
dashboard_project_excel/
├── Excel Project Dataset.xlsx     # Original raw dataset
├── excel_dashboard_project.xlsx   # Excel file containing sheets: bike_buyers (original data), working_sheet (data cleaning), pivot_table (analysis), dashboard (visualisation)
└── README.md                      # Project overview and instructions
```

---

## Data Cleaning

The data cleaning process is implemented in the "working_sheet" of `excel_dashboard_project.xlsx`, using data from the "bike_buyers" sheet. Follow these steps to replicate:

- **Copy Data to Working Sheet**:
  - Open `excel_dashboard_project.xlsx` and navigate to the "bike_buyers" sheet.
  - Select all data (Ctrl+A) and copy it.
  - Paste the data into a new sheet named "working_sheet" within the same file.
- **Standardise Column Headers**:
  - In "working_sheet", rename headers for brevity: change `Marital Status` to `M` (Married) or `S` (Single), and `Gender` to `M` (Male) or `F` (Female).
  - Example: In the header row, manually edit cells (e.g., replace “Marital Status” with “M/S”).
- **Check for Duplicate Records**:
  - Select all data in "working_sheet".
  - Go to the “Data” tab, click “Remove Duplicates”, and ensure all columns are checked. Confirm no duplicates are found.
- **Handle Blank and NULL Values**:
  - Use Excel’s filter feature: Click “Data” &gt; “Filter”, then check each column (e.g., `ID`, `Age`, `Purchased Bike`) for blanks or NULLs.
  - Verify no missing values exist, as the dataset is complete.
- **Create Derived Columns**:
  - Add an “Age Bracket” column:
    - Insert a new column named “Age Bracket” (e.g., column M).
    - Use an `IF` formula: `=IF(B2<31,"Youth",IF(B2<=45,"Adult","Senior"))`, assuming `Age` is in column B, to categorise ages into Youth (&lt;31), Adult (31-45), and Senior (&gt;45).
    - Copy the formula down for all rows using the fill handle.
- **Format Fields**:
  - Select the `Income` column and format as currency: Go to Home &gt; Number Format &gt; Currency, choose £ symbol for UK settings.
  - Standardise text fields like `Region` and `Education`:
    - Use Excel’s filter to check for inconsistencies (e.g., “north america” vs. “North America”).
    - Manually correct or use Find and Replace (Ctrl+H) to ensure uniformity (e.g., replace “north america” with “North America”).
- **Add Calculations**:
  - Create a binary flag for `Purchased Bike`:
    - Insert a new column “Purchase Flag” (e.g., column N).
    - Use `=IF(J2="Yes",1,0)` (assuming `Purchased Bike` is in column J) to assign 1 for “Yes” and 0 for “No”.
    - Copy the formula down for all rows.

---

## Data Analysis

Exploratory data analysis is performed in the "pivot_table" sheet of `excel_dashboard_project.xlsx`, using data from "working_sheet". Follow these steps to replicate:

- **Create PivotTables in "pivot_table" sheet**:
  - Select the cleaned data in "working_sheet".
  - Go to Insert &gt; PivotTable, place it in a new sheet named "pivot_table".
  - Create the following PivotTables:
    - **Income by Gender and Purchase Status**:
      - Drag `Gender` to Rows, `Purchased Bike` to Columns, and `Income` to Values (set to Average).
    - **Purchase Count by Commute Distance**:
      - Drag `Commute Distance` to Rows, `Purchased Bike` to Columns, and `ID` to Values (set to Count).
    - **Purchase Count by Age Bracket**:
      - Drag `Age Bracket` to Rows, `Purchased Bike` to Columns, and `Purchase Flag` to Values (set to Sum).
    - **Purchase Count by Region**:
      - Drag `Region` to Rows, `Purchased Bike` to Columns, and `Purchase Flag` to Values (set to Sum).
  - Add a calculated field for purchase rates:
    - In the PivotTable Fields pane, click “Fields, Items & Sets” &gt; “Calculated Field”.
    - Name it “Purchase Rate”, use formula `=Purchase Flag/COUNT(ID)`, and add to Values.
- **Analyse Purchase Trends**:
  - In the `Commute Distance` PivotTable, note higher purchase counts for 0-1 mile commutes.
  - Sort by “Sum of Purchase Flag” (descending) to highlight top categories.
- **Segment by Demographics**:
  - In the `Age Bracket` PivotTable, identify that Adults (31-45) have higher purchase rates.
  - In the `Gender` PivotTable, compare purchase rates for `M` vs. `F`.
- **Examine Additional Factors**:
  - In the `Region` PivotTable, observe North America has the highest purchase volume.
  - In the `Income` PivotTable, note higher average income for customers who purchased bikes.

### Key Insights

- **Commute Distance Impact**: Customers with 0-1 mile commutes had the highest bike purchase rates, suggesting proximity to work drives purchases.
- **Demographic Trends**: Adult males (aged 31-45) with higher incomes were the most likely to purchase bikes, indicating a key demographic for targeting.
- **Regional Patterns**: North America led in bike purchase volume, followed by Europe, reflecting regional market differences.

These insights guide the dashboard’s design to highlight key purchase drivers.

---

## Data Visualisation

The dashboard is built in the "dashboard" sheet of `excel_dashboard_project.xlsx`, using PivotCharts linked to PivotTables in "pivot_table". Follow these steps to replicate:

- **Create PivotCharts in "dashboard" sheet**:
  - **Bar Chart for Income by Gender and Purchase Status**:
    - In the "pivot_table" sheet, select the `Income by Gender` PivotTable.
    - Go to Insert &gt; PivotChart &gt; Bar.
    - Set title to “Average Income by Gender and Purchase Status”.
  - **Column Chart for Commute Distance**:
    - Select the `Commute Distance` PivotTable.
    - Insert a Column PivotChart.
    - Set title to “Purchases by Commute Distance”.
  - **Bar Chart for Age Bracket**:
    - Select the `Age Bracket` PivotTable.
    - Insert a Bar PivotChart.
    - Set title to “Purchases by Age Bracket”.
  - **Bar Chart for Region**:
    - Select the `Region` PivotTable.
    - Insert a Bar PivotChart.
    - Set title to “Purchases by Region”.
- **Organise Dashboard**:
  - Copy each PivotChart from "pivot_table" to the "dashboard" sheet.
  - Arrange charts in a 2x2 grid layout for clarity.
  - Use consistent colours (e.g., blue for “Yes” purchases, orange for “No”) and fonts (e.g., Calibri, size 12).
- **Add Slicers**:
  - In the "dashboard" sheet, go to Insert &gt; Slicer.
  - Add slicers for `Age Bracket`, `Gender`, `Region`, `Commute Distance`, `Marital Status`, and `Education`.
  - Connect each slicer to all PivotCharts:
    - Right-click a slicer, select “Report Connections”, and check all relevant PivotTables.
  - Arrange slicers horizontally above the charts for easy access.
- **Apply Formatting**:
  - For each chart, ensure clear axis labels and legends:
    - Right-click chart elements to format (e.g., set axis titles like “Average Income” or “Purchase Count”).
  - Add a dashboard header: Insert &gt; Text Box, type “Bike Sales Dashboard”, format with bold, size 16, and place at the top.
- **Finalise Dashboard**:
  - Ensure the dashboard fits on one screen with interactive slicers.
  - Test slicers by filtering (e.g., select “North America” in `Region` slicer) to confirm charts update dynamically.

---

## Usage

To explore or replicate the Excel Bike Sales Dashboard Project, follow these steps:

1. **Clone the Repository**:

   ```bash
   git clone https://github.com/charles-pugh-tech/dashboard_project_excel.git
   cd dashboard_project_excel
   ```

2. **Explore the Project**:

   - Open `excel_dashboard_project.xlsx` in Microsoft Excel 2016 or later.
   - The file contains four sheets:
     - **bike_buyers**: Original raw dataset, identical to `Excel Project Dataset.xlsx`.
     - **working_sheet**: Cleaned and prepared data with derived columns and calculations.
     - **pivot_table**: PivotTables analysing purchase trends and demographics.
     - **dashboard**: Interactive dashboard with PivotCharts and slicers.
   - Navigate to the "dashboard" sheet to interact with the dashboard using slicers (e.g., filter by `Gender` or `Region`).
   - Review the "working_sheet" and "pivot_table" sheets to see the data cleaning and analysis steps.

3. **Replicate the Project from Scratch** (Optional):

   - If you want to rebuild the project:
     - Use the provided `Excel Project Dataset.xlsx` in the repository or download it from Excel Dataset.
     - Create a new Excel file named `excel_dashboard_project.xlsx`.
     - Add a sheet named "bike_buyers" and paste the dataset into it.
     - Create additional sheets: "working_sheet", "pivot_table", and "dashboard".
     - Follow the steps in Data Cleaning to prepare data in "working_sheet".
     - Perform analysis as described in Data Analysis in "pivot_table".
     - Build the dashboard as outlined in Data Visualisation in "dashboard".
   - Verify formulas in "working_sheet" (e.g., `IF` for “Age Bracket” or “Purchase Flag”) and PivotTable calculations in "pivot_table".

Results are available in `excel_dashboard_project.xlsx`. Check cells in "working_sheet" and "pivot_table" for formulas and calculations used.

---

## Contact

For inquiries or data analytics services, please contact:

**Charles Pugh**

Google-certified Data Analyst

Email: [charlespughtech@gmail.com](mailto:charlespughtech@gmail.com)

LinkedIn: [https://www.linkedin.com/in/charlespughtech/](https://www.linkedin.com/in/charlespughtech/)
