# Transit API  

Transit API allows user to get all kinds of information about the various transit options provides throughout Manitoba.From mode of transport, destinations, routes etc.  This API would be highly benifical for a number of areas including tourism industry, local transit applications. map feartures etc.  

### Endpoints:
The API will have the following endpoints.  
- `GET /api/route/{start point,end point}`
- `GET /api/route/{id}`
- `GET /api/mode/{route_id}`

##### Parameter:
* start point(string)= The place where the route starts.(required)   
* end point(string)= The final point of the route.(required)  
* route_id(int)= The id of the route.(required) 



### Resources:  
This API has the following resources:-  
#### 1. Route

Route is the resource that returns the specified route by the parameter which cointains information given below:  
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

Here, `Mode` is the method of travel (bus,train,car) `Start Point` is the base from where the transit originally starts and `End Point` is the final destination. `Duration` is the estimated time it takes to travell the route and `Frequency` as the name suggests is the interval between 2 consecutive travells and finally `Stops` are the name of all the stations on the way.  
#### 2. Modes 

Modes are all the modes that are available fot a particular route. It returns the following object:
```
{
    "Modes": [{ "Name": "string","Time": int},....]
}
    
```
Here, a list of all the modes are returned which cointains `Name` is the mode name and `Time` is the estimated time of travel for that given mode.  

### Example::
(add example here) 
