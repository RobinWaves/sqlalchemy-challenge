# SQLAlchemy-Challenge
## SQL Alchemy Assignment - Surfs Up!
***
This assignment runs an analysis on Hawaii's climate using Python and SQLAlchemy.  Additionally it creates a Hawaii climate app using Flask.

Inside this repository you will find:

"Resources" directory - contains all the files needed to complete climate analysis and data exploration.
* hawaii.sqlite - database
* hawaii_measurements.csv
* hawaii_stations.csv

"Images" directory - contains all plots and charts
* PrecipitationBar - last 12 months of precipitation data in the dataset
* TobsHist - last 12 months of temperature observation data for the station with the most observations.
 
"climate.ipynb"- creates an engine to connect to sqlite database, reflects tables into classes, saves references to those classes and then creates a seesion to query the database. Closes the session when done with queries.
#### Precipitation Analysis
* finds most recent date in dataset
* finds the date a year prior to the most recent date and retrieves the last 12 months of precipitation data
* loads query results into data frame
* plots the resuls as a bar chart (PrecipitationBar)
#### Station Analysis
* calculates the total number of stations in the dataset
* finds the most active stations
* lists the stations and observations in descending order
* calculates the lowest, highest, and average temperature using the most active station id
* retrieves the last 12 months of temperature observation data (TOBS) and filters by the most active station 
* gets the last 12 months of temperature observation data for this station
* plot the results as a histogram (TobsHist)

"app.py" - a Flask API based on the queries developed in climate.ipynb.  Routes are created using Flask.
#### Routes
* `/` - homepage that lists all routes that are available
* `/api/v1.0/precipitation` - converts query results to a dictionary using `date` as the key and `prcp` as the value, returns a JSON represntation of the dictonary
* `/api/v1.0/stations` - returns a JSON list of stations from the dataset
* `/api/v1.0/tobs` - queries the dates and temperature observations of the most active station for the last year of data, returns a JSON list of temperature observations (TOBS)
* `/api/v1.0/<start>` - calculates minimum temp, average temp, and maximum temp for all dates greater than and equal to the given start date, returns a JSON list
* `/api/v1.0/<start>/<end>` - calculates minimum temp, average temp, and maximum temp for all dates between the given start and end date inclusive, returns a JSON list

### Bonus
"temp_analysis_bonus_1.ipynb" - seeks to find if there is a meaningful difference between the temperature in June and December
#### Temperature Analysis I
* uses pandas to convert the date column format from string to datetime
* sets the date column as the DataFrame index and drops the date column
* calculates the average temperature in June and December at all stations across all available years in the dataset
* uses the t-test to determine whether the difference in the means is statistically significant

***
Usage: Using postgres, create a new database. Open and run schema.sql in the EmployeeSQL directory to create the necessary tables. Import the six CSV files found in the data directory into the corresponding tables. Open and run Analysis.sql for the queries. Reference the ERD-Employee Database.png for table details.

Bonus: Open jupyter notebook file Bonus.ipynb. Before you run the file, you must modify the password to your pgAdmin password and edit the parameters for your username, host, port, and database name.
