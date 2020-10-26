# Titanic - to be or not to be

![Titanic](https://user-images.githubusercontent.com/5339011/97196060-69042a00-1782-11eb-9acb-8b79019f913a.png)

Titanic is the very famous ship in the world. The ship crushed into the big ice and many people died.
I got the data of the people on the ship and investigate how to survive in such a situation.

## Data at a glance

Now let's see the data.

> RangeIndex: 891 entries, 0 to 890  
> Data columns (total 12 columns):  
> PassengerId    891 non-null int64  
> Survived       891 non-null int64  
> Pclass         891 non-null int64  
> Name           891 non-null object  
> Sex            891 non-null object  
> Age            714 non-null float64  
> SibSp          891 non-null int64  
> Parch          891 non-null int64  
> Ticket         891 non-null object  
> Fare           891 non-null float64  
> Cabin          204 non-null object  
> Embarked       889 non-null object  
> dtypes: float64(2), int64(5), object(5)

There are 12 categories and 891 of people's data.
*Age* and *Cabin* have some missing values. Embarked has a few.

![correlation](https://user-images.githubusercontent.com/5339011/97213917-a8d60c00-1798-11eb-99b0-9070b8ec0864.png)
When taking a correlation between these numeric data, *Pclass, Age, and Fare* look like strongly correlated with Survived(target).

## Data cleaning
We use the mean value of age for lacked age data.
The test set has a NaN value in Fare. For this, we use the mean value for fare.

## Exploring the data
Here, the target value of survived poeple corresponds to 1 and that of not survived does 0.
The mean of the target value close to 1 means likely to survive.

![Pclass]
For Pclass, this means the passenger class, the passengers in pclass 1 were the most survived.
The worst was pclass 3.

For Embarked, this means where passenger embarked the ship, Embarked C has the most survived. S was the worst.

For sex, women tend to survived more than men.

## Establish a baseline
Firstly, I am going to aim the model accuracy avobe 0.9.

## Hypothesize solution
We use "Pclass", "Sex", "SibSp", "Parch","Embarked" and "Age" for establish a model.
For Age, I use "AgeBucket", binned the age into 15 years.
For model, I use RandomForestClassifier.

## Develop
The accuracy of the model results shown in the table below.
Also I used another model based on SVM from other people made.

|   | with embarked | without embarked | GSSVM |
| --- | ----------- | --------- | ------ |
| test accuracy | 0.821 | 0.827 | 0.815 |
| leaderboard score | 0.782 | 0.770 | 0.775 |

The best model is now Randomforest with embarked.

## Feature importance



