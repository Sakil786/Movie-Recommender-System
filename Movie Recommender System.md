

```python
#Importing Pandas and Numpy
import pandas as pd
import numpy as np
import warnings
warnings.filterwarnings('ignore')
#reading rating dataset
rating = pd.read_csv('/home/sakil/Desktop/DataScience/Project/ml-latest-small/ratings.csv')
rating.head()
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
      <th>userId</th>
      <th>movieId</th>
      <th>rating</th>
      <th>timestamp</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>1</td>
      <td>4.0</td>
      <td>964982703</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1</td>
      <td>3</td>
      <td>4.0</td>
      <td>964981247</td>
    </tr>
    <tr>
      <th>2</th>
      <td>1</td>
      <td>6</td>
      <td>4.0</td>
      <td>964982224</td>
    </tr>
    <tr>
      <th>3</th>
      <td>1</td>
      <td>47</td>
      <td>5.0</td>
      <td>964983815</td>
    </tr>
    <tr>
      <th>4</th>
      <td>1</td>
      <td>50</td>
      <td>5.0</td>
      <td>964982931</td>
    </tr>
  </tbody>
</table>
</div>




```python
#reading movies data
movie = pd.read_csv('/home/sakil/Desktop/DataScience/Project/ml-latest-small/movies.csv')
movie.head()
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
      <th>movieId</th>
      <th>title</th>
      <th>genres</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>Toy Story (1995)</td>
      <td>Adventure|Animation|Children|Comedy|Fantasy</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>Jumanji (1995)</td>
      <td>Adventure|Children|Fantasy</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3</td>
      <td>Grumpier Old Men (1995)</td>
      <td>Comedy|Romance</td>
    </tr>
    <tr>
      <th>3</th>
      <td>4</td>
      <td>Waiting to Exhale (1995)</td>
      <td>Comedy|Drama|Romance</td>
    </tr>
    <tr>
      <th>4</th>
      <td>5</td>
      <td>Father of the Bride Part II (1995)</td>
      <td>Comedy</td>
    </tr>
  </tbody>
</table>
</div>




```python
moviedata=pd.merge(rating,movie,on="movieId")
moviedata.head()
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
      <th>userId</th>
      <th>movieId</th>
      <th>rating</th>
      <th>timestamp</th>
      <th>title</th>
      <th>genres</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>1</td>
      <td>4.0</td>
      <td>964982703</td>
      <td>Toy Story (1995)</td>
      <td>Adventure|Animation|Children|Comedy|Fantasy</td>
    </tr>
    <tr>
      <th>1</th>
      <td>5</td>
      <td>1</td>
      <td>4.0</td>
      <td>847434962</td>
      <td>Toy Story (1995)</td>
      <td>Adventure|Animation|Children|Comedy|Fantasy</td>
    </tr>
    <tr>
      <th>2</th>
      <td>7</td>
      <td>1</td>
      <td>4.5</td>
      <td>1106635946</td>
      <td>Toy Story (1995)</td>
      <td>Adventure|Animation|Children|Comedy|Fantasy</td>
    </tr>
    <tr>
      <th>3</th>
      <td>15</td>
      <td>1</td>
      <td>2.5</td>
      <td>1510577970</td>
      <td>Toy Story (1995)</td>
      <td>Adventure|Animation|Children|Comedy|Fantasy</td>
    </tr>
    <tr>
      <th>4</th>
      <td>17</td>
      <td>1</td>
      <td>4.5</td>
      <td>1305696483</td>
      <td>Toy Story (1995)</td>
      <td>Adventure|Animation|Children|Comedy|Fantasy</td>
    </tr>
  </tbody>
</table>
</div>




```python
#removing genres from moviedata
moviedataset_col=["userId","movieId","rating","timestamp","title"]
moviedataset=moviedata[moviedataset_col]
moviedataset.head()

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
      <th>userId</th>
      <th>movieId</th>
      <th>rating</th>
      <th>timestamp</th>
      <th>title</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>1</td>
      <td>4.0</td>
      <td>964982703</td>
      <td>Toy Story (1995)</td>
    </tr>
    <tr>
      <th>1</th>
      <td>5</td>
      <td>1</td>
      <td>4.0</td>
      <td>847434962</td>
      <td>Toy Story (1995)</td>
    </tr>
    <tr>
      <th>2</th>
      <td>7</td>
      <td>1</td>
      <td>4.5</td>
      <td>1106635946</td>
      <td>Toy Story (1995)</td>
    </tr>
    <tr>
      <th>3</th>
      <td>15</td>
      <td>1</td>
      <td>2.5</td>
      <td>1510577970</td>
      <td>Toy Story (1995)</td>
    </tr>
    <tr>
      <th>4</th>
      <td>17</td>
      <td>1</td>
      <td>4.5</td>
      <td>1305696483</td>
      <td>Toy Story (1995)</td>
    </tr>
  </tbody>
