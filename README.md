# StackOverflowSalaryProject
The goal of this Notebook is to use the results of the [Stack Overflow 2022 Developer Survey](https://insights.stackoverflow.com/survey) to train a regression neural network for predicting total compensation among programmers.

## Analysis of RMSE

The neural net performed with staggeringly higher accuracy than the SKLearn regression forest for the outlier dataset while getting results just below the forest on the rest of the data. With a RMSE of \$62.99k, the neural net's error on the main data was only 5.1% greater than the random forest's \$59.911k. And when considering the outlier dataset, a RMSE of \$3179.269k (that's $3.1 million) from the regression forest means the neural net's \$63.96k RMSE  was **49.7 times more accurate!**

Such a RMSE for the normal dataset isn't the most impressive, as $60k is a lot of money when the maximum total compensation is confined to $550,000. The same value for the outlier dataset is much more noteworthy, considering the average TC was \$2.2 million! If the RMSE of the regression forest is even higher than the average value of the `upper` dataset, this indicates it probably didn't handle the huge range of TC as well as the neural net can.

## Next Steps

Further steps would be to better visualize how the target variable is distributed across different features. While data visualization did include, for example, the % of respondents who identified as Full Stack Developers, it didn't visualize how much Full Stack Developers make on average compared to other occupations, for example.

Along with more visualization, more thorough feature engineering might yield better results. Lots of time was spent on tuning hyperparameters and making sure the neural net was functioning correctly, none of which resulted in significant improvements in performance. 

To begin, an SKLearn regression tree can be constructed on the data, and the data to be used for the neural net can be reduced down to the top N features in the tree. Imputing age, work experience, and education levels off of each other would fill NaNs without relying on target encoding to handle them. Merging similar job titles, binning work experience, binning lesser-used programming languages as 'other,' etc. are all ways to modify the data in a way to hopefully make the relationship of these features with the target variable more direct.

Of course, there might also be a possibility that the survey data is simply too unreliable to properly predict salary off of. Only after more thorough feature engineering and data preprocessing can this possibility be accepted.
