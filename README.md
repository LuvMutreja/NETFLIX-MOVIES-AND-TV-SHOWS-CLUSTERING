# NETFLIX-MOVIES-AND-TV-SHOWS-CLUSTERING

PROBLEM STATEMENT
This dataset consists of tv shows and movies available on Netflix as of 2019. The dataset is
collected from Flixable which is a third-party Netflix search engine. In 2018, they released
an interesting report which shows that the number of TV shows on Netflix has nearly tripled
since 2010. The streaming service's number of movies has decreased by more than 2,000
titles since 2010, while its number of TV shows has nearly tripled. It will be interesting to
explore what all other insights can be obtained from the same dataset.

SUMMARY
Clustering is the grouping of objects based on their characteristics such that there is high intra-cluster similarity and low inter-cluster similarity. It has a lot of uses in a variety of industries, including market segmentation, social network analysis, search result grouping, medical imaging, image segmentation and anomaly detection.
Data scientists and others use clustering to gain important insights from data by observing what groups (or clusters) the data points fall into when they apply a clustering algorithm to the data. Clustering can also be used for anomaly detection to find data points that are not part of any cluster, or outliers. Clustering is a part of unsupervised learning, which is a machine learning technique that does not require the supervision of models by users. In unsupervised machine learning, we use a learning algorithm to discover unknown patterns in unlabeled datasets i.e there is no target variable.
The dataset I have here is containing 7787 rows and 12 columns where each row is for a show. The columns are-
* Show id- Unique Identifier for each record.
* Type- Telling if a show is a movie or a tv show.
* Title- Telling the title of the show.
* Director- Telling the name of the director of the show.
* Cast- Actors that acted in the show.
* Country- The nation that produced that particular show.
* Date Added- Date at which the show was added on NETFLIX.
* Release Year- Year in which the show released.
* Rating- The rating of the show.
* Duration- Duration of the show in minutes for movies and in season for tv shows.
* Listed in- The genre of the show.
* Description- The description of the show.
Then I checked the null values in the dataset and found that 5 columns had null values i.e Director=2389, Cast=718, Country=507, Date added=10 and rating=7.
Which I imputed by replacing in 4 of the columns by unknown, and dropped the null values in date added column. Date added column's null values were dropped because it only had 0.09% values as null.
Then I did some manipulations-
* Created a function to extract the number of movies and tv shows an actor has appeared in.
* Created a new dataframe from the orignal dataframe which only contained the details for movies.
* Converted the duration for movies to int.
* The values for country and genre column are not ideal so only considering the first values from both the columns.
* Created a function to convert date_added column value's datatype from string to datetime datatype.
* Extracted the year from date_added column and assigned the values to a new column named year_added.
* Made a new column named latest which showed if a show was added in the same year it was released or not.
* Replaced the values of the rating column.
* Created a function to create wordcloud given dataset and column as argument.
Then I conducted 2 hypothesis tests-
* Sample mean and population mean are the same for the release year column.
in which I failed to reject the null hypothesis.
* Duration for movies is normally distributed in which I rejected the null hypothesis.
Then features were selected to conduct NLP on for further passing them into the Custering algorithms. The selected columns were [director,cast,country,listed_in,description,rating]
Then Natural Language Processing was done on the selected columns in order to apply clustering algorithm on them.TFIDF vectorizer was used to vectorize the the data because it assigns a score to each word that reflects its importance in the document and the whole corpus, which is not done by the Count Vectorizer. Then the data was scaled using Standard Scaler and then PCA was fitted over the data in order to reduce the dimensionality with the n components' value = 3.
The 1st ML model that I used was K Means clustering whose value of K was chosen by plotting the elbow chart and silhouette scores for each value of K from 1 to 25. Finally n clusters in K means was taken as 5 which was giving variance of 58185 and silhouette score of 0.458. The 2nd model that I used was Agglomerative Hierarchical Clustering in which I took n clusters as 11 by looking at the denrogram. Agglomerative Hierarchical Clustering was giving silhouette score of 
0.389. As we can make out that KMeans had better silhouette score than Agglomerative Hierarchical Clustering. Therefore it was my final chosen clustering model.
At the end, I made a recommender system that suggested me a similar show to the one that I mentioned.
