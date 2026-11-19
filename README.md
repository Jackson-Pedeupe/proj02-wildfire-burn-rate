# Project 02 Proposal: Wild Fire Burn Rates

**Team members:** Jackson Pedeupe

See the [Project 02 instructions](https://data385.github.io/project/proj02_wholegame.html) for what goes in each section. Bullet points are great. Put any images in an `img/` folder.

## 1. Problem statement

The problem: Large wildfires have burned huge areas of California's forests and destroyed neighborhoods, homes, property, and taken lives over the past couple of years. Fast-spreading fires are the hardest to contain. 
Who has the problem? Communities that are in fire-prone areas in California and the agencies that are supposed to fight the fires, such as Cal Fire, U.S. Forest Service, and county fire departments. 
The decisions or needs: The agencies have limited prevention and early response resources and must decide where and when to focus them. 
Why it matters: Knowing which conditions are linked to fast-burning fires can help agencies decide when to increase prevention efforts and be ready to respond. 
What I expect to find: fires that start in the hot, dry months, such as June and July, especially during high droughts, will burn fastest because dry conditions leave plenty of fuel and very little to slow the fire down. 

## 2. Research question

How is a California wildfire’s burn rate (acres burned per day) associated with its cause, the month it started, and statewide drought conditions at the time?

## 3. Data acquisition

The data I plan to collect comes from Cal Fire's California Fire Parameters, which is a record of each fire's cause, start date, containment date, and acres burned. This comes from data.ca.gov. I will be joining it by year and month to NOAA's monthly statewide California Palmer Drought Severity Index and average temperature, and that will come from NOAA Climate at a Glance. 

### a. Confirm viability

I am downloading published CSV files. The scraping checklist does not apply to my data. 
Both of my datasets are public government data that anyone can download. 
Citations:
Fire Data: 
California Department of Forestry and Fire Protection (CAL FIRE), Fire and Resource Assessment Program (FRAP). California Fire Perimeters (all). California Natural Resources Agency Open Data. https://gis.data.ca.gov/datasets/CALFIRE-Forestry::california-fire-perimeters-all/explore. Accessed November 18, 2026.
NOAA Data:
NOAA National Centers for Environmental Information. Climate at a Glance: Statewide Time Series, California, Average Temperature, 1-month, all months, 1990–2026. https://www.ncei.noaa.gov/access/monitoring/climate-at-a-glance/statewide/time-series/4/tavg/1/0/1990-2026. Accessed November 18, 2026.
NOAA National Centers for Environmental Information. Climate at a Glance: Statewide Time Series, California, Palmer Drought Severity Index, 1-month, all months, 1990–2026. https://www.ncei.noaa.gov/access/monitoring/climate-at-a-glance/statewide/time-series/4/pdsi/1/0/1990-2026. Accessed November 18, 2026.
 The wildfire data was collected because Cal Fire submits fire parameters for each time that a certain amount of a type of vegetation burns (for example, 10 acres of timber or 50 acres of brush). These all then get combined into the dataset that I'm using, and NOAA's monthly values come from its climate divisional database. 

### b. Variables of interest

 burn_rate, quantitative, calculated from GIS_calculated_acres / days from alarm_date to containment_date.
 cause, categorical, cause
 start_month: categorical, month taken from alarm date 
 year, quantitative, year 
 agency, categorical, agency 
 pdsi quantitative, value in the drought file, joined by year and month 
 avg_temp: quantitative value in the temperature file, joined by year and month 

## 4. Data example

_Scraping: a URL and an annotated screenshot. Downloading: a link to your rendered `data_management.pdf` with `glimpse()`. Collecting: a screenshot of one example row._


## 5. EDA

To import the data, all three of my files are CSV files, so I'm going to use `read_csv`, and then I can use `glimpse` to check column types and any issues with importing. 
I will use `filter`, which will remove any prescribed burns and will only show actual wildfires. 
I will use `mutate` to calculate stuff such as burn rate and also to be able to split apart dates from the NOAA into the years and months. 
I will use left joins to join drought and temperature to the actual wildfire data by year and month. 
For missing data, I will use stuff such as `is.na` to drop any missing dates, and I can report how many were dropped. 
To explore the data, I will use different plots, such as a scatter plot, which can show burn rate versus drought and temperature. 

## 6. Modeling

Model: Multiple linear regression
Response: Burn rate being acres per day
Predictors: cause, start month, drought index, year, agency, and average temperature 
Why it works: My response is a numberr and I have multiple predictors of both categorical anbd quantitave variables. So linear regression lets me see how each predictor relates to burn rate.

## 7. Communicate

I will use a Querto website. 

## 8. LLM disclaimer

I used AI when brainstorming different project topics and then, once I got my topic, to help me narrow down possible sources that I could go and look at to find data similar to what we did for Project 1.
