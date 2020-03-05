# Analyzing Departure and Arrival Delays Between Airlines

Using the publicly avialble data from the [Bureau of Transportation Statistics](https://www.transtats.bts.gov/DL_SelectFields.asp) arrival and departure delay times were compared between airlines. The data is shown over the course of an average week. This data can be applicable for travelers trying to make decisions about what flights they book with which airlines and when.

## With Which Airlines is it Best to Book Flights, and When?

Travelers booking flights for trips have many options when it comes to how they get to their destination. Whether they are going on a long journey that has multiple conecting flights, all of which depend on the pervious one being on-time, or they are simply trying to get to their destination as soon as possible, travelers booking their flights would want to know how likely it is for their flight to experience delays, and how long those delays typically are. 
While travelers book their flights, if they are looking to minimize the delays experienced, they may change which airline they fly with, as well as which day of the week they choose to fly, as different airlines provide different levels of reliability, and different days of the week experience differe volumes of travelers leading to more delays.

## Which Airlines Have the Smallest Amount of Time between Expected Arrival and True Arrival Time Throughout the Week?

Flight data from 2019 was collected from the [Bureau of Transportation Statistics](https://www.transtats.bts.gov/DL_SelectFields.asp). The data selected to be used for analysis included the day of the week, the airline, the departure delay (difference in minutes between scheduled and actual departure time with early departures show negative numbers) and arrival delay (difference in minutes between scheduled and actual arrival time with early arrivals show negative numbers). Departure delay was not neccessary to include for the simple analysis of which airlines delayed passengers the most from arriving at their destination, but I though it would be interesting to see if the amount of delay time stayed constant throughout the process, if the airlines did anything to minimize departure delays to ultimately result in lower arrival delays, or if departure delays compounded and led to larger arrival delays. 

## Results for Comparing Arrival and Departure Delays

Using a [Python file](https://github.com/karinafrank/analyzing-airline-delays-by-weekday/blob/master/Project4_Python_Visualization%20(1).ipynb), the data from the Bureau of Transportation Statistics was processed to produce a figure that allows for selection of particular airline data. 

1. The raw data file was downloaded from the [Bureau of Transportation Statistics](https://www.transtats.bts.gov/DL_SelectFields.asp), and the selected data sets to be included were: day of the week, the airline, the departure delay, and arrival delay. Year, original airport ID, and desitnation airport ID were also downloaded but were not used in this analysis. 
2. A [Python file](https://github.com/karinafrank/analyzing-airline-delays-by-weekday/blob/master/Project4_Python_Visualization%20(1).ipynb) was created in google colaboratory.
3. Packages to be used throughout analysis were imported, including pandas and plotly.express.
4. The raw csv file was uploaded, read, and translated into a dataframe using
```
airline_data = "https://raw.githubusercontent.com/karinafrank/analyzing-airline-delays-by-weekday/master/Airline%20Delay%20Raw%20Data.csv"
df_airline = pd.read_csv(airline_data)
```
5. The data for each individual flight arrival and departure delay was grouped by the day of the week, and was aggregated to only show the average delay for each airline on each day of the week.
`df_airline_dep_delays = df_airline.groupby(["DAY_OF_WEEK", "MKT_UNIQUE_CARRIER"])["DEP_DELAY"].agg(["mean"]).reset_index()`
  * This step was done separately for arrival delays and departure delays
  * The two different aggregated means were combined into one dataframe by adding a column to the departure delays dataframe with arrival delay average time using `df_airline_dep_delays['ARR_DELAYS'] = df_airline_arr_delays['mean']`
6. Using the melt function, the two columns of delay data (departure and arrival) are combined into one variable column, with arrival delays listed after departure delays. 
  * This step is done so the two sets of y values may be simultaneously graphed using one variable
```
df_melt = df_airline_dep_delays.melt(id_vars=['DAY_OF_WEEK','MKT_UNIQUE_CARRIER'],value_vars=['mean','ARR_DELAYS'])
```
7. A line graph is then made using plotly.express. The graph shows the difference between the departure and arrival delays among all the airlines, and allows for selection of a particular airline to examine its particular trends throughout the week days.

![alt text](https://github.com/karinafrank/analyzing-airline-delays-by-weekday/blob/master/Plotly%20Visualization.png)

## How Travelers Should Book Their Flights

According to the results of the above analysis, ...

However, it can be seen on the interactive plot most airports have larger departure delays than arrival delay times. This indicates that airlines do something to make the delay in departure not have as large an effect on overall flight plans, possibly by taking alternate routes, or simply the airline calculates in a longer expected flight time, adn therefore later expected arrival time, to allow for delays in departure. Therefore, if a flight is leaving much later than expected, passengers can at least rest assured that their delay at their arrival destination will not be as drastic as the one experienced waiting in the airport. 

Given more time, it would be interesting to investigate how delay times correlated with airport origin and destination, as some locations like Chicago are known for having frequent flight delays and cancellations due to weather. 





