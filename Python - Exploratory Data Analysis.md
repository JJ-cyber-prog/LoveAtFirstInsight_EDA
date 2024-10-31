```python
!pip install kaggle
```

    Requirement already satisfied: kaggle in c:\users\jerome oldan\anaconda3\lib\site-packages (1.6.17)
    Requirement already satisfied: six>=1.10 in c:\users\jerome oldan\anaconda3\lib\site-packages (from kaggle) (1.16.0)
    Requirement already satisfied: certifi>=2023.7.22 in c:\users\jerome oldan\anaconda3\lib\site-packages (from kaggle) (2024.7.4)
    Requirement already satisfied: python-dateutil in c:\users\jerome oldan\anaconda3\lib\site-packages (from kaggle) (2.9.0.post0)
    Requirement already satisfied: requests in c:\users\jerome oldan\anaconda3\lib\site-packages (from kaggle) (2.32.2)
    Requirement already satisfied: tqdm in c:\users\jerome oldan\anaconda3\lib\site-packages (from kaggle) (4.66.4)
    Requirement already satisfied: python-slugify in c:\users\jerome oldan\anaconda3\lib\site-packages (from kaggle) (5.0.2)
    Requirement already satisfied: urllib3 in c:\users\jerome oldan\anaconda3\lib\site-packages (from kaggle) (2.2.2)
    Requirement already satisfied: bleach in c:\users\jerome oldan\anaconda3\lib\site-packages (from kaggle) (4.1.0)
    Requirement already satisfied: packaging in c:\users\jerome oldan\anaconda3\lib\site-packages (from bleach->kaggle) (23.2)
    Requirement already satisfied: webencodings in c:\users\jerome oldan\anaconda3\lib\site-packages (from bleach->kaggle) (0.5.1)
    Requirement already satisfied: text-unidecode>=1.3 in c:\users\jerome oldan\anaconda3\lib\site-packages (from python-slugify->kaggle) (1.3)
    Requirement already satisfied: charset-normalizer<4,>=2 in c:\users\jerome oldan\anaconda3\lib\site-packages (from requests->kaggle) (2.0.4)
    Requirement already satisfied: idna<4,>=2.5 in c:\users\jerome oldan\anaconda3\lib\site-packages (from requests->kaggle) (3.7)
    Requirement already satisfied: colorama in c:\users\jerome oldan\anaconda3\lib\site-packages (from tqdm->kaggle) (0.4.6)
    


```python
!kaggle datasets download -d nelgiriyewithana/top-spotify-songs-2023
```

    Dataset URL: https://www.kaggle.com/datasets/nelgiriyewithana/top-spotify-songs-2023
    License(s): other
    top-spotify-songs-2023.zip: Skipping, found more recently modified local copy (use --force to force download)
    


```python
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
import zipfile

with zipfile.ZipFile('top-spotify-songs-2023.zip', 'r') as zip_ref: zip_ref.extractall('spotify_data')

df = pd.read_csv('spotify_data/spotify-2023.csv', encoding = 'latin1')
print('Shape of the dataset: ', df.shape)

```

    Shape of the dataset:  (953, 24)
    

## Overview of Dataset


