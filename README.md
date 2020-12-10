PROJECT OVERVIEW:

The objective of the project was to use Azure to run AutoML Classification task ( without enabling deep learning ) on Bank-Marketing Dataset and then deploy the best model ( i.e. VotingEnsemble in our case with accuracy 0.91775) with "Authentication" enabled using Azure Container Instance ( ACI ) and consume it with the help of endpoint.py script provided ( after modifying scoring_uri and key ).
(1) The first step of project is 'Authentication' : after ensuring 'az' command is installed 'az login' was used for logging in. Since I was using the lab provided by Udacity, I was not allowed the privileges to create a Service Pricipal which was evident when I ran the command to create one.
(2) The second step of project was running 'Automated ML Experiment' : after exploring registered 'Bank-Marketing' dataset in Dataset section, a new Automated ML run was created using this dataset. A new compute cluster with machine size of 'Standard_DS3_v2' ( with minimum nodes equal to 1 and maximum nodes equal to 5 ) was also created to run the experiment. The task performed was classification ( without enabling deep learning ).
(3) The third step of project was to 'Deploy the Best Model' : The experiment produced VotingEnsemble as the best model with accuracy score being 0.91775. It was then deployed using Azure Container Instance ( ACI ) with 'Authentication' enabled. The check box for 'enabling Application Insights' will be left untouched during deployment.
(4) The fourth step of project was to 'Enable logging' : After downloading config.json file and saving it in the same folder as logs.py, logs.py script was edited using vim command in git bash terminal. After necessary edits, it was run using python command and the 'Application Insights Enabled' was observed to be 'True'.
(5) The fifth step of project was to use 'Swagger Documentation' : swagger.json file was downloaded using curl command and put in the same folder as swagger.sh and serve.py file. Necessary editing was done in swagger.sh and serve.py file using vim command and then both of them were run in the terminal using bash and python command respectively.
(6) The sixth step of project was to 'Consume Model Endpoints' : After editing endpoint.py script using vim command and entering scoring_uri and key, we run the endpoint.py script using python command. after ensuring ab commands are installed, edited the benchmark.sh file using vim command and then it was run using bash command in the terminal.
(7) The seventh and final step of project was to 'Create and Publish a Pipeline' : After editing the 'aml-pipelines-with-automated-machine-learning-step.ipynb' python notebook, all the cells were run and pipeline was published. 


ARCHITECTURAL DIAGRAM:

I have created the following architectural diagram with the help of Adobe Photoshop.

