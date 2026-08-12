

# ------EDA project:  The Hidden Housing Portfolio: A Spatial and Temporal Analysis of King County House Sales---------                 Amy Williams, a seller wants to sell high-value (top 10%) houses in central areas and average-priced houses in outskirt areas, with both types of sales distributed over time.  Our EDA is helping to understand and plan a diversified house-selling strategy-------------------


--------------------------------------------------
# Step 1 Data Understanding and Join Validation
---------------------------------------
The analysis uses two tables:
king_county_house_details: property attributes such as size, bedrooms, bathrooms, location, and condition.
king_county_house_sales: transaction information such as sale price and sale date.

# 1. Inspect both datasets

First, inspect the structure and available columns in each table.
SELECT *
FROM eda.king_county_house_details;

SELECT *
FROM eda.king_county_house_sales;
This helps identify the primary key (id) in the house-details table and the matching foreign key (house_id) in the sales table.

# 2. Count records before merging
Check the number of rows in each dataset before performing the join.
SELECT COUNT(*)
FROM eda.king_county_house_details;

SELECT COUNT(*)
FROM eda.king_county_house_sales;

These counts provide a baseline for validating the merge and detecting missing or duplicated records.


# 3. Merge house details with sales data
Join the tables using the property identifier.

SELECT d.*, s."date", s.price
FROM eda.king_county_house_details AS d
JOIN eda.king_county_house_sales AS s
ON d.id = s.house_id;

An INNER JOIN is used, so the resulting dataset contains only sales records that can be matched to an existing property in the details table.



# 4. Validate the joined dataset
Count the rows after joining both tables.

SELECT d.*, s."date", s.price
FROM eda.king_county_house_details AS d
JOIN eda.king_county_house_sales AS s
ON d.id = s.house_id;

Compare this count with the original table counts. If the joined count is unexpectedly larger than the sales-table count, it may indicate duplicate property IDs in the details table or multiple matching records. If it is smaller, some sales may not have matching property details.


# 5. Use the joined dataset for EDA

The final joined table combines property characteristics with transaction outcomes. It is use to:
- Compare the percentage of her sales in the top 10% of property prices with other sellers.
- Compare the location/distance from the center of her properties.
- Plot her number of sales and average sale price over time.

# Hypotheses:

5.1. High-value central houses
H1: Houses in central areas are more likely to belong to the top 10% of property values.
Compare the proportion of top-10% high-priced houses located in central areas with those located in outskirts areas.

5.2. Sales over time
H2: High-value central houses are sold across multiple time periods rather than being concentrated in a single period.
Analyze the number of high-value central houses sold and their average sale price over time.

5.3. Average-priced outskirts houses
H3: Houses in outskirts areas are more likely to have average sale prices than houses in central areas.
Compare the sale-price distribution of outskirts houses with that of central houses, focusing on properties around the middle of the price distribution.


# insights after the implementation of the EDA: 

H1: Amy Williams sells a higher proportion of high-priced properties than other sellers.
H2: Amy Williams' sales activity and average sale price vary over time.
H3: Amy Williams sells more centrally located properties than outskirt properties.


# My recommendation 
..............
.............
..............
.............