```python
df.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>track_name</th>
      <th>artist(s)_name</th>
      <th>artist_count</th>
      <th>released_year</th>
      <th>released_month</th>
      <th>released_day</th>
      <th>in_spotify_playlists</th>
      <th>in_spotify_charts</th>
      <th>streams</th>
      <th>in_apple_playlists</th>
      <th>...</th>
      <th>bpm</th>
      <th>key</th>
      <th>mode</th>
      <th>danceability_%</th>
      <th>valence_%</th>
      <th>energy_%</th>
      <th>acousticness_%</th>
      <th>instrumentalness_%</th>
      <th>liveness_%</th>
      <th>speechiness_%</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Seven (feat. Latto) (Explicit Ver.)</td>
      <td>Latto, Jung Kook</td>
      <td>2</td>
      <td>2023</td>
      <td>7</td>
      <td>14</td>
      <td>553</td>
      <td>147</td>
      <td>141381703</td>
      <td>43</td>
      <td>...</td>
      <td>125</td>
      <td>B</td>
      <td>Major</td>
      <td>80</td>
      <td>89</td>
      <td>83</td>
      <td>31</td>
      <td>0</td>
      <td>8</td>
      <td>4</td>
    </tr>
    <tr>
      <th>1</th>
      <td>LALA</td>
      <td>Myke Towers</td>
      <td>1</td>
      <td>2023</td>
      <td>3</td>
      <td>23</td>
      <td>1474</td>
      <td>48</td>
      <td>133716286</td>
      <td>48</td>
      <td>...</td>
      <td>92</td>
      <td>C#</td>
      <td>Major</td>
      <td>71</td>
      <td>61</td>
      <td>74</td>
      <td>7</td>
      <td>0</td>
      <td>10</td>
      <td>4</td>
    </tr>
    <tr>
      <th>2</th>
      <td>vampire</td>
      <td>Olivia Rodrigo</td>
      <td>1</td>
      <td>2023</td>
      <td>6</td>
      <td>30</td>
      <td>1397</td>
      <td>113</td>
      <td>140003974</td>
      <td>94</td>
      <td>...</td>
      <td>138</td>
      <td>F</td>
      <td>Major</td>
      <td>51</td>
      <td>32</td>
      <td>53</td>
      <td>17</td>
      <td>0</td>
      <td>31</td>
      <td>6</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Cruel Summer</td>
      <td>Taylor Swift</td>
      <td>1</td>
      <td>2019</td>
      <td>8</td>
      <td>23</td>
      <td>7858</td>
      <td>100</td>
      <td>800840817</td>
      <td>116</td>
      <td>...</td>
      <td>170</td>
      <td>A</td>
      <td>Major</td>
      <td>55</td>
      <td>58</td>
      <td>72</td>
      <td>11</td>
      <td>0</td>
      <td>11</td>
      <td>15</td>
    </tr>
    <tr>
      <th>4</th>
      <td>WHERE SHE GOES</td>
      <td>Bad Bunny</td>
      <td>1</td>
      <td>2023</td>
      <td>5</td>
      <td>18</td>
      <td>3133</td>
      <td>50</td>
      <td>303236322</td>
      <td>84</td>
      <td>...</td>
      <td>144</td>
      <td>A</td>
      <td>Minor</td>
      <td>65</td>
      <td>23</td>
      <td>80</td>
      <td>14</td>
      <td>63</td>
      <td>11</td>
      <td>6</td>
    </tr>
  </tbody>
</table>
<p>5 rows × 24 columns</p>
</div>




```python
df.info()
```

    <class 'pandas.core.frame.DataFrame'>
    RangeIndex: 953 entries, 0 to 952
    Data columns (total 24 columns):
     #   Column                Non-Null Count  Dtype 
    ---  ------                --------------  ----- 
     0   track_name            953 non-null    object
     1   artist(s)_name        953 non-null    object
     2   artist_count          953 non-null    int64 
     3   released_year         953 non-null    int64 
     4   released_month        953 non-null    int64 
     5   released_day          953 non-null    int64 
     6   in_spotify_playlists  953 non-null    int64 
     7   in_spotify_charts     953 non-null    int64 
     8   streams               953 non-null    object
     9   in_apple_playlists    953 non-null    int64 
     10  in_apple_charts       953 non-null    int64 
     11  in_deezer_playlists   953 non-null    object
     12  in_deezer_charts      953 non-null    int64 
     13  in_shazam_charts      903 non-null    object
     14  bpm                   953 non-null    int64 
     15  key                   858 non-null    object
     16  mode                  953 non-null    object
     17  danceability_%        953 non-null    int64 
     18  valence_%             953 non-null    int64 
     19  energy_%              953 non-null    int64 
     20  acousticness_%        953 non-null    int64 
     21  instrumentalness_%    953 non-null    int64 
     22  liveness_%            953 non-null    int64 
     23  speechiness_%         953 non-null    int64 
    dtypes: int64(17), object(7)
    memory usage: 178.8+ KB
    

## Basic Descriptive Statistics


```python
df['streams'] = pd.to_numeric(df['streams'], errors = 'coerce')

mean_streams = df['streams'].mean()
median_streams = df['streams'].median()
std_streams = df['streams'].std()

print('The mean is: ', mean_streams)
print('The median is: ', median_streams)
print('The standard deviation is: ', std_streams)
```

    The mean is:  514137424.93907565
    The median is:  290530915.0
    The standard deviation is:  566856949.0388832
    


```python
released_year_stats = df['released_year'].describe()
artist_count_stats = df['artist_count'].describe()

print('The released year statistics are:\n ', released_year_stats)

