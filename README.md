# PWC_Diversity_Inclusion

## Objective
The objective of this analysis is to provide actionable insights that will enable the Human Resources department to improve gender balance at the executive management level. This analysis will focus on identifying existing challenges, uncovering trends, and highlighting opportunities to enhance diversity and inclusion within the organization. Specifically, the goals are to:
- **Evaluate Current Gender Distribution:** Analyze the gender composition across all levels of the organization, with a particular focus on executive management, to identify any imbalances.

### Requested KPIs
- hiring
- promotion
- performance
- turnover

## Data Source
The data is given by Pwc Switzerland.

## Tools & Technologies
- **Excel:** For initial data exploration and preparation.
- **Power BI:** To transform data, create interactive dashboards and visualizations

## Process Overview
### 1. Get the Data
- The dataset is obtained from the Pwc Switzerland.

### 2. Explore the Data in Excel, in this stage, the data is being explored, and after closely examining the dataset, the following points were observed:
- **Data Exploration:** Initial exploration of the dataset to understand its structure and identify necessary columns for analysis.
- After exploring the data, it is found that the data is already cleaned, there are many cells that are blank or empty but we can use "Filter" option in Power BI to deal with empty cells.

### 3. Visualize the data in Power BI

Coming on to Visualizations, we have used:
Cards, Clustered Column Chart, Stacked Bar Chart, Line Chart & Gauge and Filters are used to filter data according to departments, time type and Age group.

#### 1. Cards

The cards give a quick insight on total number of employees, number of men & women employees, no of leavers and other useful insights 

#### 2. Clustered Column Chart

This chart gives the visual on number of men and women Job Level after FY20 promotion FY21 promotion

#### 3. Stacked Bar Chart

This chart gives the visual representation of number of hiring and promotion of men and women in FY20 and FY21.

#### 4. Line Chart

It shows the number of leavers from men and women by their Age group.

#### 5. Gauge

It shows the average performance rating of men and women

![Screenshot (235)](https://github.com/user-attachments/assets/d1a287cc-2304-4efc-91cd-f8ceb551f46b)

## DAX Measures

### 1. # of leavers
```sql
# of leavers = CALCULATE(COUNT('Pharma Group AG'[FY20 leaver?]), 'Pharma Group AG'[FY20 leaver?]="Yes")

```

### 2. # men leaver
```sql
# men leaver = CALCULATE(COUNT('Pharma Group AG'[In base group for turnover FY20]), 
'Pharma Group AG'[In base group for turnover FY20]= "Y",
'Pharma Group AG'[FY20 leaver?]="Yes", 'Pharma Group AG'[Gender]="Male")

```

### 3. # women leaver
```sql
# women leaver = CALCULATE(COUNT('Pharma Group AG'[In base group for turnover FY20]),
'Pharma Group AG'[In base group for turnover FY20]= "Y",
'Pharma Group AG'[FY20 leaver?]="Yes", 'Pharma Group AG'[Gender]="Female")

```

### 4. # of men
```sql
# of men = CALCULATE(DISTINCTCOUNT('Pharma Group AG'[Employee ID]), 
 'Pharma Group AG'[Gender]="Male")

```

### 5. # of women
```sql
# of women = CALCULATE(DISTINCTCOUNT('Pharma Group AG'[Employee ID]),
'Pharma Group AG'[Gender]= "Female")
    )

```

### 6. % of emp promoted(FY21)
```sql
% of emp promoted(FY21) = DIVIDE(CALCULATE(COUNT('Pharma Group AG'[Promotion in FY21?]),
'Pharma Group AG'[Promotion in FY21?]= "Yes")
, CALCULATE(COUNT('Pharma Group AG'[Promotion in FY21?])))
)

```

### 7. % of turnover
```sql
% of turnover = DIVIDE(CALCULATE(COUNT('Pharma Group AG'[In base group for turnover FY20]),
'Pharma Group AG'[In base group for turnover FY20]= "Y", 'Pharma Group AG'[FY20 leaver?]="Yes")
, CALCULATE(COUNT('Pharma Group AG'[In base group for turnover FY20])))
)

```

### 8. % of women promoted
```sql
% of women promoted = DIVIDE('Pharma Group AG'[count of women promoted], 'Pharma Group AG'[count of promo in FY21])
)

```

### 9. % of men promoted
```sql
% of men promoted = DIVIDE('Pharma Group AG'[count of men promoted], 'Pharma Group AG'[count of promo in FY21])

```

### 10. Average performance rating men
```sql
Average performance rating men = CALCULATE(AVERAGE('Pharma Group AG'[FY20 Performance Rating]), 
'Pharma Group AG'[Gender]="Male")

```

### 11. Average performance rating women
```sql
Average performance rating women = CALCULATE(AVERAGE('Pharma Group AG'[FY20 Performance Rating]), 
'Pharma Group AG'[Gender]="Female")

```

### 12. % of men hire in FY20
```sql
% of men hire in FY20 = DIVIDE('Pharma Group AG'[count of new hire men], 'Pharma Group AG'[count of new hire in FY20])

```

### 13. % of women hire in FY20
```sql
% of women hire in FY20 = DIVIDE('Pharma Group AG'[count of new hire women], 'Pharma Group AG'[count of new hire in FY20])
```


### 5. Conclusions from the Analysis

Based on the data, here are some insights and findings that can be derived using the visualizations from Power BI:

#### **Executive Management Level:** Number of women at executive level after FY20 and FY21 promotion
- After FY20 promotion, there are 16 employees at this position out of which only 2 are women, rest are men.
- After FY21 promotion, there are 19 employees at this position out of which only 3 are women, rest are men.

#### **Employees Promoted:** 51 employees were promoted in FY 2021 out of 500, in percentage it’s go around 10.20 %.
- Percentage of women promoted are 35% i.e. 18 women promoted out of 51

#### **New Hire (FY20):** 66 new hires:
- 52% are women
- 48% are men

#### **Departments:** 
- **Finance:** Total emp 18, 12 are men 6 are women.
- **HR:** Total emp 17, 5 are men, 12 are women.
- **Internal Services:** Total emp 72, 48 are men and 24 are women.
- **Operations:** Total emp 203, 103 are men and 100 are women.
- **Sales & Marketing:** Total emp 168, 109 are men and 59 are women.
- **Strategy:** Total emp 22, 18 are men and 4 are women.

#### **Leavers:** 47 employees left the company in FY20
- 26 are men
- 21 are women

#### The age group **40-49** has the highest number of leavers, with a count of **12** from the female group.

#### Average performance rating of men is **2.41**

#### Average performance rating of men is **2.42**

