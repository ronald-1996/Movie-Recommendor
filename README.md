# Movie-Recommendor
## A Movie Recommender System using multiple algorithms
I built a recommender system for users to recommend movies using 3 methods: based on user ratings (demographic filtering), based on similarity of movie description (content-based filtering) and based on users' preferences for different movies (collaborative filtering). Apache Spark was used to process the large dataset.

## Demographic Filter 
This recommendation engine type essentially considers user’s demographics into account in order to make recommendations. For each of the movies in the dataset, the 90th percentile of ‘vote count’ (c) is calculated. Movies with vote count more than 'c' are the candidates for the movie recommendation engine. A score is calculated for the candidate movies based on the formula provided by the IMDb website: score = v/((v+m)).R +m/((m+v)).C Movies are then sorted in descending order based on the values of the score obtained from the above formula. High scoring movies are recommended to the users.

## Content Filter

This recommender system computes the similarity between textual data. We convert these textual data into vectors and check the cosine angle between each of them and form a cosine score for each of them with respect to others. TF-IDF vector is generated using the 'overview' column in the data which is the description of the movie. Based on the similarity of movies users have watched and want to watch, movies with higher similarity scores are recommended to the user.

## Collaborative Filter

This technique uses matrix factorization at its core for generating recommendations. An interesting hyperprameter that separates this technique from the rest is the 'latent factors'. Latent factors capture the users' tastes and biases. Matrix factorization uses these latent factors to represent user tastes and biases in a lower dimension. The more the number of latent factors, the more personalized the recommendation will be. However, we need to be careful while deciding the number of latent factors as a very high number of latent factors can also lead to overfitting. Regularization is also incorporated to avoid any overfitting.

## Alternate Least Squares
Alternating Least Squares (ALS) machine learning tool in Spark’s ML library was used in order to perform collaborative filtering for this dataset. The main feature that enables the ALS algorithm to handle large-scale data is its parallelization. Like conventional machine learning models, ALS also minimizes the loss function by performing gradient descent. The unique thing in ALS performing gradient descent is that it runs it in parallel across different batches of the training data from different clusters of machines. This allows it to process large amounts of data relatively easily. Item-based filtering was performed over user-based filtering as the nature of users is usually unpredictable and dynamic with time, while items’ characteristics don’t change over a period of time.

# Tableau Visualizations 
## Demographic Filter
https://public.tableau.com/profile/vindhya.rudrappa#!/vizhome/DemographicFiltering/Dashboard1

## Content Filter 
https://public.tableau.com/profile/ronald6572#!/vizhome/ContentBasedFiltering_16067848201130/Dashboard1

## Reference
https://www.kaggle.com/ibtesama/getting-started-with-a-movie-recommendation-system