print('\nThe artist count statistics are:\n ', artist_count_stats)
```

    The released year statistics are:
      count     953.000000
    mean     2018.238195
    std        11.116218
    min      1930.000000
    25%      2020.000000
    50%      2022.000000
    75%      2022.000000
    max      2023.000000
    Name: released_year, dtype: float64
    
    The artist count statistics are:
      count    953.000000
    mean       1.556139
    std        0.893044
    min        1.000000
    25%        1.000000
    50%        1.000000
    75%        2.000000
    max        8.000000
    Name: artist_count, dtype: float64
    


```python
plt.figure(figsize = (14, 6))

plt.subplot(1, 2, 1)
sns.histplot(df['released_year'], kde = True, bins = 20)
plt.title('Distribution of Released Year')
plt.xlabel('Released Year')
plt.ylabel('Frequency')
```




    Text(0, 0.5, 'Frequency')




    
![png](output_9_1.png)
    



```python
plt.subplot(1, 2, 2)
sns.histplot(df['artist_count'], kde = True, bins = 8)
plt.title('Distribution of Artist Count')
plt.xlabel('Artist Count')
plt.ylabel('Frequency')
```




    Text(0, 0.5, 'Frequency')




    
![png](output_10_1.png)
    



```python
plt.tight_layout()
plt.show()
```


    <Figure size 640x480 with 0 Axes>



```python
plt.figure(figsize = (12, 6))
```




    <Figure size 1200x600 with 0 Axes>




    <Figure size 1200x600 with 0 Axes>



```python
plt.subplot(1, 2, 1)
sns.boxplot(x = df['released_year'])
plt.title('Box Plot of Released Year')
```




    Text(0.5, 1.0, 'Box Plot of Released Year')




    
![png](output_13_1.png)
    



```python
plt.subplot(1, 2, 2)
sns.boxplot(x = df['artist_count'])
plt.title('Box Plot of Artist Count')
```




    Text(0.5, 1.0, 'Box Plot of Artist Count')




    
![png](output_14_1.png)
    



```python
plt.tight_layout()
plt.show()
```


    <Figure size 640x480 with 0 Axes>



```python
for column in ['released_year', 'artist_count']:
    Q1 = df[column].quantile(0.25)
    Q3 = df[column].quantile(0.75)
    IQR = Q3 - Q1
    lower_bound = Q1 - 1.5 * IQR
    upper_bound = Q3 + 1.5 * IQR
    outliers = df[(df[column] < lower_bound) | (df[column] > upper_bound)]

print(f'Outliers in {column}: ')
print(outliers[[column]])
print('\n')
```

    Outliers in artist_count: 
         artist_count
    35              8
    135             4
    137             5
    141             4
    197             4
    200             4
    201             5
    238             5
    328             5
    365             4
    393             6
    402             6
    457             4
    488             4
    506             7
    540             4
    605             4
    638             4
    642             8
    667             7
    749             4
    759             6
    833             4
    837             4
    864             5
    894             4
    920             4
    
    
    

##  Top Performers


```python
# Inspecting the first few rows
df.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>track_name</th>
      <th>artist(s)_name</th>
      <th>artist_count</th>
      <th>released_year</th>
      <th>released_month</th>
      <th>released_day</th>
      <th>in_spotify_playlists</th>
      <th>in_spotify_charts</th>
      <th>streams</th>
      <th>in_apple_playlists</th>
      <th>...</th>
      <th>bpm</th>
      <th>key</th>
      <th>mode</th>
      <th>danceability_%</th>
      <th>valence_%</th>
      <th>energy_%</th>
      <th>acousticness_%</th>
      <th>instrumentalness_%</th>
      <th>liveness_%</th>
      <th>speechiness_%</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Seven (feat. Latto) (Explicit Ver.)</td>
      <td>Latto, Jung Kook</td>
      <td>2</td>
      <td>2023</td>
      <td>7</td>
      <td>14</td>
      <td>553</td>
      <td>147</td>
      <td>141381703.0</td>
      <td>43</td>
      <td>...</td>
      <td>125</td>
      <td>B</td>
      <td>Major</td>
      <td>80</td>
      <td>89</td>
      <td>83</td>
      <td>31</td>
      <td>0</td>
      <td>8</td>
      <td>4</td>
    </tr>
    <tr>
      <th>1</th>
      <td>LALA</td>
      <td>Myke Towers</td>
      <td>1</td>
      <td>2023</td>
      <td>3</td>
      <td>23</td>
      <td>1474</td>
      <td>48</td>
      <td>133716286.0</td>
      <td>48</td>
      <td>...</td>
      <td>92</td>
      <td>C#</td>
      <td>Major</td>
      <td>71</td>
      <td>61</td>
      <td>74</td>
      <td>7</td>
      <td>0</td>
      <td>10</td>
      <td>4</td>
    </tr>
    <tr>
      <th>2</th>
      <td>vampire</td>
      <td>Olivia Rodrigo</td>
      <td>1</td>
      <td>2023</td>
      <td>6</td>
      <td>30</td>
      <td>1397</td>
      <td>113</td>
      <td>140003974.0</td>
      <td>94</td>
      <td>...</td>
      <td>138</td>
      <td>F</td>
      <td>Major</td>
      <td>51</td>
      <td>32</td>
      <td>53</td>
      <td>17</td>
      <td>0</td>
      <td>31</td>
      <td>6</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Cruel Summer</td>
      <td>Taylor Swift</td>
      <td>1</td>
      <td>2019</td>
      <td>8</td>
      <td>23</td>
      <td>7858</td>
      <td>100</td>
      <td>800840817.0</td>
      <td>116</td>
      <td>...</td>
      <td>170</td>
      <td>A</td>
      <td>Major</td>
      <td>55</td>
      <td>58</td>
      <td>72</td>
      <td>11</td>
      <td>0</td>
      <td>11</td>
      <td>15</td>
    </tr>
    <tr>
      <th>4</th>
      <td>WHERE SHE GOES</td>
      <td>Bad Bunny</td>
      <td>1</td>
      <td>2023</td>
      <td>5</td>
      <td>18</td>
      <td>3133</td>
      <td>50</td>
      <td>303236322.0</td>
      <td>84</td>
      <td>...</td>
      <td>144</td>
      <td>A</td>
      <td>Minor</td>
      <td>65</td>
      <td>23</td>
      <td>80</td>
      <td>14</td>
      <td>63</td>
      <td>11</td>
      <td>6</td>
    </tr>
  </tbody>