</table>
</div>




```python
#writing moviedataset to moviedatasetwritetofile,it automatically creates file moviepreprocesseddata and writes all
#values of moviedataset to moviepreprocesseddata
moviedatasetwritetofile=moviedataset.to_csv('/home/sakil/Desktop/DataScience/Project/ moviepreprocesseddata.csv')
moviedatasetwritetofile
```


```python
#now we have dataset"moviedataset",we have done preprocessing part now we have to go for other steps using this dataset
moviedataset.shape
#moviedataset has 100836 rows and 5 columns
```




    (100836, 5)




```python
#to know about more dataset
moviedataset.describe()
#The movie dataset has 100836 recors,average rating is 3.50 and max rating is 5
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
      <th>userId</th>
      <th>movieId</th>
      <th>rating</th>
      <th>timestamp</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>count</th>
      <td>100836.000000</td>
      <td>100836.000000</td>
      <td>100836.000000</td>
      <td>1.008360e+05</td>
    </tr>
    <tr>
      <th>mean</th>
      <td>326.127564</td>
      <td>19435.295718</td>
      <td>3.501557</td>
      <td>1.205946e+09</td>
    </tr>
    <tr>
      <th>std</th>
      <td>182.618491</td>
      <td>35530.987199</td>
      <td>1.042529</td>
      <td>2.162610e+08</td>
    </tr>
    <tr>
      <th>min</th>
      <td>1.000000</td>
      <td>1.000000</td>
      <td>0.500000</td>
      <td>8.281246e+08</td>
    </tr>
    <tr>
      <th>25%</th>
      <td>177.000000</td>
      <td>1199.000000</td>
      <td>3.000000</td>
      <td>1.019124e+09</td>
    </tr>
    <tr>
      <th>50%</th>
      <td>325.000000</td>
      <td>2991.000000</td>
      <td>3.500000</td>
      <td>1.186087e+09</td>
    </tr>
    <tr>
      <th>75%</th>
      <td>477.000000</td>
      <td>8122.000000</td>
      <td>4.000000</td>
      <td>1.435994e+09</td>
    </tr>
    <tr>
      <th>max</th>
      <td>610.000000</td>
      <td>193609.000000</td>
      <td>5.000000</td>
      <td>1.537799e+09</td>
    </tr>
  </tbody>
</table>
</div>




```python
#We group the dataset by the title column and compute its mean to obtain the average rating for each movie.
ratings = pd.DataFrame(moviedataset.groupby('title')['rating'].mean())
ratings.head()
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
      <th>rating</th>
    </tr>
    <tr>
      <th>title</th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>'71 (2014)</th>
      <td>4.0</td>
    </tr>
    <tr>
      <th>'Hellboy': The Seeds of Creation (2004)</th>
      <td>4.0</td>
    </tr>
    <tr>
      <th>'Round Midnight (1986)</th>
      <td>3.5</td>
    </tr>
    <tr>
      <th>'Salem's Lot (2004)</th>
      <td>5.0</td>
    </tr>
    <tr>
      <th>'Til There Was You (1997)</th>
      <td>4.0</td>
    </tr>
  </tbody>
</table>
</div>




