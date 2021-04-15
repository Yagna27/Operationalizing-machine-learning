# MLOps-Azure

## Project Overview
I was working with the Bank-Marketing dataset, that contains information about a previous bank marketing campaign from a Portuguese institution, i.e. attributed of the people the campaign dealt with and <ins>if a client will subscribe to a term deposit product (which is a binary outcome)</ins>.
We seek to predict that outcome. This can be helpful in developing future marketing campaigns.
The best model, was the **VotingEnsemble** that had an accuracy of **91.654%**. Furthermore, we deployed the model, and consumed it through a REST endpoint. Thereby, we published our pipeline of steps, automating the whole procedure.

Following flow diagram depicts the process.
<img src="mlops-flow.png"/>


# Table of Contents
 * [Architecture Diagram](#arch)
 * [Future Improvements](#fi)
 * [The Process in Practice](#tpip)
     * [Authentication](#auth)
     * [Automated ML Experiment](#automl)
     * [Deploy the best model](#deploy)
     * [Enable logging](#logging)
     * [Swagger Documentation](#swagger)
     * [Consume model endpoints](#consume)
     * [Create and publish a pipeline](#pipeline)
 * [Screen Recording](#sr)
 * [Standout Suggestions](#ss)
 
 
## Architecture Diagram<a name="arch"></a>
Following is the architecture diagram to depict our approach and organisation.
<img src="mlops-arch.png"/>

## Future Improvements<a name="fi"></a>
* One can work with diferent datapoints, and visualise and benchmark the performance while actually using Application Insights.
* We may focus more time on exploring the data generating a more random dataset. The following columns have a broad gap in terms of number of instances:
    * There are far more married people than single and divorced.
    * There are far more people without a loan than with one.
    * The campaign maybe spread across the year for a better understanding of the customer's mood according to time of the year.
*Better data is bound to yield better results.*
* We can observe and generate a report on, to what extent does which factor affect the likeliness of a client to subscribe, and develop marketing campaigns around them.
* The AutoML experiment could also be run for a longer while which might as well fetch more effective models.
* Different parameters can be used in AutoML config in order to make more effective models.

## The Process in Practice<a name="tpip"></a>

#### Authentication <a name="auth"></a>
Skipped this section, since I used the provided labs.

#### Automated ML Experiment<a name="automl"></a>
We have been provided with the *Bank-Marketing* dataset for the task, visible as follows.
<img src="screenshots for project/Screenshot (521).png"/>
<img src="screenshots for project/Screenshot (594).png"/>
We created the appropriate compute required for running an automl run on our dataset. Furthermore, we created an automl run for the same, which completed as follows.
<img src="screenshots for project/Screenshot (523).png"/>

The best model was found out to be the Voting Ensemble with an accuracy of 91.654%
from the above screenshot

#### Deploy the Best Model<a name="deploy"></a>
We choose the best model for deployment and enable "Authentication" while deploying the model using Azure Container Instance (ACI).

#### Enable Application Insights<a name="logging"></a>
We performing loggin on our endpoint, by running `logs.py`.
<img src="screenshots for project/Screenshot (527).png"/>
<img src="screenshots for project/Screenshot (595).png"/>
The executed code in logs.py enables Application Insights. "Application Insights enabled" is disabled before executing logs.py.
<img src="screenshots for project/Screenshot (528).png"/>

The application insights URL in the bottom opens of the above screenshot opens as follows. Notice the insihts generated, for the calls we made while testing.
from the above screenshot you can see it

#### Swagger Documentation<a name="swagger"></a>
In order to view the swagger documentation provided by Microsoft Azure, for our endpoint in an appealing and understandable way we required the swagger-ui. I pulled the latest swagger-ui docker image and to run it on port 80.
To view our own documentation, I downloaded the swagger.json file and exposed it to a local HTTP server. This can now be run on the swagger-ui.
The API methods are:
<img src="screenshots for project/swagger1.png"/>
<img src="screenshots for project/swagger2.png"/>
<img src="screenshots for project/swagger3.png"/>

#### Consume Model Endpoints<a name="consume"></a>
Now that we have implemented and understood our endpoint, we may consume it. This is done by passing appropriate ingormation to the endpoint using the `endpoint.py` file. We entered Scoring URI and primary key in `endpoint.py` in order to run it. The output is as follows:
<img src="screenshots for project/Screenshot (532).png"/>
<img src="screenshots for project/Screenshot (533).png"/>
I dont performd *benchmarking* as it is optional and i am running out of time.(Beachmarking will help us create a baseline or acceptable performance measure)
#### Create, Publish and Consume a Pipeline<a name="pipeline"></a>
With the help of the `aml-pipelines-with-automated-machine-learning-step.ipynb` file, we made the pipeline Run. The RunDetails widget in our Jupyter Notebook, displays the Run Output as follows:
<img src="screenshots/run-details-widget-nb.png"/>

Following is how the Pipeline Run looks like in the sdk, with automl module and bank marketing dataset.
<img src="screenshots for project/Screenshot (540).png"/>

Active status of pipeline and endpoint of pipeline 
<img src="screenshots for project/Screenshot (543).png"/>
<img src="screenshots for project/Screenshot (551).png"/>
It got completed successfuly, as follows.
<img src="screenshots for project/Screenshot (544).png"/>
<img src="screenshots for project/Screenshot (545).png"/>
<img src="screenshots for project/Screen Shot .png"/>
final submission of pipeline in sdk
<img src="screenshots for project/Screenshot (552).png"/>
<img src="screenshots for project/Screenshot (599).png"/>
<img src="screenshots for project/Screenshot (604).png"/>
<img src="screenshots for project/Screenshot (605).png"/>
## Screen Recording<a name="sr"></a>
<a href="https://youtu.be/otFyHKmV_To">YouTube Video Link</a> contains the Working deployed ML model endpoint, Deployed Pipeline, Available AutoML Model, 
Successful API requests to the endpoint with a JSON payload et cetera in a screen recording.


