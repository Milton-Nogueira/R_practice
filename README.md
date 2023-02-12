## Practicing R language with machine learning models

In this project a dataset about costs for health insurance was used to practice a few machine learning models in R.

The dataset can be found on [Kaggle](https://www.kaggle.com/datasets/mirichoi0218/insurance).

### Data Dictionary

* Age: Their Age.

* Sex: Their Gender.

* BMI: Body Mass Index.

* Children: Number of children they have.

* Region: Region where they live.

* Smoker: Binary variable stating if they smoke or not.

* Charges: Cost of the Health Insurance plan.

### 1. EDA and Multiple Linear Regression

After checking missing data and duplicated rows (none in this dataset), was checked the correlation of the independent variables with the response variable (charges).

![correlation](https://user-images.githubusercontent.com/121902546/218335544-41d8fe4a-a1f7-46b5-97b9-631652dda925.png)

The only variable with strong correlation with Charges is Smoker.

For this analysis the independt variables used were Smoker and also Age and BMI, the next ones with highest correlation (Altough still weak).

![BMIxcharges](https://user-images.githubusercontent.com/121902546/218335549-a59dffbb-a39b-4354-8586-117b8b286c93.png)

![AgexCharges](https://user-images.githubusercontent.com/121902546/218335553-96d3c522-6ffc-4baa-bf05-8f2af8bebeac.png)
 
 It's clear from the plots that people who smoke have the biggest costs, regardless of age or BMI.
 
 Splitting the model into 80% train, 20% test we obtained an R² = 0.784, so around 78% of the variability observed in the response variable is explained by the regression model.
 
The Mean absolute percentage error (MAPE) of this approach was 3.21%.

![LR](https://user-images.githubusercontent.com/121902546/218336180-fd7fccca-1b92-433b-b80c-6ed5503f3b38.png)


## 2. Decision Tree

The second model was made utilizing the same variables and returned the following tree:

![DecisionTree](https://user-images.githubusercontent.com/121902546/218336211-d145abc9-b1ca-464a-a601-cf3fb861fda5.png)

MAPE in this approach was 2.75%


## 3. Decision Tree (Classification)

Now, let's change our point of view. 

People can lie about their smoking habits when filling their register for insurance. This can be configured as fraud since it will generate higher insurance costs. 

Suppose that we already have the medical costs, we want to determine if people smoke or not.

The response variable now is smoker and all the other ones were considered as independent variables.

![Class_Tree](https://user-images.githubusercontent.com/121902546/218336362-b01db254-f307-4a61-a394-8f229baa841c.png)

![CM](https://user-images.githubusercontent.com/121902546/218336372-50cffbd0-bba0-4f34-b7d7-28335bf378ce.png)


The idea of this approach is to check the False Positives:

Instead of thinking about it just as a prediction error from the model, we can also look at it as people who stated they don't smoke but our model predicts they do. Considering the strong correlation of the smoker variable with the charges, this could mean financial loss to the company if those people are lying in their register. It sounds reasonable for the company to investigate those cases and similar profiles in the future.


