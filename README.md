# Python - Exploratory Data Analysis
This program aims to perform an Exploratory Data Analysis on a dataset containing information about popular tracks on 2023's Most Streamed Spotify Songs. The program will utilize the pandas, matplotlib, and seaborn libraries to analyze, visualize, and interpret the data to extract meaningful insights about the Most Streamed Spotify Songs back in 2023. 

# Questions to ponder:

## Overview of the Dataset:
How many rows and columns does the dataset contain?
- The dataset contains 953 rows and 24 columns.

What are the data types of each column? Are there any missing values?
- Two data types appear on each column of my code: 'int64' for integer values and 'object' for textual data (or a string). To be precise, 17 columns of the data type 'int64' are shown, while there are 7 columns of the data type 'object'.

## Basic Descriptive Statistics:
What are the streams column's mean, median, and standard deviation?
- The mean, median, and the standard deviation are as follows:
  mean: 514137424.93907565 \n
  \n median: 290530915.0 \n
  \n standard deviation: 566856949.0388832 \n

What is the distribution of released_year and artist_count? Are there any noticeable trends or outliers?

Released_Year:
- The data has a mean release year of 2018 and a standard deviation of 11 years. Most data points are concentrated around recent years, with the 25th percentile in 2020, the 50th percentile (median) in 2022, and the same goes with the 75th percentile in 2022. This indicates that a distribution is turned toward more recent years, suggesting that many come from the 2020s.

Artist_Count:
- The data has a mean artist count of approximately 1.56, with a standard deviation of 0.89. The distribution is heavily turned towards single-artist entries as the 25th and 50th percentiles are 1, and the 75th percentile is 2. The data shows that most works are by a single artist, with fewer involving collaborations of more than two artists. The maximum count recorded is 8, indicating occasional larger collaborations.

Noticeable Trends or Outliers:
In the case of the Released_Year, outliers were not explicitly listed in the output, but any entries significantly earlier than 2020 may be considered outliers. For the case of Artist_Count, outliers may indicate large group collaborations or tracks with multiple featured artists.

## Top Performers:
Which track has the highest number of streams? Display the top 5 most streamed tracks.

The top 5 most streamed tracks are as follows; attached also are the artists and number of streams:
- Cruel Summer, Taylor Swift - 800840817 streams
- WHERE SHE GOES, Bad Bunny - 303236322 streams
- Seven (feat. Latto) (Explicit Ver.), Latto, Jung Kook - 141381703 streams
- vampire, Olivia Rodrigo - 140003974	streams
- LALA, Myke Towers - 133716286	streams

Who are the top 5 most frequent artists based on the number of tracks in the dataset?

The top 5 most frequent artists based on the number of tracks:
- Taylor Swift, with 34 tracks
- The Weeknd, with 22 tracks
- Bad Bunny, with 19 tracks
- SZA, with 19 tracks as well
- Harry Styles, with 17 tracks

## Temporal Trends
Analyze the trends in the number of tracks released over time. Plot the number of tracks released per year.

- The trend indicates a long period of stability, followed by rapid growth starting in the late 2010s, with a peak and a slight decline in the 2020s. This pattern reflects the impact of modern technology and digital distribution on music production and release.

Does the number of tracks released per month follow any noticeable patterns? Which month sees the most releases?

- From the graph, January and May have high numbers of track releases compared to other months, with January being the peak month. After January, the graph deviates but spikes in May again. The later months, October to December, also see a gradual increase compared to the summer months, suggesting a potential seasonal trend with high releases at the beginning and towards the end of the year.

## Genre and Music Characteristics:
Examine the correlation between streams and musical attributes like bpm, danceability_%, and energy_%. Which attributes seem to influence streams the most?

- None of the musical attributes(bpm, danceability_%, and energy_%) strongly influence the number of streams, as all the correlations are close to zero.


Is there a correlation between danceability_% and energy_%? How about valence_% and acousticness_%?

danceability_% and energy_%:
- Yes, there is a correlation between these two musical attributes. They have a correlation of 0.2. This is a positive correlation, so the relationship between these two attributes are directly proportional. As one attribute increases, so does the other one.