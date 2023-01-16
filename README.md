# Hotel-Revenue-SQL-PowerBI-Project

## **1. Objective of Project:**
* Design a Power BI Dashboard imported from a SQL database that contains a hotel revenue dataset retrieved from https://absentdata.com/hotel_revenue_historical_full/ in order to answer the questions of the stakeholders:
  1. Is there growth in hotel revenue?
  2. Should they increase their parking lot size?
  3. What trends can be identified in the data?
  
## **2. Data Description:**
* Tables:
  * dbo.'2018$': Table consisting of hotel revenue data from 2018.
  * dbo.'2019$': Table consisting of hotel revenue data from 2019.
  * dbo.'2020$': Table consisting of hotel revenue data from 2020.
  * dbo.market_segment$: Table consisting of the value of discount as a factor to be applied in relevance to market segment.
  * dbo.meal_cost$: Table consisting of the cost value of relative meals.
  
* Fields:
  * adr: Average daily rate of hotel stay.
  * arrival_date_year: Consumer's year of arrival to hotel.
  * country: Hotel's location defined as a country code.
  * discount: Discount applied
  * hotel: Hotel type
  * Parking Percentage: Custom field created to generate percentage of guests occupying parking spaces with consideration of total booked nights. Equates to Sum(required_car_parking_spaces)/(Total Nights).  
  * required_car_parking_spaces: Parking spaces required for a stay
  * Revenue: Custom field created to generate total hotel revenue. Equates to ([stays_in_week_nights]+[stays_in_weekend_nights])*([adr]*(1-[Discount]).     
  * stays_in_weekend_nights: Amount of weekend stays
  * stays_in_week_nights: Amount of weeknight stays
  * Total Nights: Custom field created to generate total quantity of hotel night stays. Equates to Sum(stays_in_week_nights)+ Sum(stays_in_weekend_nights).
  
## **3. Project Sequence:**
A. Transfered all of the hotel revenue excel data into a local SQL database. Executed various queries on relevant fields in preparation for dashboard.
  * Use the union command to combine all selected columns: 2018, 2019, and 2020 revenue data.
  * Using the new combined table, add JOINs to the: 
    * Market Segment table on market_segment column.
    * Meal Cost table on meal column.
  
  Since it is a LEFT JOIN; all columns are maintained in the tables with the matching columns(market segment and meal tables), along with the combined table. Thus, two tables are joined with a commonality in columns and entries of matching values from the left table.   
  

![SQL](https://user-images.githubusercontent.com/122722167/212630311-e6b9406b-f59f-4f71-b3cf-6c83db17bd73.png)

B. Imported SQL server queries to Power BI. Generated new fields through Power BI to enhance overall data visualization.

![FFormula](https://user-images.githubusercontent.com/122722167/212637755-0a830c0e-0cda-49cf-97fc-03958de9ee49.png)

C. Designed a clear and concise visual dashboard that helps solve the stakeholder’s questions. 
* The top portion of the Power BI dashboard displays total revenue, average ADR, total nights, average discount, and car spaces. Each contains a mini line chart below the data, except for total revenue. 
* The middle portion of the dashboard displays changes in revenue by reservation status date spanning from 2018-2020 using an enlarged line chart. 
* The bottom portion of the dashboard displays proportions of the total revenue between the hotel types using a donut chart with the incorporation of a pivot table that shows the two hotel type's yearly revenue, parking space, and parking percentage.  

![Dash](https://user-images.githubusercontent.com/122722167/212638767-598ddbb4-7247-4015-9fb6-af7fc60eea02.png)

* Usage of dashboard slicer that enables the user to filter the desired country's data to be displayed on the visual dashboard.

![country](https://user-images.githubusercontent.com/122722167/212644042-bf27a793-406f-4e0a-a8e9-cf855148d1f2.png)

* Usage of dashboard slicer that enables the user to filter the desired hotel type's data to be displayed on the visual dashboard.

![HotelType](https://user-images.githubusercontent.com/122722167/212644180-1efa9b8e-def2-49de-98ef-6bea72c1482b.png)

* Usage of dashboard slicer (slider) that enables the user to filter the desired dates or span of dates to be displayed on the visual dashboard.

![Date](https://user-images.githubusercontent.com/122722167/212644602-157fda1f-9bcb-4c0c-b47f-1446f0cd82c2.png)

## **4. Findings:**

* Upon analyzing the dashboard, it is evident that there is growth in hotel revenue from 2018 to 2019, with a minor decrease in the year of 2020. The decrease in 2020 still equated to a higher total revenue than the year of 2018. The mini line charts also indicated a positive trend for average of ADR, total nights, average of discount, and required car spaces. However, taking into consideration the percentage of parking spaces occupied (2-3%), there is not enough evidence to suggest that parking lot sizes should be expanded. A trend can be identified between hotel types, where city hotels experience a spike in revenue towards the end of September, while resort hotels experience a spike in revenue around the summer months, especially in July.  





