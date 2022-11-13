# Sales-Insights




` select mar.markets_name,x.product_code,cust,order_date,sales_amount,currency,profit_margin_percentage,profit_margin,cost_price as market from (
select tr.*,cu.custmer_name as cust from transactions tr 
	inner join customers cu on tr.customer_code = cu.customer_code) as x
inner join markets mar on x.market_code = mar.markets_code `
