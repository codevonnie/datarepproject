# datarepproject

# Project title
## Data Representation and Querying Project 2015
### Yvonne Grealy

## Introduction
This project provides the design and documentation for the dataset "Disabled Parking Spaces" which is available at [data.gov.ie](https://data.gov.ie/dataset/disabled-parking-spaces).  The use of this dataset is to provide information to people who require disabled parking. The idea would be to make use of this information through an app which could provide up-to-date information regarding the exact location of spaces, nearby facilities and other pertinant information such as the marking of such spaces.  The original dataset is provided by Fingal County Council but the view would be that similar information would be held by other county councils around the country.  This dataset also contains a value called "Occupied" which could have a future idea of providing realtime information regarding whether a parking space is occupied at the time of a request.  

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
     
    ## List of spaces in a given street
You can get a list of spaces located in a given year using the GET method at the following URL:
*http://spacessapi.com/roadname/[roadname]*
where you replace [roadname] with the required road name.
For example, the URL:
*http://spacessapi.com/roadname/howthroad*
will return a list of disabled parking spaces on the Howth Road.
The data will be returned in JSON format, with the following properties for each space:

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

An example of a response would be:
```json    
{
    "ID":1084,
    "AREA_DESC":"St Marys Church",
    "ROADNAME":"Howth Road",
    "Area":"",
    "TOTAL_SPACES":2,
    "DIPPED_FOOTPATH":null,
    "PARK_SIGN":TRUE,
    "ROAD_MARKING":"No",
    "OCCUPIED":"No",
    "Adjacent_Services":"Church",
    "LAT":53.3883511,
    "LONG":-6.079238564
  }
```
