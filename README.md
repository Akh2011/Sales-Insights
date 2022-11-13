# Sales-Insights

## Files
- Sales_data_set.xlsx has five Tables which Contains the data of a Company 
- Combined_data.xlsx has the modified data after sql Operations
- PowerBI sales data.pbix is the Powerbi Dashboard
- Dashboard_screenShots.pdf contains the Screenshots of the PowerBI Dashboard

## Data Analysis Using SQL

1. Doing Basic Operations in Sql

` select * from customers; `

` select count(*) from transactions;`

` select count(*),transactions.currency from transactions group by currency;`

2. Instead of Making Connection b/w tables in PowerBI lets Combine and Take Only the necessary columns needed as Combined_data
```
  select mar.markets_name,x.product_code,cust,order_date,sales_amount,currency,profit_margin_percentage,profit_margin,cost_price as market from
		(select tr.*,cu.custmer_name as cust from transactions tr 
		inner join customers cu on tr.customer_code = cu.customer_code) as x
   inner join markets mar on x.market_code = mar.markets_code; 
```
## Data Analysis using PowerBI

1. Multiplying 75 to the Sales Amount Coulumn whose currency is USD using Conditional Column in Power Query the formula it generates is 
`  Table.AddColumn(#"Promoted Headers", "sales", each if [currency] = "usd" then ([sales_amount] * 75) else [sales_amount]) ` 

2. To Calculate ToTal Profit Margin
`  ToTal Profit Margin = sum([profit_margin])`

3. To Calculate Revenue
`  Revenue = SUM([sales_amount 2]) `

4. To Calculate Total margin % 
`  Total margin % = DIVIDE([ToTal Profit Margin],[Revenue])`

5. To Calculate Revenue Contribution %
`  Revenue Contribution % = DIVIDE([Revenue],CALCULATE([Revenue],ALL(Sheet1)))`

6. To Calculate Profit_contribution %
`  Profit_contribution % = DIVIDE([ToTal Profit Margin],CALCULATE([ToTal Profit Margin],ALL(Sheet1))) `





