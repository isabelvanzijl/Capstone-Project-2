# Epicurious Meal Kit Service Recipe Recommendations by Clustering

### Final Report: 
https://docs.google.com/document/d/1cmI2O-MeGLxfaJkBGdNJ9FEENysehrQuw00pGc4wRp4/edit?usp=sharing 

### Slide Deck:
https://docs.google.com/presentation/d/1K98uyo-t5YKfLCrVNAy8-CWbntwFrNiqDRqPlSNOgKg/edit?usp=sharing

### Final Code:
ipython notebook in this repo: Final_Analysis_Code.ipynb

# Overview

## The Problem

Epicurious is interested in joining the meal kit service business. Similar to companies like Blue Apron and Chef’d, they would offer a mail subscription of ingredients and recipes so customers can easily cook great recipes from home without overbuying ingredients in the store. Epicurious’ menu items would consist of recipes from their website and customers would ideally be able enter their food preferences, allergies, or dietary restrictions while looking for menu items they’re interested in purchasing. Epicurious wants to provide its customers with intelligent recommendations, but they don’t have any customer order history data to base their recommendations on. By leveraging the categories, ingredients, ratings, and nutritional data available for each recipe, can we decide on a set of recipes to offer customers in our new business that covers enough of our customers preferences?

## Limitations

Overall, we were unable to identify very clear clusters in our recipe data. The two biggest limitations faced in this project were discrepancies in Category and Ingredient tags and high variation in recipe title phrases. 

The first issue was the accuracy of tagging Categories and Ingredients for each recipe. These tags are added to each recipe by the recipe publisher, so there can be a lot of variety in what tags they choose to use. For example, you could have two basically identical recipes for a basic meal such as vegetarian chili. The two recipes essentially contain the same ingredients, but the one of the two recipe publishers could have added 15 tags and the other could have added only 3. I reduced the data set by removing recipes that had 2 or fewer tags, but this only removed so many recipes. 

Our results were likely even more limited due to the fact that we’re using binary data for our Category and Ingredient tags. Clustering on binary data can yield decent results, but we likely would have been able to see clearer results if we had a measure of importance for each Category and Ingredient tag.

I decided to try clustering on similarities between recipe titles since I could actually measure correlations between words and phrases within the titles. I expected to get better results and my clusters did seem to do a better job of grouping recipes together, but it also depended too much on the values for single words and phrases. The K-Means model essentially wanted to create a cluster for every word and phrase, of which there were just too many. If our recipes had more simple titles and then the actual recipes were very different, this likely would have yielded better results. Our titles are very unique though, so we ran into the problem of not being able to match up similar recipes by title.

## Conclusions

Although the word2vec matrix provided us with lower silhouette scores, it was clearer how the recipes in the clusters were related to each other compared to the clusters that were identified for the meal category recipes. Using the word2vec algorithm and K-Means clustering algorithm, we were able to identify 21 clusters that group similar recipe titles together. The result only provides us with a silhouette score of 0.0379, but when visually looking through the clustered recipes, there are more clear trends than when clustering on categories. From the 21 recipes, approximately 5 recipes from each cluster should be offered as part of Epicurious’ meal kit service, totalling 105 recipe offerings. This number would just be used to initially start the business. Depending on the popularity of certain recipes by cluster, recipes can be added and removed and we can retest our algorithm with some kind of popularity score for each recipe, possibly resulting in more or fewer clusters. Also, once we have customer data, we can use network analysis to further study customer preferences and improve our meal kit offerings.
