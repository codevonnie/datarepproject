# datarepproject

# Project title
## Data Representation and Querying Project 2015
### Yvonne Grealy

## Introduction
This project provides the design and documentation for the dataset "Disabled Parking Spaces" which is available at [data.gov.ie](https://data.gov.ie/dataset/disabled-parking-spaces).  

## About the data
This dataset was received in Comma Separated Values (CSV) format, and was downloaded from [data.gov.ie](https://data.gov.ie/dataset/disabled-parking-spaces).
The CSV file contains 1187 rows, the first being a header row with the names of each field.
There are twelve values on each line, which are as follows:
    - **id**: the unique id of the specific entry.
    - **Area_Desc**: a basic description of the area.
    - **ROADNAME**: the name of the street.
    - **Area**: currently blank column.
    - **TOTAL_SPACES**: the number of disabled spaces in given area.
    - **DIPPED_FOOTPATH**: true if the footpath nearby is dipped for access by people with wheelchairs.
    - **PARK_SIGN**: true if there is a sign indicating the parking space.
    - **ROAD_MARKING**: true if there is a road marking indicating the parking space.
    - **OCCUPIED**: true if the space is currently occupied.
    - **Adjacent_Services**: what services are in the immediate locale.
    - **LAT**: the latitude co-ordinates of the space.
     - **LONG**: the longtitude co-ordinates of the space.
    
    ## List of cars for a given year
You can get a list of cars purchased in a given year using the GET method at the following URL:
*http://carsapi.com/year/[year]*
where you replace [year] with the year.
For example, the URL:
*http://carsapi.com/year/2005*
will return a list of cars purchased in 2005.
The data will be returned in JSON format, with the following properties for each car:
    - *price*: the price of the car.
    - *model*: the model of the car.
    ...
An example of a response would be:
    ```json
    [ {"price": 20000, "model": "Skoda", ...}, {...}, ...]
