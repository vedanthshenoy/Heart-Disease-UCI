# Heart-Disease-UCI
This project explores the heart disease dataset by UCI available on kaggle. It studies the performance of three different algorithms with manual feature selection and recursive feature elimination method.

You can find the dataset [here](https://www.kaggle.com/borapajo/food-choices) or in the file in this repository named `<heart-disease-data.csv>`

## Feature Selection

Any machine learning algorithm finds the dependence of the features with the output. Often we encounter situations where either the features are sparse (i.e; there are a lot of 0 or no value in most of the feature fields) or they are interdependent which means there is a strong correlation within the features. 

Including correlated features in your dataset and training any algorithm on that data will surely give you less accuracy and will be far from the desired accuracy score.

One way to remove the unwanted data is to manually check which all data are correlated. for eg; if the dataset contains the price of a plot as the value and features are length,breadth,area and locality security measure. Assuming the plots covered here are all rectangular, we can infer that since area ofa rectangle is nothing but length times breadth, length,breadth and area are interrelated parameters and it will be inefective to keep all three or even two among them in the dataset, so here we can knock out length and breadth since we can obtain the information required about the length and readth both if we only take the area measure.

The above mentioned example was too simple but in real world scenarios, data will not be that evident to you about it's interdependency.
So, we have to depend on feature selection algorithms ehich will figure out which features to eliminate and which to keep.

Broadly there are three types of feature selection techniques
- Filter Method
- Wrapper Method
- Embedded Method

- **Filter Method**

As the name suggest, in this method, you filter and take only the subset of the relevant features.The model is built after selecting the features.it is most commonly done using [Pearson correlation](https://www.spss-tutorials.com/pearson-correlation-coefficient/).

To see how this was practically implemented, click [here](https://towardsdatascience.com/feature-selection-with-pandas-e3690ad8504b).

Click [here](https://en.wikipedia.org/wiki/Pearson_correlation_coefficient) to go to wikipedia of Pearson correlation which also give the details.

- **Wrapper Method**

Here you feed the features to the selected Machine Learning algorithm and based on the model performance you add/remove the features. This is an iterative and computationally expensive process but it is more accurate than the filter method.

There are different wrapper methods such as Backward Elimination, Forward Selection, Bidirectional Elimination and RFE. We will discuss  RFE here since we are using RFE in our code.

The Recursive Feature Elimination (RFE) method works by recursively removing attributes and building a model on those attributes that remain. It uses accuracy metric to rank the feature according to their importance. The RFE method takes the model to be used and the number of required features as input. It then gives the ranking of all the variables, 1 being most important. It also gives its support, True being relevant feature and False being irrelevant feature.

To know more about RFE, [This](https://towardsdatascience.com/feature-selection-with-pandas-e3690ad8504b) is a great reference article, i have reffered from [this](https://towardsdatascience.com/feature-selection-with-pandas-e3690ad8504b) only. Click [here](https://towardsdatascience.com/feature-selection-with-pandas-e3690ad8504b) to see.

- **Embedded Method**

Embedded methods are iterative in a sense that takes care of each iteration of the model training process and carefully extract those features which contribute the most to the training for a particular iteration.
For more information on regularization aka  embedded method click [here](https://towardsdatascience.com/feature-selection-with-pandas-e3690ad8504b).

## Sci-kit Methods

For RFE in the code `<heart-disease-with-RFE-code.ipynb>` i have used the in-built sklearn method `<RFE(model,# of features to remain)>`. More information about this method can be found in the sklearn documentation [page](https://scikit-learn.org/stable/modules/generated/sklearn.feature_selection.RFE.html) and also find an example [here](https://scikit-learn.org/stable/auto_examples/feature_selection/plot_rfe_digits.html).

For selecting from model method which was in-built method in sklearn `<SelectFromModel(model,..)>` i used the inbuilt sklearn method of the same name whose information can be found in it's documentation [page](https://scikit-learn.org/stable/modules/generated/sklearn.feature_selection.SelectFromModel.html) and an example can be found [here](https://www.programcreek.com/python/example/93976/sklearn.feature_selection.SelectFromModel).

## References

- https://scikit-learn.org/stable/modules/feature_selection.html
- https://www.programcreek.com/python/example/93976/sklearn.feature_selection.SelectFromModel
- http://fatihsarigoz.com/tag/machine_learning-feature_selection-rfe.html
- https://machinelearningmastery.com/feature-selection-machine-learning-python/
- https://towardsdatascience.com/feature-selection-with-pandas-e3690ad8504b
- https://scikit-learn.org/stable/auto_examples/feature_selection/plot_rfe_digits.html
- https://scikit-learn.org/stable/modules/generated/sklearn.feature_selection.RFE.html
- https://scikit-learn.org/stable/modules/generated/sklearn.feature_selection.SelectFromModel.html
