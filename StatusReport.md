## Steven Wu

## Sree Datla
As part of this milestone, I was responsible for the data documentation for our project. I authored a data dictionary, DataDictionary.md, that describes each one of our four datasets, Bus_Routes.csv, L_Stations.csv, Temperature.csv, and Water.csv. For each dataset, I wrote about its origin, the meaning of each row, the total number of rows, and the interpretation of each column. I also recorded the data types and the missing values in each column utilizing the data available in initial_exploration.ipynb.

I also provided information on the tables we created in basic_clean_merge.ipynb, such as transit, weather_daily, and transit_weather_merged, as well as the number of rows in each table. Additionally, I described the steps that were undertaken by the team to clean this data; for example, removing commas from ride counts, replacing day type codes, averaging duplicates for L station rows, and filling in missing values of precipitation. Having all of this in one place makes it easier to understand the collected data.

In my review of the data, I noticed some issues that may be of interest to the team. First, the Temperature.csv file comprises data from two different stations, with the Park Ridge station lacking temperature data. Second, a lot of the snow data is missing, and certain L stations have 0 entries on some days. I’ve made a note of this to ensure we address these issues prior to analysis.

My next step will be to work on developing the metadata files and documenting the data quality process for the final submission.
