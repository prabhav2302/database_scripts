## Part 1: Restaurant Finder


**This is the code to create the restaurants table. Here the primary key is the restaurant_id which is an integer.**
|Field |Data Type|
|------|----------|  
|restaurant_name| TEXT|  
|category|TEXT|
|price_tier|TEXT|
|neighborhood|TEXT|  
|opening_hours|TEXT|
|average_rating|REAL| 
|good_for_kids|INTEGER|

```mysql
CREATE TABLE restaurants (
    restaurant_id INTEGER PRIMARY KEY,
    restaurant_name TEXT, 
    category TEXT,
    price_tier TEXT,
    neighborhood TEXT, 
    opening_hours TEXT, 
    average_rating REAL, 
    good_for_kids INTEGER
);
```


**This is the code to the create the reviews table. Here the primary key is review_id which is an integer. There is a foreign key called restaurant_id which connects to the restaurants table.**  
|Field |Data Type|
|------|----------|  
|review_id|INTEGER| 
|restaurant_id|INTEGER| 
|review_content|TEXT|

```mysql
CREATE TABLE reviews (
    review_id INTEGER PRIMARY KEY,
    restaurant_id INTEGER,
    review_content TEXT 
);
```

**These are the commands to import data**
```
.mode csv 
.headers on
.import /Users/prabhavarora/Desktop/DB_Design/sql-crud-prabhav2302/data/rest_data.csv restaurants
```
[Link to restaurant dataset](https://github.com/database-design-assignments/sql-crud-prabhav2302/blob/main/data/rest_data.csv)

**Here are the queries**
```mysql
1)  
select restaurant_name from restaurants WHERE price_tier = "Cheap" and neighborhood = "Sunset Park";
2)  
select restaurant_name from restaurants WHERE category = "Japanese" and average_rating>=3 ORDER BY average_rating DESC;
3)  
select restaurant_name from restaurants WHERE opening_hours <= strftime('%H:%M', 'now');
4)  
INSERT INTO reviews (restaurant_id,review_content) VALUES (42, "The food was very spicy but I liked it. The staff was also very friendly and the place had a great ambience");
5)  
delete from restaurants where good_for_kids = 0;
6)  
select neighborhood, count(restaurant_id) from restaurants group by neighborhood;
```

## Part 2: Social Media App

**This is the code to create the users table. Here the primary key is the user_id which is an integer.**  
|Field |Data Type|
|------|----------|  
|user_id|INTEGER| 
|email_id|TEXT|
|password|TEXT|  
|username|TEXT|

```mysql
CREATE TABLE users(
    user_id INTEGER PRIMARY KEY,
    email_id TEXT, 
    password TEXT, 
    username TEXT
); 
```

**This is the code to create the posts table. Here the primary key is the post_id which is an integer. The table has a foriegn key which called sender_id which links it to the users table. We can also consider sender_id to be a foreign key**  
|Field |Data Type|
|------|----------|  
|post_id|INTEGER|  
|post_type|TEXT| 
|visibility_status|TEXT|  
|post_time|TEXT|  
|post_content|TEXT|  
|sender_id|INTEGER| 
|recv_id|INTEGER|

```mysql
CREATE TABLE posts(
    post_id INTEGER PRIMARY KEY,
    post_type TEXT,
    visibility_status TEXT,
    post_time TEXT,
    post_content TEXT,
    sender_id INTEGER,
    recv_id INTEGER
);
```
**These are the commands to import data**
```mysql
.mode csv  
.headers on  
.import /Users/prabhavarora/Desktop/DB_Design/sql-crud-prabhav2302/data/users.csv users  
.import /Users/prabhavarora/Desktop/DB_Design/sql-crud-prabhav2302/data/posts.csv posts
```
[Link to users dataset](https://github.com/database-design-assignments/sql-crud-prabhav2302/blob/main/data/users.csv)  
[Link to posts dataset](https://github.com/database-design-assignments/sql-crud-prabhav2302/blob/main/data/posts.csv)

**Here are the queries**
```mysql
1) 
INSERT into users (email_id,password,username) VALUES ("pa1363@nyu.edu","12345","pa1363");
2) 
INSERT into posts (post_type, visibility_status, post_time, post_content, sender_id, recv_id) VALUES ("message","invisible","2020-11-20 08:13:29","pls give me an A",211,413);
3)  
INSERT into posts (post_type, visibility_status, post_time, post_content, sender_id, recv_id) VALUES ("story", "invisible","2021-03-06 13:55:18", "lebron is over-rated",523,NULL);
4) 
select post_id, post_type, post_content, post_time from posts where visibility_status = "visible" ORDER BY post_time DESC LIMIT 10;  
5) 
select post_id, post_type, post_content from posts WHERE sender_id = 527 and recv_id = 194 and post_type = "message" and visibility_status = "visible" ORDER BY post_time DESC LIMIT 10;
6) 
update posts set visibility_status = "invisible" where ROUND((JULIANDAY('now') - JULIANDAY(post_time)) * 60) >= 24; 
7) 
select * from posts where visibility_status = "invisible" ORDER BY post_time DESC;
8) 
select users.user_id, users.username, count(posts.post_id) from users left join posts on users.user_id = posts.sender_id GROUP BY users.user_id;
9) 
select users.email_id, posts.post_content from users INNER JOIN posts WHERE ROUND((JULIANDAY('now') - JULIANDAY(post_time)) * 60) <= 24;
10) 
select users.email_id from users left join posts on users.user_id = posts.sender_id WHERE posts.post_id is NULL;
```

