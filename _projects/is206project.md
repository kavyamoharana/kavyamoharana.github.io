---
name: Project - Designing an IMDb Database for Movies
tools: [SQL, SQLite]
image: assets/pngs/206-cover.png
description: Project which uses SQLite for designing a database for Movie reviews and ratings 
custom_js:
  - vega.min
  - vega-lite.min
  - vega-embed.min
  - justcharts
---

## Database Design for a Movie Ratings and Review Website

*Final project for [IS 206](https://ischool.illinois.edu/degrees-programs/courses/is206): Intro to Database Concepts and Applications at UIUC*

<div class="left">
  {% include elements/button.html link="https://github.com/kavyamoharana/kavyamoharana.github.io/blob/main/assets/pdfs/206-Report.pdf" text="View Full Report" %}
</div>
<br>
<br>

#### Purpose and Scope
This project consists of designing and creating an IMDb-esque movie reviews and ratings database---a platform for users to be able to access basic movie information such as cast and crew information, genre, and roles while also writing reviews, ratings, and interacting with other users’ posts. The purpose for the database is to enhance the movie experience for users with up-to-date movie details while providing insight into what kinds of movies or media resonate the most with audiences and the general public. 

#### Entity-Relationship Diagram
This diagram, created with [LucidChart](https://www.lucidchart.com), highlights the key entities, attributes, primary keys, and relationships for the database schema.
![image tooltip here](/assets/pngs/206project-ERD.png)

#### Creation of Database
Here are some of the tables created with SQLite.
```
CREATE TABLE Movie(id INT PRIMARY KEY,
        title varchar(100),
        year INT,
        release_date varchar(100),
        duration INT,
        country varchar(100),
        worldwide_gross_income INT,
        languages varchar(100),
        production_company varchar(100)
    );

CREATE TABLE Genre(movie_id varchar(100) PRIMARY KEY,
        genre_name varchar(100)
    );

CREATE TABLE Ratings(movie_id varchar(100) PRIMARY KEY, 
        avg_rating INT, 
        total_votes INT,
        median_rating varchar(100)
    );

CREATE TABLE Actors(id INT PRIMARY KEY,
        name_id varchar(100), 
        height INT,
        date_of_birth varchar(100), 
        movies_known_for varchar(100)
    );
...
```
![image tooltip here](/assets/pngs/206-movie.png)
![image tooltip here](/assets/pngs/206-actors.png)
<img src="/assets/pngs/206-ratings.png" alt="image tooltip here" width="700"/>

#### Sample Queries
1. Top 5 movies that have the highest worldwide gross income
    <img src="/assets/pngs/query1.png" alt="image tooltip here" width="650"/>
2. Average ratings for movies released in Korean or Mandarin
    <img src="/assets/pngs/query2.png" alt="image tooltip here" width="650"/>
3. Average ratings for each movie genre
    <img src="/assets/pngs/query3.png" alt="image tooltip here" width="650"/>

