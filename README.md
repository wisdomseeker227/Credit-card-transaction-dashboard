Credit-Card_Weekly_Status_Report(interactive dashboard Creation using Micorsoft power power bi )

## Project Objective

To develop a comprehensive credit card weekly dashboard that provides real-time insights into key performance metrics and trends, 
enabling stakeholders to monitor and analyze credit card operations effectively.

Steps
Load the csv files into power bi

DAX Queries

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

DAX Queries

week_num2 = WEEKNUM('public cc_detail'[week_start_date])

Revenue = 'public cc_detail'[annual_fees] + 'public cc_detail'[total_trans_amt] + 'public cc_detail'[interest_earned]

Current_week_Reveneue = CALCULATE(

SUM('public cc_detail'[Revenue]),

FILTER(

ALL('public cc_detail'),

'public cc_detail'[week_num2] = MAX('public cc_detail'[week_num2])))

Previous_week_Reveneue = CALCULATE(

SUM('public cc_detail'[Revenue]),

FILTER(

ALL('public cc_detail'),

'public cc_detail'[week_num2] = MAX('public cc_detail'[week_num2])-1))

Project Insights--
1.Overall revenue is  55 M

2.Overal Transcation Amount is 45 M

3.AVG customer Satisfaction score is 3.19

4.Total interest is 7.84 M

5.Total transaction count is 656K

6. Age Group between(40-50) contributes highest in the revenue

7.Blue and sliver card are contibuting to the 93% of the overall transactions








