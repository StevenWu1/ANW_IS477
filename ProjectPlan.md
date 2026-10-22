Overview: Describe the overall goal of your project and your planned approach
to achieve it. Explain what you aim to accomplish and outline the main steps or
methods you will use to execute the project (max 250 words).

○ Team: Clearly define team member roles and planned responsibilities.

○ Research or Business Question(s): What is/are the question(s) you intend to
address? These could be research questions, business questions, or analytical
questions you want to answer through data analysis.

### Chicago Climate Daily Summary

The climate data comes from the National Ocean and Atmospheric Administration (NOAA), National Centers for Environmental Information (NCEI), and consists of two station level daily summary datasets.
- The first dataset, from Park Ridge 0.7 Station, records precipitation and snow-related observations from August 31, 2011 through October 10, 2026. It contains **4495** rows and includes variables such as multiday precipitation total and snowfall. The data coverage is **78%** for precipitation, **54%** for snowfall and **21%** for snow depth.
- The second dataset, from Chicago Northerly Island Station, records air temperature data from June 1, 2005 through October 17, 2026. It contains **12059** rows of data and includes information such as max temperature, min temperature, and temperature at time of observation. The observations have a coverage of above **95%** for all three variables. 

Because the stations are geographically close to each other and the City of Chicago, together they provide precipitation/snow and temperature information for the area. The two datasets share the date variable, which allows them to be linked for joint analysis of weather conditions.

**Sources:**
- Precipitation: https://www.ncdc.noaa.gov/cdo-web/datasets/GHCND/stations/GHCND:US1ILCK0192/detail
- Air Temperature: https://www.ncdc.noaa.gov/cdo-web/datasets/GHCND/stations/GHCND:USC00111550/detail

### CTA Ridership: Route Total
The data originates from Chicago Transit Authority (CTA) published in the Chicago Data Portal. It displays the total bus rides for each route for every day between January 1, 2001 and July 31, 2026 amounting to a total of roughly **1.12 million** records. It contains four fields, which are route no(s), date, day type records, and total rides. Route refers to the route number. Day type indicates the nature of the day (whether it is a weekday (**W**), Saturday (**A**), or Sunday/holiday (**U**)). This dataset provides information for the first research question, since we can join it to the NOAA weather data on the date column. A key limitation is that some stations counted 0 daily riders for certain stops and should be double checked before making any conclusions.

**Source:** https://data.cityofchicago.org/Transportation/CTA-Ridership-Bus-Routes-Daily-Totals-by-Route/jyb9-n7fm/data_preview

### CTA Ridership: L Line Daily Totals
This dataset is also produced by the CTA and covers the same dates from January 1, 2001 to July 31, 2026 with almost **1.33 million** rows. The dataset consists of five columns: station_id, station name, date, day type, and rides. Each row shows the number of trapassengers entering that station on each day considering all the station’s turnstiles combined. Since it has the same date and day type columns as the data from the bus, comparisons can be made regarding trains and buses in terms of the effect of weather. However, this dataset counts passengers by stations, so it doesn’t specify whether the person at Belmont took Red, Brown, or Purple Line. Some station-days have 0 entries, so we should check those cases before making any conclusions.

**Source:** https://data.cityofchicago.org/Transportation/CTA-Ridership-L-Station-Entries-Daily-Totals/5neh-572f/about_data

### Data Linkage
The four main datasets will be integrated in the following sets
- Weather – Weather: Park Ridge Station precipitation/snow data and Northerly Island temperature data are merged on date to create a daily weather dataset.
- Weather – L-line: The daily weather profile is joined with the L-line dataset on date. This supports day level analysis of how temperature, precipitation, and snow related to rail ridership.
- Weather – Bus: The daily weather profile is joined with the bus dataset on date. This supports day level analysis of how temperature, precipitation, and snow related to bus ridership.
- L-line – Bus: The CTA bus route totals and L station entries share date, enabling comparison between bus and train ridership under weather and day-type.

Together, these datasets provide weather conditions and transit demands and can examine how daily precipitation, snow, and temperature affect Chicago bus and rail ridership while accounting for day type.


Timeline: Provide a draft of the plan and timeline for completing your project.
Include a list of specific tasks you need to accomplish, a brief description of each
task, when each task will be completed, and who will be responsible for
completing it.

Constraints: Describe any known limitations or challenges with your datasets or
approach. These might include legal or ethical restrictions, unknown data
provenance, technical difficulties in processing the data, issues with data
completeness, limited temporal or spatial coverage, accessibility barriers, or
other relevant concerns that could affect your work.

○ Gaps: Identify any known gaps or areas where you need additional input.

○ Your plan should anticipate later course topics even if you don’t yet know all the
details. It is expected that your plan will evolve over time.
