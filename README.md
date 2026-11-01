# pyspark-music-listening-analysis
PySpark analysis of 13M+ music listening records: top tracks, artists, genres and user preferences
# Music Listening Analysis with PySpark

PySpark analysis of 13,758,905 music listening records (after removing
rows with missing values) to find popular tracks, artists, albums and
genres, and each user's favourite genre.

This is my completed notebook from the Coursera guided project
*Data Analysis Using PySpark*.

## PySpark skills used
- **Spark setup:** creating a `SparkSession`
- **Loading data:** `spark.read` with `header` and `inferSchema` options for CSV files
- **Cleaning:** `drop()` to remove columns, `na.drop()` to remove null rows,
  `printSchema()` and `count()` to check the data
- **Querying:** `select()`, `filter()`, `col()`
- **Aggregations:** `groupBy()` with `agg()`, `count()` and `alias()`
- **Sorting and limiting:** `orderBy()` with `desc()`, `limit()`
- **Joins:** inner `join()` between listening and genre data
- **Top item per group:** `max(struct())` to find each user's favourite genre
- **Bringing results to Python:** `collect()` to pass results to matplotlib

## Data
Two CSV files provided with the course (not included in this repo):
- **listenings.csv** – user_id, track, artist, album, date
- **genre.csv** – artist, genre

## What the notebook does
- Loads both files into Spark DataFrames
- Cleans the data (drops the date column and null rows)
- Finds:
  - top 10 tracks and albums overall
  - top 10 listeners of a given artist (Rihanna)
  - top 10 tracks of that artist
  - most popular genres
- Joins listening data with genre data
- Finds the top 10 listeners of pop music
- Finds each user's favourite genre
- Plots a bar chart of how many artists are listed under pop, rock,
  metal and hip hop in genre.csv

## Some results
- Most played track: *Sorry* by Justin Bieber (3,381 plays)
- Most played album: *The Life of Pablo* by Kanye West (22,310 plays)
- Rock is the most common genre in the joined data

## Observation
In the joined data, some genre values are actually artist names
(for example "Kanye West" and "SZA"), and some artists match more than
one genre row. This means genre-based counts are likely inflated.
Cleaning genre.csv before the join would fix this.

## Tools
PySpark, Google Colab, matplotlib