</table>
<p>5 rows × 24 columns</p>
</div>




```python
top_5_artists = df['artist(s)_name'].value_counts().head(5)
print(top_5_artists)
```

    artist(s)_name
    Taylor Swift    34
    The Weeknd      22
    Bad Bunny       19
    SZA             19
    Harry Styles    17
    Name: count, dtype: int64
    

##  Temporal Trends


```python
tracks_per_year = df['released_year'].value_counts().sort_index()

plt.figure(figsize = (10, 6))
tracks_per_year.plot(kind = 'line', marker = 'o')
plt.title('Number of Tracks Released per Year')
plt.xlabel('Year')
plt.ylabel('Number of Tracks')
plt.grid()
plt.show()
```


    
![png](output_21_0.png)
    



```python
df = pd.read_csv('spotify_data/spotify-2023.csv', encoding = 'latin1')

df = df.dropna(subset = ['released_year', 'released_month'])

df['released_year'] = df['released_year'].astype(int)
df['released_month'] = df['released_month'].astype(int)

monthly_df = df.groupby('released_month')['track_name'].count()

monthly_df = monthly_df.reindex(range(1, 13), fill_value = 0)

plt.figure(figsize=(10, 6))
monthly_df.plot(kind='bar', color='skyblue')
plt.title('Total Number of Tracks Released per Month')
plt.xlabel('Month')
plt.ylabel('Number of Tracks Released')
plt.xticks(ticks = range(12), labels=['Jan', 'Feb', 'Mar', 'Apr', 'May', 'Jun', 'Jul', 'Aug', 'Sep', 'Oct', 'Nov', 'Dec'], rotation = 45)
plt.show()

```


    
![png](output_22_0.png)
    


##  Genre and Music Characteristics



```python
# List of columns to analyze
columns_of_interest = ['streams', 'bpm', 'danceability_%', 'energy_%', 'valence_%', 'acousticness_%']

# Convert columns to numeric, coercing errors to NaN to handle non-numeric data
for col in columns_of_interest:
    df[col] = pd.to_numeric(df[col], errors = 'coerce')

# Drop rows with NaN values in the selected columns to clean data
df_subset = df.dropna(subset = columns_of_interest)

# Calculate the correlation matrix
correlation_matrix = df_subset[columns_of_interest].corr()

# Visualize the correlation matrix
plt.figure(figsize = (10, 8))
sns.heatmap(correlation_matrix, annot = True, vmin = -1, vmax = 1)
plt.title("Correlation Matrix of Streams and Musical Attributes")
plt.show()

```


    
![png](output_24_0.png)
    


## Platform Popularity