![alt text](https://github.com/ujjwalbb30/nd00333_AZMLND_C2/blob/master/architecural_structure.png)


SCOPE OF IMPROVEMENT IN PROJECT IN FUTURE:

(1) Dataset Imbalance : While executing 'Test the Model' section of 'aml-pipelines-with-automated-machine-learning-step.ipynb' python notebook, data imbalance is evident i.e. inputs for one class of labels are way more than the other class of labels. Due to this fact, it can be observed in the confusion matrix that almost 1/3rd of the inputs belonging to the minority class were incorrectly classified. Although Auto-ML has some built-in capabilities to deal with imbalance data we can try something in addition. In order to address this issue, we can try some sampling techniques to balance the number of inputs of both the classes while maintaining the variance. Also, we can try to upscale the minority class or downscale the majority class but keeping in mind that such resampling method will require a proper way to analyze the dataset. Also, use of weight column as input in auto-ml to weight up or down the rows, might be another way to handle imbalance in data. Defining appropriate weight column will result in penalizing the model less for errors made on samples belonging to majority class and also in penalizing the model more for errors made on sample belonging to minority class. Therefore, there is a possibility to achieve a VotingEnsemble Model giving a better classification result on this imbalanced data. 
Source for answer : https://docs.microsoft.com/en-us/azure/machine-learning/concept-manage-ml-pitfalls


SCREENSHOTS OF TASKS ACCOMPLISHED:

(1) screenshot of 'Bank-Marketing' dataset present in 'Registered Dataset' section of Azure ML Studio. Dataset contains the data about different characteristics of customers of a bank (e.g. marital status, job specification, age, previous loan, defaulting status, education qualifications etc.) and 'y' label column answers wheather a customer applied for a fixed term deposit. This 'y' label column is used as target column in the auto-ml classification experiment. However, as discussed above, this dataset is imbalanced i.e. the inputs of one class of label is way more than other class of label.

![alt text](https://github.com/ujjwalbb30/nd00333_AZMLND_C2/blob/master/registered_datasets.PNG)

(2) screenshot of completed experiment. Auto-ml classification (without enabling deep learning) task is run on the given dataset. The exit criterion which was 3 hours by default was changed to 1 hour so that experiment is completed within a given frame of time. Also, 'Application Insights' were not enabled.

![alt text](https://github.com/ujjwalbb30/nd00333_AZMLND_C2/blob/master/experiment_completed.PNG)

(3) screenshot of best model produced by the experiment i.e. VotingEnsemble with 0.91775 Accuracy. VotingEnsemble is an ensemble model which combines multiple models to improve machine learning results. It does so by predicting output on the weighted average of predicted class probabilities.

![alt text](https://github.com/ujjwalbb30/nd00333_AZMLND_C2/blob/master/best_experiment.PNG)

(4) screenshot showing enabled 'Application insights' in Details tab of Endpoint. After deploying the best model i.e. VotingEnsemble (with enabled 'Authentication') with the help of Azure Container Instance (ACI), config.json was downloaded and kept in the same folder as logs.py. Then, logs.py was edited with the help of vim command in git bash terminal and deployment name was entered. Afterwards, logs.py script was run using python command and 'Application Insights Enabled' was then observed to be 'True'.

![alt text](https://github.com/ujjwalbb30/nd00333_AZMLND_C2/blob/master/applications_insights_enabled.PNG)

(5) screenshots of logs. After running the logs.py script, no error tracebacks in its execution was observed in the git bash terminal and 'Application Insights' of our deployed model were enabled as well.

![alt text](https://github.com/ujjwalbb30/nd00333_AZMLND_C2/blob/master/logs_running.PNG)

![alt text](https://github.com/ujjwalbb30/nd00333_AZMLND_C2/blob/master/logs_running_2.PNG)

![alt text](https://github.com/ujjwalbb30/nd00333_AZMLND_C2/blob/master/logs_running_3.PNG)

(6) screenshots of swagger running on local host showing the HTTP API methods and responses for the model. swagger.json file was downloaded using curl command and Swagger URI (of the deployed model). It was ensured that swagger.json, swagger.sh and serve.py were kept in the same folder. swagger.sh was edited using vim command and the port was changed from 80 to 9000. Afterwards, it was run using bash command and Swagger container on port 9000 was opened. serve.py was run using python command in git bash terminal and it started a python server on port 8000. The link is then entered in Swagger container to open the swagger instance for interaction. HTTP API methods and responses were present in the documentation for exploring.

![alt text](https://github.com/ujjwalbb30/nd00333_AZMLND_C2/blob/master/swagger_1.PNG)

![alt text](https://github.com/ujjwalbb30/nd00333_AZMLND_C2/blob/master/swagger_2.PNG)

![alt text](https://github.com/ujjwalbb30/nd00333_AZMLND_C2/blob/master/swagger_3.PNG)

![alt text](https://github.com/ujjwalbb30/nd00333_AZMLND_C2/blob/master/swagger_4.PNG)

![alt text](https://github.com/ujjwalbb30/nd00333_AZMLND_C2/blob/master/swagger_5.PNG)

![alt text](https://github.com/ujjwalbb30/nd00333_AZMLND_C2/blob/master/swagger_6.PNG)

(7) screenshot of endpoint.py script running against the API producing JSON output from the model. endpoint.py script was edited using vim command and scoring_uri and key were entered. REST Endpoint of the deployed model was filled in scoring_uri and Primary Key was filled as key. Then, endpoint.py script was run using python command in git bash terminal and data.json file was created.

![alt text](https://github.com/ujjwalbb30/nd00333_AZMLND_C2/blob/master/endpoint_1.PNG)

![alt text](https://github.com/ujjwalbb30/nd00333_AZMLND_C2/blob/master/endpoint_2.PNG)

(8) screenshot of Apache Benchmark (ab) running against the HTTP API using authentication keys to retrieve performance results. benchmark.sh file was edited using vim command and REST Endpoint as well as Primary Key were entered. Then, benchmark.sh file was run using bash command in git bash terminal and performance results were retrieved.

![alt text](https://github.com/ujjwalbb30/nd00333_AZMLND_C2/blob/master/benchmark.PNG)

(9) screenshot of pipeline section of Azure ML Studio, showing the pipeline has been created. After entering 'experiment_name', 'key' and 'amlcompute_cluster_name', we run the cells in the notebook. Ultimately, a pipeline is created which is available to view in pipeline section of Azure ML Studio.

![alt text](https://github.com/ujjwalbb30/nd00333_AZMLND_C2/blob/master/ppp111.PNG)

(10) screenshot of pipeline section of Azure ML Studio, showing the pipeline endpoint. Bankmarketing Train endpoint is created when the pipeline is published and can be observed in the Pipeline Endpoint section in Azure ML Studio.

![alt text](https://github.com/ujjwalbb30/nd00333_AZMLND_C2/blob/master/ppp222.PNG)

(11) screenshot of Bank Marketing Dataset with the auto-ml module. When we click the endpoint mentioned above, we can see the Bank Marketing Dataset linked with the auto-ml module. This is kind of a visual representation of the pipeline we published.

![alt text](https://github.com/ujjwalbb30/nd00333_AZMLND_C2/blob/master/ppp333.PNG)

(12) screenshot of 'Published Pipeline Overview' showing a REST Endpoint and a status of ACTIVE. REST endpoint is enabled to rerun the pipeline from any HTTP library on any platform.

![alt text](https://github.com/ujjwalbb30/nd00333_AZMLND_C2/blob/master/ppp444.PNG)

(13) screenshot from Jupyter Notebook, showing that the 'Use RunDetails Widget' shows the step runs. RunDetails widget helps in monitoring the progress of pipeline training. It provides updates until training is finished.

![alt text](https://github.com/ujjwalbb30/nd00333_AZMLND_C2/blob/master/pppp5555.PNG)

(14) screenshots of ML Studio showing the scheduled runs. auth_header was retrieved and HTTP POST request to the endpoint (to trigger the run) was created specifying the authentication header.

![alt text](https://github.com/ujjwalbb30/nd00333_AZMLND_C2/blob/master/pppp6666.PNG)

![alt text](https://github.com/ujjwalbb30/nd00333_AZMLND_C2/blob/master/pppp7777.PNG)

![alt text](https://github.com/ujjwalbb30/nd00333_AZMLND_C2/blob/master/pppp8888.PNG)

![alt text](https://github.com/ujjwalbb30/nd00333_AZMLND_C2/blob/master/pppp9999.PNG)

(15) screenshots of compute instances. To accomplish the above mentioned tasks, low priority compute instances with minimum nodes 1 and maximum nodes 5, were created.

![alt text](https://github.com/ujjwalbb30/nd00333_AZMLND_C2/blob/master/pppp11110000.PNG)


LINK TO SCREENCAST VIDEO:

https://youtu.be/zR6OtYgfE3o