```python
#Next we would like to see the number of ratings for each movie. 
#We do this by creating a number_of_ratings column. 
ratings['number_of_ratings'] = moviedataset.groupby('title')['rating'].count()
ratings.head()
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
      <th>rating</th>
      <th>number_of_ratings</th>
    </tr>
    <tr>
      <th>title</th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>'71 (2014)</th>
      <td>4.0</td>
      <td>1</td>
    </tr>
    <tr>
      <th>'Hellboy': The Seeds of Creation (2004)</th>
      <td>4.0</td>
      <td>1</td>
    </tr>
    <tr>
      <th>'Round Midnight (1986)</th>
      <td>3.5</td>
      <td>2</td>
    </tr>
    <tr>
      <th>'Salem's Lot (2004)</th>
      <td>5.0</td>
      <td>1</td>
    </tr>
    <tr>
      <th>'Til There Was You (1997)</th>
      <td>4.0</td>
      <td>2</td>
    </tr>
  </tbody>
</table>
</div>




```python
#now plotting a Histogram using pandas plotting functionality to visualize the distribution of the ratings
import matplotlib.pyplot as plt
%matplotlib inline
ratings['rating'].hist(bins=50)
```




    <matplotlib.axes._subplots.AxesSubplot at 0x7fad88d402b0>




![png](output_9_1.png)



```python
#visualize the number_of_ratings column in as similar manner.
ratings['number_of_ratings'].hist(bins=60)
```




    <matplotlib.axes._subplots.AxesSubplot at 0x7fad898e8278>




![png](output_10_1.png)



```python
#now checking the relationship between the rating of a movie and the number of ratings
#We do this by plotting a scatter plot using seaborn. 
#Seaborn enables us to do this using the jointplot() function.
import seaborn as sns
sns.jointplot(x='rating', y='number_of_ratings', data=ratings)
```




    <seaborn.axisgrid.JointGrid at 0x7fad888a6d30>




![png](output_11_1.png)



```python
#In order to do this we need to convert our dataset into a matrix with the movie titles as the columns,
#the user_id as the index and the ratings as the values. 
#By doing this we shall get a dataframe with the columns as the movie titles and the rows as the user ids. 
#Each column represents all the ratings of a movie by all users.
# The rating appear as NAN where a user didn't rate a certain movie.
#We shall use this matrix to compute the correlation between the ratings of a single movie and the rest of the movies in the matrix. 
#We use pandas pivot_table utility to create the movie matrix.
moviedataset_matrix = moviedataset.pivot_table(index='userId', columns='title', values='rating')
moviedataset_matrix.head()
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
      <th>title</th>
      <th>'71 (2014)</th>
      <th>'Hellboy': The Seeds of Creation (2004)</th>
      <th>'Round Midnight (1986)</th>
      <th>'Salem's Lot (2004)</th>
      <th>'Til There Was You (1997)</th>
      <th>'Tis the Season for Love (2015)</th>
      <th>'burbs, The (1989)</th>
      <th>'night Mother (1986)</th>
      <th>(500) Days of Summer (2009)</th>
      <th>*batteries not included (1987)</th>
      <th>...</th>
      <th>Zulu (2013)</th>
      <th>[REC] (2007)</th>
      <th>[REC]² (2009)</th>
      <th>[REC]³ 3 Génesis (2012)</th>
      <th>anohana: The Flower We Saw That Day - The Movie (2013)</th>
      <th>eXistenZ (1999)</th>
      <th>xXx (2002)</th>
      <th>xXx: State of the Union (2005)</th>
      <th>¡Three Amigos! (1986)</th>
      <th>À nous la liberté (Freedom for Us) (1931)</th>
    </tr>
    <tr>
      <th>userId</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>1</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>4.0</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>3</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>4</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>5</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
<p>5 rows × 9719 columns</p>
</div>