```python
results_simplified = {
    'Spotify Playlists': (df['in_spotify_playlists'].sum(), df['in_spotify_playlists'].mean()),
    'Spotify Charts': (df['in_spotify_charts'].sum(), df['in_spotify_charts'].mean()),
    'Apple Playlists': (df['in_apple_playlists'].sum(), df['in_apple_playlists'].mean()),
    'Apple Charts': (df['in_apple_charts'].sum(), df['in_apple_charts'].mean())
}

popularity_df = pd.DataFrame(results_simplified, index=['Total Count', 'Average Count per Track']).T
popularity_df
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Total Count</th>
      <th>Average Count per Track</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Spotify Playlists</th>
      <td>4955719.0</td>
      <td>5200.124869</td>
    </tr>
    <tr>
      <th>Spotify Charts</th>
      <td>11445.0</td>
      <td>12.009444</td>
    </tr>
    <tr>
      <th>Apple Playlists</th>
      <td>64625.0</td>
      <td>67.812172</td>
    </tr>
    <tr>
      <th>Apple Charts</th>
      <td>49469.0</td>
      <td>51.908709</td>
    </tr>
  </tbody>
</table>
</div>



## Advanced Analysis


```python
average_streams_by_key = df.groupby('key')['streams'].mean()

average_streams_by_mode = df.groupby('mode')['streams'].mean()

print("Average Streams by Key:")
print(average_streams_by_key)
print("\nAverage Streams by Mode:")
print(average_streams_by_mode)

```

    Average Streams by Key:
    key
    A     4.088414e+08
    A#    5.524754e+08
    B     5.193480e+08
    C#    6.042802e+08
    D     5.295256e+08
    D#    5.530365e+08
    E     5.774972e+08
    F     4.684464e+08
    F#    5.223632e+08
    G     4.525994e+08
    G#    4.769119e+08
    Name: streams, dtype: float64
    
    Average Streams by Mode:
    mode
    Major    5.348328e+08
    Minor    4.859445e+08
    Name: streams, dtype: float64
    


```python
artist_playlist_chart_counts = df.groupby('artist(s)_name')[['in_spotify_playlists', 'in_spotify_charts', 'in_apple_playlists', 'in_apple_charts']].sum()

artist_playlist_chart_counts['total_appearances'] = artist_playlist_chart_counts.sum(axis=1)

top_artists = artist_playlist_chart_counts.sort_values(by='total_appearances', ascending=False).head(10)

top_artists

```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>in_spotify_playlists</th>
      <th>in_spotify_charts</th>
      <th>in_apple_playlists</th>
      <th>in_apple_charts</th>
      <th>total_appearances</th>
    </tr>
    <tr>
      <th>artist(s)_name</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>The Weeknd</th>
      <td>144053</td>
      <td>180</td>
      <td>1677</td>
      <td>1348</td>
      <td>147258</td>
    </tr>
    <tr>
      <th>Taylor Swift</th>
      <td>132974</td>
      <td>542</td>
      <td>1796</td>
      <td>1866</td>
      <td>137178</td>
    </tr>
    <tr>
      <th>Ed Sheeran</th>
      <td>128758</td>
      <td>94</td>
      <td>1448</td>
      <td>488</td>
      <td>130788</td>
    </tr>
    <tr>
      <th>Harry Styles</th>
      <td>110026</td>
      <td>185</td>
      <td>1741</td>
      <td>545</td>
      <td>112497</td>
    </tr>
    <tr>
      <th>Eminem</th>
      <td>87331</td>
      <td>152</td>
      <td>475</td>
      <td>281</td>
      <td>88239</td>
    </tr>
    <tr>
      <th>Arctic Monkeys</th>
      <td>84016</td>
      <td>190</td>
      <td>241</td>
      <td>340</td>
      <td>84787</td>
    </tr>
    <tr>
      <th>Coldplay</th>
      <td>75716</td>
      <td>72</td>
      <td>381</td>
      <td>25</td>
      <td>76194</td>
    </tr>
    <tr>
      <th>Avicii</th>
      <td>68241</td>
      <td>42</td>
      <td>407</td>
      <td>282</td>
      <td>68972</td>
    </tr>
    <tr>
      <th>Dr. Dre, Snoop Dogg</th>
      <td>65728</td>
      <td>0</td>
      <td>283</td>
      <td>118</td>
      <td>66129</td>
    </tr>
    <tr>
      <th>Adele</th>
      <td>65049</td>
      <td>69</td>
      <td>646</td>
      <td>331</td>
      <td>66095</td>
    </tr>
  </tbody>
</table>
</div>


