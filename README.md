
# Operationalizing Machine Learning

This project is part of the Udacity Azure ML Nanodegree. In this project, we will use Azure to configure a cloud-based machine learning production model, deploy it, and consume it. We will also create, publish, and consume a pipeline. In the end, we will demonstrate all of your work by creating a screencast video.

The dataset used here contains contextual information of some of the clients of a bank such as age, job, marital status, education, housing status, loan status, etc. Using this dataset, we seek to predict the reaction of the clients (positive or negative) to a marketing campaign ran by the bank.

## Architectural Diagram
*TODO*: Provide an architectual diagram of the project and give an introduction of each step.
In this project, we will be following the below main steps:

### 1. Authentication
In this step, we will need to install the Azure Machine Learning Extension which allows us to interact with Azure Machine Learning Studio, part of the az command. After having the Azure machine Learning Extension, we will create a Service Principal account and associate it with our specific workspace.

### 2. Automated ML Experiment
In this step, we will create an experiment using Automated ML, configure a compute cluster, and use that cluster to run the experiment.

### 3. Deploy the best model
After the experiment run completes, a summary of all the models and their metrics are shown, including explanations. The *Best Model* will be shown in the *Details* tab. We will select this best model for deployment.

### 4. Enable logging
Now that the *Best Model* is deployed, we will enable Application Insights and retrieve logs. Application Insights is a very useful tool to detect anomalies, visualize performance. It can be enabled before or after a deployment. However, in this project, we will enable it after the deployment.

### 5. Swagger Documentation
Swagger is a tool that helps build, document, and consume RESTful web services like the ones we are deploying in Azure ML Studio. It further explains what types of HTTP requests that an API can consume, like POST and GET. In this step, you will consume the deployed model using Swagger. Azure provides a Swagger JSON file for deployed models.

### 6. Consume model endpoints
We can consume a deployed service via an HTTP API. An HTTP API is a URL that is exposed over the network so that interaction with a trained model can happen via HTTP requests. We can initiate an input request, usually via an HTTP POST request. Once the model is deployed, we will use the script provided to interact with the trained model that contains the required piece of code for initiating an input request.

### 7. Create, publish and consume a pipeline
Automation is a core pillar of DevOps applicable to Machine Learning operations. A good feature of Azure is Pipelines, and these are closely related to automation. For this part of the project, we will use the Jupyter Notebook provided in the starter files for creating, publishing, and consuming a pipeline.

## Key Steps
*TODO*: Write a short discription of the key steps. Remeber to include all the screencasts required to demonstrate key steps. 

*TODO* Remeber to provide screenshots of the `RunDetails` widget as well as a screenshot of the best model trained with it's parameters.
As you follow there is a list of all the key steps of this project alongwith the required screenshots. Screenshots are included to provide clarity.

1. Register the required dataset and make sure it is present in the *Registered Dataset* section.
2. Create a new Automated ML run and experiment and configure it as a *Classification* task. Wait till it gets completed. It will take 30-40 minutes for this run to complete.
As we can see, the best model found by AutoML is Voting Ensemble.
3. To deploy this newly trained model we need to fill the *Deployment form* as shown in the following screenshot. Make sure the *Authentication* is enabled.
4. After deployment, make sure the *Deployment state* is *Healthy* in the studio.
5. Next we will enable *Application Insights* to retrieve logs whenever needed. For this step we will run `logs.py` in the terminal as shown in the following screenshot. This is retrieving some logs also for us.
As a result, *Endpoint* section in Azure ML studio is showing *Applications Insights* as ***True***.
This is the dashboard of *Application Insights* which makes analysis way easier.
6. Swagger UI running on the localhost showing the HTTP API methods and responses for the model.
7. The following screenshot shows the *Consume* tab of the deployed model with the key for the service and the URI that was generated after deployment.
8. Here we can see the file `endpoint.py` running in the terminal against the API producing JSON output from the model. This call creates another file in the root directory, `data.json`.
9. This step will benchmark the endpoint using Apache Benchmark (ab). `benchmark.sh` contains one line of `ab`. The following screenshot shows Apache Benchmark (ab) running against the HTTP API using authentication keys to retrieve performance results.
10. For this part of the project, you will use the Jupyter Notebook provided in the starter files. This following screenshot shows the *Run Details Widget* with AutoML steps from the notebook.
11. Make sure that the pipeline is created by checking out the *Pipeline* section in the studio.
12. This is the pipeline structure showing Bankmarketing dataset with the AutoML module.
13. We used the following piece of code from the notebook for publishing the pipeline.
14. The *Published Pipeline overview*, showing a REST endpoint and a status of ACTIVE meaning our pipeline has been published successfully and ready to use.
15. The following piece of code from the notebook demonstrates how we can send a POST request to trigger the pipeline published in the previous step.
16. Azure ML studio showing the pipeline endpoint as *ACTIVE*.

## Screen Recording
*TODO* Provide a link to a screen recording of the project in action. Remember that the screencast should demonstrate:

## Future Work
*TODO (Optional):* This is where you can provide information about any standout suggestions that you have attempted.
