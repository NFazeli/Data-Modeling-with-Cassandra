# Data-Modeling-with-Cassandra
To analyze the data of a fictionary startup company that collected songs and user activity on their new music streaming app. 
We are particularly interested in understanding what songs users are listening to. The data reside in a directory of CSV files on user activity on the app. (For this project the data can be downloaded from Udacity CQL course projects)

We need to create an Apache Cassandra database which can create queries on song play data to answer the questions such as:

1. Give me the artist, song title and song's length in the music app history that was heard during  sessionId = 338, and itemInSession  = 4

2. Give me only the following: name of artist, song (sorted by itemInSession) and user (first and last name) for userid = 10, sessionid = 182
    
3. Give me every user name (first and last) in my music app history who listened to the song 'All Hands Against His Own'

I created a database for this analysis and testd the database by running queries given to me by udacity to create the results.

## The dataset

The dataset in the event_data directory consists of several CSV files partitioned by date. The first step of the ETL pipeline is to make one csv file including all the files in the event_data folder. 

**event_datafile_new.csv**

 ![Tux, Star_scheme](/images/image_event_datafile_new.jpg)

## Cassandra data modeling project Steps
Below are steps to follow to complete each component of this project.

Modeling the NoSQL database or Apache Cassandra database
1. Design tables to answer the queries outlined above
2. Write Apache Cassandra CREATE KEYSPACE and SET KEYSPACE statements
3. Develop a CREATE statement for each of the tables to address each question (Include IF NOT EXISTS clauses)
4. Load the data with INSERT statement for each of the tables
5. include DROP TABLE statement for each table, this way we can run drop and create tables whenever we want to reset the database and test the ETL pipeline
6. The pipeline can be tested by running the proper select statements with the correct WHERE clause

## Table Schema

### For Query 1:

* Column 1: sessionId INT
* Column 2: itemInSession INT
* Column 3: artist TEXT
* Column 4: song_title TEXT
* Column 5: length FLOAT
* PRIMARY KEY (sessionId, itemInSession)

### For Query 2:

* Column 1: userId INT
* Column 2: sessionId INT
* Column 3: itemInSession INT
* Column 4: artist TEXT
* Column 5: song_title TEXT
* Column 6: firstName TEXT
* Column 7: lastName TEXT
* PRIMARY KEY ((userId, sessionId), itemInSession))


### For Query 3:

* Column 1: song_title TEXT
* Column 2: userId INT
* Column 3: firstName TEXT
* Column 4: lastName TEXT
* PRIMARY KEY (song_title, userId)

## Instructions to run the project:

Launch Project_1B_ Project_Template.ipynb to run validation and example queries.

For this project I used the following:

+ Python 3.6.3
+ pandas 0.23.3

