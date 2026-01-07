# :love_letter: Notes and conclusions of ``02-preprocessing.ipynb``

## Data cleaning
There are two features available where some datapoints are medically or physically implausible, namely `RestingBP` and `Cholesterol`.

### RestingBP
A systolic blood pressure at rest is considered low if it is less than 90 mm Hg.
We check if there are RestingBP values lower than 90 in the dataset, and indeed there are: 0 and 80. 

#### RestingBP = 0
It is certain that a RestingBP value of 0 can't be right, so this will be imputed with the median value of RestingBP.

#### RestingBP = 80
A RestingBP of 80 is medically and physically possible but it comes with concerns since it is advised to go see a medic and receive treatment/medication. Because this value is possible but extreme, it will not be cleaned.

### Cholesterol
It isn't specified in the dataset description if the cholesterol value is LDL (low-density lipoprotein), VLDL (very-low density lipoprotein), HDL (high-desnity lipoprotein) or the total cholesterol. Based on the numbers, we can conclude that this will probably be about the total cholesterol. With that in mind, we should take a look at both sides of the extreme values.

#### Extreme high values
A total cholesterol value is considered 'borderline high' if it ranges between 200 and 239 mg/dL and 'high' if it's 240 or higher. We see a very big amount (123 to be precise) of patients who have a cholesterol value higher than 240, so we'll up the limit to 500 to gain some more information. There we see that we have 4 patients left with a cholesterol value higher than 500, namely 518, 529, 564 and 603. Even though those values are very high, we will not remove them because they are still plausible.

#### Extreme low values
There is no lower limit to a normal cholesterol level, so for convenience we will take a look at values lower than 100. Here we have only two different values left: 0 (172 entries) and 85 (1 entry).

##### Cholesterol = 0
A cholesterol level of 0 is medically implausible so these have to be imputed with the median.

##### Cholesterol = 85
A cholesterol level of 85 may sound as 'too low' but it's very likely an entry from a (probably) very healthy person and is indeed medically possible, so no cleaning is needed.

## Preprocessing pipelines
A numerical and categorical pipeline was made to automize the preprocessing.

An imputer was used in both numerical en categorical pipelines; a median strategy for numerical features and most frequent strategy for categorical features. The choice of using median over mean was conciously made. The dataset is a bit skewed and has some outliers here and there, and because the mean is affected by outliers and the median is not, it was pretty straightforward to use the median over mean strategy.

The categorical pipeline also implements one-hot encoding. Note that the numerical pipeline doesn't implement a scaler; this is because tree-based models don't require them and since we will train our data on Random Forest and XGBoost (which are both tree-based classifiers), we don't need a scaler.

## Feature subsets
Six different subsets were created to train the models on so we can see if feature subsets have an influence on model performance.
