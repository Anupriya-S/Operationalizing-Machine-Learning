
# Operationalizing Machine Learning

This project is part of the Udacity Azure ML Nanodegree. In this project, we will use Azure to configure a cloud-based machine learning production model, deploy it, and consume it. We will also create, publish, and consume a pipeline. In the end, we will demonstrate all of your work by creating a screencast video.

The dataset used here contains contextual information of some of the clients of a bank such as age, job, marital status, education, housing status, loan status, etc. Using this dataset, we seek to predict the reaction of the clients (positive or negative) to a marketing campaign ran by the bank.

## Architectural Diagram
Overall workflow can be described with the help of following diagram.

![Overall_Workflow](https://github.com/Anupriya-S/Operationalizing-Machine-Learning/blob/main/Architectural%20Diagrams/Architectural_Diagram.png)

On a high level, this project is divided into two parts and that's why I will be presenting two architechtural diagrams as follows.

The first part of the project is basically creating, deploying and consuming a model. The following image shows the part where we are ineteracting with a deployed service.

![Part_1](https://github.com/Anupriya-S/Operationalizing-Machine-Learning/blob/main/Architectural%20Diagrams/Real_Time_Scoring.jpg)

In the second part of the project we are creating, publishing and consuming a pipeline using Azure SDK. The following image somehow describes the entire process and even more.

![Part_2](https://github.com/Anupriya-S/Operationalizing-Machine-Learning/blob/main/Architectural%20Diagrams/MLOps_in_Azure.png)

***In this project, we will be following the below main steps:***

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
As you follow, there is a list of all the key steps of this project alongwith the required screenshots. Screenshots are included to provide clarity.

1. Register the required dataset and make sure it is present in the *Registered Dataset* section.

![Step_1](https://github.com/Anupriya-S/Operationalizing-Machine-Learning/blob/main/Screenshots/Dataset_Registered.png)

2. Create a new Automated ML run and experiment and configure it as a *Classification* task. Wait till it gets completed. It will take 30-40 minutes for this run to complete.

![Step_2](https://github.com/Anupriya-S/Operationalizing-Machine-Learning/blob/main/Screenshots/Completed_AutoML_Run.png)

As we can see, the best model found by AutoML is Voting Ensemble.

![Step_3](https://github.com/Anupriya-S/Operationalizing-Machine-Learning/blob/main/Screenshots/Best_AutoML_Model.png)

3. To deploy this newly trained model we need to fill the *Deployment form* as shown in the following screenshot. Make sure the *Authentication* is enabled.

![Step_4](https://github.com/Anupriya-S/Operationalizing-Machine-Learning/blob/main/Screenshots/Deployment_Form.png)

4. After deployment, make sure the *Deployment state* is *Healthy* in the studio.

![Step_5](https://github.com/Anupriya-S/Operationalizing-Machine-Learning/blob/main/Screenshots/Healthy_Deployment_State.png)

5. Next we will enable *Application Insights* to retrieve logs whenever needed. For this step we will run `logs.py` in the terminal as shown in the following screenshot. This is retrieving some logs also for us.

![Step_6](https://github.com/Anupriya-S/Operationalizing-Machine-Learning/blob/main/Screenshots/Ruunig_logspy_in_Terminal.png)

As a result, *Endpoint* section in Azure ML studio is showing *Applications Insights* as ***True***.

![Step_7](https://github.com/Anupriya-S/Operationalizing-Machine-Learning/blob/main/Screenshots/Application_Insights_True.png)

This is the dashboard of *Application Insights* which makes analysis way easier.

![Step_8](https://github.com/Anupriya-S/Operationalizing-Machine-Learning/blob/main/Screenshots/Application_Insights_Dashboard.png)

6. Swagger UI running on the localhost showing the HTTP API methods and responses for the model.

![Step_9](https://github.com/Anupriya-S/Operationalizing-Machine-Learning/blob/main/Screenshots/Swagger_UI_1.png)

![Step_10](https://github.com/Anupriya-S/Operationalizing-Machine-Learning/blob/main/Screenshots/Swagger_UI_2.png)

![Step_11](https://github.com/Anupriya-S/Operationalizing-Machine-Learning/blob/main/Screenshots/Swagger_UI_3.png)

7. The following screenshot shows the *Consume* tab of the deployed model with the key for the service and the URI that was generated after deployment.

![Step_12](https://github.com/Anupriya-S/Operationalizing-Machine-Learning/blob/main/Screenshots/REST_Endpoint_and_Key.png)

8. Here we can see the file `endpoint.py` running in the terminal against the API producing JSON output from the model.

![Step_13](https://github.com/Anupriya-S/Operationalizing-Machine-Learning/blob/main/Screenshots/Running_endpointpy_in_Terminal.png)

This call creates another file in the root directory, `data.json`.

![Step_14](https://github.com/Anupriya-S/Operationalizing-Machine-Learning/blob/main/Screenshots/Data_JSON_Created.png)

9. This step will benchmark the endpoint using Apache Benchmark (ab). `benchmark.sh` contains one line of `ab`. The following screenshot shows Apache Benchmark (ab) running against the HTTP API using authentication keys to retrieve performance results.

![Step_15](https://github.com/Anupriya-S/Operationalizing-Machine-Learning/blob/main/Screenshots/Benchmark_SH_Running_in_Terminal.png)

10. For this part of the project, you will use the Jupyter Notebook provided in the starter files. This following screenshot shows the *Run Details Widget* with AutoML steps from the notebook.

![Step_16](https://github.com/Anupriya-S/Operationalizing-Machine-Learning/blob/main/Screenshots/Create_Pipeline_1.png)

![Step_17](https://github.com/Anupriya-S/Operationalizing-Machine-Learning/blob/main/Screenshots/Create_Pipeline_2.png)

11. Make sure that the pipeline is created by checking out the *Pipeline* section in the studio.

![Step_18](https://github.com/Anupriya-S/Operationalizing-Machine-Learning/blob/main/Screenshots/Created_Pipeline_Studio.png)

12. This is the pipeline structure showing Bankmarketing dataset with the AutoML module.

![Step_19](https://github.com/Anupriya-S/Operationalizing-Machine-Learning/blob/main/Screenshots/Pipeline_Graph.png)

13. We used the following piece of code from the notebook for publishing the pipeline.

![Step_20](https://github.com/Anupriya-S/Operationalizing-Machine-Learning/blob/main/Screenshots/Publish_Pipeline.png)

14. The *Published Pipeline overview*, showing a REST endpoint and a status of ACTIVE meaning our pipeline has been published successfully and ready to use.

![Step_21](https://github.com/Anupriya-S/Operationalizing-Machine-Learning/blob/main/Screenshots/Published_Pipeline_Endpoint.png)

15. The following piece of code from the notebook demonstrates how we can send a POST request to trigger the pipeline published in the previous step.

![Step_22](https://github.com/Anupriya-S/Operationalizing-Machine-Learning/blob/main/Screenshots/Sending_POST_Request.png)

16. Azure ML studio showing the pipeline endpoint as *ACTIVE*.

![Step_23](https://github.com/Anupriya-S/Operationalizing-Machine-Learning/blob/main/Screenshots/Pipeline_Endpoint_ACTIVE.png)

17. Azure ML studio showing a completed run executed as a result of triggering the published pipeline through a POST request as shown in the previous step.

![Step_24](https://github.com/Anupriya-S/Operationalizing-Machine-Learning/blob/main/Screenshots/Submitted_Pipeline_Run.png)


## Screen Recording
Here is the link to the screencast demonstrating the entire working of how we can Operationalize Machine Learning using Azure ML platform.

[Let's go to the screencast!](https://youtu.be/BXZeRN934_8 "Screencast Demonstrating Operationalizing Machine Learning")

## Future Work
No matter what, we can always improvise one way or the other. I uderstand that the end goal of this project is not to find the most optimized model but to automate the process of training such models and to interact with such models. However, I have some suggestions that we can try to achieve better results in terms of the accuracy of the trained model.

1. Dataset should be balanced before feeding it to the model for getting better results.
2. While configuring the AutoML run, we can increase the time limit in the *Exit Criterion* so that more possibilities can be explored.

This obviously is not the limit and there must be more ways to improvise the above workflow.
