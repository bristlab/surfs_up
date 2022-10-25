# Surf's Up with Advanced Data Storage and Retrieval

## Overview

Our goal with this project is to analyze weather data for Awahoo, Hawaii to determine whether or not the climate is suitable for a surf shop that also serves ice cream. The SQLite database provided contains temperature and precipitation data, and we use Python in conjunction with SQLAlchemy to read the data into Pandas dataframes. We also create an API proof of concept using Flask.

## Results

|  | june_temps | december_temps | june_prcp | december_prcp
|----------|--------------|---|----------|--------------
| count | 1700.000000 | 1517.000000 | 1574.000000 | 1405.000000
| mean | 74.944118 | 71.041529 | 0.136360 | 0.216819
| std | 3.257417 | 3.745920 | 0.335731 | 0.541399
| min | 64.000000 | 56.000000 | 0.000000 | 0.000000
| 25% | 73.000000 | 69.000000 | 0.000000 | 0.000000
| 50% | 75.000000 | 71.000000 | 0.020000 | 0.030000
| 75% | 77.000000 | 74.000000 | 0.120000 | 0.150000
| max | 85.000000 | 83.000000 | 4.430000 | 6.420000

The table above was built by extracting the months of June and December from the dataset and comparing how the weather differs between seasons.


* The average day in December is only about 4° cooler than the average day in June.
* The coldest day in December was 8° colder than the coldest day in June.
* The hottest day in June was only 2° hotter than the hotest day in December.
* The average December day receives 60% more precipitation than the average June day. 

## Summary


The temperatures in June and December are consistently pleasent, and while December is slightly cooler on average, most days are nearly as hot as the hottest days in June.

We did include two additional queries that collate precipitation data when building the table above.

###June:

`june_prcp_results = session.query(Measurement.date, Measurement.prcp).filter(extract('month', Measurement.date)==6).all()`

###December:

`december_prcp_results = session.query(Measurement.date, Measurement.prcp).filter(extract('month', Measurement.date)==12).all()`


While it does rain in Awahoo more in December than in June, the rainy days appear to be few, and it's unlikely that the amount of rain will be enough to dissuade potential ice cream customers entirely.

With this information, it is safe to assume that an ice cream shop should do pretty well all year round, although it should be expected that the winter season will probably be a little slower on days with inclimate weather.