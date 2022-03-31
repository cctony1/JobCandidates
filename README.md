# JobCandidates

In this project, I take a look at job candidates and how well they fit certain keywords. 

The fun bits I learned:
-how to effectively utilize/combine PCA with clustering algorithms
-some basic webscraping
-data augmentation techniques for NLP.

Goals: 
1. Predict and rank how well each candidate fits the role based on their available information.
2. Re-rank them whenever a candidate is starred as the ideal choice during a manual review.

-----

I first augmented this small dataset via webscraping and contextual word embedding insertion/deletion methods. 

KMeans clustering worked best (better than agglomerative, spectral, and bayesian gaussian mixtures) to segregate data into ~4 clusters based on TFIDF-encoded text concatenated from augmented job titles, locations, and connnections.

Once the dataset was organized using this unsupervised approach, I implemented a keyword search algorithm based on nearest neighbors.

1. First, the cluster is chosen based on keywords.
2. Then, potential candidates in the cluster are determined by selecting the nearest neighbors to the keywords.
3. Candidates are ranked using a normal probability distribution centered about the keywords, assuming a standard deviation equal to the mean of the nearest neighbor Euclidean distances (in TFIDF space) to the keywords.
4. Iterative manual review chooses the best candidate from the top ranked candidates.
5. New candidates and rankings are generated on each iteration in the manner above, except that the starred candidate becomes the center of the normal distribution.
6. The search ends when the candidate chosen during manual review is already at the top of the rankings.



fPlTFeDYM5nDWECB
