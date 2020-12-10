PROJECT OVERVIEW:
The objective of the project was to use Azure to run AutoML Classification task ( without enabling deep learning ) on Bank-Marketing Dataset and then deploy the best model ( i.e. VotingEnsemble in our case with accuracy 0.91775) with "Authentication" enabled using Azure Container Instance ( ACI ) and consume it with the help of endpoint.py script provided ( after modifying scoring_uri and key ).
(1) The first step of project is 'Authentication' : after ensuring 'az' command is installed 'az login' was used for logging in. Since I was using the lab provided by Udacity, I was not allowed the privileges to create a Service Pricipal which was evident when I ran the command to create one.
(2) The second step of project was running 'Automated ML Experiment': after exploring registered 'Bank-Marketing' dataset in Dataset section, a new Automated ML run was created using this dataset. A new compute cluster with machine size of 'Standard_DS3_v2' ( with minimum nodes equal to 1 and maximum nodes equal to 5 ) was also created to run the experiment. The task performed was classification ( without enabling deep learning ).
(3) The third step of project was to 'Deploy the Best Model': The experiment produced VotingEnsemble as the best model with accuracy score being 0.91775. It was then deployed using Azure Container Instance ( ACI ) with 'Authentication' enabled. The check box for 'enabling Application Insights' will be left untouched during deployment.
(4) The fourth step of project was to 'Enable logging': After downloading config.json file and saving it in the same folder as logs.py, logs.py script was edited using vim command in git bash terminal. After necessary edits, it was run using python command and the 'Application Insights Enabled' was observed to be 'True'.
(5) The fifth step of project was to use 'Swagger Documentation': 
(6) The sixth step of Project was Consume Model Endpoints.
(7) The seventh and final step of Project was Create and Publish a Pipeline.


ARCHITECTURAL DIAGRAM:



SCOPE OF IMPROVEMENT IN PROJECT IN FUTURE:



SCREENSHOTS OF TASKS ACCOMPLISHED:



LINK TO SCREENCAST VIDEO:


![alt text](https://github.com/ujjwalbb30/nd00333_AZMLND_C2/blob/ujjwalbb30-patch-1/registered_datasets.PNG)
