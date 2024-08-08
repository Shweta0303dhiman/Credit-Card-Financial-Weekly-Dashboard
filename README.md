# Credit-Card-Financial-Weekly-Status-Dashboard

  ![download](https://github.com/user-attachments/assets/9687b634-7886-440a-acda-ebed9b6d96a8)

## Table of Contents
1. [Project Objective](#project-objective)
2. [Tools Used](#tools-used)
3. [Steps included](#steps-included)
4. [Data Processing & DAX](#data-processing--dax)
5. [Dashboard](#dashboard)
6. [Insights](#dashboard)


## Project Objective
Developed a comprehensive credit card weekly dashboard that provides real-time insights into key performance metrics and trends, enabling stakeholders to monitor and analyze credit card operations effectively.


## Tools Used 
- Microsoft Excel
- PowerBI
- Power Query


### Import Data to PowerBI 
1. Prepare the CSV files
3. Import CSV files into PowerBI tool


## Data Processing & DAX
### DAX Queries

```dax
AgeGroup = SWITCH(
    TRUE(),
    'public cust_detail'[customer_age] < 30, "20-30",
    'public cust_detail'[customer_age] >= 30 && 'public cust_detail'[customer_age] < 40, "30-40",
    'public cust_detail'[customer_age] >= 40 && 'public cust_detail'[customer_age] < 50, "40-50",
    'public cust_detail'[customer_age] >= 50 && 'public cust_detail'[customer_age] < 60, "50-60",
    'public cust_detail'[customer_age] >= 60, "60+",
    "unknown"
)

IncomeGroup = SWITCH(
    TRUE(),
    'public cust_detail'[income] < 35000, "Low",
    'public cust_detail'[income] >= 35000 && 'public cust_detail'[income] <70000, "Med",
    'public cust_detail'[income] >= 70000, "High",
    "unknown"
)

week_num2 = WEEKNUM('public cc_detail'[week_start_date])

Revenue = 'public cc_detail'[annual_fees] + 'public cc_detail'[total_trans_amt] + 'public cc_detail'[interest_earned]

Current_week_Reveneue = CALCULATE(
    SUM('public cc_detail'[Revenue]),
    FILTER(
        ALL('public cc_detail'),
        'public cc_detail'[week_num2] = MAX('public cc_detail'[week_num2])
    )
)

Previous_week_Reveneue = CALCULATE(
    SUM('public cc_detail'[Revenue]),
    FILTER(
        ALL('public cc_detail'),
        'public cc_detail'[week_num2] = MAX('public cc_detail'[week_num2])-1
    )
)
```

## Dashboard

![01](https://github.com/user-attachments/assets/6214f146-fbc3-4173-ac30-e416bff1152b)
![02](https://github.com/user-attachments/assets/8872fd40-8b1e-40f9-9715-3c33496ed243)
![03](https://github.com/user-attachments/assets/294a6fe8-3a2e-4c52-90f2-1ca7314eff94)
## Insights 

1.Customer Analysis -
Revenue by Job Type:
- Businessmen generate the highest revenue at $17.7M, followed by White-collar workers at $10.2M and Self-employed individuals at $8.5M.
- Blue-collar and Government employees also contribute significantly, with revenues of $7M and $8.3M respectively.

Revenue by Income Group:
- High-income groups contribute $28M, medium-income groups $18M, and low-income groups $11M.

Revenue by Age Group:
- The 30-40 age group is the most lucrative, generating $14M. The 40-50 age group follows with $11M, while the 20-30 and 50-60 age groups generate $9M and $6M respectively.

Revenue by Education Level:
- Graduates generate the highest revenue at $23M, followed by high school graduates at $11M. post-graduates and those with unknown education levels contribute $9M and $8M respectively.

Revenue by Marital Status:
- Married customers contribute $27M, while single customers contribute $22M. The revenue from customers with unknown marital status is $4M.

Revenue by State:
- Texas, New York, and California each contribute approximately $13M, followed by Florida with $10M and New Jersey with $4M.

Total revenue:
- Total revenue generated approx. 57M.

2.Transaction Analysis -

Revenue by Expenditure Type:
- Bills generate the highest revenue at $14M, followed by Entertainment ($10M), Fuel ($10M), Grocery ($9M), and Food ($8M).

Revenue by Card Type:
- Blue cards generate $47M, Silver cards $6M, Gold cards $3M, and Platinum cards $1M.

Revenue by Card Use:
- Swipe transactions contribute $36M, chip transactions $17M, and online transactions $4M.

3.Additional Insights -

Delinquency Rates by Job:
- Self-employed individuals have the highest delinquency rate at 25.53%, followed by Businessmen at 18.80% and White-collar workers at 15.19%. Retirees have the 
  lowest delinquency rate at 9.77%.
- Overall Delinquent rate is 6.06%.

Card Activation Percentage:
- 57.46% of transactions are activated within 30 days, with the highest activation for bills (16.76%) and the lowest for travel (4.23%).

Week-on-Week Revenue Changes:
- Revenue shows fluctuations on a weekly basis with notable changes such as a 28.8% increase in week 53 and a 12.8% decrease in week 52.
- Revenue increased by 28.8% in Week 53rd






