```python
# look at the most rated movies and choose two of them to work with in this simple recommender system.
#We use pandas sort_values utility and set ascending to false in order to arrange the movies from the most rated.
#We then use the head() function to view the top 10.
ratings.sort_values('number_of_ratings', ascending=False).head(10)
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
      <th>rating</th>
      <th>number_of_ratings</th>
    </tr>
    <tr>
      <th>title</th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Forrest Gump (1994)</th>
      <td>4.164134</td>
      <td>329</td>
    </tr>
    <tr>
      <th>Shawshank Redemption, The (1994)</th>
      <td>4.429022</td>
      <td>317</td>
    </tr>
    <tr>
      <th>Pulp Fiction (1994)</th>
      <td>4.197068</td>
      <td>307</td>
    </tr>
    <tr>
      <th>Silence of the Lambs, The (1991)</th>
      <td>4.161290</td>
      <td>279</td>
    </tr>
    <tr>
      <th>Matrix, The (1999)</th>
      <td>4.192446</td>
      <td>278</td>
    </tr>
    <tr>
      <th>Star Wars: Episode IV - A New Hope (1977)</th>
      <td>4.231076</td>
      <td>251</td>
    </tr>
    <tr>
      <th>Jurassic Park (1993)</th>
      <td>3.750000</td>
      <td>238</td>
    </tr>
    <tr>
      <th>Braveheart (1995)</th>
      <td>4.031646</td>
      <td>237</td>
    </tr>
    <tr>
      <th>Terminator 2: Judgment Day (1991)</th>
      <td>3.970982</td>
      <td>224</td>
    </tr>
    <tr>
      <th>Schindler's List (1993)</th>
      <td>4.225000</td>
      <td>220</td>
    </tr>
  </tbody>
</table>
</div>




```python
#I am choosing "Forrest Gump (1994)" and "Shawshank Redemption, The (1994)" movies.
#We would like like to recommend movies to this user based on this watching history.
#The goal is to look for movies that are similar to Forrest Gump (1994) and Shawshank Redemption, The (1994) which we shall recommend 
#to this user.
#We can achieve this by computing the correlation between these two movies’ ratings
#and the ratings of the rest of the movies in the dataset.
# The first step is to create a dataframe with the ratings of these movies from our moviedataset_matrix.
#Forrest Gump (1994) user rating
FG_user_rating = moviedataset_matrix['Forrest Gump (1994)']
FG_user_rating.head(10)
```




    userId
    1     4.0
    2     NaN
    3     NaN
    4     NaN
    5     NaN
    6     5.0
    7     5.0
    8     3.0
    9     NaN
    10    3.5
    Name: Forrest Gump (1994), dtype: float64




```python
#Shawshank Redemption, The (1994) user rating
SR_user_rating = moviedataset_matrix['Shawshank Redemption, The (1994)']
SR_user_rating.head(10)
```




    userId
    1     NaN
    2     3.0
    3     NaN
    4     NaN
    5     3.0
    6     5.0
    7     NaN
    8     5.0
    9     NaN
    10    NaN
    Name: Shawshank Redemption, The (1994), dtype: float64




```python
#In order to compute the correlation between two dataframes we use pandas corwith functionality.
#Corrwith computes the pairwise correlation of rows or columns of two dataframe objects.
#Let's use this functionality to get the correlation between each movie's rating 
#and the ratings of the Forrest Gump (1994) movie.
similar_to_forest_gump=moviedataset_matrix.corrwith(FG_user_rating)
similar_to_forest_gump.head(10)
#We can see that the correlation between Forrest Gump (1994) movie and batteries not included (1987) is 0.8927. This indicates a very strong similarity between these two movies.

```




    title
    '71 (2014)                                      NaN
    'Hellboy': The Seeds of Creation (2004)         NaN
    'Round Midnight (1986)                          NaN
    'Salem's Lot (2004)                             NaN
    'Til There Was You (1997)                       NaN
    'Tis the Season for Love (2015)                 NaN
    'burbs, The (1989)                         0.197712
    'night Mother (1986)                            NaN
    (500) Days of Summer (2009)                0.234095
    *batteries not included (1987)             0.892710
    dtype: float64




```python
#Let’s move on and compute the correlation between Shawshank Redemption, The (1994) ratings and the rest of the movies ratings. 
#The procedure is the same as the one used above.
similar_to_Shawshank_Redemption  = moviedataset_matrix.corrwith(SR_user_rating)
similar_to_Shawshank_Redemption.head(15)
#We realize from the computation that there is a correlation (of 0.419) between Shawshank Redemption, The (1994)
#burbs, The (1989) 
```




    title
    '71 (2014)                                          NaN
    'Hellboy': The Seeds of Creation (2004)             NaN
    'Round Midnight (1986)                              NaN
    'Salem's Lot (2004)                                 NaN
    'Til There Was You (1997)                           NaN
    'Tis the Season for Love (2015)                     NaN
    'burbs, The (1989)                             0.419543
    'night Mother (1986)                                NaN
    (500) Days of Summer (2009)                    0.249580
    *batteries not included (1987)                 0.404520
    ...All the Marbles (1981)                           NaN
    ...And Justice for All (1979)                 -1.000000
    00 Schneider - Jagd auf Nihil Baxter (1994)         NaN
    1-900 (06) (1994)                                   NaN
    10 (1979)                                           NaN
    dtype: float64




```python
#As noticed earlier our matrix had very many missing values since not all the movies were rated by all the users.
#We therefore drop those null values and transform correlation results into dataframes to make the 
#results look more appealing.
corr_FG= pd.DataFrame(similar_to_forest_gump, columns=['Correlation'])
corr_FG.dropna(inplace=True)
corr_FG.head()
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
      <th>Correlation</th>
    </tr>
    <tr>
      <th>title</th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>'burbs, The (1989)</th>
      <td>0.197712</td>
    </tr>
    <tr>
      <th>(500) Days of Summer (2009)</th>
      <td>0.234095</td>
    </tr>
    <tr>
      <th>*batteries not included (1987)</th>
      <td>0.892710</td>
    </tr>
    <tr>
      <th>...And Justice for All (1979)</th>
      <td>0.928571</td>
    </tr>
    <tr>
      <th>10 Cent Pistol (2015)</th>
      <td>-1.000000</td>
    </tr>
  </tbody>
