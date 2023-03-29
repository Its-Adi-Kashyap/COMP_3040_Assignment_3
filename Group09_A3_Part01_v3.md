# Transit API  

The Transit API enables users to access comprehensive information about various transit options available throughout Manitoba. By providing details on modes of transportation, destinations, routes, and more, this API proves highly beneficial for several sectors, including the tourism industry, local transit applications, and map features.

### Endpoints:

The API offers the following endpoints. 

- `GET /api/route/{start point}&{end point}`
- `GET /api/route/{id}`
- `GET /api/mode/{route_id}`

##### Parameter:

* start_point (string) - The place where the route begins (required).
* end_point (string) - The final point of the route (required).
* route_id (int) - The ID of the route (required).


### Resources:  

This API has the following resources:-  

#### 1. Route

The Route resource returns the specified route based on the provided parameters. It contains the following information:

```JSON
{
    "Mode": "string",
    "City": "string",
    "Start Point": "string",
    "End Point": "string",
    "Duration": "string",
    "Frequency": "string",
    "Stops": ["string_1","string_2",...]
}
```

In this response, Mode represents the method of travel (e.g., bus, train, car),City is where the transit is located in, Start_Point is the location where the transit originates, and End_Point is the final destination. Duration is the estimated time it takes to travel the route, Frequency indicates the interval between two consecutive trips, and Stops list the names of all stations along the way. 

#### 2. Modes 

Modes represent all the available transportation options for a particular route. This resource returns the following object:

```JSON
{
    "Modes": [{ "Name": "string","Time": "string"},....]
}
    
```

In this response, a list of all the modes is returned, with each item containing the Name of the transportation mode and the estimated time of travel for that specific mode.

### Example:

1. `GET /api/route/Winnipeg&Churchill`
    * On a STATUS Code 200 OK the response is:
    ```JSON
    {
        "Mode": "Train",
        "City": "Winnipeg"
        "Start Point": "Union Station Winnipeg",
        "End Point": "Churchill",
        "Duration": "2 days",
        "Frequency": "Once a week",
        "Stops": ["The Pas","Pukatawagan","Thompson"]
    }
    ```
    * On a STATUS Code of 400 it returns ***INVALID_REQUEST***
    * On a STATUS Code of 404 it returns ***NO_ROUTE_FOUND***
    
2. `GET /api/route/5`
    * On a STATUS Code of 200 it returns:
    ```JSON
    {
        "Mode": "Bus",
        "City": "Winnipeg",
        "Start Point": "Chancellor Matheson",
        "End Point": "Osborn Station",
        "Duration": "15 mins",
        "Frequency": "Every 15 minutes",
        "Stops": ["Pembina@Bison Nort","SouthWest Transit Way@Chancellor Station","SouthWest Transit Way@Plaza"]
    }
    ```
    * On a STATUS Code of 400 it returns ***INVALID_REQUEST***
    * On a STATUS Code of 404 it returns ***NO_ROUTE_FOUND***
    
3.  `GET /api/mode/12`
    * On a STATUS Code of 200 it returns:
    ```JSON
    {
      {"Name": "Bus","Time": "3 hours"},
      {"Name": "Train","Time": "6 hours"},
      {"Name": "Plane","Time": "1 hours"}
      
    }
    ```
    * On a STATUS Code of 400 it returns ***INVALID_REQUEST***
    * On a STATUS Code of 404 it returns ***NO_ROUTE_FOUND***
