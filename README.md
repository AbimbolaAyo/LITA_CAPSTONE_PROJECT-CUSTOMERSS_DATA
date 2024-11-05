# LITA_CAPSTONE_PROJECT-CUSTOMERS_DATA
Making reference to the Capstone Project Document, carrying out the following exploratory process and tell a compelling story by building an interactive dashboard report to gather insight and making business decisions.

## OUTLINE

[ PROJECT OVERVIEW: ].(project-overview)

[DATA DESCRIPTION:].(data-description)

[DASH BOARD REVIEW:].(dashboard-review)

[STATISTICS ABOUT THE DATASET:].(statistics about the dataset)

[METHODOLOGY:].(methodology)

[DATA ANALYSIS:].(data-analysis)

[DASHBOARD OVERVIEW WITH POWERBI:].(dashboard overview with powerbi)

[INSIGHTS GENERATION:].(insights generation)

[RECOMMENDATION:].(recommendation)

[CONCLUSION:].(conclusion)

## PROJECT OVERVIEW:

Making reference to the data and capstone project document shared earlier, by analyzing the sales performance of a retail store and carrying out the following exploratory process of the sales data to uncover key insights such as

- Average subscription duration
- Most popular subscription types
- Total revenue by subscription type and By telling a compelling story and building an interactive dashboard Power BI report: To gather insight, Highlight findings, And make business decisions.

## DATA DESCRIPTION:

This dataset includes the following Columns:

- CustomerID
- CustomerName
- Region
- SubscriptionType
- SubscriptionStart
- SubscriptionEnd
- Canceled
- Revenue

## DASH BOARD REVIEW:

- Customer Id
- CustomerName
- Region: The other regional branches of the store ( North, South, East West).
- Subscription Type: The type of subscription that was subscribed (Basic, Premium, Standard).
- Subscription Start: The day the subscription started.
- Subscription End: The day the subscription ended.
- Canceled: The cancellation of the subscription.
- Revenue: The income of each subscription.

## STATISTICS ABOUT THE DATA:

- Number of Unique Customers: 33,787
- Subscription Type: 3
- Total Revenue:  67,540,175
- Total Region: 4

## METHODOLOGY:

Data Collection

LITA_ The Incubator Hub provided the dataset for this analysis for learning and training purposes. The data was provided in an Excel sheet [download Here].(https://canvas.instructure.com/files/273182802/download?download_frd=1)
The Excel sheet made it accessible to analyze the Excel sheet The Excel sheet was further converted to CSV format for easy importing of files into:
- SQL to write various queries
- Power BI to create dashboards using various charts (PieChart and clustered Column Chart)

  ## DATA ANALYSIS: 

### Calculation in Excel
- Generating Subscription Duration (=F2-E2)
![SubDuration Customers data](https://github.com/user-attachments/assets/cb245bbf-960c-4190-afc1-dc007447d24c)

- calculating most popular subscription type =SUMIF($D1:$D33788,$D8,$H1:$H33788)
![Excel Customers Data](https://github.com/user-attachments/assets/0638b68d-7a82-489c-a3a8-aaeed6e4c3e9)

- Calculating average subscription duration =AVERAGE(I1:I33788)
![Excel Customers Data](https://github.com/user-attachments/assets/0638b68d-7a82-489c-a3a8-aaeed6e4c3e9)
  
  ## Excel Chart
![Excel Customers Data 3](https://github.com/user-attachments/assets/ea360151-8a49-46a3-92dd-a3843f425ccd)
![Excel Customers Data 2](https://github.com/user-attachments/assets/c47964a4-1161-451a-86de-8d931a4a2ebe)
 
  ## Pivot Table
![Pivot Table foe Customers Data 4](https://github.com/user-attachments/assets/6faeecb7-621b-44a4-9527-f5b68e3f21c7)

## Queries in SQL

``` SQL
  1. select Region, count (CustomerID) as Region_customers from [dbo].[Customer data sec]
     GROUP BY Region
```
```
  2. select subscriptionType, count (CustomerID) as cust_subscription from [dbo].[Customer data sec]
     Group by SubscriptionType
     Order by cust_subscription desc
```
```
  3. SELECT *
     FROM [dbo].[Customer data sec]
     WHERE DATEDIFF(month, SubscriptionStart, SubscriptionEnd) <= 6
```
```
  4. SELECT AVG(DATEDIFF(month, SubscriptionStart, SubscriptionEnd)) AS average_duration
     FROM [dbo].[Customer data sec]
```
```
  5. SELECT customerid, subscriptiontype, SubscriptionStart, SubscriptionEnd
     FROM [dbo].[Customer data sec]
     WHERE DATEDIFF(month, SubscriptionStart, SubscriptionEnd) > 12
```
```
  6. SELECT subscriptiontype, SUM(revenue) AS total_revenue
     FROM [dbo].[Customer data sec]
     GROUP BY subscriptiontype
```
```
  7. SELECT region, COUNT(*) AS canceled_sub
     FROM [dbo].[Customer data sec]
     WHERE canceled = 1
     GROUP BY region
     ORDER BY canceled_sub DESC
  
     SELECT region, COUNT(*) AS canceled_sub
     FROM [dbo].[Customer data sec]
     WHERE canceled = 0
     GROUP BY region
     ORDER BY canceled_sub DESC
```
```
  6.SELECT canceled, COUNT(*) AS total_subscriptions
    FROM [dbo].[Customer data sec]
    GROUP BY canceled
```
