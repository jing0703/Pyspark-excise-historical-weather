# Historical Weather Data Anlysis By Pyspark

## Introduction

The aim of this project is to build a Spark ETL pipeline to load and process historical weather data from UK to analyze the climate change.

## Datasets

Monthly data are available for a selection of long-running historic stations across UK. The series typically range from 50 to more than 100 years in length.

[Data source](https://www.metoffice.gov.uk/public/weather/climate-historic): total 37 station's data is ingested for the analysis.

Data content: 
- Mean daily maximum temperature (tmax)
- Mean daily minimum temperature (tmin)
- Days of air frost (af)
- Total rainfall (rain)
- Total sunshine duration (sun)

## Goals

1. Load and parse UK Weather Station History data. 
2. Combine all stations so can run queries across all stations and all time periods.
3. Handle source file format anomalies.
4. Statistics analysis for climate change:

   a. Rank stations by how long they have been online 
   
   b. Rank stations by rainfall and / or sunshine
   
   c. When was the worst rainfall and / or best sunshine for each station
   
   d. What are the averages for May across all stations, what was the best / worst years 

## Other considerations
1. The code is set up to run standalone but could be modified to fit scaled up data with spark configrations.
2. The code parse all files and handle known issues as some have quirks and inconsistencies:

    a. Ignore the header / metadata section of the files but keep in mind the length of the header varies in a few cases. We’re only interested in the measures per station.
    
    b. Columns are fixed width, whitespace separated but there are columns missing and not consistently marked with “---”.
    
    c. Strip out other special annotations (e.g. “provisional” or *).
