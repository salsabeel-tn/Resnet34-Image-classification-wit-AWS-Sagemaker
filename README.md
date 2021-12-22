# Resnet34-Image-classification-with-sagemaker
In this project I used Resnet which is a pretrained model to classify different dog types availabe in the dataset provided by Udacity in its ND program.

## Project Set Up and Installation
Enter AWS through the gateway in the course and open SageMaker Studio. 
Download the starter files.
Download/Make the dataset available. 

## Dataset
Dog breed: consists of 3 sub atasets, train/test/evaluation.

## Access
Upload the data to an S3 bucket through the AWS Gateway so that SageMaker has access to the data. 

## helper files: <br>
hpo.py: used to tune the hyperparameters by setting up a search space where it traines the model with different values of "lr" and "batch-size" till it finds the best set of HPs.<br>
train_model.py: after choosing best HPs, this script traines the model using them, here i set the profiling and debugging configs. <br>
ineference_alt.py: for endpoint deployment and for processing the data before it is passed to the endpoint for testing puposes. <br><br>

## Hyperparameter Tuning
What kind of model did you choose for this experiment and why? Give an overview of the types of parameters and their ranges used for the hyperparameter search
I used Resnet34 pretrained model and 3 fully connected layers,hyperparameter searchspaces are "lr" which is the learning rates and "batch-size"<br>

HPs tuning summery:
![hptunning.jpg](https://github.com/salsabeel-tn/Resnet34-Image-classification-with-sagemaker/blob/master/img/hptunning.jpg)

Remember that your README should:
- Include a screenshot of completed training jobs
- Logs metrics during the training process
- Tune at least two hyperparameters
- Retrieve the best best hyperparameters from all your training jobs

## Debugging and Profiling
**TODO**: Give an overview of how you performed model debugging and profiling in Sagemaker

### Results
**TODO**: What are the results/insights did you get by profiling/debugging your model?

**TODO** Remember to provide the profiler html/pdf file in your submission.


## Model Deployment
**TODO**: Give an overview of the deployed model and instructions on how to query the endpoint with a sample input.

**TODO** Remember to provide a screenshot of the deployed active endpoint in Sagemaker.

## Standout Suggestions
**TODO (Optional):** This is where you can provide information about any standout suggestions that you have attempted.

