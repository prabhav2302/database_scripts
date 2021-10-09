# AirBnB MongoDB Analysis

A little assignment to practice importing and analyzing data within a MongoDB database.


## Dataset Details
My dataset is about AirBnB listings in Broward County,Florida. This is the [link](http://data.insideairbnb.com/united-states/fl/broward-county/2021-02-23/data/listings.csv.gz) to the dataset. The file was originally in a CSV format, however MongoDB has no problem dealing with data which has a fixed schema.  
  

## Data Analysis

### Query 1
```javascript
db.listings.find().limit(2)
```  
  
Sample Documents:
```javascript
{ "_id" : ObjectId("6068accb7c6a86bb058d3b99"), "id" : 69824, "listing_url" : "https://www.airbnb.com/rooms/69824", "scrape_id" : NumberLong("20210223032208"), "last_scraped" : "2021-02-24", "name" : "2 bd/2ba Oceanfront Condo", "description" : "The space  Beautiful and meticulous 2 master suite luxury oceanfront condo fully furnished and equipped with WIFI, digital cable and unlimited long distance in the US and Canada.    Building is full of amenities including tennis court, swimming pool, jacuzzi, workout room, covered and valet parking, direct beach access.    Conveniently located in Hallandale Beach between Miami and Fort Lauderdale, you’re just minutes from two international airports, two seaports, as well as world-class shopping at Bal Harbour and Aventura. And just minutes away from Hollywood Beach Boardwalk, one of the five best boardwalks in the country as ranked by Travel & Leisure.    Minimum rental is 30 days.  Available beginning May 1st, 2011.    Call for additional details.", "neighborhood_overview" : "", "picture_url" : "https://a0.muscache.com/pictures/443102/f6b94ead_original.jpg", "host_id" : 351303, "host_url" : "https://www.airbnb.com/users/show/351303", "host_name" : "Tracy", "host_since" : "2011-01-17", "host_location" : "Silver Spring, Maryland, United States", "host_about" : "", "host_response_time" : "within an hour", "host_response_rate" : "100%", "host_acceptance_rate" : "80%", "host_is_superhost" : "t", "host_thumbnail_url" : "https://a0.muscache.com/im/users/351303/profile_pic/1304341323/original.jpg?aki_policy=profile_small", "host_picture_url" : "https://a0.muscache.com/im/users/351303/profile_pic/1304341323/original.jpg?aki_policy=profile_x_medium", "host_neighbourhood" : "", "host_listings_count" : 2, "host_total_listings_count" : 2, "host_verifications" : "['email', 'phone', 'facebook', 'kba']", "host_has_profile_pic" : "t", "host_identity_verified" : "t", "neighbourhood" : "", "neighbourhood_cleansed" : "Hallandale Beach", "neighbourhood_group_cleansed" : "", "latitude" : 25.9784, "longitude" : -80.12028, "property_type" : "Entire apartment", "room_type" : "Entire home/apt", "accommodates" : 6, "bathrooms" : "", "bathrooms_text" : "2 baths", "bedrooms" : 2, "beds" : 4, "amenities" : "[\"Smart lock\", \"Hair dryer\", \"Iron\", \"Dryer\", \"Dedicated workspace\", \"Elevator\", \"Free parking on premises\", \"Long term stays allowed\", \"Hot tub\", \"Pool\", \"Cable TV\", \"Wifi\", \"Washer\", \"Hangers\", \"TV\", \"Heating\", \"Kitchen\", \"Air conditioning\", \"Gym\"]", "price" : "$140.00", "minimum_nights" : 30, "maximum_nights" : 365, "minimum_minimum_nights" : 30, "maximum_minimum_nights" : 30, "minimum_maximum_nights" : 365, "maximum_maximum_nights" : 365, "minimum_nights_avg_ntm" : 30, "maximum_nights_avg_ntm" : 365, "calendar_updated" : "", "has_availability" : "t", "availability_30" : 0, "availability_60" : 29, "availability_90" : 59, "availability_365" : 334, "calendar_last_scraped" : "2021-02-24", "number_of_reviews" : 1, "number_of_reviews_ltm" : 0, "number_of_reviews_l30d" : 0, "first_review" : "2018-02-11", "last_review" : "2018-02-11", "review_scores_rating" : 100, "review_scores_accuracy" : "", "review_scores_cleanliness" : "", "review_scores_checkin" : "", "review_scores_communication" : "", "review_scores_location" : "", "review_scores_value" : "", "license" : "", "instant_bookable" : "f", "calculated_host_listings_count" : 2, "calculated_host_listings_count_entire_homes" : 2, "calculated_host_listings_count_private_rooms" : 0, "calculated_host_listings_count_shared_rooms" : 0, "reviews_per_month" : 0.03 }
{ "_id" : ObjectId("6068accb7c6a86bb058d3b98"), "id" : 57818, "listing_url" : "https://www.airbnb.com/rooms/57818", "scrape_id" : NumberLong("20210223032208"), "last_scraped" : "2021-02-23", "name" : "Private house close to the beach!", "description" : "Beautifully private duplex that allows you to enjoy the zen of life!  Watch the neighbors walking their pets...jogging near the lake...or riding their bikes, or join in and jog to the beach!  If you don't want to disconnect...we have WIFI!  Please note:  Since this is my home, I only rent to people who aren't afraid to put a validated picture/profile (that AIRBNB has verified) on their page before I decide. Don't hide who you are...  The space  Peaceful house on Nature Preserve Close to everything. Hollywood, Florida Vacation Rental, South East, Florida, USA  Accommodations: 2 bedrooms and 1 full bathrooms. This house has a living room with a leather sectional and a beautiful fireplace (even though it's Florida). Beautifully loaded kitchen w/granite countertops and bar, Dining Room, Living room. Tres Chique!   New flat screen TV.  Can sleep 4.   This precious house is located on a quiet street. There is beautiful walking, jogging and biking", "neighborhood_overview" : "This is a family oriented, quiet, peaceful neighborhood, so please respect your neighbors.  This is a duplex, renters in back house (seperate).", "picture_url" : "https://a0.muscache.com/pictures/347696/9d51689b_original.jpg", "host_id" : 275948, "host_url" : "https://www.airbnb.com/users/show/275948", "host_name" : "VonJon", "host_since" : "2010-11-01", "host_location" : "Hollywood, Florida, United States", "host_about" : "I love my house...the neighbors are wonderful, and I would love to share it with you!  We love food...big foodies!  We try to eat healthy, but do like our deserts!     I will help you in anyway possible...I know a lot of things to do...restaurants in the area that are exceptional...kid activities, golf courses, etc.  Just let me know!  ", "host_response_time" : "within an hour", "host_response_rate" : "100%", "host_acceptance_rate" : "71%", "host_is_superhost" : "f", "host_thumbnail_url" : "https://a0.muscache.com/im/pictures/user/1f2670bf-576e-4ec9-bb6c-69276c8f520f.jpg?aki_policy=profile_small", "host_picture_url" : "https://a0.muscache.com/im/pictures/user/1f2670bf-576e-4ec9-bb6c-69276c8f520f.jpg?aki_policy=profile_x_medium", "host_neighbourhood" : "", "host_listings_count" : 1, "host_total_listings_count" : 1, "host_verifications" : "['email', 'phone', 'facebook', 'reviews', 'jumio', 'offline_government_id', 'selfie', 'government_id', 'identity_manual']", "host_has_profile_pic" : "t", "host_identity_verified" : "t", "neighbourhood" : "Hollywood, Florida, United States", "neighbourhood_cleansed" : "Hollywood", "neighbourhood_group_cleansed" : "", "latitude" : 26.0167, "longitude" : -80.12437, "property_type" : "Entire house", "room_type" : "Entire home/apt", "accommodates" : 5, "bathrooms" : "", "bathrooms_text" : "1 bath", "bedrooms" : 2, "beds" : 2, "amenities" : "[\"Bed linens\", \"Dedicated workspace\", \"BBQ grill\", \"Indoor fireplace\", \"Dishes and silverware\", \"Single level home\", \"Hangers\", \"TV\", \"Stove\", \"Wifi\", \"Kitchen\", \"Free street parking\", \"Dishwasher\", \"Hair dryer\", \"Iron\", \"Refrigerator\", \"Microwave\", \"Patio or balcony\", \"Coffee maker\", \"Cable TV\", \"Shampoo\", \"Essentials\", \"Oven\", \"Children\\u2019s dinnerware\", \"Private entrance\", \"Lockbox\", \"Fire extinguisher\", \"Heating\", \"Air conditioning\", \"Children\\u2019s books and toys\", \"Hot water\", \"Extra pillows and blankets\", \"Smoke alarm\", \"Free parking on premises\", \"Long term stays allowed\", \"Bathtub\", \"Cooking basics\"]", "price" : "$125.00", "minimum_nights" : 2, "maximum_nights" : 30, "minimum_minimum_nights" : 2, "maximum_minimum_nights" : 2, "minimum_maximum_nights" : 30, "maximum_maximum_nights" : 30, "minimum_nights_avg_ntm" : 2, "maximum_nights_avg_ntm" : 30, "calendar_updated" : "", "has_availability" : "t", "availability_30" : 8, "availability_60" : 26, "availability_90" : 56, "availability_365" : 331, "calendar_last_scraped" : "2021-02-23", "number_of_reviews" : 43, "number_of_reviews_ltm" : 4, "number_of_reviews_l30d" : 0, "first_review" : "2013-01-03", "last_review" : "2021-01-11", "review_scores_rating" : 92, "review_scores_accuracy" : 9, "review_scores_cleanliness" : 9, "review_scores_checkin" : 10, "review_scores_communication" : 10, "review_scores_location" : 10, "review_scores_value" : 9, "license" : "", "instant_bookable" : "f", "calculated_host_listings_count" : 1, "calculated_host_listings_count_entire_homes" : 1, "calculated_host_listings_count_private_rooms" : 0, "calculated_host_listings_count_shared_rooms" : 0, "reviews_per_month" : 0.43 }
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
	"description" : "The space  Beautiful and meticulous 2 master suite luxury oceanfront condo fully furnished and equipped with WIFI, digital cable and unlimited long distance in the US and Canada.    Building is full of amenities including tennis court, swimming pool, jacuzzi, workout room, covered and valet parking, direct beach access.    Conveniently located in Hallandale Beach between Miami and Fort Lauderdale, you’re just minutes from two international airports, two seaports, as well as world-class shopping at Bal Harbour and Aventura. And just minutes away from Hollywood Beach Boardwalk, one of the five best boardwalks in the country as ranked by Travel & Leisure.    Minimum rental is 30 days.  Available beginning May 1st, 2011.    Call for additional details.",
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
	"host_thumbnail_url" : "https://a0.muscache.com/im/users/351303/profile_pic/1304341323/original.jpg?aki_policy=profile_small",
	"host_picture_url" : "https://a0.muscache.com/im/users/351303/profile_pic/1304341323/original.jpg?aki_policy=profile_x_medium",
	"host_neighbourhood" : "",
	"host_listings_count" : 2,
	"host_total_listings_count" : 2,
	"host_verifications" : "['email', 'phone', 'facebook', 'kba']",
	"host_has_profile_pic" : "t",
	"host_identity_verified" : "t",
	"neighbourhood" : "",
	"neighbourhood_cleansed" : "Hallandale Beach",
	"neighbourhood_group_cleansed" : "",
	"latitude" : 25.9784,
	"longitude" : -80.12028,
	"property_type" : "Entire apartment",
	"room_type" : "Entire home/apt",
	"accommodates" : 6,
	"bathrooms" : "",
	"bathrooms_text" : "2 baths",
	"bedrooms" : 2,
	"beds" : 4,
	"amenities" : "[\"Smart lock\", \"Hair dryer\", \"Iron\", \"Dryer\", \"Dedicated workspace\", \"Elevator\", \"Free parking on premises\", \"Long term stays allowed\", \"Hot tub\", \"Pool\", \"Cable TV\", \"Wifi\", \"Washer\", \"Hangers\", \"TV\", \"Heating\", \"Kitchen\", \"Air conditioning\", \"Gym\"]",
	"price" : "$140.00",
	"minimum_nights" : 30,
	"maximum_nights" : 365,
	"minimum_minimum_nights" : 30,
	"maximum_minimum_nights" : 30,
	"minimum_maximum_nights" : 365,
	"maximum_maximum_nights" : 365,
	"minimum_nights_avg_ntm" : 30,
	"maximum_nights_avg_ntm" : 365,
	"calendar_updated" : "",
	"has_availability" : "t",
	"availability_30" : 0,
	"availability_60" : 29,
	"availability_90" : 59,
	"availability_365" : 334,
	"calendar_last_scraped" : "2021-02-24",
	"number_of_reviews" : 1,
	"number_of_reviews_ltm" : 0,
	"number_of_reviews_l30d" : 0,
	"first_review" : "2018-02-11",
	"last_review" : "2018-02-11",
	"review_scores_rating" : 100,
	"review_scores_accuracy" : "",
	"review_scores_cleanliness" : "",
	"review_scores_checkin" : "",
	"review_scores_communication" : "",
	"review_scores_location" : "",
	"review_scores_value" : "",
	"license" : "",
	"instant_bookable" : "f",
	"calculated_host_listings_count" : 2,
	"calculated_host_listings_count_entire_homes" : 2,
	"calculated_host_listings_count_private_rooms" : 0,
	"calculated_host_listings_count_shared_rooms" : 0,
	"reviews_per_month" : 0.03
}
{
	"_id" : ObjectId("6068accb7c6a86bb058d3b98"),
	"id" : 57818,
	"listing_url" : "https://www.airbnb.com/rooms/57818",
	"scrape_id" : NumberLong("20210223032208"),
	"last_scraped" : "2021-02-23",
	"name" : "Private house close to the beach!",
	"description" : "Beautifully private duplex that allows you to enjoy the zen of life!  Watch the neighbors walking their pets...jogging near the lake...or riding their bikes, or join in and jog to the beach!  If you don't want to disconnect...we have WIFI!  Please note:  Since this is my home, I only rent to people who aren't afraid to put a validated picture/profile (that AIRBNB has verified) on their page before I decide. Don't hide who you are...  The space  Peaceful house on Nature Preserve Close to everything. Hollywood, Florida Vacation Rental, South East, Florida, USA  Accommodations: 2 bedrooms and 1 full bathrooms. This house has a living room with a leather sectional and a beautiful fireplace (even though it's Florida). Beautifully loaded kitchen w/granite countertops and bar, Dining Room, Living room. Tres Chique!   New flat screen TV.  Can sleep 4.   This precious house is located on a quiet street. There is beautiful walking, jogging and biking",
	"neighborhood_overview" : "This is a family oriented, quiet, peaceful neighborhood, so please respect your neighbors.  This is a duplex, renters in back house (seperate).",
	"picture_url" : "https://a0.muscache.com/pictures/347696/9d51689b_original.jpg",
	"host_id" : 275948,
	"host_url" : "https://www.airbnb.com/users/show/275948",
	"host_name" : "VonJon",
	"host_since" : "2010-11-01",
	"host_location" : "Hollywood, Florida, United States",
	"host_about" : "I love my house...the neighbors are wonderful, and I would love to share it with you!  We love food...big foodies!  We try to eat healthy, but do like our deserts!     I will help you in anyway possible...I know a lot of things to do...restaurants in the area that are exceptional...kid activities, golf courses, etc.  Just let me know!  ",
	"host_response_time" : "within an hour",
	"host_response_rate" : "100%",
	"host_acceptance_rate" : "71%",
	"host_is_superhost" : "f",
	"host_thumbnail_url" : "https://a0.muscache.com/im/pictures/user/1f2670bf-576e-4ec9-bb6c-69276c8f520f.jpg?aki_policy=profile_small",
	"host_picture_url" : "https://a0.muscache.com/im/pictures/user/1f2670bf-576e-4ec9-bb6c-69276c8f520f.jpg?aki_policy=profile_x_medium",
	"host_neighbourhood" : "",
	"host_listings_count" : 1,
	"host_total_listings_count" : 1,
	"host_verifications" : "['email', 'phone', 'facebook', 'reviews', 'jumio', 'offline_government_id', 'selfie', 'government_id', 'identity_manual']",
	"host_has_profile_pic" : "t",
	"host_identity_verified" : "t",
	"neighbourhood" : "Hollywood, Florida, United States",
	"neighbourhood_cleansed" : "Hollywood",
	"neighbourhood_group_cleansed" : "",
	"latitude" : 26.0167,
	"longitude" : -80.12437,
	"property_type" : "Entire house",
	"room_type" : "Entire home/apt",
	"accommodates" : 5,
	"bathrooms" : "",
	"bathrooms_text" : "1 bath",
	"bedrooms" : 2,
	"beds" : 2,
	"amenities" : "[\"Bed linens\", \"Dedicated workspace\", \"BBQ grill\", \"Indoor fireplace\", \"Dishes and silverware\", \"Single level home\", \"Hangers\", \"TV\", \"Stove\", \"Wifi\", \"Kitchen\", \"Free street parking\", \"Dishwasher\", \"Hair dryer\", \"Iron\", \"Refrigerator\", \"Microwave\", \"Patio or balcony\", \"Coffee maker\", \"Cable TV\", \"Shampoo\", \"Essentials\", \"Oven\", \"Children\\u2019s dinnerware\", \"Private entrance\", \"Lockbox\", \"Fire extinguisher\", \"Heating\", \"Air conditioning\", \"Children\\u2019s books and toys\", \"Hot water\", \"Extra pillows and blankets\", \"Smoke alarm\", \"Free parking on premises\", \"Long term stays allowed\", \"Bathtub\", \"Cooking basics\"]",
	"price" : "$125.00",
	"minimum_nights" : 2,
	"maximum_nights" : 30,
	"minimum_minimum_nights" : 2,
	"maximum_minimum_nights" : 2,
	"minimum_maximum_nights" : 30,
	"maximum_maximum_nights" : 30,
	"minimum_nights_avg_ntm" : 2,
	"maximum_nights_avg_ntm" : 30,
	"calendar_updated" : "",
	"has_availability" : "t",
	"availability_30" : 8,
	"availability_60" : 26,
	"availability_90" : 56,
	"availability_365" : 331,
	"calendar_last_scraped" : "2021-02-23",
	"number_of_reviews" : 43,
	"number_of_reviews_ltm" : 4,
	"number_of_reviews_l30d" : 0,
	"first_review" : "2013-01-03",
	"last_review" : "2021-01-11",
	"review_scores_rating" : 92,
	"review_scores_accuracy" : 9,
	"review_scores_cleanliness" : 9,
	"review_scores_checkin" : 10,
	"review_scores_communication" : 10,
	"review_scores_location" : 10,
	"review_scores_value" : 9,
	"license" : "",
	"instant_bookable" : "f",
	"calculated_host_listings_count" : 1,
	"calculated_host_listings_count_entire_homes" : 1,
	"calculated_host_listings_count_private_rooms" : 0,
	"calculated_host_listings_count_shared_rooms" : 0,
	"reviews_per_month" : 0.43
}
{
	"_id" : ObjectId("6068accb7c6a86bb058d3b9a"),
	"id" : 83449,
	"listing_url" : "https://www.airbnb.com/rooms/83449",
	"scrape_id" : NumberLong("20210223032208"),
	"last_scraped" : "2021-02-25",
	"name" : "MARY POP APTS 2/1 APT SLEEP 5",
	"description" : "MARY POP APARTMENTS 1&2 BEDROOM SUITES ACCOMMODATION 1-5 PEOPLE, WE ARE OFFERING TEMPORARY ACCOMMODATIONS SHORT TERM, LONGER TERM UP TO 6 MONTHS , VACATIONERS, RELOCATIONS FROM OTHER SATES OR COUNTRIES TO SOUTH FLORIDA, CORPORATE HOUSING,  The space  NOTE: WE ARE HERE TO HELP YOU . TEMPORARY ACCOMMODATION, VACATION RENTALS, CORPORATE HOUSING, RELOCATIONS, HOUSING FOR TRAVELING NURSES,  HOUSING FOR STUDENTS, CONTACT US FOR DETAILS   RENOVATED 2 BEDROOM 1 BATH APARTMENT 900 SQ FT.  MARY POP APARTMENTS 29 E SHERIDAN ST, DANIA BEACH FL   FREE TRANSPORTATION TO FORT LAUDERDALE AIRPORT AND PORT EVERGLADES FREE BIKES TO THE BEACH   HOTEL RATES IN THIS AREA ARE $100-$150/NIGHT FOR 1 ROOM, MARY POP APARTMENTS IS OFFERING 4 ROOMS FOR LESS Activities  Pier Fishing  Medical Services  Massage Therapist  Kayaking  Snorkeling  Scuba Diving Or Snorkeling  ATM/Bank  Fitness Center  Shopping  L",
	"neighborhood_overview" : "",
	"picture_url" : "https://a0.muscache.com/pictures/13dd4c7e-4914-449e-950e-a83e56c48316.jpg",
	"host_id" : 454736,
	"host_url" : "https://www.airbnb.com/users/show/454736",
	"host_name" : "Jon,  Mary Pop Apartments",
	"host_since" : "2011-03-21",
	"host_location" : "Dania Beach, Florida, United States",
	"host_about" : " LOCATION,LOCATION,LOCATION, NUMBER 1 ACCOMMODATION WITHIN 10 MINUTES DRIVE FROM PORT EVERGLADES AND FORT LAUDERDALE/HOLLYWOOD/DANIA BEACH INTERNATIONAL AIRPORT\n\nI was born in former Yugoslavija, emigrated to New York in (Phone number hidden by Airbnb) , Moved to Dania Beach Fl in (Phone number hidden by Airbnb) , I am the owner of Mary Pop Apartments a 22 Unit Complex with Studio and 1&2 bedroom apartments, Mary Pop Apartments is registered and Licensed with the STATE OF FLORIDA : DEPARTMENT OF BUSINESS  AND PROFESIONAL REGULATION, DIVISION OF HOTELS AND RESTAURANTS\nPROPERTY USE: TRANSIENT APARTMENTS\nLICENSE # TAP (Phone number hidden by Airbnb) AIRBNB IS DELETING MY LICENSE NUMBER BUT YOU CAN DO A SEARCH ON MARY POP APARTMENTS AND FIND THE INFORMATION. WE ARE ALSO ON MAP SEARCH.WE PAY 11% FLORIDA TOURIST TAX ON ALL BOOKINGS.\nWE DID UPGRADES TO ALL APARTMENTS WITH NEW KITCHENS WITH GRANITE COUNTER TOPS, STAINLESS STEEL APPLIANCES , LEATHER SOFAS AND LOVE SEATS, NEW KITCHEN TABLES, IN MOST APARTMENTS NEW BEDROOM SETS ACCOMMODATION 1-6 PEOPLE PER APARTMENT, GROUPS OF (Phone number hidden by Airbnb) PEOPLE WELCOME.\nMOST UPGRADES WHERE DONE IN (Phone number hidden by Airbnb) NOT ALL THE PICTURES ARE UPDATED ON MY LISTINGS. (Phone number hidden by Airbnb) GROSS INCOME WITH AIRBNB USERS 5% ( 37 RESERVATIONS (Phone number hidden by Airbnb) GROSS INCOME WITH AIRBNB USERS 8% (92 RESERVATIONS) (Phone number hidden by Airbnb) GROSS INCOME WITH AIRBNB USERS 11% ( 99 RESERVATIONS)\nDUE TO LOW RATINGS FROM 1 NIGHT RESERVATIONS, WE ARE NO LONGER ACCEPT THEM\nCome in as guests, leave as family\nI speak Serbian, Roumanian and English",
	"host_response_time" : "within a few hours",
	"host_response_rate" : "90%",
	"host_acceptance_rate" : "90%",
	"host_is_superhost" : "t",
	"host_thumbnail_url" : "https://a0.muscache.com/im/users/454736/profile_pic/1323695982/original.jpg?aki_policy=profile_small",
	"host_picture_url" : "https://a0.muscache.com/im/users/454736/profile_pic/1323695982/original.jpg?aki_policy=profile_x_medium",
	"host_neighbourhood" : "",
	"host_listings_count" : 8,
	"host_total_listings_count" : 8,
	"host_verifications" : "['email', 'phone', 'facebook', 'reviews']",
	"host_has_profile_pic" : "t",
	"host_identity_verified" : "t",
	"neighbourhood" : "",
	"neighbourhood_cleansed" : "Dania Beach",
	"neighbourhood_group_cleansed" : "",
	"latitude" : 26.03392,
	"longitude" : -80.14201,
	"property_type" : "Entire apartment",
	"room_type" : "Entire home/apt",
	"accommodates" : 5,
	"bathrooms" : "",
	"bathrooms_text" : "1 bath",
	"bedrooms" : 2,
	"beds" : 3,
	"amenities" : "[\"Hair dryer\", \"Iron\", \"Dryer\", \"Dedicated workspace\", \"Carbon monoxide alarm\", \"Fire extinguisher\", \"Smoke alarm\", \"Free parking on premises\", \"Long term stays allowed\", \"Pool\", \"Cable TV\", \"Shampoo\", \"Washer\", \"Essentials\", \"Wifi\", \"Hangers\", \"TV\", \"Heating\", \"Kitchen\", \"Air conditioning\"]",
	"price" : "$125.00",
	"minimum_nights" : 7,
	"maximum_nights" : 180,
	"minimum_minimum_nights" : 7,
	"maximum_minimum_nights" : 7,
	"minimum_maximum_nights" : 180,
	"maximum_maximum_nights" : 180,
	"minimum_nights_avg_ntm" : 7,
	"maximum_nights_avg_ntm" : 180,
	"calendar_updated" : "",
	"has_availability" : "t",
	"availability_30" : 0,
	"availability_60" : 0,
	"availability_90" : 9,
	"availability_365" : 284,
	"calendar_last_scraped" : "2021-02-25",
	"number_of_reviews" : 20,
	"number_of_reviews_ltm" : 0,
	"number_of_reviews_l30d" : 0,
	"first_review" : "2011-11-01",
	"last_review" : "2020-01-26",
	"review_scores_rating" : 95,
	"review_scores_accuracy" : 10,
	"review_scores_cleanliness" : 10,
	"review_scores_checkin" : 10,
	"review_scores_communication" : 10,
	"review_scores_location" : 10,
	"review_scores_value" : 10,
	"license" : "",
	"instant_bookable" : "f",
	"calculated_host_listings_count" : 8,
	"calculated_host_listings_count_entire_homes" : 8,
	"calculated_host_listings_count_private_rooms" : 0,
	"calculated_host_listings_count_shared_rooms" : 0,
	"reviews_per_month" : 0.18
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
