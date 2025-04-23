# Exploartory-Data-Analysis-on-Kaggle-data


## Table Of Content
---
- [Objective](#objective)
- [Tools](#tools)
- [Data Cleaning](#data-cleaning)
- [Exploratory Data Analysis](#exploratory-data-analysis)
- [Key Analyses Performed](#key-analysis-performed)
- [My Data Analysis Approach](#my-data-analysis-approach)
- [Result And Findings ](#result-and-findings)
- [Key Insights](#key-insights)
- [Ideas for Deeper Analysis](#ideas-for-deeper-analysis)
- [Recommendations](#recommendations)
- [References](#references)



### Objective
 The objective of this analysis is to:

Understand customer behavior and sales patterns in order to uncover what factors truly influence purchases, with the goal of helping the business make data-driven decisions to improve marketing strategies, optimize product offerings, and increase revenue.

### Objective in simpler terms:
It aims to figure out who buys, when they buy, and what really drives them to spend, so the company can focus on what works and drop what doesn’t.

### Data Source: Kaggle

### Tools 
 Microsoft Excel, MySQL, Python and Powerpoint.
 
- Microsoft Excel: To properly view all the data entries and for data cleaning.
     - [Download here](https://microsoft.com)
- MySQL: To write Queries that solve specfic Business problem.
- Python: To visualize qriiten Sql query ( I connected MySql with Python).
- Powerpoint : To Present Insight from Analytics.

### Data Cleaning
In the intial dat presentation phase , i perform the following task
- Data loading and Inspection
- Handling missing values
- Data Cleaning and Formatting
- 

# Exploratory Data Analysis
### Key Questions Answered
1. What is the gender distribution of customers?
→ The customer base is fairly balanced, with a slight male dominance.

2. Which branch has the highest sales performance?
→ Branch A leads in total revenue and transaction volume.

3. Which customer type (Member or Normal) generates higher revenue?
→ Members spend more on average than Normal customers.

4. What is the preferred payment method across genders?
→ Female customers prefer e-wallets, while males lean toward cash.

5. Which product lines are most profitable?
→ The Food and Beverage and Fashion Accessories product lines are top performers.

6. How does customer satisfaction vary by branch and gender?
→ Branch A shows higher customer ratings, with female customers reporting slightly higher satisfaction.

7. Which customer segment is the most loyal and profitable?
→ Loyal customers (repeat buyers) contribute significantly to revenue and rate their experiences more positively.

8. How does customer education level impact loyalty and spending?
→ Customers with higher education (especially Master's degrees) show stronger loyalty and preference for digital payments.

9. Is there a trend in purchase behavior by time, gender, or payment method?
→ Spending patterns vary by time of day and gender, with peak sales often occurring during midday.

### Key Analyses Performed
- Pivot & Unpivot:

Used SQL to pivot data for clearer visualization (e.g., seasonal sales by category).

Discovered how SUM(CASE WHEN...) works for pivoting.

- Sales by Demographics:

- Gender: Male vs. female sales compared.

- Age: Age grouped using quartiles (Q1=31, Median=44, Q3=57).

- Location: Top 10 performing locations by sales.

- Sales by Category & Season:

Clothing, Accessories, Footwear, and Outerwear across Fall, Spring, Summer, and Winter.

Fall is the season with the highest total sales.

- Customer Insights:

Subscription users buy less than non-subscribers.

Discounts, promo codes, and subscriptions do not significantly boost sales.

No correlation found between age and total spending.

Item color has no impact on sales.

- Sales Behavior Patterns:

Frequency of purchases vs. sales amount.

Explored gender, age, and review relationships with sales.

Hat was the top-selling item in Fall, but due to lack of quantity data, can’t confirm if it's due to price or volume.



### My Data Analysis Approach📌

Include the code and features work with
```Python
# Sales-Analysis-With-Kaggle-Data
I did an Explorative data Analysis for a sales data on Kaggle
import pandas as pd
import seaborn as sns
import matplotlib.pyplot as plt
import pymysql
import squarify
import  numpy as np


# Database connection details
config = {
    'host': 'localhost',
    'user': 'root',
    'password': '',
    'database': 'kaggledata'
}
connection = pymysql.connect(**config)
cursor = connection.cursor()
#query = "SELECT sum(Amount), Subs FROM `shopping` GROUP by subs ORDER by sum(Amount) DESC"
#query = "SELECT PaymentMethod, count(PaymentMethod) FROM `shopping` GROUP by PaymentMethod ORDER by count(PaymentMethod) desc"
#query = "SELECT Location, count(Location) FROM `shopping` GROUP by Location order by count(Location) DESC"
#query = "SELECT itemp, count(ItemP) FROM `shopping` GROUP by ItemP order by count(itemp) DESC"
#query = "select Color, count(Color) from `shopping` group by Color order by count(Color) Desc"
#query = "Select Size,count(Size) from `shopping` group by size order by count(Size) Desc"
#query = "SELECT Season,sum(Amount)as sales FROM `shopping` group by Season"
#query = " select Category, sum(Amount) as sales from `shopping` group by category "
#query = "SELECT Season,count(Amount) FROM `shopping` group by Season"
#query = "SELECT ItemP, SUM(Amount)as price FROM `shopping` WHERE Season = 'fall' GROUP by ItemP ORDER by price DESC"
#query ="SELECT Category, SUM(Amount)as price FROM `shopping` WHERE Season = 'fall' GROUP by Category ORDER by price DESC"
#query ="SELECT Category, season, sum(Amount) as SalesPrice FROM `shopping` GROUP by Season,Category"
#query = "SELECT Category, SUM(CASE WHEN Season = 'Spring' THEN Amount ELSE 0 END) AS Spring, SUM(CASE WHEN Season = 'Summer' THEN Amount ELSE 0 END) AS Summer, SUM(CASE WHEN Season = 'Fall' THEN Amount ELSE 0 END) AS Fall, SUM(CASE WHEN Season = 'Winter' THEN Amount ELSE 0 END) AS Winter FROM shopping GROUP BY Category"
#query = "SELECT location,sum(Amount) as sales FROM `shopping` GROUP by Location ORDER by sales DESC" # THIS QUERY IS TO SHOW SALES BY LOCATION
#query = "SELECT Age, SUM(Amount) AS Sales FROM shopping GROUP BY Age ORDER BY Sales DESC limit 10"
#query = "SELECT Gender, sum(Amount) as sales FROM `shopping` GROUP by Gender"
#query = "SELECT Gender, count(Amount) as sales FROM `shopping` GROUP by Gender"
#query = "SELECT Gender, Category, SUM(Amount) AS Sales FROM shopping GROUP BY Gender, Category ORDER BY Gender, Category"
#query = "SELECT itemp,Category, sum(Amount)as sales FROM `shopping`GROUP by Category,ItemP order by sales DESC"
#query = "SELECT CASE WHEN Age BETWEEN 18 AND 30 THEN '18-30' WHEN Age BETWEEN 31 AND 44 THEN '31-44' WHEN Age BETWEEN 45 AND 57 THEN '45-57' WHEN Age BETWEEN 58 AND 70 THEN '58-70' ELSE 'Old' END AS Age_Group, COUNT(Age) AS Total_Age_count FROM shopping GROUP BY CASE WHEN Age BETWEEN 18 AND 30 THEN '18-30' WHEN Age BETWEEN 31 AND 44 THEN '31-44' WHEN Age BETWEEN 45 AND 57 THEN '45-57' WHEN Age BETWEEN 58 AND 70 THEN '58-70' ELSE 'Old' END ORDER BY Age_Group"
#query = "SELECT CASE WHEN Age BETWEEN 18 AND 30 THEN '18-30' WHEN Age BETWEEN 31 AND 44 THEN '31-44' WHEN Age BETWEEN 45 AND 57 THEN '45-57' WHEN Age BETWEEN 58 AND 70 THEN '58-70' ELSE 'Old' END AS AgeGroup, COUNT(Age) AS AgePerGroup FROM shopping GROUP BY CASE WHEN Age BETWEEN 18 AND 30 THEN '18-30' WHEN Age BETWEEN 31 AND 44 THEN '31-44' WHEN Age BETWEEN 45 AND 57 THEN '45-57' WHEN Age BETWEEN 58 AND 70 THEN '58-70' ELSE 'Old' END ORDER BY AgeGroup"
#query = "SELECT CASE WHEN Age BETWEEN 18 AND 30 THEN '18-30' WHEN Age BETWEEN 31 AND 44 THEN '31-44' WHEN Age BETWEEN 45 AND 57 THEN '45-57' WHEN Age BETWEEN 58 AND 70 THEN '58-70' ELSE 'Old' END AS Age_Group, SUM(CASE WHEN Season = 'Spring' THEN Amount ELSE 0 END) AS Spring_Sales, SUM(CASE WHEN Season = 'Summer' THEN Amount ELSE 0 END) AS Summer_Sales, SUM(CASE WHEN Season = 'Fall' THEN Amount ELSE 0 END) AS Fall_Sales, SUM(CASE WHEN Season = 'Winter' THEN Amount ELSE 0 END) AS Winter_Sales FROM shopping GROUP BY CASE WHEN Age BETWEEN 18 AND 30 THEN '18-30' WHEN Age BETWEEN 31 AND 44 THEN '31-44' WHEN Age BETWEEN 45 AND 57 THEN '45-57' WHEN Age BETWEEN 58 AND 70 THEN '58-70' ELSE 'Old' END ORDER BY Age_Group"
#this is to have the items that sold best in fall, since Fall has the best sales
#query = "SELECT ItemP ,sum(Amount)as sales FROM `shopping` WHERE Season = 'fall' GROUP by ItemP ORDER by sales DESC"
#begining
# ## Write your SQL query (This is to show the data frame of an SQL data)
# query = "select * from `shopping`"
# # Load data into a Pandas DataFrame
# df = pd.read_sql(query, connection)
# # Close the connection
# connection.close()
# print(df.head())
#end
cursor.execute(query)
# Fetch all rows from the result
results = cursor.fetchall() #you can fetch one, fetchtwo or fetch all (all will show all result, one will show just one,...
#print(results)
# for row in results: #(this is to make the result look neat, and show each information per row)
    # print (row)
df = pd.DataFrame(results, columns = ['sum(Amount)','Subs'])
#df = pd.DataFrame(results,columns = ['Season','sales']) #when i was calculating fall only
#df = pd.DataFrame(results,columns = ['Category','Season','Price']) #dis is for season, category and price
#df = pd.DataFrame(results,columns = ['Category','Spring','Summer','Fall','Winter']) #DAtaframe after pivoting the data in SQL
#df = pd.DataFrame(results, columns = ['location','sales'])
#df = pd.DataFrame(results, columns = ['Age','sales'])
#df = pd.DataFrame(results, columns = ['Gender','sales'])
#df = pd.DataFrame(results,columns = ['Gender','Category','sales'])
#df = pd.DataFrame(results,columns = ['ItemP', 'Category', 'sales'])
#df = pd.DataFrame(results,columns=['AgeGroup','TotalAgecount'])
#df = pd.DataFrame(results, columns=['Age_Group','Spring_Sales','Summer_Sales','Winter_Sales','Fall_Sales'])
#df = pd.DataFrame(results, columns = ['ItemP','sales'])
#df = pd.DataFrame(results, columns = ['Category', 'sales'])
#df = pd. DataFrame(results, columns = ['Size','count(Size)'])
#df = pd. DataFrame (results, columns = ['Color' , 'count(Color)'])
#df = pd. DataFrame (results, columns = ['Itemp', 'count(Itemp)'])
#df = pd. DataFrame (results,columns = ['Location','count(Location)'])
#df = pd.DataFrame(results, columns = ['PaymentMethod','count(PaymentMethod)'])
print(df) #Dataframe is print the data as an excel table
## #BAR GRAPH OF SALES AND SUCCRIPTION
# #Bar chart for sum(Amount)  by Subscrition
# plt.figure(figsize=(6, 4))
# SubscriptionCategory= {
#     "Yes": "navy",
#     "No": "royalblue"
# }
# # # Assign colors based on the category
# colors = [SubscriptionCategory[cat] for cat in df['Subs']]
# plt.bar(df['Subs'], df['sum(Amount)'], color=colors, alpha= 0.7)
# plt.title('Sales By Subscription Status')
# plt.xlabel('Subs')
# plt.ylabel('count(Amount)')
# plt.xticks(rotation=45)  # Rotate x-axis labels for better readability
# # plt.grid(True) # this will add graph background to the graph, you can remove it to make your graph look plain or change the true in front of it to False
# plt.show()
#
#
#GRAPH OF PAYMENT METHOD AND TOTAL COUNT OF SALES TRANSACTION FOR EACH
# sorted_df = df.sort_values(by='count(PaymentMethod)', ascending=False)
# # #
# #
# # # Get the sorted item names and sales values
# sorted_items = sorted_df['PaymentMethod'].tolist()
# sorted_sales = sorted_df['count(PaymentMethod)'].tolist()
#
# # Create a horizontal bar chart
# plt.figure(figsize=(6, 6))  # Set figure size
# bars = plt.barh(sorted_items, sorted_sales, color='royalblue')
# plt.xlabel('Payment', fontsize=12)
# plt.ylabel('count(PaymentMethod)', fontsize=12)
# plt.title('Total Count of Sales by Payment Method', fontsize=14)
# # Display sales values next to the bars
# for bar, value in zip(bars, sorted_sales):
#     # Add text to the right of each bar
#     plt.text(value + 50, bar.get_y() + bar.get_height() / 2, f'{value}', va='center', fontsize=10)
#
# # Invert the y-axis to show the items with the highest sales at the top
# plt.gca().invert_yaxis()
#
# # Adjust layout to ensure everything fits
# plt.tight_layout()
#
# # Save the chart as an image
# plt.savefig('Total Count ofSales By Payment Method', dpi=300)
# plt.show()
#
#
#
#GRAPH OF COUNT OF SALES BY LOCATION
#sorted_df = df.sort_values(by='count(Location)', ascending=False)
# #
# # # Get the sorted item names and sales values
# sorted_items = sorted_df['Location'].tolist()
# sorted_sales = sorted_df['count(Location)'].tolist()
#
# # Create a horizontal bar chart
# plt.figure(figsize=(8, 6))  # Set figure size
# bars = plt.barh(sorted_items, sorted_sales, color='royalblue')
# plt.xlabel('Location', fontsize=12)
# plt.ylabel('count(Location)', fontsize=12)
# plt.title('Total Count of Purchased in each location', fontsize=14)
# # Display sales values next to the bars
# for bar, value in zip(bars, sorted_sales):
#     # Add text to the right of each bar
#     plt.text(value + 50, bar.get_y() + bar.get_height() / 2, f'{value}', va='center', fontsize=10)
#
# # Invert the y-axis to show the items with the highest sales at the top
# plt.gca().invert_yaxis()
#
# # Adjust layout to ensure everything fits
# plt.tight_layout()
#
# # Save the chart as an image
# plt.savefig('Total Count of Each Location', dpi=300)
# plt.show()
#
#GRAPH FOR ITEMS PURCHASED AND COUNT OF ITEM
# sorted_df = df.sort_values(by='count(Itemp)', ascending=False)
# # #
# # # Get the sorted item names and sales values
# sorted_items = sorted_df['Itemp'].tolist()
# sorted_sales = sorted_df['count(Itemp)'].tolist()
#
# # Create a horizontal bar chart
# plt.figure(figsize=(6, 6))  # Set figure size
# bars = plt.barh(sorted_items, sorted_sales, color='royalblue')
# plt.xlabel('Item Purchased', fontsize=12)
# plt.ylabel('count(Item Purchased)', fontsize=12)
# plt.title('Total Count of Each Item Purchased', fontsize=14)
# # Display sales values next to the bars
# for bar, value in zip(bars, sorted_sales):
#     # Add text to the right of each bar
#     plt.text(value + 50, bar.get_y() + bar.get_height() / 2, f'{value}', va='center', fontsize=10)
#
# # Invert the y-axis to show the items with the highest sales at the top

# plt.gca().invert_yaxis()
#
# # Adjust layout to ensure everything fits
# plt.tight_layout()
#
# # Save the chart as an image
# plt.savefig('Total Count of Each Colors', dpi=300)
# plt.show()
#
#
#
## #HORISONTAL GRAPH FOR COLOR  and COUNT(COLOR)
# # # Assuming 'df' is your DataFrame with 'ItemP', 'Category', and 'sales' columns
# # # Sort the data by 'sales' in descending order
# sorted_df = df.sort_values(by='count(Color)', ascending=False)
# #
# # # Get the sorted item names and sales values
# sorted_items = sorted_df['Color'].tolist()
# sorted_sales = sorted_df['count(Color)'].tolist()
#
# # Create a horizontal bar chart
# plt.figure(figsize=(6, 6))  # Set figure size
# bars = plt.barh(sorted_items, sorted_sales, color='skyblue')
# plt.xlabel('Color', fontsize=12)
# plt.ylabel('count(Color)', fontsize=12)
# plt.title('Total Count of Each Colors', fontsize=14)
# # Display sales values next to the bars
# for bar, value in zip(bars, sorted_sales):
#     # Add text to the right of each bar
#     plt.text(value + 50, bar.get_y() + bar.get_height() / 2, f'{value}', va='center', fontsize=10)
#
# # Invert the y-axis to show the items with the highest sales at the top
# plt.gca().invert_yaxis()
#
# # Adjust layout to ensure everything fits
# plt.tight_layout()
#
# # Save the chart as an image
# plt.savefig('Total Count of Each Colors', dpi=300)
# plt.show()
#
#
#
#
#Bar chart for size of goods  by total count
# plt.figure(figsize=(6, 4))
# category_colors = {
#     "M": "Gray",
#     "L": "navy",
#     "S": "skyblue",
#     "XL": "royalblue"
# }
# # # Assign colors based on the category
# colors = [category_colors[cat] for cat in df['Size']]
# plt.bar(df['Size'], df['count(Size)'], color=colors, alpha= 0.7)
# plt.title('Total Number of items sold per size')
# plt.xlabel('Size')
# plt.ylabel('count(Size)')
# plt.xticks(rotation=45)  # Rotate x-axis labels for better readability
# # plt.grid(True) # this will add graph background to the graph, you can remove it to make your graph look plain or change the true in front of it to False
# plt.show()
#Plot a pie chart using the DataFrame
#pie chart
# plt.figure(figsize=(8, 8))
# plt.pie(df['Price'], labels=df['Season'], autopct='%1.1f%%', startangle=90, colors=['#ff9999','#66b3ff','#99ff99','#ffcc99'])
# plt.title('Price Distribution by Season')
# plt.axis('equal')  # Equal aspect ratio ensures that pie is drawn as a circle.
# plt.show()
#
#line Graph (this isnt doing justisce to the analysis)/ i
# #
# plt.figure(figsize=(10, 6))
# plt.plot(df['Season'], df['Price'], marker='o', linestyle='--', color='b')
# plt.title('Total Price by Item for the Seasons in the year')
# plt.xlabel('Season')
# plt.ylabel('Total Price')
# plt.xticks(rotation=45)  # Rotate x-axis labels for better readability
# # plt.grid(True) # this will add graph background to the graph, you can remove it to make your graph look plain or change the true in front of it to False
# plt.show()
#Bar chart for sales by season
# plt.figure(figsize=(6, 4))
# category_colors = {
#     "Fall": "Gray",
#     "Spring": "navy",
#     "Summer": "skyblue",
#     "Winter": "royalblue"
# }
# # # Assign colors based on the category
# colors = [category_colors[cat] for cat in df['Season']]
# plt.bar(df['Season'], df['sales'], color=colors, alpha= 0.7)
# plt.title('Total Price season for sales')
# plt.xlabel('Season')
# plt.ylabel('sales')
# plt.xticks(rotation=45)  # Rotate x-axis labels for better readability
# # plt.grid(True) # this will add graph background to the graph, you can remove it to make your graph look plain or change the true in front of it to False
# plt.show()
#
#
#Bar Graph for Season and Price
# plt.figure(figsize=(10, 6))
# plt.bar(df['Season'], df['Price'], color='b', alpha=0.7)
# plt.title('Total Price by Item for the Seasons in the Year')
# plt.xlabel('Season')
# plt.ylabel('Total Price')
# plt.xticks(rotation=45)  # Rotate x-axis labels for better readability
# # plt.grid(True) # Uncomment to add a grid background
# plt.show()
#
#
# #Bar Graph for category and sales
# plt.figure(figsize=(10, 6))
# category_colors = {
#     "Accessories": "royalblue",
#     "Clothing": "navy",
#     "Footwear": "skyblue",
#     "Outerwear": "Gray"
# }
# # Assign colors based on the category
# colors = [category_colors[cat] for cat in df['Category']]
# plt.bar(df['Category'], df['sales'], color=colors, alpha=0.7)
# plt.title('Total sales by Item for each Category')
# plt.xlabel('Season')
# plt.ylabel('Total Price')
# plt.xticks(rotation=45)  # Rotate x-axis labels for better readability
# # plt.grid(True) # Uncomment to add a grid background
# plt.show()
#
#
#line graph for list of items sold in fall and their prices
#line graph before pivoting in SQL
# Pivot the DataFrame to get the appropriate format for plotting multiple series
# pivot_df = df.pivot(index='Category', columns='Season', values='Price')  # Pivoting DataFrame
# # Plot the line graph
# plt.figure(figsize=(10, 6))
# for season in pivot_df.columns:  # Iterate through each season column
#     plt.plot(pivot_df.index, pivot_df[season], marker='o', label=season)# Plot each season as a series
# plt.title('Total Price by Category and Season')
# plt.xlabel('Season')
# plt.ylabel('Total Price')
# plt.xticks(rotation=45)  # Rotate x-axis labels for better readability
# plt.legend(title="Seasons") # this is what made the label of each line graph to show. i mean what is call series in excel
# #plt.grid(True)  # Add grid for better visualization
# plt.show()
#
#
#line graph
#Line Graph after pivoting in SQL
# # Plot the line graph (Method 1)
# plt.figure(figsize=(10, 6))
# # Plot each season as a separate line
# plt.plot(df['Category'], df['Spring'], marker='o', linestyle='-', label='Spring')
# plt.plot(df['Category'], df['Summer'], marker='o', linestyle='-', label='Summer')
# plt.plot(df['Category'], df['Fall'], marker='o', linestyle='-', label='Fall')
# plt.plot(df['Category'], df['Winter'], marker='o', linestyle='-', label='Winter')
# # Adding titles and labels
# plt.title('Sales Data by Season and Category')
# plt.xlabel('Category')
# plt.ylabel('Amount')
# # Add the legend to the plot
# plt.legend(title='Seasons')
# # Display the plot
# plt.show()
#
#
#line graph after pivot method 2
#simplifying method 1
# Plot the line graph
# plt.figure(figsize=(10, 6))
# #Loop over the season columns and plot them
# for season in ['Spring', 'Summer', 'Fall', 'Winter']:
#     plt.plot(df['Category'], df[season], marker='o', linestyle='-', label=season)
# # Adding titles and labels
# plt.title('Sales Data by Season and Category')
# plt.xlabel('Category')
# plt.ylabel('Amount')
# # Display the legend
# plt.legend(title='Seasons')
# Show the plot
#plt.show()
#
#
#
#LOCATION AND SALES
#for location and sales plot (Dayo's idea)
# Assuming 'df' is your DataFrame with 'location' and 'sales' columns
# # Sort the data by 'sales' in descending order
# sorted_df = df.sort_values(by='sales', ascending=False)
# # Get the sorted locations and sales values
# sorted_location = sorted_df['location'].tolist()
# sorted_sales = sorted_df['sales'].tolist()
# #Create horizontal bar chart with larger figure height for more space
# plt.figure(figsize=(12, 14))  # Increased height for more space between bars
# bars = plt.barh(sorted_location, sorted_sales, color='skyblue')
# plt.xlabel('Sales', fontsize=12)
# plt.ylabel('Location', fontsize=12)
# plt.title('Horizontal Bar Chart for Sales by Location', fontsize=14)
# plt.show()
# # Display values next to the bars
# for bar, value in zip(bars, sorted_sales):  # Use sorted_sales
#     # Ensure value is treated as a number and add 50 for text position
#     plt.text(value + 50, bar.get_y() + bar.get_height() / 2,  # Position text next to the bar
#              f'{int(value)}', va='center', fontsize=10)  # Convert value to integer and then string
# # Invert the y-axis to show bars in descending order
# plt.gca().invert_yaxis()
# # Adjust layout to ensure that labels fit
# plt.tight_layout()
# # Save the chart as an image
# plt.savefig('Sales_by_location.png', dpi=300)
# # plt.show()
# print("Chart saved as 'Sales_by_location.png'.")

#CHART OF AGE AND SALES
## Scatter Plot
# plt.figure(figsize=(10, 6))
# plt.scatter(df['Age'], df['sales'], color='b')
# plt.title('Total Sales by Age of Customer')
# plt.xlabel('Age')
# plt.ylabel('Total Sales')
# plt.xticks(rotation=45)  # Rotate x-axis labels for better readability
# # plt.grid(True)  # Uncomment if you want to add gridlines
# plt.show()
#piechart of Gender and sales
#pie chart
# Group data by Gender and sum sales
#grouped_data = df.groupby('Gender')['sales'].sum()
# Plot pie chart
# plt.pie(grouped_data, labels=grouped_data.index, autopct='%1.1f%%',
#         startangle=90, colors=['#ff8999', '#67b3ff'])
# plt.title('Sales Distribution by Gender')
# plt.legend()
# plt.show()
#
#
#
#Bar Chart for Gender & Sales
# plt.figure(figsize=(6, 6))
# plt.bar(df['Gender'], df['sales'], color='b', alpha= 0.7)
# plt.title('Total Price by Gender for the sales')
# plt.xlabel('Gender')
# plt.ylabel('sales')
# plt.xticks(rotation=45)  # Rotate x-axis labels for better readability
# # plt.grid(True) # this will add graph background to the graph, you can remove it to make your graph look plain or change the true in front of it to False
# plt.show()
#
#Bar Chart of count of sales by Gender
# plt.figure(figsize=(10, 6))
# plt.bar(df['Gender'], df['sales'], color='b', alpha= 0.7)
# plt.title('Total Count of Items by Gender')
# plt.xlabel('Gender')
# plt.ylabel('CountOfSales')
# plt.xticks(rotation=45)  # Rotate x-axis labels for better readability
# # plt.grid(True) # this will add graph background to the graph, you can remove it to make your graph look plain or change the true in front of it to False
# plt.show()
#
#
# ## Plot the line
# #Plotting line graph for gender,category and sales while
# plt.figure(figsize=(10, 6))
# # Pivot the data so that 'Category' becomes rows and 'Gender' becomes columns
# df_pivot = df.pivot(index='Category', columns='Gender', values='sales')
# # Plot the data
# plt.figure(figsize=(10, 6))
# # Loop over the columns (Male, Female) and plot the respective data
# for gender in df_pivot.columns:
#     plt.plot(df_pivot.index, df_pivot[gender], marker='o', linestyle='-', label=gender)
# # Adding titles and labels
# plt.title('Sales Distribution by Category & Gender')
# plt.xlabel('Category')  # Category is now on the x-axis
# plt.ylabel('Sales')  # Sales is now on the y-axis
# # Display the legend
# plt.legend(title='Gender')
# # Show the plot
# plt.show()
#
#
#bdvjsv
# #GRAPH FOR ITEMP  and SALES (dayo's idea final one)
# # # Assuming 'df' is your DataFrame with 'ItemP', 'Category', and 'sales' columns
# # # Sort the data by 'sales' in descending order
# sorted_df = df.sort_values(by='sales', ascending=False)
#
# # Get the sorted item names and sales values
# sorted_items = sorted_df['ItemP'].tolist()
# sorted_sales = sorted_df['sales'].tolist()
#
# # Create a horizontal bar chart
# plt.figure(figsize=(10, 8))  # Set figure size
# bars = plt.barh(sorted_items, sorted_sales, color='skyblue')
# plt.xlabel('Sales', fontsize=12)
# plt.ylabel('Item', fontsize=12)
# plt.title('Sales by Item', fontsize=14)
# # Display sales values next to the bars
# for bar, value in zip(bars, sorted_sales):
#     # Add text to the right of each bar
#     plt.text(value + 50, bar.get_y() + bar.get_height() / 2, f'{value}', va='center', fontsize=10)
#
# # Invert the y-axis to show the items with the highest sales at the top
# plt.gca().invert_yaxis()
#
# # Adjust layout to ensure everything fits
# plt.tight_layout()
#
# # Save the chart as an image
# plt.savefig('Sales_by_Item.png', dpi=300)
# plt.show()
# #
# # #print("Chart saved as 'Sales_by_Item.png'.")
# #
#
#
#SALES BY ITEMP AND CATEGORY
# Ensure your DataFrame has the necessary columns
# df should have columns: 'ItemP', 'Category', and 'Sales'
# Sort the DataFrame by sales for better visualization
# Convert the 'sales' column to float
# sizes = df["sales"].astype(float)
# labels = [f"{item}\n{sales}" for item, sales in zip(df["ItemP"], df["sales"])]
#
# # Plot the treemap
# plt.figure(figsize=(12, 8))
# squarify.plot(sizes=sizes, label=labels, alpha=0.8, color=plt.cm.tab20.colors)
# plt.title("Sales Treemap")
# plt.axis("off")
# plt.tight_layout()
# plt.show()
#
#import seaborn as sns
# #Grouped Bar Chart (Category-based) - I KIND OF LIKE THIS GRAPH
# # Grouped bar chart
# plt.figure(figsize=(12, 8))
# sns.barplot(x="sales", y="ItemP", hue="Category", data=df, palette="pastel")
# plt.xlabel("Sales")
# plt.ylabel("Items")
# plt.title("Sales of Items by Category")
# plt.legend(title="Category", bbox_to_anchor=(1.05, 1), loc="upper left")
# plt.tight_layout()
# plt.show()
##
##
##THE SAME GRAPH BUT I WANT IT TO SHOW THE VALUE OF EACH ITEMS
# Grouped bar chart #GROUPED BAR CHART FOR SALES OF ITEMS BY CATEGORY
# plt.figure(figsize=(12, 8))
# sns.barplot(x="sales", y="ItemP", hue="Category", data=df, palette="pastel")
#
# # Add labels (text) to each bar
# for container in plt.gca().containers:
#     for bar in container:
#         # Get the bar's width (sales value) and y-position
#         width = bar.get_width()
#         y = bar.get_y() + bar.get_height() / 2
#
#         # Add text slightly to the right of the bar
#         plt.text(width + 50, y, f'{int(width)}', va='center', fontsize=10)
#
# # Set labels and title
# plt.xlabel("Sales")
# plt.ylabel("Items")
# plt.title("Sales of Items by Category")
# plt.legend(title="Category", bbox_to_anchor=(1.05, 1), loc="upper left")
#
# # Adjust layout and display
# plt.tight_layout()
# plt.show()
#
##Grouped bar chart with reduced size(THIS IS THE SAME WITH WHAT I HAVE ABOVE, JUST REDUCTION IN SIZE)
# plt.figure(figsize=(8, 6))  # Adjust the size here (width=8, height=6)
# sns.barplot(x="sales", y="ItemP", hue="Category", data=df, palette="pastel")
#
# # Add labels (text) to each bar
# for container in plt.gca().containers:
#     for bar in container:
#         # Get the bar's width (sales value) and y-position
#         width = bar.get_width()
#         y = bar.get_y() + bar.get_height() / 2
#
#         # Add text slightly to the right of the bar
#         plt.text(width + 50, y, f'{int(width)}', va='center', fontsize=8)  # Reduce font size for smaller chart
#
# # Set labels and title
# plt.xlabel("Sales", fontsize=10)  # Reduce font size for labels
# plt.ylabel("Items", fontsize=10)
# plt.title("Sales of Items by Category", fontsize=12)  # Reduce font size for title
# plt.legend(title="Category", bbox_to_anchor=(1.05, 1), loc="upper left", fontsize=8,
#            title_fontsize=10)  # Smaller legend
#
# # Adjust layout and display
# plt.tight_layout()
# plt.show()
#
# #i thought of making it a bit more smaller
# #the same graph but a smalller look, Smaller than the first and 2nd
##Grouped bar chart with reduced size(THIS IS THE SAME WITH WHAT I HAVE ABOVE, JUST REDUCTION IN SIZE)
# plt.figure(figsize=(6, 6))  # Adjust the size here (width=8, height=6)
# #Define custom colors for each bar
# #custom_colors = ["#FF5733", "#33FF57", "#3357FF", "#FFD700"]  # List of color codes
# # Define custom color names for each bar
# custom_colors = ["royalblue", "navy", "skyblue", "Gray"]  # Named colors
# sns.barplot(x="sales", y="ItemP", hue="Category", data=df, palette = custom_colors)
#
# # Add labels (text) to each bar
# for container in plt.gca().containers:
#     for bar in container:
#         # Get the bar's width (sales value) and y-position
#         width = bar.get_width()
#         y = bar.get_y() + bar.get_height() / 2
#
#         # Add text slightly to the right of the bar
#         plt.text(width + 50, y, f'{int(width)}', va='center', fontsize=8)  # Reduce font size for smaller chart
#
# # Set labels and title
# plt.xlabel("Sales", fontsize=8)  # Reduce font size for labels
# plt.ylabel("Items", fontsize=8)
# plt.title("Sales of Items by Category", fontsize=8)  # Reduce font size for title
# plt.legend(title="Category", bbox_to_anchor=(1.05, 1), loc="upper left", fontsize=8,
#            title_fontsize=8)  # Smaller legend
#
# # Adjust layout and display
# plt.tight_layout()
# plt.show()
#AGE ANALYSIS
#I WANT TO GROUP AGE FIRST
#Bar Chart plot of Age group and the number of customers per group
#Bar Graph
#this code plot the Graph but the Graph plotted from the code below is better
# plt.figure(figsize=(8, 6))
# plt.bar(df['AgeGroup'], df['TotalAgecount'], color='b', alpha=0.7)
# plt.title('The count of Customers for Each Age Group')
# plt.xlabel('AgeGroup')
# plt.ylabel('TotalAgecount')
# plt.xticks(rotation=45)  # Rotate x-axis labels for better readability
# # plt.grid(True) # Uncomment to add a grid background
# plt.show()
#
#Another code to plot a bar chart (This is better)
#Bar chart of Age group against age count per group
# plt.figure(figsize=(8, 6))
#
# # # Plot Bar Graph
# plt.bar(df['AgeGroup'], df['TotalAgecount'], color='blue', alpha=0.7)
#
# # Labeling
# plt.title('Customer Count for Each Age Group', fontsize=14)
# plt.xlabel('Age Group', fontsize=12)
# plt.ylabel('Total Count', fontsize=12)
# plt.xticks(rotation=45)  # Rotate x-axis labels for readability
#
# # Show values on top of bars
# for i, count in enumerate(df["TotalAgecount"]):
#     plt.text(i, count + 10, str(count), ha='center', fontsize=10)
#
# plt.show()
#AVERAGE SALES FOR EACH AGE GROUP
#
#Group Bar Chart For age, sales, season
#i was trying to replicate what i have used earlier here (THIS HASNT WORK YET)
# plt.figure(figsize=(6, 6))  # Adjust the size here (width=8, height=6)
# #Define custom colors for each bar
# #custom_colors = ["#FF5733", "#33FF57", "#3357FF", "#FFD700"]  # List of color codes
# # Define custom color names for each bar
# custom_colors = ["royalblue", "navy", "skyblue", "Gray"]  # Named colors
# sns.barplot(x="sales", y="ItemP", hue="Category", data=df, palette = custom_colors)
#
# # Add labels (text) to each bar
# for container in plt.gca().containers:
#     for bar in container:
#         # Get the bar's width (sales value) and y-position
#         width = bar.get_width()
#         y = bar.get_y() + bar.get_height() / 2
#
#         # Add text slightly to the right of the bar
#         plt.text(width + 50, y, f'{int(width)}', va='center', fontsize=8)  # Reduce font size for smaller chart
#
# # Set labels and title
# plt.xlabel("Sales", fontsize=8)  # Reduce font size for labels
# plt.ylabel("Items", fontsize=8)
# plt.title("Sales of Items by Category", fontsize=8)  # Reduce font size for title
# plt.legend(title="Category", bbox_to_anchor=(1.05, 1), loc="upper left", fontsize=8,
#            title_fontsize=8)  # Smaller legend
#
# # Adjust layout and display
# plt.tight_layout()
# plt.show()
#
#
# ##Group Bar Chart For age, sales, season
# # Set the 'Age_Group' as the index
# df.set_index('Age_Group', inplace=True)
#
# # Define the width of the bars
# bar_width = 0.2
#
# # Define the positions of the bars on the x-axis
# r1 = np.arange(len(df))
# r2 = [x + bar_width for x in r1]
# r3 = [x + bar_width for x in r2]
# r4 = [x + bar_width for x in r3]
#
# # Create the figure and axis
# fig, ax = plt.subplots(figsize=(6, 6))
#
# # Plot bars for each season
# ax.bar(r1, df['Spring_Sales'], color='navy', width=bar_width, edgecolor='grey', label='Spring')
# ax.bar(r2, df['Summer_Sales'], color='royalblue', width=bar_width, edgecolor='grey', label='Summer')
# ax.bar(r3, df['Fall_Sales'], color='gray', width=bar_width, edgecolor='grey', label='Fall')
# ax.bar(r4, df['Winter_Sales'], color='skyblue', width=bar_width, edgecolor='grey', label='Winter')
#
# # Add labels and title
# ax.set_xlabel('Age_Group', fontweight='bold')
# ax.set_ylabel('Total Sales', fontweight='bold')
# ax.set_title('Sales Distribution by Age Group and Season', fontweight='bold')
#
# # Set the x-axis ticks and labels
# ax.set_xticks([r + bar_width * 1.5 for r in range(len(df))])
# ax.set_xticklabels(df.index)
#
# # Add a legend
# ax.legend()
#
# # Display the plot
# plt.tight_layout()
# plt.show()
#
#A CHART OF ITEMS SOLD IN FALL(FALL HAS THE HIGHEST SEASON SALE)
#ITEMP AND SALES
#for ITEMS and sales plot (Dayo's idea)
# Assuming 'df' is your DataFrame with 'location' and 'sales' columns
# Sort the data by 'sales' in descending order
# sorted_df = df.sort_values(by='sales', ascending=False)
# # Get the sorted items and sales values
# sorted_location = sorted_df['ItemP'].tolist()
# sorted_sales = sorted_df['sales'].tolist()
# #Create horizontal bar chart with larger figure height for more space
# plt.figure(figsize=(6,6))  # Increased height for more space between bars
# bars = plt.barh(sorted_location, sorted_sales, color='skyblue')
# plt.xlabel('sales', fontsize=12)
# plt.ylabel('ItemP', fontsize=12)
# plt.title('Revenue by Item in Fall', fontsize=14)
# plt.show()
#
#
## #GRAPH FOR ITEMP SALES (dayo's idea final one)
# # # Assuming 'df' is your DataFrame with 'ItemP', 'Category', and 'sales' columns
# # # Sort the data by 'sales' in descending order
# sorted_df = df.sort_values(by='sales', ascending=False)
#
# # Get the sorted item names and sales values
# sorted_items = sorted_df['ItemP'].tolist()
# sorted_sales = sorted_df['sales'].tolist()
#
# # Create a horizontal bar chart
# plt.figure(figsize=(6, 6))  # Set figure size
# bars = plt.barh(sorted_items, sorted_sales, color='skyblue')
# plt.xlabel('Sales', fontsize=10)
# plt.ylabel('Item', fontsize=10)
# plt.title('Revenue by Item in Fall', fontsize=10)
# # Display sales values next to the bars
# for bar, value in zip(bars, sorted_sales):
#     # Add text to the right of each bar
#     plt.text(value + 50, bar.get_y() + bar.get_height() / 2, f'{value}', va='center', fontsize=10)
#
# # Invert the y-axis to show the items with the highest sales at the top
# plt.gca().invert_yaxis()
#
# # Adjust layout to ensure everything fits
# plt.tight_layout()
#
# # Save the chart as an image
# plt.savefig('Revenue by Item in Fall.png', dpi=300)
# plt.show()
```


### Result And Findings 
### Findings
1. Sales by Season and Category
Fall is the highest-performing season, especially in the Clothing and Accessories categories.

Across all seasons, Clothing consistently outperforms other categories, followed by Accessories, Footwear, and Outerwear.

2. Sales by Gender
Female customers contribute more to total sales compared to male customers.

Both genders show significant interest in Clothing, but females purchase slightly more across all categories.

3. Subscription and Discounts
Customers without subscriptions spend more than those with subscriptions.

Discounts, promo codes, and subscriptions do not positively influence sales as expected. The combination (3-in-1 offer) appears to have minimal or no impact on revenue.

4. Demographic Insights
The average customer age is 44 years, with the majority falling between 31 and 57 years (Q1 to Q3).

There is no clear correlation between age and total sales, indicating that people across different age brackets shop equally.

The store does not target or attract a teenage demographic, as the minimum age of customers is 18.

5. Location-Based Insights
Sales are concentrated in the top 10 locations, suggesting a strong regional performance.

These high-performing locations could represent urban areas or regions with higher purchasing power.

6. Review, Gender, and Sales Relationship
There is no strong correlation between reviews and sales.

Linking reviews with gender shows that gender does not significantly affect review ratings or influence purchase decisions based on reviews.

7. Data Limitation – Quantity vs. Revenue
The dataset does not include the quantity of items sold, which makes it impossible to determine whether an item’s popularity is due to its price or volume sold.

Example: “Hat” appears to perform well in fall, but this might be due to high unit price rather than high quantity sold.

### Recommendations
1. Improve Data Collection
Include quantity sold per item in future datasets to enable more accurate analysis of best-selling items by volume, not just by revenue.

Collect product-level reviews, stock quantity, and item price, which will help distinguish price-driven sales from popularity.

2. Rethink Subscription and Discount Strategies
Since subscriptions and discounts are not improving sales, the company should:

Re-evaluate its loyalty programs to provide more attractive and personalized incentives.

Consider A/B testing various discount levels and types (e.g., % off vs. BOGO) to determine more effective offers.

3. Focus Marketing on High-Performing Seasons and Categories
Boost marketing efforts during the Fall season, especially around Clothing and Accessories.

Allocate more ad spend and promotions to top-selling locations and demographics (age 31–57).

4. Expand Target Audience
Consider developing youth-specific product lines to tap into the teenage market (currently unrepresented).

Explore customized marketing campaigns for different age groups using the quantile-based age segmentation.

5. Enhance Customer Segmentation
Segment customers not just by age and gender, but by purchase frequency and item category.

Use this segmentation to implement targeted email campaigns, product recommendations, and retargeting ads.

6. Sales Prediction and Forecasting
Use the current dataset to build predictive models to forecast:

High-demand seasons

Likely-to-return customers

Category performance over time.

### Ideas for Deeper Analysis
Segment analysis: Sales by age group, gender, category, and location.

Tie in reviews with sales and demographics.

Analyze subscription vs. non-subscription sales patterns.

Look into sales forecasting and customer retention models.


### References
1. SQl For Business Anlayisis by Werty
2. YOutube Tutorials By Alex the Data Analyst

|Heading1|Heading2|
|-------|----------|
|content1|content2|
|Python1|pyhton2|
|MySql1|Mysql2|


#another way to write code here 🫵


`select all from customers`

*to write in italic*


😄
💻 
🙂
🆒 😄 💻 🙂 🆒 😄 💻 🙂 🆒 😄 💻 🙂 🆒 😄 💻 🙂 🆒 😄 💻 🙂 🆒 😄 💻 🙂 🆒 











