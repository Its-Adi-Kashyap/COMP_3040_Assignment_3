# Transit API  

The Transit API enables users to access comprehensive information about various transit options available throughout Manitoba. By providing details on modes of transportation, destinations, routes, and more, this API proves highly beneficial for several sectors, including the tourism industry, local transit applications, and map features.

### Endpoints:

The API offers the following endpoints. 

- `GET /api/route/{start point,end point}`
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

```
{
    "Mode": "string"
    "Start Point": "string",
    "End Point": "string",
    "Duration": int,
    "Frequency": int,
    "Stops": ["string_1","string_2",...]
}
```

In this response, Mode represents the method of travel (e.g., bus, train, car), Start_Point is the location where the transit originates, and End_Point is the final destination. Duration is the estimated time it takes to travel the route, Frequency indicates the interval between two consecutive trips, and Stops list the names of all stations along the way. 

#### 2. Modes 

Modes represent all the available transportation options for a particular route. This resource returns the following object:

```
{
    "Modes": [{ "Name": "string","Time": int},....]
}
    
```

In this response, a list of all the modes is returned, with each item containing the Name of the transportation mode and the estimated time of travel for that specific mode.

### Example::
(add example here) 
