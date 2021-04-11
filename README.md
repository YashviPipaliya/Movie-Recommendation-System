# -CSE523-Machine-Learning-Abraca-data
# Movie Recommendation System
# Introduction 

As we know, there's an explosive amount of growth on the Internet in terms of digital information and the number of users. Due to this, there's an information overload hindering timely access of different items on the Internet. Therefore, there's an increasing demand for recommendation systems. They are information filtering systems which handle the problem of information overload by filtering out the important chunks of data from the available data according to user's preferences or interests about the item and provide them with personalized recommendations. 

There are different filter-based approaches to building recommendation systems.We are doing a content-based movie recommendation system. It suggests a set of movies based on other movies of the user's preference. It filters out movies based on different attributes like genre, directors, countries etc. using three different methods 1) clustering and TF-IDF Vectorization 2) TF-IDF Vectorization 3) Count Verctorization. We then compare the results from all three methods and recommend the most probable.
These systems are beneficial for organizations that collect data from large number of customers and who wish to effectively provide the best suggestions possible.

# Exploratory Data Analysis
Count of movies VS TV-shows
![](https://github.com/YashviPipaliya/-CSE523-Machine-Learning-Abraca-data/blob/main/Results/EDA/Count%20of%20movies%20VS%20TV-shows.PNG)

Distribution of content uploaded
![](https://github.com/YashviPipaliya/-CSE523-Machine-Learning-Abraca-data/blob/main/Results/EDA/Distribution%20of%20content%20uploaded.PNG)

Movie Rating Analysis
![](https://github.com/YashviPipaliya/-CSE523-Machine-Learning-Abraca-data/blob/main/Results/EDA/Movie%20Rating%20Analysis.PNG)

Types of Genres
![](https://github.com/YashviPipaliya/-CSE523-Machine-Learning-Abraca-data/blob/main/Results/EDA/Types%20of%20Genres.PNG)


# Recommendation Model 1
Using the feature importances calculated by Drop column feature importance, we computed a score by multiplying the respective feature importance values with the features and then summed up the products. Thus we now have a parameter score for every movie in the dataset. Next, we plot the distribution of score and then apply Kernel Density Estimation from the range of the peak from the plot, that is, -1050 to 10,000.

After computing the density, we find the local maxima and minima values and form clusters based on these values. As there are 25 local maxima and local minima points, we obtain 25 clusters containing different movies. Once the clusters are formed, we move to computing TF-IDF vectorization matrix on the feature "genre" to obtain a similarity score for various movies using cosine similarity. Next, we define a function to get the input movie title from the user and based on the title, the function would compute the similarity score of the input movie to all the movies in the dataset and return the movies with similarity index greater than 0.7 from the same cluster or from the same director. Thus, a recommendation system using clustering is obtained.

![](https://github.com/YashviPipaliya/-CSE523-Machine-Learning-Abraca-data/blob/main/Results/Final%20Results/Model1%20Movie3.PNG)

# Recommendation Model 2
Now for the second approach, we built a single parameter based movie recommendation system by computing the TF-IDF vectorization matrix on the feature "description" and defined a function to compute the similarity score of the input movie with other movies in the dataset and return the top 10 movies with highest similarity score.

![](https://github.com/YashviPipaliya/-CSE523-Machine-Learning-Abraca-data/blob/main/Results/Final%20Results/Model2%20Movie3.PNG)

# Recommendation Model 3
For the third type of recommendation system, we first chose top 5 features: genre, director, cast, country, and title. Following that, we conducted Data Prepossessing where we convert all the upper case data to lower case data and eliminate the unnecessary space and defined a new parameter "Bag of words" to combine all of the 5 parameters. After creating the BOW parameter, we compute the sparse matrix using count vectorization and cosine similarity. Lastly, we define a function which will compute the similarity score of the input movie to all the movies in the dataset using the sparse matrix. The function will return the top 10 movies with the highest similarity score as output. Thus, a recommendation system with multiple parameters is obtained.

![](https://github.com/YashviPipaliya/-CSE523-Machine-Learning-Abraca-data/blob/main/Results/Final%20Results/Model3%20Movie3.PNG)

# Recommendation Model 4
For the last type of recommendation system, we use clustering as well as count vectorization. Here, we take the clustered movie dataset obtained in the first type of recommendation system and then choose top 3 features which are genre, cast and description. As the features are selected, next step would be data prepossessing as we did in 3rd type of recommendation system. Next, we again create a new parameter "Bag Of Words" to combine all the three parameters. Now, using count vectorization and cosine similarity to compute sparse matrix which helps in defining a function to calculate the similarity score of input movie with other movies in the clusters. The function will return all the movies with similarity score greater than 0.12. Here, we need to keep the limiting similarity score very less as the number of parameters taken into consideration are more and the number of movies in the cluster with similarity score similar to the input movie's score is less due which a problem like over-fitting may occur. But keeping the similarity score very less may produce extraneous movies as well. Thus, the 4th recommendation system is not the most efficient system for recommending movies.

![](https://github.com/YashviPipaliya/-CSE523-Machine-Learning-Abraca-data/blob/main/Results/Final%20Results/Model4%20Movie3.jpeg)

# Conclusion 

![](https://github.com/YashviPipaliya/-CSE523-Machine-Learning-Abraca-data/blob/main/Results/Comparision.PNG)

# Refrences 
TF-IDF & Cosine Similarity

https://monkeylearn.com/blog/what-is-tf-idf/

https://janav.wordpress.com/2013/10/27/tf-idf-and-cosine-similarity/

Feature Importance using Random Forest & KDE

https://towardsdatascience.com/explaining-feature-importance-by-example-of-a-rand

https://scikit-learn.org/stable/modules/density.html

CountVectorizer & KDE

https://scikit-learn.org/stable/modules/generated/sklearn.feature_extraction.text.CountVectorizer.html

Netflix and imdb Dataset

https://www.kaggle.com/shivamb/netflix-shows

https://www.kaggle.com/stefanoleone992/imdb-extensive-dataset

EDA Analysis & Kaggle Tutorial

https://www.datacamp.com/community/tutorials/kaggle-machine-learning-eda






