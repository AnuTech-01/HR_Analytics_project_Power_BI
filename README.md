## HR_Employee_Attrition

#### Step 1 — Open Power BI Desktop

#### Step 2  
▪ Load Data
▪ Click Get Data → Text/CSV
▪ Select the downloaded file → click Open
▪ Click Transform Data (not Load)

#### Step 3 
▪ Clean Data in Power Query
▪ Click Add Column → Custom Column
▪ Name it "Age Group" → paste this formula:

--> if [Age] <= 25 then "18-25"
else if [Age] <= 30 then "26-30"
else if [Age] <= 35 then "31-35"
else if [Age] <= 45 then "36-45"
else "45+"

▪ Click OK → Click Close & Apply

#### Step 4 
▪ Create DAX Measures
▪ Right-click table → New Measure → type each formula → press Enter:
▪ Total Employees = COUNT(HR_Analytic[EmployeeNumber])
▪ Attrited = CALCULATE(COUNT(HR_Analytic[Attrition]), HR_Analytic[Attrition]="Yes")
▪ Attrition Rate = DIVIDE([Attrited],[Total Employees])
▪ Avg Income = AVERAGE(HR_Analytic[MonthlyIncome])
▪ Avg Tenure = AVERAGE(HR_Analytic[YearsAtCompany])
▪ Select Attrition Rate measure → Measure tools tab → Format → Percentage

#### Step 5 
▪ Canvas Setup
▪ View → Page view → Actual size
▪ Click blank canvas → Format pane → Canvas settings → Width: 1280, Height: 720
▪ Background color → #FAF9FF

#### Step 6 
▪ Build Header
▪ Insert → Shapes → Rectangle → draw across full top
▪ Fill color → #3C3489 (purple) → Border: Off
▪ Insert → Text box → type "HR Analytics Dashboard" → Size: 20, Bold, White
▪ Another text box → "IBM Employee Dataset · 1,470 records · FY 2024" → Size: 12, Color: #AFA9EC
▪ Right side text box → "16.1%" (Size: 18, Bold, White) + "Attrition Rate" (Size: 11, #AFA9EC)
▪ Select all → right click → Group

#### Step 7 
▪ Add Slicers
▪ Insert Slicer visual → Field: Department
▪ Format pane → Slicer settings → Style → Tile
▪ Buttons → State: Unselected → Background: #EEEDFE, Font: #534AB7
▪ State: Selected → Background: #3C3489, Font: White
▪ Repeat for Gender column

#### Step 8 
▪ 4 KPI Cards
▪ Insert Card visual → Field: Total Employees
▪ Callout value → Size: 28, Color: #26215C, Bold
▪ Background: White, Border: #CECBF6
▪ Copy paste 3 more times → change measures to: Attrited, Avg Income, Avg Tenure
▪ Attrited card value color → #D85A30 (coral red)
▪ Select all 4 cards → Format → Align → Top edges

#### Step 9 
▪ Bar Chart (Attrition by Department)
▪ Insert Clustered bar chart (horizontal)
▪ Y-axis: Department | Values: Attrition Rate
▪ Sales bar color → #D85A30 | HR, R&D bars → #7F77DD
▪ Data labels: On | Gridlines: Off
▪ Background: White, Border: #CECBF6

#### Step 10 
▪ Donut Chart (Gender Split)
▪ Insert Donut chart
▪ Legend: Gender | Values: EmployeeNumber (Count)
▪ Male color → #534AB7 | Female color → #F0997B
▪ Inner radius: 50%
▪ Background: White, Border: #CECBF6

#### Step 11 
▪ Column Chart (Attrition by Age Group)
▪ Insert Clustered column chart (vertical)
▪ X-axis: Age Group | Values: Attrition Rate
▪ 31-35 bar color → #993C1D (darkest — highest attrition)
▪ Other bars → #7F77DD to #AFA9EC
▪ Data labels: On | Gridlines: Off

#### Step 12 
▪ Key Insight Boxes
▪ Insert → Text box → type "Sales dept high risk" → Bold, Size: 13, Color: #712B13
▪ Below type detail text → Size: 11, Color: #993C1D
▪ Background: #FAECE7, Border: #F0997B
▪ Copy → paste → change to R&D insight → Background: #EAF3DE, text color: #27500A

#### Step 13 
▪ Final Alignment
▪ Select charts in a row → Format → Align → Top edges
▪ View → turn OFF Gridlines and Snap to grid
▪ Ctrl+S to save
