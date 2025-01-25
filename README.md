Echocardiogram Heart Health Analysis

Load Required Libraries
library(ggplot2)
library(dplyr)
library(tidyr)
library(broom)

Set Working Directory
setwd("path/to/your/directory")

Load Data
data <- read.csv("echocardiogram.csv")

Inspect Data
head(data)
summary(data)

Data Preprocessing
Convert necessary columns to factors if needed
data$status <- as.factor(data$status) # Assuming 'status' is the target variable

Logistic Regression Model
logistic_model <- glm(status ~ ., data = data, family = binomial)

Model Summary
summary(logistic_model)

Shapiro-Wilk Test for Normality
numeric_columns <- data %>% select_if(is.numeric)
shapiro_results <- lapply(numeric_columns, shapiro.test)

Print Shapiro-Wilk Test Results
shapiro_results

QQNorm Plot for Normality Check
par(mfrow = c(1, ncol(numeric_columns)))
for (col_name in names(numeric_columns)) {
  qqnorm(numeric_columns[[col_name]], main = paste("QQ Plot -", col_name))
  qqline(numeric_columns[[col_name]], col = "red")
}

Predictive Model Evaluation
Generate predictions
predictions <- predict(logistic_model, type = "response")

Evaluate Model Performance
library(pROC)
roc_curve <- roc(data$status, predictions)
plot(roc_curve, col = "blue")
auc(roc_curve)

Save Model Output
saveRDS(logistic_model, "logistic_model.rds")


Dataset

The dataset includes echocardiogram measurements capturing the structure and function of patients' hearts after a heart attack. Demographic information such as age is also included.


  - Source:
  - [UCI Machine Learning Repository]
  - Dua, D. and Karra Taniskidou, E. (2017). UCI Machine Learning Repository. Irvine, CA: University of California, School of Information and Computer Science.

Each row in the dataset corresponds to a patient, and specific variables were selected to develop the predictive model.

Built With

- [RStudio]

Author

- Madelyn Matura

License

This project is licensed under the [MIT License]

---



