# Resnet34-Image-classification-with-sagemaker
In this project I used Resnet which is a pretrained model to classify different dog types availabe in the dataset provided by Udacity in its ND program.

## Project Set Up and Installation 

use sagemaker UI to clone the repo and follow the steps in the starter notebook.

## Dataset
Dog breed: consists of 3 sub atasets, train/test/evaluation.

## Access
Upload the data to an S3 bucket through the AWS Gateway so that SageMaker has access to the data. 

## helper files: <br>
hpo.py: used to tune the hyperparameters by setting up a search space where it traines the model with different values of "lr" and "batch-size" till it finds the best set of HPs.<br>
train_model.py: after choosing best HPs, this script traines the model using them, here i set the profiling and debugging configs. <br>
ineference_alt.py: for endpoint deployment and for processing the data before it is passed to the endpoint for testing puposes. <br><br>

## Hyperparameter Tuning
What kind of model did you choose for this experiment and why? Give an overview of the types of parameters and their ranges used for the hyperparameter search<br>
I used Resnet34 pretrained model and 3 fully connected layers,hyperparameter searchspaces are "lr" which is the learning rates and "batch-size"<br>

### HPs tuning summery:<br><br>

![hptunning.jpg](https://github.com/salsabeel-tn/Resnet34-Image-classification-with-sagemaker/blob/master/img/hptunning.jpg) <br>

### best training and best HPs: <br><br>
![bestjob.jpg](https://github.com/salsabeel-tn/Resnet34-Image-classification-with-sagemaker/blob/master/img/besttrainingjobconfig.jpg)<br>
### in the contrary, here is the least effective Hps and their job:<br>
![worstjob.jpg](https://github.com/salsabeel-tn/Resnet34-Image-classification-with-sagemaker/blob/master/img/worstHP.jpg)<br>



## Debugging and Profiling
The Debugger Hook is set to record the Loss Criterion of the process in both training and validation/testing. The Plot of the Cross Entropy Loss is shown below.<br>
![debugplot.jpg](https://github.com/salsabeel-tn/Resnet34-Image-classification-with-sagemaker/blob/master/img/debuggingplot.jpg)<br>
we can see that the line is volatile during the validation phase. We can eliminate this by changing weights and/or adding more fully connected layers.<br>
### profiling report is automatically generated and the .html file is availabe in profiler folder.<br>
### Results
results are in general satisfying as the profiler report indicates that there were no bottleneck rules triggered at all.


## Model Deployment

**for inefernce i used a helper script "inference_alt.py" to deploy my endpoint:**<br>
this is the deployed endpoint<br>
![endpoint](https://github.com/salsabeel-tn/Resnet34-Image-classification-with-sagemaker/blob/master/img/endpoint.jpg)

### Querying:
I made one which is a random image from the test dataset that i uploaded, the restults were very close to the actual species of the dog, you can find the result in the notebook and the following are the logs from CloudWatch:<br>
![logs](https://github.com/salsabeel-tn/Resnet34-Image-classification-with-sagemaker/blob/master/img/queries.jpg)



