# AirBnB MongoDB Analysis

A little assignment to practice importing and analyzing data within a MongoDB database.


## Dataset Details
My dataset is about AirBnB listings in Broward County,Florida. This is the [link](http://data.insideairbnb.com/united-states/fl/broward-county/2021-02-23/data/listings.csv.gz) to the dataset. The file was originally in a CSV format, however MongoDB has no problem dealing with data which has a fixed schema.  
  

## Data Analysis

### Query 1
```javascript
db.listings.find().limit(2)
```  

### Query 2

```javascript
db.listings.find().limit(10).pretty()
```  
Sample Documents:

```javascript
{
	"_id" : ObjectId("6068accb7c6a86bb058d3b99"),
	"id" : 69824,
	"listing_url" : "https://www.airbnb.com/rooms/69824",
	"scrape_id" : NumberLong("20210223032208"),
	"last_scraped" : "2021-02-24",
	"name" : "2 bd/2ba Oceanfront Condo",
	"description" : "The space  Beautiful and meticulous 2 master suite luxury oceanfront condo fully furnished and equipped with WIFI, digital cable and unlimited long distance in the US and Canada.    Building is full of amenities including tennis court, swimming pool, jacuzzi, workout room, covered and valet parking, direct beach access. Call for additional details.",
	"neighborhood_overview" : "",
	"picture_url" : "https://a0.muscache.com/pictures/443102/f6b94ead_original.jpg",
	"host_id" : 351303,
	"host_url" : "https://www.airbnb.com/users/show/351303",
	"host_name" : "Tracy",
	"host_since" : "2011-01-17",
	"host_location" : "Silver Spring, Maryland, United States",
	"host_about" : "",
	"host_response_time" : "within an hour",
	"host_response_rate" : "100%",
	"host_acceptance_rate" : "80%",
	"host_is_superhost" : "t",
}

```

### Query 3  
After observing the query above, I noticed that both Tracy and Paul were superhosts. Tracy had a host_id of 351303. Paul had a host_id of 1097874

```javascript
let q3_filter = {
  "$or": [
    {
      host_id: 351303,
    },
    {
      host_id: 1097874,
    },
  ],
}

let q3_projection = {
    _id:0, 
    name: 1,
    price: 1, 
    neighbourhood: 1, 
    host_name: 1, 
    host_is_superhost: 1,
}

db.listings.find(q3_filter,q3_projection)
```  
Sample Documents: 
```javascript  
{ "name" : "2 bd/2ba Oceanfront Condo", "host_name" : "Tracy", "host_is_superhost" : "t", "neighbourhood" : "", "price" : "$140.00" }
{ "name" : "Gorgeous Private Las Olas-Idlewyld Home", "host_name" : "Paul", "host_is_superhost" : "t", "neighbourhood" : "Fort Lauderdale, Florida, United States", "price" : "$479.00" }
{ "name" : "Luxury Oceanfront Condo with Two Master suites", "host_name" : "Tracy", "host_is_superhost" : "t", "neighbourhood" : "", "price" : "$175.00" }
```
Insight:  
This shows that Tracy has two listings and Paul has one listing. Paul's listing costs about 479$, whereas Tracy has one listing for 140 and one listing for 175$.

### Query 4  
```javascript  
db.listings.distinct( "host_name" )
```  
Sample Documents:
```javascript
"A. Hanes",
"AMG Luxe",
"Aaron",
"Aaron Isaac",
```

### Query 5
```javascript
let q5_filter = {
  $match:{
    "neighbourhood_cleansed": "Hollywood",
    "beds": {
        $gt:2,
    },
    "review_scores_rating":{
        $ne:"",
    }
  }
}

let q5_projection = {
  $project:{
    _id:0,
    name:1,
    beds:1,
    city:1,
    review_scores_rating:1,
    price:1,
  }
}

let q5_sorting = {
    $sort:{
    review_scores_rating: -1
    }
}

db.listings.aggregate([q5_filter,q5_projection,q5_sorting])
```

Sample Documents: 
```javascript
{ "name" : "SPECTACULAR DIRECT OCEANFRONT VIEWS - Amazing", "beds" : 3, "price" : "$125.00", "review_scores_rating" : 100 }
{ "name" : "Quiet and Cozy yet Convenient", "beds" : 3, "price" : "$150.00", "review_scores_rating" : 100 }
{ "name" : "PENTHOUSE SUITE HOLLYWOOD BEACH,FL", "beds" : 3, "price" : "$128.00", "review_scores_rating" : 100 }
```  
  
Insight:  
One can rent a nice place in Hollywood Florida, with 3 or more beds for around the price range of $100-300. My dataset did not have the "neighbourhood_group_cleansed" field so instead I used the "neighbourhood_cleansed" field instead for the matching.

### Query 6

```javascript
let q6_grouping = {
  $group: {
  _id: "$host_id",
  listingCount: {$sum: 1}
  }
}
db.listings.aggregate([q6_grouping])
```
Sample Documents: 
```javascript
{ "_id" : 377647361, "listingCount" : 1 }
{ "_id" : 41837361, "listingCount" : 2 }
{ "_id" : 151861939, "listingCount" : 1 }
```

### Query 7

```javascript
let q7_grouping = {
  $group: {
    _id:"$neighbourhood_cleansed",
    avg_rating: {$avg:"$review_scores_rating"},
  },
};

let q7_matching = {$match:
  {avg_rating:{$gt:95 }}
}

let q7_sorting = {$sort:
  {avg_rating:-1}
}

db.listings.aggregate([q7_grouping,q7_matching,q7_sorting])
```  
  
Sample Documents: 
```javascript
{ "_id" : "Tribal Land", "avg_rating" : 100 }
{ "_id" : "Hillsboro Beach", "avg_rating" : 99.63636363636364 }
{ "_id" : "Southwest Ranches", "avg_rating" : 99.23076923076923 }
```
  
Insights:  
It appears Tribal Land, Hillsboro Beach, and Southwest Ranches are the 3 neighbourhoods in Broward country with the top average review score rating. Potential visitors may want to take this into account when choosing which neighbourhood to live in for their stay. My dataset did not have the "neighbourhood_group_cleansed" field so instead I used the "neighbourhood_cleansed" field instead for the grouping.

## Extra-credit
This assignment deserves extra credit. The file named extra_credit.py in the main directory reproduces query 5 using the pymongo module. This was the output on the terminal:

![sc1](./images/sc1.png)
![sc2](./images/sc2.png)
