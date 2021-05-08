# SQLAlchemy-Challenge

### Directory Overview
* The "climate_final.ipynb" contains the code for Step 1 of the assignment.  "climate_starter.ipynb" is the starter code provided.
* The "Resources" directory has the sqlite file for the Hawaii data which the analyses will be conducted off of.  
* The "Images" directory contains visualizations of the plots required in Step 1 of the assignment.
* app.py is a flask API that was created in accordance with Step 2 of the assignment.  Execute the file in a terminal window to recieve the API URL created.  Paste the URL into the Internet browser of your choice.  API documentation for the /api/v1.0/<start> requires the user to input a start date in the ISO (yyyy-mm-dd) format for the API to return results.  For example, if you wanted temperature data starting on March 1, 2016 you would input the following URL into your browser: http://127.0.0.1:5000//api/v1.0/2016-03-01.  If you wanted temperature data from January 16, 2016 to September 16, 2017 then you would input the following URL into your browser: http://127.0.0.1:5000//api/v1.0/2016-01-16/2017-09-16. These are examples of dynamic API routes.

## Step 1 - Climate Analysis and Exploration

To begin, use Python and SQLAlchemy to do basic climate analysis and data exploration of your climate database. All of the following analysis should be completed using SQLAlchemy ORM queries, Pandas, and Matplotlib.

* Use the provided [starter notebook](climate_starter.ipynb) and [hawaii.sqlite](Resources/hawaii.sqlite) files to complete your climate analysis and data exploration.

* Choose a start date and end date for your trip. Make sure that your vacation range is approximately 3-15 days total.

* Use SQLAlchemy `create_engine` to connect to your sqlite database.

* Use SQLAlchemy `automap_base()` to reflect your tables into classes and save a reference to those classes called `Station` and `Measurement`.

### Precipitation Analysis

* Design a query to retrieve the last 12 months of precipitation data.

* Select only the `date` and `prcp` values.

* Load the query results into a Pandas DataFrame and set the index to the date column.

* Sort the DataFrame values by `date`.

* Plot the results using the DataFrame `plot` method.

* Use Pandas to print the summary statistics for the precipitation data.

### Station Analysis

* Design a query to calculate the total number of stations.

* Design a query to find the most active stations.

  * List the stations and observation counts in descending order.

  * Which station has the highest number of observations?
![Precipitation_Barchart](Images/Precipitation_Barchart.png)

  * Hint: You will need to use a function such as `func.min`, `func.max`, `func.avg`, and `func.count` in your queries.

* Design a query to retrieve the last 12 months of temperature observation data (TOBS).

  * Filter by the station with the highest number of observations.

  * Plot the results as a histogram with `bins=12`.

![TOBS_Histogram](Images/TOBS_Histogram.png)
- - -

## Step 2 - Climate App

Now that you have completed your initial analysis, design a Flask API based on the queries that you have just developed.

* Use Flask to create your routes.

### Routes

* `/`

  * Home page.

  * List all routes that are available.

* `/api/v1.0/precipitation`

  * Convert the query results to a dictionary using `date` as the key and `prcp` as the value.

  * Return the JSON representation of your dictionary.

* `/api/v1.0/stations`

  * Return a JSON list of stations from the dataset.

* `/api/v1.0/tobs`
  * Query the dates and temperature observations of the most active station for the last year of data.
  
  * Return a JSON list of temperature observations (TOBS) for the previous year.

* `/api/v1.0/<start>` and `/api/v1.0/<start>/<end>`

  * Return a JSON list of the minimum temperature, the average temperature, and the max temperature for a given start or start-end range.

  * When given the start only, calculate `TMIN`, `TAVG`, and `TMAX` for all dates greater than and equal to the start date.

  * When given the start and the end date, calculate the `TMIN`, `TAVG`, and `TMAX` for dates between the start and end date inclusive.

## Hints

* You will need to join the station and measurement tables for some of the queries.

* Use Flask `jsonify` to convert your API data into a valid JSON response object.