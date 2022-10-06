# PyBer_Challenge
## Overview
The purpose of this project is to create visualizations of rideshare data for PyBer to help improve access to ride-sharing services and determine affordability for underserved neighborhoods. Specifically, the client was interested in the following metrics:
- The total rides for each city type
- The total drivers for each city type
- The total amount of fares for each city type
- The average fare per ride for each city type
- The average fare per driver for each city type<br />

The data was divided into three categories based on geographic region. A total of 66 cities qualified as "Urban," another 36 cities qualified as "Suburban," and the remaining 18 cities were considered "Rural" in this analysis. There were a total of 2,375 rides in the ride_data.csv data set.
### Resources
- Software Python 3.7.13, Matplotlib 3.5.2, Jupyter Notebook 6.4.12
- Data: [city_data.csv](https://github.com/banasibb/PyBer_Challenge/blob/5d32d5b7639859f38554408e4ce69212f63ee2e8/Resources/city_data.csv), [ride_data.csv](https://github.com/banasibb/PyBer_Challenge/blob/5d32d5b7639859f38554408e4ce69212f63ee2e8/Resources/ride_data.csv)<br />
## Results
### Total Rides by City Type
Across all regions, the total number of rides was 2,375, with the total rides for Urban cities as 1625, total rides for Suburban cities equal to 625 and total rides for Rural cities as 125. The breakdown as a percentage of total PyBer rides is in the pie chart below:<br />

![Chart 4](https://github.com/banasibb/PyBer_Challenge/blob/14d2de6b8cb327daaf58c95ffa0faef100c95097/Analysis/Pie%20total%20rides%20by%20city%20type.png)<br />

### Total Drivers by City Type
The total number of drivers across all three regions included in the client's data sets were 68,709. The total drivers for Urban cities as 59,602, total drivers for Suburban cities is 8570, and total drivers for Rural cities as just 537.The percentage breakdown is pictured below:<br />

![Chart 5](https://github.com/banasibb/PyBer_Challenge/blob/14d2de6b8cb327daaf58c95ffa0faef100c95097/Analysis/Pie%20Total%20Drivers%20by%20City%20Type.png)<br />
### Total Fares by City Type
Across all regions, the total dollar amount for fares was $63,538.64. The total fares for Urban cities is $39,854.38, total fares for Suburban cities is $19,356.33 and the total fares for Rural areas is $4,327.93. Please see the pie chart for the visual representation of each dollar amount a percentage of the total fare sales.<br />

   ![Chart 3](https://github.com/banasibb/PyBer_Challenge/blob/cd42bdcb23750da7497d19c461ccc46a7e6118d6/Analysis/Pie%20Total%20Fares%20by%20City%20Type.png)<br />

### Average Fare per Driver by Geographic Region
What follows is a visual representation of the average fare per number of rides based on the geographic region. Note that the circle size correlates to the driver count per city. This table will be referenced in the Summary section.
![Chart 6](https://github.com/banasibb/PyBer_Challenge/blob/7328bd752ce2a0ed202e223a0a5447b27fd347b7/Analysis/bubble%20ride%20sharing%20data%20averages%20reformatted.png)<br />


### PyBer Summary DataFrame
The data in the bullets aboved were summarized into a single dataframe for the client. The excerpted code is below:
 ```
    city_type = pyber_data_df.set_index([""type""])
rides_by_type = pyber_data_df.groupby([""type""]).count()[""ride_id""]
drivers_by_type = pyber_data_df.groupby([""type""]).sum()[""driver_count""]
sum_fares_by_type = pyber_data_df.groupby([""type""]).sum()[""fare""]
average_fares_ride = sum_fares_by_type / rides_by_type
averages_fares_driver = sum_fares_by_type / drivers_by_type

pyber_summary_df = pd.DataFrame({
    ""Total Rides"": rides_by_type,
    ""Total Drivers"": drivers_by_type,
    ""Total Fares"": sum_fares_by_type, 
    ""Average Fare per Ride"": average_fares_ride,
    ""Average Fare per Driver"": averages_fares_driver
})
pyber_summary_df
  ```
![Chart 1](https://github.com/banasibb/PyBer_Challenge/blob/b92c1f54bb98a4eb85f556feca867702e6d5be68/Analysis/pyber_summary_df.png)<br />
### Total Fare by City Type
The final line chart was created using the object-oriented interface method, plot the resample DataFrame using the df.plot() function. The excerpt of code is as follows:
 ```
ax = january_to_april_month_df.plot(figsize=(15, 6))
# Add y-axis label
ax.set_ylabel(""Fare ($USD)"")
x_axis = ax.axes.get_xaxis()
x_label = x_axis.get_label()
x_label.set_visible(False)
ax.set_title(""Total Fare by City Type"")
lgnd = plt.legend(loc=""center"", title=""type"")
# Import the style from Matplotlib.
from matplotlib import style
# Use the graph style fivethirtyeight.
style.use('fivethirtyeight')
plt.show()
  ```
![Chart 2](https://github.com/banasibb/PyBer_Challenge/blob/b92c1f54bb98a4eb85f556feca867702e6d5be68/Analysis/pyber_fare_summary.png)<br />


## Summary
- Based on the analysis, more drivers are needed in rural areas. With only 537 drivers out of the total 15,067 drivers in the PyBer market, rural drivers make up 3.56% of the driver population. However, rural drivers make up 6.81% of all PyBer sales, accounting for $4,327 out of the total $63,538 made in 2019 across all geographic regions. This is an underserved market in terms of drivers.
- The suburban driver market is saturated. PyBer should incentivize those drivers who operate out of cities categorized as suburban to instead consider accepting rides in the rural regions, as this may be more logistically plausible assuming drivers operate out of the market the live in. To help make this case, leadership could educate drivers on the average fare per rural driver, which is $8.06. This is approximately 2.5 times higher than the average fare per driver in the suburban region of $2.26. 
- Urban drivers take, on average, more rides with lower fares. This is evident in the PyBer Ride-Sharing Data (2019) bubble chart referenced in the Results section above. It is also evident in the summary table above, where in the last row of the last column, Average Fare per Driver for Urban areas, where the summary dollar amount of $0.67 can be found. This is only 8% of the average fare per driver in the rural geographic region, and 29.6% of the average fare per driver in the suburban market. This finding may also help incentivize some portion of the urban drivers to consider operating out of the rural or even suburban markets, where the number of rides given may be lower, but the fare per ride and per driver are significantly higher.
