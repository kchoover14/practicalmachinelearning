## Overview: Fitness Tracking: Performance versus Regularity
Fitness tracking focuses on regularity of exercise rather than how well exercise is performed. The goal of this project was to predict the manner in which subjects performed barbell lifts, using accelerometer data from belt, forearm, arm, and dumbbell. There were 5 performance methods, stored in the "classe" variable, that were either 'correct' and 'incorrect'. Using parallel processing in caret, data were trained using four different algorithms: decision tree, resampled decision tree, random forest, and resampled random forest. All models used cross validation via the trcontrol function in caret. Decision trees are a good choice for categorical variables but the decision tree accuracy was no better than could be expected by chance. The resampled decision tree using the bag method balances bias against variance through an across resampled models--that increased accuracy to 0.962. The highest accuracy was that of the random forest model (0.995) with low out of sample error (0.005)--the resampled random forest model using boosting was similar to resampled tree accuracy at 0.963. Given the fitted model plots there is potential for colinearity so the accuracy might be inflated and the model over-fitted. Domain expertise in exercise physiology would be helpful in understanding which of the 27 (out of 52 variables) were the most important at model accuracy peak.

**Get train and test data.** The data are found here: http://groupware.les.inf.puc-rio.br/har. More information on the data is found here:
http://web.archive.org/web/20161224072740/http:/groupware.les.inf.puc-rio.br/har (see the section on the Weight Lifting Exercise Dataset).
```{r get data, results='hide'}
trainUrl <- "https://d396qusza40orc.cloudfront.net/predmachlearn/pml-training.csv"
testUrl <- "https://d396qusza40orc.cloudfront.net/predmachlearn/pml-testing.csv"
training <- read.csv(url(trainUrl),na.strings=c("NA", "#DIV/0!", ""))
testing <- read.csv(url(testUrl),na.strings=c("NA","#DIV/0!",""))
names(training)[1:10]
