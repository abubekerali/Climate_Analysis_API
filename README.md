# Climate_Analysis_API
Step 1 - Data Engineering

The climate data for Hawaii is provided through two CSV. The content of these files inspected and cleaned using Python and Pandas.


 a Jupyter Notebook file called data_engineering.ipynb created and used to complete all of  Data Engineering tasks.
Pandas used to read in the measurement and station CSV files as DataFrames and inspected for NaNs and missing values. 
 the cleaned CSV files saved with the prefix clean_.





Step 2 - Database Engineering

SQLAlchemy used to model  table schemas and create a sqlite database for the tables. it include one table for measurements and one for stations.


Jupyter Notebook called database_engineering.ipynb  created and used to complete all of  Database Engineering work.
Pandas used to read the cleaned measurements and stations CSV data.
the engine and connection string used to create a database called hawaii.sqlite.

a declarative_base was used  and  ORM classes were created for each table.


 a class for Measurement and for Station.
 primary keys were defined.



Step 3 - Climate Analysis and Exploration

ready to use Python and SQLAlchemy to do basic climate analysis and data exploration on the new weather station tables. All of the following analysis  completed using SQLAlchemy ORM queries, Pandas, and Matplotlib.


a Jupyter Notebook file called climate_analysis.ipynb created and used to complete the climate analysis and data exporation.
a start date and end date choosen for the trip with vacation range of approximately 3-15 days total.
SQLAlchemy create_engine used to connect to the sqlite database.
SQLAlchemy automap_base() used to reflect the tables into classes and  a reference was saved to those classes called Station and Measurement.



Precipitation Analysis


a query was designed to retrieve the last 12 months of precipitation data.
only the date and prcp values selected.
the query results loaded into a Pandas DataFrame and  the index was set to the date column.
the results was ploted using the DataFrame plot method.
Pandas was used to print the summary statistics for the precipitation data.



Station Analysis


 a query was designed to calculate the total number of stations.

a query  was designedto find the most active stations.

 the stations and observation counts listed in descending order
The station with  the highest number of observations identified.



a query designed to retrieve the last 12 months of temperature observation data (tobs).


Filtered by the station with the highest number of observations.
the results ploted  as a histogram with bins=12.

Temperature Analysis


a function called calc_temps  that accept a start date and end date in the format %Y-%m-%d and return the minimum, average, and maximum temperatures for that range of dates.
the calc_temps function used to calculate the min, avg, and max temperatures for your trip using the matching dates from the previous year (i.e. use "2017-01-01" if your trip start date was "2018-01-01")
 the min, avg, and max temperature ploted from previous query as a bar chart.


the average temperature used as the bar height.
the peak-to-peak (tmax-tmin) value used as the y error bar (yerr).

Optional Recommended Analysis



The following are optional challenge queries. These are highly recommended to attempt, but not required for the homework.


Calcualte the rainfall per weather station using the previous year's matching dates.



Calculate the daily normals. Normals are the averages for min, avg, and max temperatures.


Create a function called daily_normals that will calculate the daily normals for a specific date. This date string will be in the format %m-%d. Be sure to use all historic tobs that match that date string.
Create a list of dates for your trip in the format %m-%d. Use the daily_normals function to calculate the normals for each date string and append the results to a list.
Load the list of daily normals into a Pandas DataFrame and set the index equal to the date.
Use Pandas to plot an area plot (stacked=False) for the daily normals.
Step 4 - Climate App

Now that you have completed your initial analysis, design a Flask api based on the queries that you have just developed.


Use FLASK to create your routes.



Routes



/api/v1.0/precipitation


Query for the dates and temperature observations from the last year.
Convert the query results to a Dictionary using date as the key and tobs as the value.
Return the json representation of your dictionary.



/api/v1.0/stations


Return a json list of stations from the dataset.



/api/v1.0/tobs


Return a json list of Temperature Observations (tobs) for the previous year



/api/v1.0/<start> and /api/v1.0/<start>/<end>


Return a json list of the minimum temperature, the average temperature, and the max temperature for a given start or start-end range.
When given the start only, calculate TMIN, TAVG, and TMAX for all dates greater than and equal to the start date.
When given the start and the end date, calculate the TMIN, TAVG, and TMAX for dates between the start and end date inclusive.





Hints


You will need to join the station and measurement tables for some of the analysis queries.
Use Flask jsonify to convert your api data into a valid json response object.
