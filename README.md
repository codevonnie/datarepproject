# Data Representation and Querying Project 2015
## Disabled Parking Spaces Dataset
### Yvonne Grealy

## Introduction
This project provides the design and documentation for the dataset "Disabled Parking Spaces" which is available at [data.gov.ie](https://data.gov.ie/dataset/disabled-parking-spaces).  

The use of this dataset is to provide information to people who require disabled parking. The idea would be to make use of this information through an app which could provide up-to-date information regarding the exact location of spaces, nearby facilities and other pertinant information such as the marking of such spaces and whether there are dipped footpaths for users that use wheelchairs or walking aids.  The original dataset is provided by Fingal County Council but the view would be that similar information would be held by other county councils around the country.  

This dataset also contains a value called "Occupied" which could have a future idea of providing realtime information regarding whether a parking space is occupied at the time of a request. 

## About the data
This dataset was received in Comma Separated Values (CSV) format, and was downloaded from [data.gov.ie](https://data.gov.ie/dataset/disabled-parking-spaces).
The CSV file contains 1187 rows, the first being a header row with the names of each field.
There are twelve values on each line, which are as follows:

- __id__: the unique id of the specific entry.
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

#### List of spaces in a given street
You can get a list of spaces located in a given street using the GET method at the following URL:
*http://spacessapi.com/roadname/[roadname]*
where you replace [roadname] with the required road name.
For example, the URL:
*http://spacessapi.com/roadname/howthroad*
will return a list of disabled parking spaces on the Howth Road.
The data will be returned in JSON format, with the following properties for each space:

- **ROADNAME**: the name of the street.
- **Area_Desc**: a basic description of the area.
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
    "ROADNAME":"Howth Road",
    "AREA_DESC":"St Marys Church",
    "TOTAL_SPACES":2,
    "DIPPED_FOOTPATH":"TRUE",
    "PARK_SIGN":"TRUE",
    "ROAD_MARKING":"No",
    "OCCUPIED":"No",
    "Adjacent_Services":"Church",
    "LAT":53.3883511,
    "LONG":-6.079238564
  }
```

#### List of spaces close to a given service
 
You can get a list of spaces located near a specified service using the GET method at the following URL:
*http://spacessapi.com/services/[services]*
where you replace [service] with the requested service.
For example, the URL:
*http://spacessapi.com/service/hairdresser*
will return a list of disabled parking spaces near to the specified serviced.
The data will be returned in JSON format, with the following properties for each space:

- **Adjacent_Services**: what services are in the immediate locale.
- **ROADNAME**: the name of the street.
- **Area_Desc**: a basic description of the area.
- **TOTAL_SPACES**: the number of disabled spaces in given area.
- **DIPPED_FOOTPATH**: true if the footpath nearby is dipped for access by people with wheelchairs.
- **PARK_SIGN**: true if there is a sign indicating the parking space.
- **ROAD_MARKING**: true if there is a road marking indicating the parking space.
- **OCCUPIED**: true if the space is currently occupied.
- **LAT**: the latitude co-ordinates of the space.
- **LONG**: the longtitude co-ordinates of the space.

An example of a response would be:
```json    
{
    "Adjacent_Services":"Hairdressers",
    "AREA_DESC":"Chapel Street",
    "ROADNAME":"Chapel Street",
    "TOTAL_SPACES":2,
    "DIPPED_FOOTPATH":"TRUE",
    "PARK_SIGN":"TRUE",
    "ROAD_MARKING":"TRUE",
    "LAT":53.61029459,
    "LONG":-6.186854504
  }
```
#### List of spaces close to a users current location

*This query may require extra information for use with GPS.*
 
You can get a list of spaces located near the users current location using the POST method at the following URL:
*http://spacessapi.com/location/[location]*
where the [location] is replaced with the users current location.
This would work where the URL would contain the returned longtitude and latitude of the current location and compare it to results in the dataset and then return a list of disabled parking spaces near to the specified location.  This could be used in conjunction with GPS mapping.

The data will be returned in JSON format, with the following properties for each space:

- **LAT**: the latitude co-ordinates of the space.
- **LONG**: the longtitude co-ordinates of the space.
- **Adjacent_Services**: what services are in the immediate locale.
- **ROADNAME**: the name of the street.
- **Area_Desc**: a basic description of the area.
- **TOTAL_SPACES**: the number of disabled spaces in given area.
- **DIPPED_FOOTPATH**: true if the footpath nearby is dipped for access by people with wheelchairs.
- **PARK_SIGN**: true if there is a sign indicating the parking space.
- **ROAD_MARKING**: true if there is a road marking indicating the parking space.
- **OCCUPIED**: true if the space is currently occupied.

An example of a response would be:
```json    
{
    "LAT":53.61029459,
    "LONG":-6.186854504,
    "Adjacent_Services":"Hairdressers",
    "AREA_DESC":"Chapel Street",
    "ROADNAME":"Chapel Street",
    "TOTAL_SPACES":2,
    "DIPPED_FOOTPATH":"TRUE",
    "PARK_SIGN":"TRUE",
    "ROAD_MARKING":"TRUE",
  }
```
This query could be further enhanced if the Occupied field of the dataset was in the future implemented by the county council so that users would be able to not only find disabled parking near their current location but also spaces that are currently unoccupied.

##Closing Statement

The use of this api is to provide information to users who require disabled parking including groups that may work with people with disabilities.  There is a wealth of data provided in the dataset that can be used to create useful, practical information to users.  Some of the data is such that will require minimum manipulation but will provide helpful information such as the information given from roadnames and nearby services.  Other data such as the location coordinates can be used to give exact locations and used with other api's could provide the data in map form.  

There is also potential for future growth within the dataset with the inclusion of the Occupied field which could be used to provide up-to-date, realtime information on the current availability of the space.  The dataset is provided by Fingal County Council but there is room for potential expansion if other County Councils would be interested in gathering similar data which could result in a countrywide dataset.
