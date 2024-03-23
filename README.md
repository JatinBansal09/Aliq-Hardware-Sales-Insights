
# Aliq Hardware Sales Insight

## Dashboard Link  :  3c83ab9e-c2bb-412a-a9f0-df16c1505c6c/ReportSection0fc1c5fb20738410b6ad?ctid=79c66178-6366-4fe0-a8bf-7a53289cad5d&

## Problem Statement

The Dashboard helps the Sales Director, Bhavin Patel, to get insights into his company, Aliq Hardware. The company supplies computer hardware & manufactures Peripheral items. The sales director couldn't get the proper sales insight as the local sales managers didn't show the complete picture of how the company was working; they built castles in the air because they didn't want to look bad in the company. So, the Dashboard will provide fundamental insights into the sales and help the director make data-driven decisions.

This will help the company improve its sales and be more specific about the decrement/ increment in sales (like a 96% decrease in sales from 2019 to 2020). So, the company can drastically improve its sales using this Dashboard.

### Steps Followed:

- Step 1: Connect the Mysql server with PowerBi by plugging the server and database name into it.

- Step 2: Made a connection with the sales SQL database and added all five tables, e.g., 'sales.customers', 'sales.date', 'sales.markets', 'sales.products', and 'sales.transactions'.

- Step 3: Adjustments needed to be made in the 'Model View' tab. Thus, updated the star relation by creating the 'one to many' link between 'cy_date' column of 'sales.date' table and 'order_date' column of 'sales.transactions' table, and 'markets_code' column of 'sales.markets' table and 'market_code' column of 'sales.transactions' table.

- Step 4: Punch in some queries in the Mysql application. I also checked some discrepancies/ superfluous data via Mysql.

- Step 5: Cleaning the data by using Power Query Editor. E.g., cleaning the table by removing the rows with blank values in 'sales.markets' table, cleaning the 'sales.transactions' table by removing the cells which have 'sale_amount' values as 0 or 1, removing the duplicate values with '[currency] ="USD#(cr)"' and '[currency] ="INR#(cr)"', and converting the 'sales_amount' column with dollar values.

- Step 6: Create a New-Parameter with 'Profit Target' Name, having 'Minimum' value as '-0.05' and a maximum as '0.15' with an increment of '0.01'.

- Step 7: Create 'Base Measures' table and add measures such as with the formulas below:

    (a) 'Sum of Revenue': 'Revenue = SUM('Sales transactions'[norm_sales_amount])'.  
    (b) 'Total Sales Qty': 'Sales Qty = SUM('sales transactions'[sales_qty]).'  
    (c) 'Total Profit Margin': 'Total Profit Margin = SUM('Sales transactions'[Profit_Margin])'.     
    (d) 'Last Year's value of Revenue': 'Revenue LY = CALCULATE([Revenue],SAMEPERIODLASTYEAR('sales date'[date]))'.  
    (e) 'Profit Margin Contribution': 'Profit Margin Contribution %age = DIVIDE([Total Profit Margin], CALCULATE([Total Profit Margin],ALL('sales products'),ALL('sales customers'), ALL('sales markets')))'  
    (f) 'Revenue Contribution': 'Revenue Contribution % = DIVIDE([Revenue],CALCULATE([Revenue],ALL('sales products'), ALL('sales customers'), ALL('sales markets')))'  
    (g) '%age Profit Margin': 'Profit Margin % = DIVIDE([Total Profit Margin],[Revenue],0)'  
    (h) 'Target Diff': 'Target Diff = [Profit Margin %] - 'Profit Target'[Profit Target Value]'

- Step 8: Now, I started creating the Dashboard. It has the following pages:

    1- I created a Dashboard with a 'Key Insights' name having tiles showing:

    (a) 'Revenue' and 'Sales Qty' card.
    (b) Slicers containing 'year' and the second containing 'cy_date' as the field.
    (c) Getting a line chart showing 'Revenue Trend' (e.g., how the revenue changed with the time and date).
    (d) Stacked charts: showing 'Top 5 customers' and 'Top 5 Products' by the revenue, then adding two more stacked charts showing 'Revenue' and 'Sales qty' based on the 'markets_name.'

    2- I created another page named 'Profit Report' that shows major profit distribution. The page contains:

    (a) 'Revenue,' 'Sales qty,' and 'Total Profit Margin' cards.
    (b) Other stacked charts showing 'Profit % by Markets,' 'Revenue Contribution %age by Markets, ' and 'Profit Contribution %age by Markets,'
    (c) Using the same slicers and the 'Revenue Trend' chart
    (d) Finally, add a table containing columns named: 'customer_name,'  'Revenue,' 'Revenue Contribution %age,' 'Profit Margin Contribution %age,' and 'Profit Margin %age.'

    3- I created another page named 'Performance Insights' that shows the major profit distribution. The page containing:

    (a) 'Revenue,' 'Sales qty,' and 'Total Profit Margin' cards.
    (b)  Adding the same slicers.
    (c)  Adding the line and column chart showing the 'Revenue' and 'Revenue Last year' via the columns, and 'Profit Margin %age' as a line.
    (d)  Adding the same table as in the previous page.
    (e)  Stacked column chart: Showing the fields in y-axis space consecutively 'zone,' 'market_name,' 'customer_name,' and 'product_code.'

- Step 9: Now, the Dashboard is ready to use by the sales director of Aliq-Hardwares.

### Inferences that can be drawn from the Dashboard are as follows:

    (a) About revenue via the 'Key Insights' page:
            - 2019: Rs. 52.5 M (For 6 Months)
            - 2020: Rs. 2.06 M (for 6 Months)
        There's a 96% decrement in the revenue over one year.

        So we can gather more insights regarding the director's needs from the first page.


    (b) About Profit via the 'Profit Report' page:
            We can gather insights into various Markets based on 'Profit Contribution %age,' 'Revenue Contribution %age,' and 'Profit %age.' E.g.:

                    - The same of Bhubaneshwar went negative from 'Feb 2020' to 'June 2020':
                        ~ Feb 2020: Profit was 20% of Rs. 278k (Rs. 61,380)
                        ~ June 2020: Profit was -7.58% of Rs. 190k (Rs. 14402)
                    
                    So, this is how we can check the profit margin of various markets.
    
    (c) About Profit target via 'Profit Report' page:
            Create a box for the profit target that takes the target value from the user. And changes the Dashboard accordingly.

        
So, the project will help the sales director to get data insights regularly.