# Exploratory Data Analysis on Spotify Popular Tracks of 2023

## Introduction 
This project explores a dataset of popular Spotify tracks in 2023. The project analyzes trends and insights into music popularity, genres, and other characteristics. We have the following questions to ponder:
- Which genres, tracks, and artists are most popular?
- What features contribute to a track's popularity?

# Questions to ponder:

## Overview of the Dataset:
How many rows and columns does the dataset contain?
- The dataset contains 953 rows and 24 columns.

What are the data types of each column? Are there any missing values?
- Two data types appear on each column of my code: 'int64' for integer values and 'object' for textual data (or a string). To be precise, 17 columns of the data type 'int64' are shown, while there are 7 columns of the data type 'object'.

## Basic Descriptive Statistics:
What are the streams column's mean, median, and standard deviation?
- The mean, median, and the standard deviation are as follows:
  - mean: 514137424.93907565 
  - median: 290530915.0 
  - standard deviation: 566856949.0388832

What is the distribution of released_year and artist_count? Are there any noticeable trends or outliers?

Released_Year:
- The data has a mean release year of 2018 and a standard deviation of 11 years. Most data points are concentrated around recent years, with the 25th percentile in 2020, the 50th percentile (median) in 2022, and the same goes with the 75th percentile in 2022. This indicates that a distribution is turned toward more recent years, suggesting that many come from the 2020s.

Artist_Count:
- The data has a mean artist count of approximately 1.56, with a standard deviation of 0.89. The distribution is heavily turned towards single-artist entries as the 25th and 50th percentiles are 1, and the 75th percentile is 2. The data shows that most works are by a single artist, with fewer involving collaborations of more than two artists. The maximum count recorded is 8, indicating occasional larger collaborations.

Noticeable Trends or Outliers:
In the case of the Released_Year, outliers were not explicitly listed in the output, but any entries significantly earlier than 2020 may be considered outliers. Meanwhile, in the case of Artist_Count, outliers may indicate large group collaborations or tracks with multiple featured artists.

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
- Yes, there is a correlation between these two musical attributes. They correlate 0.2. This is a positive correlation, so the relationship between these attributes is directly proportional. As one attribute increases, so does the other one.

valence_% and acousticness_%:
- The correlation between the two attributes (valence_% and acousticness_%) is approximately -0.081, indicating a very weak negative correlation. This shows an inverse proportionality relationship between these attributes; as one increases, the other decreases, but the relationship is not strong or significant.

## Platform Popularity:
How do the numbers of tracks in spotify_playlists, spotify_charts, and apple_playlists compare? 
- The total count in each platform is as follows:

  Spotify Playlists: 4955719.0 tracks
  Spotify Charts: 11445.0 tracks
  Apple Playlist: 64625.0 tracks

  The results show that Spotify Playlists has the most tracks, followed by Apple Playlists and then Spotify Charts.

Which platform seems to favor the most popular tracks?
- Spotify Playlist favors the most popular tracks, with an average count per track of 5200.124869. This is followed by Apple Playlist, with an average count per track of 67.812172. Next is Apple Charts, with an average count per track of 51.908709. Finally, Spotify Charts, with an average count per track of 12.009444.

## Advanced Analysis:
Based on the streams data, can you identify any patterns among tracks with the same key or mode (Major vs. Minor)?

Patterns by Key:
Tracks in the keys of C#, E, and D# have the highest average streams, with values being 6.042802e+08, 5.774972e+08, and 5.530365e+08, respectively. This suggests that tracks in these keys may be popular on average. 

Patterns by Mode:
Tracks in the Major mode have a higher average stream count of 5.348328e+08 streams. Meanwhile, tracks in the Minor mode experience a lower average stream count of 4.859445e+08 streams. This suggests that the Major mode is more popular on average than the Minor mode.

Do certain genres or artists consistently appear in more playlists or charts? Perform an analysis to compare the most frequently appearing artists in playlists or charts.
- The Weeknd, Taylor Swift, Ed Sheeran, and Harry Styles dominate the top spots in both Spotify and Apple playlists and charts. Eminem, Arctic Monkeys, and Coldplay have fewer chart appearances but still remain strong in playlists. Avicii, Dr. Dre & Snoop Dogg, and Adele have a more balanced presence across playlists and charts. 
