# Analyzing Departure and Arrival Delays Between Airlines

Using the publicly avialble data from the [Bureau of Transportation Statistics](https://www.transtats.bts.gov/DL_SelectFields.asp) arrival and departure delay times were compared between airlines. The data is shown over the course of an average week. This data can be applicable for travelers trying to make decisions about what flights they book with which airlines and when.

## With Which Airlines is it Best to Book Flights, and When?

Travelers booking flights for trips have many options when it comes to how they get to their destination. Whether they are going on a long journey that has multiple conecting flights, all of which depend on the pervious one being on-time, or they are simply trying to get to their destination as soon as possible, travelers booking their flights would want to know how likely it is for their flight to experience delays, and how long those delays typically are. 
While travelers book their flights, if they are looking to minimize the delays experienced, they may change which airline they fly with, as well as which day of the week they choose to fly, as different airlines provide different levels of reliability, and different days of the week experience differe volumes of travelers leading to more delays.

## Which Airlines Have the Smallest Amount of Time between Expected Arrival and True Arrival Time Throughout the Week?

Flight data from 2019 was collected from the [Bureau of Transportation Statistics](https://www.transtats.bts.gov/DL_SelectFields.asp). The data selected to be used for analysis included the day of the week, the airline, the departure delay (difference in minutes between scheduled and actual departure time with early departures show negative numbers) and arrival delay (difference in minutes between scheduled and actual arrival time with early arrivals show negative numbers). Departure delay was not neccessary to include for the simple analysis of which airlines delayed passengers the most from arriving at their destination, but I though it would be interesting to see if the amount of delay time stayed constant throughout the process, if the airlines did anything to minimize departure delays to ultimately result in lower arrival delays, or if departure delays compounded and led to larger arrival delays. 

## Results for Comparing Arrival and Departure Delays

Using a [Python file](), the data from the Bureau of Transportation Statistics was processed to produce a figure that allows for selection of particular airline data. 

1. The raw data file was downloaded from the [Bureau of Transportation Statistics](https://www.transtats.bts.gov/DL_SelectFields.asp), and the selected data sets to be included were: day of the week, the airline, the departure delay, and arrival delay. Year, original airport ID, and desitnation airport ID were also downloaded but were not used in this analysis. 






