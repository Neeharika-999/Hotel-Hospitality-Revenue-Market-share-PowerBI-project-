# Hotel-Hospitality-Revenue-Market-share-PowerBI-project-

# HOTEL INDUSTRY REVENUE ANALYSIS

**DOMAIN**- Hotel Hospitality         
**FUNCTION**-Revenue

AtliQ Grand owns multiple 5 star hotels across India. They have been in the hospitality industry for the past 20 years. Due to strategic moves from competitiors and ineffective decision-making in management, AtliQ Grand are losing its market share and revenue in the luxury/business hotel category. As a strategic move, the managing director of AtliQ Grand wants to incorporate *"Business and Data Intelligence"* to regain their market share and revenue.

## DATASET
Here is the dataset provided.
https://drive.google.com/drive/folders/1teCSV63tWvPWHd2PVbdR74duTPoEexlo?usp=drive_link
This are the data of hotels from months May to July.



## SITUATION

1. Why AtliQ Grand has noticed a loss in its market share? And address me the issue.
2. Why AtilQ Grand has encountered less occupancy in Tier 1 cities?
and why there is an average performance in tier 2 and 3 cities?

3. How the pricing strategy is effecting occupancy?

4. What are the other factors that is effecting the revenue?
Provide useful strategies to improve that.

## TERMS AND DISCUSSION:

Before starting, we must know few terms that are used in hotel revenue data analysis:
* RevPar(Revenue per Avaiable Rooms) =Total revenue/Total Rooms.
* ADR (Average daily rate)=Total rooms Revenue/No. of rooms sold. It is the by product of RevPar.
* Occupancy% = Total rooms occupied/ Total rooms available. Here total rooms available can be varied as if consider Total rooms=100 and 5 rooms are out of order, then the total rooms available will become 95.
* DSRN (Daily sellable rooms nights): DSRn is more helpful as it is calculated in daily basis.
* SRN (Sellable rooms nights) : It can be per months or per week basis. If DSRN= 100 Rooms. Then SRN = 100 rooms * 30 days = 300 SRN for June.
* Realisation% : This is an important metric and to introduce this concept of realisation we have to look at two new metrics:
1. URN or Utilized Rooms Nights: Say 100 rooms are there in hotel and 60 rooms were booked and 50 customer stayed so this 50 rooms, we treated it as utilized room.
2. BRN or Booked room nights: Say 100 rooms, 60 were booked and only 50 stayed in the hotel. So there is a gap of 10 rooms , but still 60 rooms were considered as BRN. It consists of Utilized rooms, no show up and cancellation.
And thus, Realization% = URN/BRN
Sometimes, no show=no refund, and that money goes for accounting purpose and not considered in revenue.


## TASK:
1. Create the Metrics.
2. Create an end to end dashboard that helps the stakeholders to understand easily.
3. Create relevant Insights that helps in making data-informed decisions.


## BI Workflow: From Data Collection to Dashboard

5 steps process for building dashboard are:

## 1. Data Source: 
-> Get data 
-> select the hotel hospitality folder

## 2. Data Transformation in Power Query Editor:
-> Transform the data
-> select the csv file and expand it.
-> check the data types. -> check the null and missing values.

## 3. Data Modelling:

Used Star Schema and created one to many relationships.

## 4. Build metrics using DAX
-> **Calculated Columns**

* week number as 'wn'- WEEKNUM(dim_date[date])

* According to client , friday and saturday are weekends, so,
day_type= WEEKDAY(dim_date[date])
var wkd = WEEKDAY(dim_date[date])
return if (wkd>5,"Weekend","Weekday")

-> **Calculated Measure**
* Revenue=sum(fact_booking[revenue_realised])
*recheck by calculating sum in excel.*

* Similarly use dax and find other required measures like Total_booking, Total_capacity, Occupancy%, ADR, Realisation% etc.

## 5. Build the visuals and dashboard using PowerBI

* Make a table by dragging and dropping the columns. property_id, property_name, city, RevPar, Occupancy%, ADRN, DURN, Realisation%, Cancellation%, Average Rating.

* Drag the week no. to the filter box and remove the week no. 32 as it contains only 1 day that is july 31.
* Number formatting: reducing decimals and adjusting.
* Add slicer: *City*-> Title: Filter by city. *Room type*-> Title: Filter by Room Type.
Add slicer: *mm yy*-> tile , *week no.*-> tile.

