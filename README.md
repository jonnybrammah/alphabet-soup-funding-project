# alphabet-soup-funding-project

<p align="center">
  <img src="https://wp-krypton.s3.amazonaws.com/wp-content/uploads/sites/3/2017/09/charity-fund-620x330.jpg" alt="Charity Funding (Image Taken from Mortgage Finance Gazette)">
</p>

-----

## Project Description

The goal of this project was to develop a neural network machine learning tool that will help a nonprofit foundation select the applicats to give funding to that have the best chance of success in their ventures. The model was fed a whole host of data about previously funded applicants, that included among other things:
- Whether the applicant was successful in their endeavour
- The 'Application Type'
- The type of organization
- The income of the organization
- The amount of funds requested
- The affilliation of the application
- The use case for funding

The neural network model was built to predict whether an applicant would be successful based on all remaining columns, and then tested to ascertain the accuracy. The model was then optimized by tweaking the neural network hyperparameters to try and increase the accuracy.

-----

## Table of Contents
1. [<b>Initial Model</b>](https://github.com/jonnybrammah/alphabet-soup-funding-project/blob/main/README.md#Initial-Model)
   - [<b>Model</b>](https://github.com/jonnybrammah/alphabet-soup-funding-project/blob/main/README.md#Model)
   - [<b>Results</b>](https://github.com/jonnybrammah/alphabet-soup-funding-project/blob/main/README.md#Results)
2. [<b>Model Optimization</b>](https://github.com/jonnybrammah/alphabet-soup-funding-project/blob/main/README.md#Model-Optimization)
   - [<b>New Model</b>](https://github.com/jonnybrammah/alphabet-soup-funding-project/blob/main/README.md#New-Model)
   - [<b>Model Optimization Results</b>](https://github.com/jonnybrammah/alphabet-soup-funding-project/blob/main/README.md#Model-Optimization-Results)
3. [<b>Summary</b>](https://github.com/jonnybrammah/alphabet-soup-funding-project/blob/main/README.md#Summary)
-----

### Initial Model

#### Model

After some cleaning of the data, and re-representing categorical data as numeric, the initial model read in all 43 columns from the dataset (excluding the column describing whether the organization was successful), and contained two dense layers with five units in each beyond the output layer. The final output layer consisted of only one unit to output the binary prediction of whether the organization was likely to be successful or not. This model is shown in the diagram below:

<p align="center">
  <img src="https://raw.githubusercontent.com/jonnybrammah/alphabet-soup-funding-project/main/Output_Images/initial_model.png" alt="Initial Model">
</p>

#### Results

The model was trained on around 80% of the initial dataset, and trained over 100 epochs. A graph displaying the accuracy of the model over these epochs is shown below:
<p align="center">
  <img src="https://raw.githubusercontent.com/jonnybrammah/alphabet-soup-funding-project/main/Output_Images/accuracy_plot.png" alt="Initial Model Accuracy Plot">
</p>

It is clear to see that the model reached its peak accuracy within around 20 epochs and then maxed out at around 73% accuracy.

When the model was fed the remaining 20% of the dataset to test on, its final accuracy was around 72.6%, and so clearly some more optimization was required.

-----

### Model Optimization

#### New Model

The model was then optimized. After following the same data cleaning and reclassification processes, changes to the model's hyperparameters were made. The changes were made incrementally in order to avoid errors with overfitting. The initial two changes made were:
1) More units per dense layer and more epochs to train on. This resulted in no significant increase in accuracy (72.7%).
2) More dense layers included, keeping the same number of epochs. This also resulted in no significant increase in accuracy (72.7%).

Finally, these hyperparameters were increased significantly further in an attempt to increase the accuracy. The number of dense layers was increased to six, including the input layer, and the number of units in each layer was increased to 50. The model was also given 200 epochs to train on, in case these other changes necessitated more training time. An image of the model is shown below:

<p align="center">
  <img src="https://raw.githubusercontent.com/jonnybrammah/alphabet-soup-funding-project/main/Output_Images/optimized_model.png" alt="Optimized Model">
</p>

#### Model Optimization Results

The results of this model are also disappointing. The graph below represents the model's training accuracy against each epoch:
<p align="center">
  <img src="https://raw.githubusercontent.com/jonnybrammah/alphabet-soup-funding-project/main/Output_Images/optimized_accuracy_plot_.png" alt="Initial Model Optimization Plot">
</p>

There is a marginal increase in the accuracy, but only to about 74%. The model takes around 50 epochs to reach this, with only slight variations in the accuracy from there.

When fed the remaining 20% of the dataset to test on, the accuracy was 73.1%, so again only a tiny and non-significant increase.

-----

### Summary

The model before and after optimization has about a 73 - 74% accuracy in predicting from the information in the dataset whether an organization will be successful in its endeavours when funded by Alphabet Soup. In its current state, this model should not be used to predict whether an organization should be funded. However, it is possible that with more optimization, this model will be able to complete this task with more accuracy. In further projects in the future, the following should be considered:
- Does reducing the number of input parameters help? There may be some input parameters that have little to no impact on whether an organization is successful but that the model is attempting to use unsuccessfully. One possible suggestion is removing classifications one by one to see if any increase accuracy can be attained.
- Does changing the activation of the dense layers affect the accuracy? In a trial run using keras-tuner for this project, this did not appear to have a significant effect but the impact was not studied in significant detail due to time constraints.
