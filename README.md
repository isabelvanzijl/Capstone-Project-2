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

