# Spotify-Data-Analysis-Project-SQL
Spotify Data Analysis Project – SQL
Your project is a Spotify Music Data Analysis project using SQL. It focuses on analyzing music tracks, artists, albums, and their popularity on Spotify and YouTube.

The project uses SQL queries to extract meaningful insights from a music dataset, such as identifying the most-streamed songs, analyzing artist performance, and comparing music engagement across platforms.
spotify_db.sql
1. Project objective
The main objective is to use SQL to analyze music data and answer business-related questions.

For example:
- Which songs have the highest number of streams?
- Which artists have the most tracks?
- Which albums have the highest average danceability?
- Which songs are popular on YouTube compared to Spotify?
- Which tracks have high energy?
- How do views, likes, and comments relate to music popularity?
2. Technologies used
Technology	Purpose
MySQL / SQL	Store and analyze data
Database	spotify_db
Table	spotify
CTE	Organize complex queries
Window functions	Rank tracks and calculate rolling averages
Aggregate functions	Calculate count, sum, average, maximum, and minimum

3. Database structure
Your project creates a database named spotify_db and a table named spotify.

The table contains columns such as:
Column	Description
artist	Name of the artist
track	Track name
album	Album name
album_type	Album, single, etc.
danceability	How suitable a track is for dancing
energy	Intensity and activity of the track
loudness	Sound loudness
acousticness	Acoustic characteristics
instrumentalness	Likelihood of instrumental music
liveness	Indicates live performance characteristics
valence	Musical positivity
tempo	Track speed in BPM
duration_min	Track duration in minutes
views	YouTube views
likes	YouTube likes
comments	YouTube comments
stream	Spotify stream count
most_playedon	Platform where the track is most played

spotify_db.sql
4. Important SQL concepts used
Aggregate functions

Used to summarize data.
- COUNT() – counts records
- SUM() – calculates total
- AVG() – calculates average
- MAX() – finds maximum
- MIN() – finds minimum













GROUP BY

Groups records by artist or album to calculate statistics for each group.













CTE (Common Table Expression)

Uses the WITH clause to create a temporary named result set that can be used within a query.













Window functions

Uses functions such as RANK(), DENSE_RANK(), and AVG() OVER() to analyze records without collapsing rows.













5. Main analysis performed in your project
Your SQL file contains several analysis queries:
1. Counts the total number of records in the Spotify table.
2. Retrieves tracks with more than 1 million streams.
3. Lists unique artist and album combinations.
4. Calculates total comments for licensed tracks.
5. Finds single tracks.
6. Counts tracks for each artist.
7. Calculates average danceability for each album.
8. Finds the top 5 tracks with the highest energy using RANK().
9. Finds tracks where views are greater than likes and the official video is true.
10. Finds tracks with above-average liveness.
11. Calculates the energy difference for each artist.
12. Finds tracks with energy_liveness > 1.2.
13. Finds the top 3 most-viewed tracks for each artist using DENSE_RANK().
14. Compares YouTube and Spotify popularity for each artist.
15. Calculates a rolling average of streams for each artist.
16. Categorizes tracks into high, medium, and low danceability.
spotify_db.sql
6. Example query explanation
Find the top 5 tracks with the highest energy
WITH my_cte AS (
    SELECT *,
           RANK() OVER (
               ORDER BY energy DESC
           ) AS my_rank
    FROM spotify
)
SELECT *
FROM my_cte
WHERE my_rank <= 5;


Explanation:
- WITH my_cte AS creates a temporary result set.
- RANK() assigns a rank to each track based on energy.
- ORDER BY energy DESC places the highest-energy tracks first.
- my_rank <= 5 returns tracks ranked in the top five positions.
Note: Because RANK() handles ties, this query can return more than five rows if multiple tracks share a ranking.
7. What did you learn from this project?
You can explain your learning in an interview like this:
- Learned how to create databases and tables using SQL.
- Practiced filtering data using WHERE and HAVING.
- Used aggregate functions to calculate business statistics.
- Learned how to group data using GROUP BY.
- Applied CTEs to simplify complex queries.
- Used window functions for ranking and analytical calculations.
- Analyzed music popularity using streams, views, likes, and comments.
- Improved SQL problem-solving and data-analysis skills.
8. Interview-ready project explanation
Project: Spotify Music Data Analysis using SQL

I developed a Spotify Music Data Analysis project using SQL to analyze music tracks, artists, albums, and their popularity across Spotify and YouTube.

The project uses a database named spotify_db with a table containing information such as artist names, track names, albums, streams, views, likes, comments, and audio features like energy, danceability, and tempo.

I performed data analysis using SQL queries, aggregate functions, GROUP BY, subqueries, Common Table Expressions, and window functions.

Some of the key analyses include identifying highly streamed tracks, finding the top tracks by energy and views, calculating average danceability, comparing YouTube and Spotify popularity, and calculating rolling averages of streams.

This project helped me improve my SQL skills and understand how to extract meaningful insights from structured data.




One important correction: Your SQL comment says “more than 1 billion streams,” but the actual condition is stream > 1000000, which means more than 1 million streams. Also, your query uses most_playedon to compare platform counts; it does not directly compare actual stream totals against YouTube views.


