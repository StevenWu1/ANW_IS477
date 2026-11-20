## Timeline

| **Task**                                   | **Target Completion** | **Status** |
| ------------------------------------------ | --------------------- | --------------------- |
| Dataset identification and acquisition     | Week 9                | Complete              |
| Initial exploration                        | Week 9-10             | Complete              |
| Data cleaning and preparation for analysis | Week 10-11            | Complete              |
| Dataset integration                        | Week 11               | Complete              |
| Exploratory analysis                       | Week 11               | In Progress           |
| Visualizations and interpretations         | Week 12-13            | In Progress           |
| Findings and recommendations               | Week 14               | Not Started           |
| Final documentation and submission         | Week 15               | Not Started           |

## Steven Wu
For this milestone, I was responsible for the initial data loading and exploratory analysis in Python. I imported the project datasets `Bus_Routes.csv`, `L_Stations.csv`, `Temperature.csv`, and `Water.csv` then inspected their structure, including rows/columns, data types, and missing values. I used this initial exploration to identify and extract columns relevant to our planned analysis, filling NA values where appropriate. I also performed an initial merge between the temperature and weather data which helped with later merged tables.

My exploration work is recorded in `initial_exploration.ipynb`, and th early merge work at the start of `basic_clean_merge.ipynb`.

## Sree Datla
As part of this milestone, I was responsible for the data documentation for our project. I authored a data dictionary, `DataDictionary.md`, that describes each one of our four datasets, `Bus_Routes.csv`, `L_Stations.csv`, `Temperature.csv`, and `Water.csv`. For each dataset, I wrote about its origin, the meaning of each row, the total number of rows, and the interpretation of each column. I also recorded the data types and the missing values in each column utilizing the data available in `initial_exploration.ipynb`.

I also provided information on the tables we created in `basic_clean_merge.ipynb`, such as transit, weather_daily, and transit_weather_merged, as well as the number of rows in each table. Additionally, I described the steps that were undertaken by the team to clean this data; for example, removing commas from ride counts, replacing day type codes, averaging duplicates for L station rows, and filling in missing values of precipitation. Having all of this in one place makes it easier to understand the collected data.

In my review of the data, I noticed some issues that may be of interest to the team. First, the `Temperature.csv` file comprises data from two different stations, with the Park Ridge station lacking temperature data. Second, a lot of the snow data is missing, and certain L stations have 0 entries on some days. I’ve made a note of this to ensure we address these issues prior to analysis.

My next step will be to work on developing the metadata files and documenting the data quality process for the final submission.


## Brandon Gacek
So far, my work has been mainly related to the initial analysis of all 4 data sets. I reviewed the content of each, and deciphered some variables that may need to be averaged or dealt with in another manner before we continue further into our analysis. Additionally, I created several visualizations depicting exploratory findings. I hope these visualizations can contribute to our basis for hypotheses.

Firstly, I created a monthly ridership graph, which displays a generally downward trend in public transit usage even before the pandemic in 2020. Ridership generally trends upward after that point, only the more recent data in the set showing a level back to where it was prior to the pandemic.

There are visualizations displaying the top 10 most popular bus routes by total ridership across our entire dataset, and the days of the week with the highest average ridership. The first shows a dominate trend in favor of route 79, amassing over 200 million riders in the 25-year span that our bus dataset covers. Bus route 9 is the second most popular, and the trend generally levels out after this. The most popular days of the week on average are weekdays to no surprise, with an average daily ridership of around 6,000. Next is Saturdays with 5,500 riders, and finally Sundays with 4,100 riders.

In fourth visualization, we combined variables from two datasets instead of relying on just the bus ridership csv. We attempted to graph the relationship between bus ridership and maximum temperature for each day. This required us to take the average maximum temperature for the days that reported multiple due to reports from multiple stations being included on the same days in the dataset. Due to the sheer number of days in the datasets, there is really no distinguishable pattern. One takeaway is that daily rides seems to decrease slightly when the maximum temperature is below 20 degrees Farenheit, but there is not enough days from the dataset to fully flesh out this claim.

Next in the project, I am aiming to investigate more about the cross-dataset relationships between all 4 compiled datasets. My analysis will likely include but not be limited to further pattern and visual analysis, metric calculation (such as correlation), and regression analysis.



## Gabe Ruiz
My work for this report was the final cleanup and merging of the different data sources. I started off with the tables that Steven hadn't merged yet, `Bus_Routes.csv` and `L_Stations.csv`, and looked at the fields that needed to be changed so they could merge nicely. I started off cleaning them individually but noticed that because the structure of both datasets are so similar, I could instead write a function that standardizes the dates and entities much faster. The function `clean_transit` makes sure that dates are the same and that numbers don't have any commas and creates and ID column based on the user's input.

With both of the datasets cleaned it was time to merge them. Because the data is now nicely formated pandas concat works fine. I then made sure the dates are usable for graphing and visualization purposes and added daytypes for future trend seeing. As we explore the data further we may need to add more columns and dummy varaibles, but these seemed fine for what we need right now. 

Next up was to merge this transit dataset with the weather one that Steven made. The main issue comes from the `temp_station` column. This row separates the two weather beacons that we're looking at and when visualizing and analyzing we need to choose whether we want to aggregate them or look at them separately. Our group hadn't come to a concrete conclusion yet, so I decided to do two merges between the weather and transit data: one that keeps the stations separate and is easily groupable by the station, and one that averages the stations and gives a view of the whole city. For the station separate one, I had to reformat the weather merge a little so that it would keep the station identity; the aggregated one didn't need such changes. 

Up next is to wait for the visualizations and basic analysis to be finished and then I'll add input to them.
