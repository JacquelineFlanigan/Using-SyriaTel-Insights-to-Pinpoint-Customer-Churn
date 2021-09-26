# SyriaTel Insights

Customer Retention for SyriaTel
SyriaTel, a telecommunications company, are looking into what is making customers cancel their services. Below we will go through different types of categorical models to see if we can predict who will churn and describe our thought processes. 

### Methodology

The file used:

Churn in Telecom's Dataset ('bigml_59c28831336c6604c800002a.csv')

### Filtering and Transformation

From this dataset there were some columns that would not be used to help streamline the process for the models. We dropped the total charges (for the individual days, evenings, nights and international), account length, phone number, state and area code. This enabled us to focus on the services rather than customer aspects that we can improve upon. Next we changed the international plan, voicemail plan and churn to numerical values to ensure that this information would work correctly with our models. To also make our dataset a little easier to read, we renamed the columns; mainly capitalizing the titles. We also clearly defined x and y, since we would want it to be clear that we will be focusing on Churn (our y) in relations to other features. And lastly, we created our own model function that would streamline the processs and cut down on repetitve code (this can be found in the jupyter notebook for those curious).

# Models

### Decision Tree Model

After taking a look into our cleaned and filtered data, the modeling process began. We tested five models in all, with the goal to find the one that would best suit our data in addition to having our results clearly defined. We began with the Decision Tree model since it easy to use and has nice attributes to get more insight for our data. For instance, it can check feature importances and with it, we were able to see that the Voicemail Plan had a high impact on customer Churn. Below here are both the decision tree as well as the feature importance chart.

![DecisionTree](https://user-images.githubusercontent.com/79724188/134824321-011f3f6c-02b2-4a9f-9926-911984778465.png)

After the Decision Tree ran, it had good numbers across precision, recall, accuracy and F1 scores. Even after testing variations from the default model, this held true but since Decision Tree models usually overgeneralize data and this could lead to overfitting.

### Random Forest Model

The Random Forest model had similar results to the Decision Tree in that it had good scores over all as well, once again even after testing different settings from the default ones; specifically changed were the number of estimators, the criterion and max depth. In addition, there was also a feature importance attribute like the Decision Tree but this one had slightly varied results. The Voicemail Plan did show as important to customer churn, but it was second to the International Plan. The only major downside to using this model is that as the dataset grows, the longer the prediction process will take.

### Logistic Regression Model

Once again, the results across the confusion matrices were good but that does make it harder to determing which model is the right one for this problem. The Logistic Regression models make it eeasy to implement them in addition to changing/adding information to reflect new data. They also tend to be more accurate than other models when dealing with simplistic data but you do need a large amount of said data to avoid overfitting your model. 

### Gaussian Naive Bayes

Our confusion matrices are once more looking good with their results with the Gaussian Naive Bayes model. The upside to using this model in particular is that it tends to do better with less training data (if the assumption of the independent features hold true), it can predict multiple classes and is easy to use. Although with Gaussian Naive Bayes, since this model assumes that all features are independent to each other, it is a bit unrealistic to real work problems. And it should be noted that this model is known to be unreliable when it comes to using "predict_proba", which is a downside in regards to it's usability.

### Nearest Neighbors (KNN)

The last model tested was the Nearest Neighbors Model (also known as KNN). This was the first model run that had differing results for the confusion matrices as shown below.

CHART

With our train set data we can see that 2,393 of the customers that did not churn were correctly classified by the model to have stayed with SyriaTel but 9 were not. Also, for the consumers who did leave/churn, we see that 19 customers were correctly classified as ending their services with SyriaTel while that 245 customers were predicted to leave, didn't. Meanwhile, within our test set data we see that 603 of the customers who stayed with SyriaTel were correctly classified by the model while 5 weren't. In addition, for 1 customer they were correctly classified as canceling while 58 people who were expected to do so, remained instead.

What does this all mean? Well, this is showing that the KNN model predicts more people churning from SyriaTel than they actually do as well as showing that some customers who were thought to stay, end up leaving. It does lean more in a way that could be seen as positive with these results, as it's better to predict that more people will leave and in the end, more end up staying. This model is also doesn't make any assumptions with the data it deals with and learns as the dataset grows, in addition to being easy to use. 

However, as the dataset does grow, so does the difficulty of finding the optimal number of neighbors to use and the potential for outlier sensitivity. There is also the fact that KNN models don't have the capability of dealing with missing value points. Over all, this model does have good aspects but there are some serious downsides to it.

# Final Model and Results

CHARTS

Random Forest Classifier model ended up the winner for our customer chrun problem! Even as the other models performed well, Random Forest stood out with high F1 scores, reliability, efficiency, and feature importances as shown above. These models are known to be resistant to outliers and having a lower risk of over fitting, while still dealing with large amounts of data. Here we ended up focusing on F1 scores since they are a good balance between recall and precision, while avoiding the class equity problem that accuracy has. We also used the best parameters feature that Random Forest has, which let us know that the most efficient class weight is balance, the criterion (a way to measure the quality of a split) was gini, with a max depth of trees being 15 and 150 estimators, our model should run smoothly.

Our final model accurately predicted that 608 people who would stay with SyriaTel would stay and those 59 people who would churn, did so. Random Forest also has feature importances, which gave us insight as to which service should be the focus of improving at SyriaTel. With almost half the results for the feature importance being the International Plan followed by the Voicemail Plan, these should be the main focuses of enhancement for the company to prevent customer Churn. 

With every model, there can be improvements and so recommendations for further insight into customer churn for SyriaTel would be to run additional models on more datasets from the company while keeping an eye on the results from this model, iterating over past and future information to provide a more accurate indication as to customers ending their services. 
