# Data Dictionary

This file goes over the four datasets in our Data folder and the tables we make from them in [basic_clean_merge.ipynb](Code/basic_clean_merge.ipynb). The row counts and missing values come from [initial_exploration.ipynb](Code/initial_exploration.ipynb).
x
## Bus_Routes.csv

This is the daily number of bus rides for each CTA route. It comes from the [Chicago Data Portal](https://data.cityofchicago.org/Transportation/CTA-Ridership-Bus-Routes-Daily-Totals-by-Route/jyb9-n7fm). Each row is one route on one day. It has 1,124,170 rows, 188 routes, and 9,374 different dates. There are no missing values.

| Column | Type | What it is |
|---|---|---|
| route | text | The bus route number. It is text because some routes have letters, like 49B. |
| date | text | The date as MM/DD/YYYY. |
| daytype | text | W is a weekday, A is Saturday, and U is Sunday or a holiday. |
| rides | text | Total rides on that route that day. It has commas in it, like 6,217, so we have to turn it into a number. |

## L_Stations.csv

This is the daily number of people entering each CTA L station. It comes from the [Chicago Data Portal](https://data.cityofchicago.org/Transportation/CTA-Ridership-L-Station-Entries-Daily-Totals/5neh-572f). Each row is one station on one day. It has 1,337,855 rows, 149 station names, and 9,374 different dates. There are no missing values.

| Column | Type | What it is |
|---|---|---|
| station_id | number | The CTA station ID. It goes from 40010 to 41710. |
| stationname | text | The station name. |
| date | text | The date as MM/DD/YYYY. |
| daytype | text | W is a weekday, A is Saturday, and U is Sunday or a holiday. |
| rides | text | How many people entered the station that day. It also has commas. 15,677 rows are 0. |

This dataset counts people entering a station, not riding a line. So if someone enters a station with more than one line, like Belmont, we can't tell which line they took.

## Temperature.csv

This is daily temperature from NOAA. We downloaded it for the Chicago Northerly Island station, but the file actually has two stations in it. It has 12,059 rows. 7,563 are from Northerly Island (USC00111550) and the other 4,496 are from Park Ridge (US1ILCK0192).

| Column | Type | What it is | Missing |
|---|---|---|---|
| STATION | text | NOAA station ID | 0 |
| NAME | text | Station name | 0 |
| LATITUDE | decimal | Station latitude | 0 |
| LONGITUDE | decimal | Station longitude | 0 |
| ELEVATION | decimal | Station elevation | 0 |
| DATE | text | The date as YYYY-MM-DD | 0 |
| TMAX | decimal | Highest temperature that day | 4,519 |
| TMIN | decimal | Lowest temperature that day | 4,546 |
| TOBS | decimal | Temperature when the reading was taken | 4,530 |
| TMAX_ATTRIBUTES, TMIN_ATTRIBUTES, TOBS_ATTRIBUTES | text | NOAA flags for each reading. We drop these. | |

## Water.csv

This is daily rain and snow from NOAA for the Park Ridge station. Each row is one day. It has 4,495 rows.

| Column | Type | What it is | Missing |
|---|---|---|---|
| STATION, NAME, LATITUDE, LONGITUDE, ELEVATION, DATE | | Same as Temperature.csv | 0 |
| PRCP | decimal | Precipitation that day | 179 |
| SNOW | decimal | Snowfall that day | 1,498 |
| SNWD | decimal | Snow depth on the ground | 3,391 |
| DAPR, MDPR | decimal | Multi-day precipitation total and the number of days it covers. We drop these. | |
| WESD, WESF | decimal | Water in the snow on the ground and in new snow. We drop these. | |
| Columns ending in _ATTRIBUTES | text | NOAA flags for each reading. We drop these. | |

## Tables we make in basic_clean_merge.ipynb

We don't save these as files yet.

- **transit** puts the bus and L data into one table. It has 2,461,407 rows. The columns are mode (bus or L), entity_id (route number or station ID), entity_name (route number or station name), date, daytype, rides, year, month, and dow (day of the week).
- **weather_daily** has one row per date with TMAX, TMIN, TOBS, PRCP, SNOW, and SNWD.
- **transit_weather_merged** joins transit and weather_daily on date. It has 1,154,613 rows. It only keeps dates that are in both tables.

## Cleaning we have done so far

- We took the commas out of rides and turned it into a number.
- We put all the dates in the same format so the tables can be joined.
- We changed W, A, and U to Weekday, Saturday, and Sunday/Holiday.
- Station 40140 shows up under two names (Skokie and Dempster-Skokie), so we kept the newest name.
- Some L stations had two rows for the same day in 2011 with slightly different counts. We averaged them, which took out 618 rows.
- We dropped the NOAA flag columns and DAPR, MDPR, WESD, and WESF.
- We filled missing PRCP, SNOW, and SNWD with 0.

## Things to look into

- Temperature.csv has 4,496 rows from the Park Ridge station, and in the merge those rows show up with no temperature values. This might explain most of the missing temperatures and why the weather merge has two rows per date. It could be worth seeing if we only need the Northerly Island rows.
- Missing rain and snow values are filled with 0 right now. SNWD has about 75% missing and SNOW has about 33% missing, so we may want to look at whether 0 is the best fill for those.
- 15,677 L rows have 0 entries. It would be good to look into why before the analysis.
- Temperature and precipitation come from two stations about 17 miles apart, which is something to keep in mind when we compare weather to ridership.