</table>
</div>




```python
corr_SR= pd.DataFrame(similar_to_Shawshank_Redemption, columns=['Correlation'])
corr_SR.dropna(inplace=True)
corr_SR.head()
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
      <th>Correlation</th>
    </tr>
    <tr>
      <th>title</th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>'burbs, The (1989)</th>
      <td>0.419543</td>
    </tr>
    <tr>
      <th>(500) Days of Summer (2009)</th>
      <td>0.249580</td>
    </tr>
    <tr>
      <th>*batteries not included (1987)</th>
      <td>0.404520</td>
    </tr>
    <tr>
      <th>...And Justice for All (1979)</th>
      <td>-1.000000</td>
    </tr>
    <tr>
      <th>10 Cloverfield Lane (2016)</th>
      <td>0.145671</td>
    </tr>
  </tbody>
</table>
</div>




```python
#These two dataframes above show us the movies that are most similar
#to Forrest Gump (1994) and Shawshank Redemption, The (1994) movies respectively.
#However we have a challenge in that some of the movies have very few ratings and may end up being recommended simply because 
#one or two people gave them a 5 star rating. 
#We can fix this by setting a threshold for the number of ratings.
#From the histogram earlier we saw a sharp decline in number of ratings from 100. 
#We shall therefore set this as the threshold, however this is a number you can play around with until you get a suitable option. 
#In order to do this we need to join the two dataframes with the number_of_ratings column in the ratings dataframe.

corr_FG = corr_FG.join(ratings['number_of_ratings'])
corr_FG.head()

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
      <th>Correlation</th>
      <th>number_of_ratings</th>
    </tr>
    <tr>
      <th>title</th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>'burbs, The (1989)</th>
      <td>0.197712</td>
      <td>17</td>
    </tr>
    <tr>
      <th>(500) Days of Summer (2009)</th>
      <td>0.234095</td>
      <td>42</td>
    </tr>
    <tr>
      <th>*batteries not included (1987)</th>
      <td>0.892710</td>
      <td>7</td>
    </tr>
    <tr>
      <th>...And Justice for All (1979)</th>
      <td>0.928571</td>
      <td>3</td>
    </tr>
    <tr>
      <th>10 Cent Pistol (2015)</th>
      <td>-1.000000</td>
      <td>2</td>
    </tr>
  </tbody>
</table>
</div>




```python
corr_SR = corr_SR.join(ratings['number_of_ratings'])
corr_SR.head()
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
      <th>Correlation</th>
      <th>number_of_ratings</th>
    </tr>
    <tr>
      <th>title</th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>'burbs, The (1989)</th>
      <td>0.419543</td>
      <td>17</td>
    </tr>
    <tr>
      <th>(500) Days of Summer (2009)</th>
      <td>0.249580</td>
      <td>42</td>
    </tr>
    <tr>
      <th>*batteries not included (1987)</th>
      <td>0.404520</td>
      <td>7</td>
    </tr>
    <tr>
      <th>...And Justice for All (1979)</th>
      <td>-1.000000</td>
      <td>3</td>
    </tr>
    <tr>
      <th>10 Cloverfield Lane (2016)</th>
      <td>0.145671</td>
      <td>14</td>
    </tr>
  </tbody>
</table>
</div>




```python
#We shall now obtain the movies that are most similar to Forrest Gump (1994) by limiting them 
#to movies that have at least 100 reviews.
#We then sort them by the correlation column and view the first 10.
corr_FG[corr_FG['number_of_ratings'] > 100].sort_values(by='Correlation', ascending=False).head(10)
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
      <th>Correlation</th>
      <th>number_of_ratings</th>
    </tr>
    <tr>
      <th>title</th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Forrest Gump (1994)</th>
      <td>1.000000</td>
      <td>329</td>
    </tr>
    <tr>
      <th>Good Will Hunting (1997)</th>
      <td>0.484042</td>
      <td>141</td>
    </tr>
    <tr>
      <th>Aladdin (1992)</th>
      <td>0.464268</td>
      <td>183</td>
    </tr>
    <tr>
      <th>American History X (1998)</th>
      <td>0.457287</td>
      <td>129</td>
    </tr>
    <tr>
      <th>Truman Show, The (1998)</th>
      <td>0.432556</td>
      <td>125</td>
    </tr>
    <tr>
      <th>Braveheart (1995)</th>
      <td>0.416976</td>
      <td>237</td>
    </tr>
    <tr>
      <th>Ferris Bueller's Day Off (1986)</th>
      <td>0.405830</td>
      <td>109</td>
    </tr>
    <tr>
      <th>Mrs. Doubtfire (1993)</th>
      <td>0.401408</td>
      <td>144</td>
    </tr>
    <tr>
      <th>Full Metal Jacket (1987)</th>
      <td>0.397241</td>
      <td>102</td>
    </tr>
    <tr>
      <th>Saving Private Ryan (1998)</th>
      <td>0.390074</td>
      <td>188</td>
    </tr>
  </tbody>
