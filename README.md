# PyBer_Challenge
## Overview of the analysis: Explain the purpose of the new analysis.
The purpose of thie project is to create visualizations of rideshare data for PyBer to help improve access to ride-sharing services and determine affordability for underserved neighborhoods. Specifically, the client was interested in the following metrics:
- The total rides for each city type
- The total drivers for each city type
- The total amount of fares for each city type
- The average fare per ride for each city type
- The average fare per driver for each city type

### Resources
- Software Python 3.7.13, Matplotlib 3.5.2
- Data: city_data.csv, ride_data.csv
## Results: Using images from the summary DataFrame and multiple-line chart, describe the differences in ride-sharing data among the different city types.
![Chart 1](https://github.com/banasibb/PyBer_Challenge/blob/b92c1f54bb98a4eb85f556feca867702e6d5be68/Analysis/pyber_summary_df.png)<br />
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


## Summary: Based on the results, provide three business recommendations to the CEO for addressing any disparities among the city types.
