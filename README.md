# Investigating-Netflix-Movies
Explore Netflix movie data and perform exploratory data analysis for a production company to uncover insights about movies from a particular decade.
    In this task I perform exploratory data analysis on the netflix_data.csv data to understand more about movies from the 1990s decade and answer two questions:
First: What was the most frequent movie duration in the 1990s? Save an approximate answer as an integer called duration.
Second: A movie is considered short if it is less than 90 minutes. Count the number of short action movies released in the 1990s and save this integer as short_movie_count.
•	I start the task by importing data 
import pandas as pd
import matplotlib.pyplot as plt
#Read in the Netflix CSV as a DataFrame
netflix_df = pd.read_csv("netflix_data.csv")
print (netflix_df['type'].unique())
•	Then I filter the data to include only movie between 1990 and 1999
netflix_df_movie = netflix_df[netflix_df['type']=='Movie']
netflix_df_movie_90 = netflix_df_movie[(netflix_df_movie['release_year']>= 1990) & (netflix_df_movie['release_year']< 2000)]
•	After that I try to answer first question by compute the  mean, median and plot histogram

plt.hist(netflix_df_movie_90['duration'],bins=10)
plt.show()
#print(netflix_df_movie_90['duration'])
duration1 = netflix_df_movie_90.loc[:,'duration'].median()   // 108.0
duration3 = netflix_df_movie_90.loc[:,'duration'].mean()  // 115.12
print("the median is : "+ str(duration1)+" the mean is : "+ str(duration3)) 
duration = 100

•	Then for second question, I need to filter data again to only include action movies which duration is less than 90 minutes
short_movie_count = len(netflix_df_movie_90.query('duration < 90 and genre == "Action" ' ))
print("the number of short action movies: "+ str(short_movie_count)) \  // 7 movies
