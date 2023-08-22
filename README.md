# nosql-challenge

_Using nosql and pandas to analyse food safety ratings data_
***

### Project Overview

The UK Food Standards Agency evaluates various establishments across the United Kingdom, and gives them a food hygiene rating. You've been contracted by the editors of a food magazine, Eat Safe, Love, to evaluate some of the ratings data in order to help their journalists and food critics decide where to focus future articles.
***

### Part 1 
- Set up a Database and Jupyter Notebook
        
### Part 2
- Update the Database
> The magazine editors have some requested modifications for the database before you can perform any queries or analysis for them. 
        
### Part 3 Exploratory Analysis
> Eat Safe, Love has specific questions they want you to answer, which will help them find the locations they wish to visit and avoid.
***
        
## Acknowledgements

__The following reference assisted in creating the code shown below:__<br>
- https://www.mongodb.com/docs/manual/reference/operator/aggregation/toDouble/

> Change the data type from String to Decimal for longitude
Change the data type from String to Decimal for latitude
establishments.update_many({}, [{'$set': {'geocode.longitude': {'$toDouble': '$geocode.longitude'},
                                         'geocode.latitude': {'$toDouble': '$geocode.latitude'}
                                         }
                                }
                               ]
                          )

__The following reference assisted in creating the code shown below:__<br>
https://www.bmc.com/blogs/mongodb-geolocation-query-examples/

> Search within 0.01 degree on either side of the latitude and longitude.
Rating value must equal 5
Sort by hygiene score
degree_search = 0.01
latitude = 51.490142
longitude = 0.08384
top5_query = {'RatingValue': '5',
        'geocode.latitude': {'$lte': (latitude + degree_search), '$gte': (latitude - degree_search)},
        'geocode.longitude': { '$lte': (longitude + degree_search), '$gte': (longitude - degree_search)}
        }


