# JobCandidates

In this project, I take a look at job candidates and how well they fit certain keywords. 

The fun bits I learned:

-how to effectively utilize/combine PCA with clustering algorithms

-some basic webscraping

-data augmentation techniques for NLP

-optimizing computation speed with Numba.

Goals: 
1. Predict and rank how well each candidate fits the role based on their available information.
2. Re-rank them whenever a candidate is starred as the ideal choice during a manual review.

-----

I first augmented this small dataset via webscraping and contextual word embedding insertion/substitution methods. 

KMeans clustering worked best (vs. agglomerative, spectral, and bayesian gaussian mixtures) to segregate data into ~6 clusters based on any of 3 different encodings (Bag of Words, TFIDF, and spaCy average word vectors), which were crafted from text I concatenated from augmented job titles, locations, and connnections.

I ended up choosing the spaCy word vector dataset in the final solution. Once the dataset was organized using the unsupervised approach mentioned above, I implemented a keyword search algorithm based on nearest neighbors (with metric = cosine similarity).

1. First, the cluster is chosen based on keywords.
2. Then, all candidates in the cluster are ranked by cosine similarity to the keywords, with the top ~10 candidates being presented to a manual reviewer.
3. The manual review leads to 1 candidate being selected (as the best). Subsequently, all other candidates are re-ranked based on similarity to the chosen one.
4. Iterative manual review continues until the most suitable candidate remains at the top of the list.



fPlTFeDYM5nDWECB