* KPI: Revenue, RevPar, DSRN, Occupancy%, ADR, Realisation%. For every KPIs add Week Over Week Change(WoW)% below with icons.
Add tooltips and add line chart for every KPIs with week no. and category such as revenue by week no. and category, RevPar by week no. and category, etc.
* Add Donut Chart: To measure the occupancy% by category.
* Line Chart: Trends by Key metrics to compare between RevPar,occupancy% and ADR.
* Bar and Line Chart: Realisation% and ADR by booking Platform.
* Mini Table below KPI (Super Key Metrics): It is the most important metric, to check the Revpar,Occupancy%, ADR, Realisation% based on Weekdays and Weekends.

## Insights , Reasoning and Recommendations:
* **Coming to the first situation**, we must know that one of the biggest level , we have in hotel industry is **Pricing**. In Hotel Industry say I can sell a room on week days for 10k and for peak days like 25k to 30k.
        
  DEMAND  <-------PRICE ELASTICITY------->   SUPPLY

**Insights (What did we find?)**
: In Key Trends Metrics we can see that RevPar is not fluctuating, RevPar is the by product of Rate and Occupancy. Observing the week data, we can see the rates are constant and fixed over the whole period of time.

**Reasoning(Why it is happening?)**
: One of the factor for decrease in revenue because of standard and constant pricing for hotel rooms.By looking at the fluctuating scene, it is evident that this hotel doesnot use any pricing strategy, which is important for increase in revenue.

**Recommendations( What to do?)**
: We know that there are 3 types of pricing in hotels. They are:
1. Flat Pricing.
2. Weekdays/Weekends Pricing.
3. Dynamic Pricing.
Since, this is the data of months-> May, June, July ; where kids are having summer vacations and people also take summer holidays. So, the rates must fluctuate during this season.

This hotel had great oppurtunities if they have the capabilities to adopt dynamic pricing.

* **According to the second and third situation**, the least occupancy is seen in one of the Tier 1 cities, which is also a major drawback.
**Insights(What did we find?)**:

Coming to the table below, based on least occupancy that is AtliQ Grand from Bangalore which has only 44.3%.

**Reasoning (Why is it happening?)**: 

Based on the observation, we can question 3 whys!
1. Why my business is not doing well?
2. Which my occupancy is less?
3. How does Pricing influence occupancy?
For all these questions, we found that there is a common solution!
It is a fact that

pricing Increase = Occupancy decrease

pricing Decrease = Occupancy Increase (excluding few market that are inelastic )
All the solution of the answer are most probably somehow related to the pricing strategy although there could be other factors also for less occupancy in AtliQ Grands, like defected Rooms, Enivornment around the hotels, gestures during the Entry, Room Types, Amenities in the Hotel etc.

**Recommendations (What to do?)**:

To Increase the oppurtunites, we must check the other factors like defected Rooms, Enivornment around the hotels, gestures during the Entry, Room Types, Amenities in the Hotel etc., and try to correct it first, then we can move to the pricing factor and if the pricing is not appropriate we must make it cost-friendly.

* **Based on 4th situation**, the other factors that are affecting the revenue are mentioned below:
**Insights (What did we find?)**:
From the table below, coincidently, we found that the average rating is also low for the same hotel that has lowest occupancy.
Another insights we got from the bar and line chart of Realisation% by Platform where offline channel has the highest rates and online channel have the lowest rates.

**Reasoning(Why is it happening?)**:
Today, the market is such that any product available online drastically affected by ratings and reviews.And the product that are sold online has a higher probability of selling if it has higher rating in online. 
Most hotels have their own website and most hotel partners, businesses try to sell cheapest on their own channel because their commission is the lowest.

Weak Point-> They are not using differential pricing in their own channel as they are not paying commission to the channel which are online to increase their rating.

**Recommendation (What to do?)**: So, the strategy here, is not pricing but promotion, like discount coupons , offers on the website or any complementary food or night stay with the tickets etc. As Bots are the one which do check if you are giving less commission on your own channels and high on other channel just to earn good rating.

To avoid this, we can use the promotions.

**FINAL DASHBOARD OF THE HOTEL HOSPITALITY ANALYSIS**
