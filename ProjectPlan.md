## Overview

Through our analysis, we will explore the relationship between weather conditions and public transportation ridership in Chicago; more specifically, what effects variables like precipitation, air temperature, snowfall, and other indicators have on the amount of riders across bus lines and train lines on that specific day. By identifying potential patterns between the linked datasets, we hope to better understand how weather can influence transportation usage / demand and identify insights that could support more efficient public transport planning.

To accomplish this, we’ll be combining three datasets from the City of Chicago and the National Centers for Environmental Information. Our data sets include Chicago climate daily summary, CTA ridership for buses, and CTA ridership for trains. After joining the tables through common variables such as day, line, and route, we will then analyze the patterns, if any, present across the datasets by calculating grouped statistics and generating visualizations. Finally, we will interpret our findings, considering any confounding factors and attempting to pin reasons for why we see the patterns (or lack thereof) that we do. Throughout the project, we will account for missing values, differences in data formats, and data limitations to ensure that our conclusions are appropriately supported by the story being told by the data itself.

## Responsibilities
Our team members will have the following responsibilities:
- Steven Wu: Download, integrate, and describe weather data.
- Gabriel Ruiz Camargo: Timeline, constraints, completeness.
- Brandon Gacek: Facilitate and organize written and visual analysis.
- Sree Datla: Data specifics and documentation.

## Research Questions
Our research questions are as follows:
- What effect do specific weather conditions have on public transportation ridership in Chicago?
- Do we see ridership increase or decrease under certain conditions? Which ones?
- Why do we think a relationship (or lack there of) exists? Are we able to draw conclusions that could be useful for the City of Chicago’s transportation department towards efficient planning? What are they?

## Data

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

## Timeline

| **Task**                                   | **Target Completion** | **Primary Member(s)** |
| ------------------------------------------ | --------------------- | --------------------- |
| Dataset identification and acquisition     | Week 9                | Steven, Gabe          |
| Initial exploration                        | Week 9-10             | All members           |
| Data cleaning and preparation for analysis | Week 10-11            | All members           |
| Dataset integration                        | Week 11               | Steven, Gabe          |
| Exploratory analysis                       | Week 11               | All members           |
| Visualizations and interpretations         | Week 12-13            | Brandon, Sree         |
| Findings and recommendations               | Week 14               | Brandon, Sree         |
| Final documentation and submission         | Week 15               | All members           |

## Constraints
Using datasets from multiple sources brings the question of possible format and upload differences. We will need to standardize the data and verify that the integration process produces sensible and valid relationships/conclusions. Additionally, we are attempting to pull specified data from a website based on our inputs, which of course could be limited in the scope of the variables and dates. For example, there may be gaps or slight differences in the date variable or line between datasets that require explicit grouping to begin. In the case of missing values/gaps, we can impute the average, median, or a value of 0 based on the variable and reasonableness given the observation, or we can afford to drop it altogether.

Another thing to take into account is the translation of weather into several numeric variables. Firstly, the isolation of variables: A sunny day and a blizzard may have similar wind speeds, for example. It’s important we take into account the overall weather situation by combining variables for analysis. Secondly, weather is arguably not able to be captured as a whole by simply reporting values for barometric pressure, UV, and rain. This inherently taints the credibility of our data slightly, and thus also our conclusions. We are limited in the final advice we can give.

The selected sources are official government providers, which should improve formality and transparency of processes. However, we will still review collection methods, definitions, and usage terms rather than assuming that every variable is complete or directly comparable. Regarding usage terms, these organizations publish this information online in a professional format, which we can assume is opening the data up for any use and analysis.

## Gaps
Several aspects of the project require further investigation as we proceed. We need to confirm the precise variables, date ranges, and levels of aggregation we are including from each dataset. In particular, we must decide and obtain our weather data from a specific (also to be determined) range. As we progress through the course, we may learn additional statistical techniques that could help us investigate relationships more in-depth. We will begin with simple descriptive statistics and visualizations, then consider whether more advanced methods are applicable for our data. Finally, we should inquire about holidays, day of the week, service disruptions, or other relevant factors that could impact our findings without knowing. These variables could help us distinguish weather-related patterns from other influences on ridership.

