# Dynamic-prediction-modelling
The code here is a modification of the DMA package in R to allow for batch updating.
Both source code here is modified version of the dma package. Load the dma package first and then run "source(x.R)" where x is the name of the modified file.

Code to fit the model is:
logistic.dma.batch(x, y, mmat, lambda, initialsamp, autotune, bite.size )

x - matrix of predictors (p x N)
y - 1 x N matrix of outcomes

mmat - should be 1 x p matrix of 1s, for example run this code if you have 2 predictors, mmat<-matrix(c(1,1),1,2,byrow=TRUE)

lambda - rate of forgetting (should be between 0.9 and 1)

initialsamp - number of rows for the initial model (not required in linear but need a batch for logistic as it runs GLM on this data)

autotune - autotuning procedure for forgetting. Computationally intensive so tent to use false and pick a lambda.

bite.size - vector with the row numbers for each update. for example c(100, 200, 300) will use rows 100 to 199 for first update and 200 to 299 for the second.

To obtain betas from the model, run something similat to, beta <- t(as.data.frame(mod$theta)) which produces a vector of all the betas (which will then need splitting, ie the first N in the vector will represent the the model intercept at each time point)

Note - categorical variables need to be split into yes/no (dummy) variables. If there are three groups in a variable, such as a smoking variables with current, past and never smoker as categories. Then you will need 2 variables, for example, one to prepresent those who are current smokers (coded 0 or 1) and similarly one for past smokers.

