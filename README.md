# Microsoft Movie Studio Insights from TMDB Data

This project is an exploration of current trends in the film industry with data gathered from The Movie Database (TMDB). The analysis will aid Microsoft in making data-driven decisions for its new movie studio.

## Table of Contents

1. [Project Overview](#project-overview)
2. [Methodology](#methodology)
3. [Data Analysis](#data-analysis)
   - [Popularity by Genre](#popularity-by-genre)
   - [Popularity of Genres Over Time](#popularity-over-time)

## Project Overview

Microsoft wants to start producing films but lacks the knowledge about which type of films are performing well. This project aims to provide insights on genre popularity over the past five years, which could guide Microsoft in deciding the type of movies to produce.

## Methodology

The analysis is based on the data gathered from The Movie Database (TMDB) API. The data covers the highest grossing films of the last five years (2018 - 2023). A Python script is written to fetch the data, process it and generate insightful visualizations.

## Data Analysis

### Popularity by Genre

The data is grouped by genre and the average popularity for each genre is calculated. The result is visualized using a horizontal bar plot, showing the top 10 most popular genres.

```python
# Sort by popularity and take top 10 genres
df_grouped = df_grouped.sort_values('popularity', ascending=False).head(10)

# Plot the average popularity of the top 10 genres
plt.figure(figsize=(10,6))
plt.barh(df_grouped[0], df_grouped['popularity'])
plt.xlabel('Average Popularity')
plt.ylabel('Genre')
plt.title('Average Popularity of the Top 10 Genres')
plt.show()


### Popularity of Genres Over Time

The data is grouped by year and genre, then the average popularity for each genre is calculated for each year. A line plot is used to show the popularity of each genre over time.

The Python code for this part of the analysis is:


# Group by year and genre, then calculate average popularity
dfYear = df.groupby(['year', 0])['popularity'].mean().reset_index()

# Plot the popularity over time for each genre
fig, ax = plt.subplots(figsize=(15,10))
for genre in dfYear[0].unique():
    genre_df = dfYear[dfYear[0] == genre]
    ax.plot(genre_df['year'], genre_df['popularity'], label=genre)
plt.xlabel('Year')
plt.ylabel('Average Popularity')
plt.title('Popularity of Genres Over Time (Last 5 years)')
plt.legend()
plt.show()


## Findings and Recommendations

Some recommendations are made to the Microsoft Movie Studio deriving the insights from the findings in the analysis done. From the analysis, the CEO is advised on the genres of film he should invest on.