</table>
</div>




```python
#We notice that Forrest Gump (1994)	has a perfect correlation with itself, which is not surprising.
#The next most similar movie to Air Force One (1997) is Good Will Hunting (1997) with a correlation of 0.484. 
#Clearly by changing the threshold for the number of reviews we get different results from the previous way of doing it. 
#Limiting the number of rating gives us better results and
#we can confidently recommend the above movies to someone who has watched Forrest Gump (1994).

```


```python
#Now let’s do the same for Shawshank Redemption, The (1994) movie and see the movies that are most correlated to it
corr_SR[corr_SR['number_of_ratings'] > 100].sort_values(by='Correlation', ascending=False).head(10)
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
      <th>Correlation</th>
      <th>number_of_ratings</th>
    </tr>
    <tr>
      <th>title</th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Shawshank Redemption, The (1994)</th>
      <td>1.000000</td>
      <td>317</td>
    </tr>
    <tr>
      <th>Four Weddings and a Funeral (1994)</th>
      <td>0.446212</td>
      <td>103</td>
    </tr>
    <tr>
      <th>Schindler's List (1993)</th>
      <td>0.402202</td>
      <td>220</td>
    </tr>
    <tr>
      <th>Usual Suspects, The (1995)</th>
      <td>0.394294</td>
      <td>204</td>
    </tr>
    <tr>
      <th>Ocean's Eleven (2001)</th>
      <td>0.391546</td>
      <td>119</td>
    </tr>
    <tr>
      <th>Green Mile, The (1999)</th>
      <td>0.382818</td>
      <td>111</td>
    </tr>
    <tr>
      <th>Inception (2010)</th>
      <td>0.377839</td>
      <td>143</td>
    </tr>
    <tr>
      <th>Catch Me If You Can (2002)</th>
      <td>0.356612</td>
      <td>115</td>
    </tr>
    <tr>
      <th>One Flew Over the Cuckoo's Nest (1975)</th>
      <td>0.354215</td>
      <td>133</td>
    </tr>
    <tr>
      <th>Godfather: Part II, The (1974)</th>
      <td>0.349872</td>
      <td>129</td>
    </tr>
  </tbody>
</table>
</div>




```python
#Once again we get different results. The most similar movie to Shawshank Redemption, The (1994) is
#Four Weddings and a Funeral (1994) with a correlation coefficient of 0.446 with 103 ratings. 
#So if somebody liked Shawshank Redemption, The (1994) we can recommend the above movies to them.
```

<p>So we build a simple movie recommender system.</p>

<p><b>Dataset used in this project:</b><br>
    Please find the following URL for dataset download:<br>
    <a href="http://files.grouplens.org/datasets/movielens/ml-latest-small.zip">dataset</a><br>
<a href="http://files.grouplens.org/datasets/movielens/ml-latest-small-README.html">Readme file for dataset</a><br>You can compare your preprocessed data from my preprocessed data named <b>moviepreprocesseddata</b><br> 
<a href="https://github.com/Sakil786/Movie-Recommender-System/blob/master/%20moviepreprocesseddata.csv">Preprocessed dataset</a></p>
