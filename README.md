# 📊Supply Chain Financial Risk Analysis
A data analytics case study using SQL and Tableau to identify financial revenue at risk and delayed profit due to operational shipping days.
# 🛠️Tech Stack
* Database and Querying: Google BigQuery SQL
* Data visualization & Dashboard: Tableau Public
* Data source: https://www.kaggle.com/datasets/shashwatwork/dataco-smart-supply-chain-for-big-data-analysis
# 📁Repository Structure
* `/queries` - Contains the BigQuery SQL scripts used for data extraction and transformation.
* `/dashboard` - Holds the Tableau workbook and visual exports.
# 💻 BigQuery SQL Code
*Query code used to extract delayed orders, revenue at risk, and lost profit by shipping mode:*
```sql
SELECT
  `Shipping Mode`,
   COUNT (`Order Id`) AS total_orders,
--how many orders are actually late
   SUM(CASE WHEN `Days for shipping _real_` > `Days for shipment _scheduled_` THEN 1 ELSE 0 END) AS delayed_orders,
--total revenues that was delayed
   SUM(CASE WHEN `Days for shipping _real_` > `Days for shipment _scheduled_` THEN sales ELSE 0 END) AS revenue_at_risk,
--the actual lost profit caused by these late orders
   SUM(CASE WHEN `Days for shipping _real_` > `Days for shipment _scheduled_` THEN `Order Profit per Order` ELSE 0 END ) AS delayed_profit,
FROM `finance-project-506111.myfirstdataset.mytable`
GROUP BY
 `Shipping Mode`
ORDER BY
 revenue_at_risk DESC
```
# 📈Tableau Dashboard Solution
*An interactive dashboard was built in Tableau Public to visualize shipping mode performance, delivery days, and financial risk* 
* Live Dashboard: https://public.tableau.com/shared/WW29QPHCN?:display_count=n&:origin=viz_share_link
* Dashboard Preview:
<img width="1200" height="600" alt="image" src="https://github.com/user-attachments/assets/08d1e6e1-0c79-492b-8977-530d09339bce" />
# 📌Project Overview & Business Problem
