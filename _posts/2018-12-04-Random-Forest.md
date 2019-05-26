---
layout: post
title: RandomForest for Mangrove Forest
image: /img/rf.png
---

```r
library(caret)
library(readxl)
library(rattle)
library(randomForest)

rm(list=ls())
delim = '/Users/michael/Documents/publication/Thesis_p1/param_final30.xlsx'
data <-read_excel(delim)
names(data)

# Define training control: 5 fold cross-validation. If you want to perform 10 fold cv, set number=10,
train_control <- trainControl(method="cv", number=5)

# Train the model using randomForest (rf)
rf <- train(Mg_Area~., data=data, trControl=train_control, method="rf")
rpart <- train(Mg_Area~., data=data, trControl=train_control, method="rpart")

##The printed summary shows the sample sizes used, the best model selected and other information.
print(rf)

# Make predictions
predictions <- predict(rf, data[,-17])
predictions

#RandomForest VarImp
mtry <- sqrt(ncol(data))
RF_Imp <- randomForest(Mg_Area~., data=data,
                       ntree = 5000,
                       mtry = mtry, 
                       importance = TRUE,
                       scale = TRUE,
                       na.action=na.omit)

RF_Imp
plot(RF_Imp) # plots error as the number of trees increases
importance(RF_Imp, type = 1) #Mean Decreace in accuracy
importance(RF_Imp, type = 2) #Mean decrease in node impurity
varImp(RF_Imp)
varImpPlot(RF_Imp, type = 1) #Plot of Mean Decreace in accuracy
varImpPlot(RF_Imp, type = 2) #Plot of Mean decrease in node impurity


```


