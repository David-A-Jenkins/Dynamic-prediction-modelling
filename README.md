# Dynamic-prediction-modelling
The code here is a modification of the DMA package in R to allow for batch updating.
Both source code here is modified version of the dma package. Load the dma package first and then run "source(x.R)" where x is the name of the modified file.

Code to run the model is:
logistic.dma.batch(x, y, mmat, lambda, initialsamp, autotune, bite.size )

x - matrix ...
lambda - rate of forgetting (should be between 0.9 and 1)

initialsamp - number of rows for the initial model (not required in linear but need a batch for logistic as it runs GLM on this data)

autotune - autotuning procedure for forgetting. Computationally intensive so tent to use false and pick a lambda.

bite.size - vector with the row numbers for each update. for example c(100, 200, 300) will use rows 100 to 199 for first update and 200 to 299 for the second.

