# GLCwithAndela Jakobus Walker

## QwikLabs Completed

<details>
<summary>App Dev Setting up a Development Environment</summary>
<img src="https://github.com/jakowalk/GLCwithAndela/blob/master/Challenge%201/App%20Dev%20Setting%20up%20a%20Development%20Enviroment.png">
</details>
<details>
<summary>Console and Cloud Shell</summary>
<img src="https://github.com/jakowalk/GLCwithAndela/blob/master/Challenge%201/Console%20and%20Cloud%20Shell.png">
</details>
<details>
<summary>Creating Virtual Machines</summary>
<img src="https://github.com/jakowalk/GLCwithAndela/blob/master/Challenge%201/Creating%20Virtual%20Machines.png">
</details>
<details>
<summary>Getting Started with BigQuery</summary>
<img src="https://github.com/jakowalk/GLCwithAndela/blob/master/Challenge%201/Getting%20Started%20with%20BigQuery.png">
</details>
<details>
<summary>Getting Started with Cloud Marketplace</summary>
<img src="https://github.com/jakowalk/GLCwithAndela/blob/master/Challenge%201/Getting%20Started%20with%20Cloud%20Marketplace.png">
</details>
<details>
<summary>Getting Started with Deployment Manager</summary>
<img src="https://github.com/jakowalk/GLCwithAndela/blob/master/Challenge%201/Getting%20Started%20with%20Delployment%20Manager.png">
</details>
<details>
<summary>Getting started with Compute Engine</summary>
<img src="https://github.com/jakowalk/GLCwithAndela/blob/master/Challenge%201/Getting%20started%20with%20Compute%20Engine.png">
</details>
<details>
<summary>Getting started with GKE</summary>
<img src="https://github.com/jakowalk/GLCwithAndela/blob/master/Challenge%201/Getting%20started%20with%20GKE.png">
</details>
<details>
<summary>Google Cloud Fundementals Getting started with App Engine</summary>
<img src="https://github.com/jakowalk/GLCwithAndela/blob/master/Challenge%201/Google%20Cloud%20Fundementals%20Getting%20started%20with%20App%20Engine.png">
</details>
<details>
<summary>Infrastructure Preview</summary>
<img src="https://github.com/jakowalk/GLCwithAndela/blob/master/Challenge%201/Infrastructure%20Preview.png">
</details>
<details>
<summary>Private Google Access and Cloud NAT</summary>
<img src="https://github.com/jakowalk/GLCwithAndela/blob/master/Challenge%201/Private%20Google%20Access%20and%20Cloud%20NAT.png">
</details>
<details>
<summary>App Dev Setting up a Development Enviroment</summary>
<img src="https://github.com/jakowalk/GLCwithAndela/blob/master/Challenge%201/Storing%20Application%20Data%20in%20the%20Cloud%20Datastore.png">
</details>

## Translation code

```
Error Reporting and Debugging

Objectives
In this lab, you learn how to perform the following tasks:

-Launch a simple Google App Engine application

-Introduce an error into the application

-Explore Cloud Error Reporting

-Use Cloud Debugger to identify the error in the code

-Fix the bug and monitor in Cloud Operations


Task 1: Create an application

	mkdir appengine-hello
	cd appengine-hello
	gsutil cp gs://cloud-training/archinfra/gae-hello/* .

	Run the application using the local development server in Cloud Shell with the following command:
	dev_appserver.py $(pwd)

	Click Web Preview > Preview on port 8080 to view the application, or run the below code:
	gcloud app browse

	Deploy the application to App Engine, run the following command:
	gcloud app deploy app.yaml

	Type Y when prompted

	When the process is done, verify that the application is working by running the following command:
	gcloud app browse

	Examine the main.py file, by running the following command:
	cat main.py

	Add the specific error by running the code below:
	sed -i -e 's/webapp2/webapp22/' main.py

	Verify the change you made in the main.py file, run the following command:
	cat main.py

	Re-deploy the application to App Engine:
	gcloud app deploy app.yaml --quiet

	When the process is done, verify that the application is broken by running the following command:
	gcloud app browse


Task 2: Explore Cloud Error Reporting	

	In the Cloud Console, on the Navigation menu, click Error Reporting.
	You should see an error regarding the failed import of webapp22.

	Click Auto reload.

	In Cloud Shell, run the following command:
	gcloud app browse

	Click the resulting link several times to generate more errors.

	Click the Error name: ImportError: No module named webapp22.

	In Cloud Shell, fix the error by running the following command:
	sed -i -e 's/webapp22/webapp2/' main.py

	Re-deploy the application to App Engine, run the following command:
	gcloud app deploy app.yaml --quiet

	Verify that the application is working again, run the following command:
	gcloud app browse

	Verify by selecting Auto-Reload option, reloading application and checking the error logs.
```
```
Google Cloud Fundamentals: Getting Started with GKE

In this lab, you create a Google Kubernetes Engine cluster containing several containers, each containing a web server. You place a load balancer in front of the cluster and view its contents.

Objectives
In this lab, you learn how to perform the following tasks:

-Provision a Kubernetes cluster using Kubernetes Engine.

-Deploy and manage Docker containers using kubectl.

Task 2: Confirm that needed APIs are enabled
	In CLoud Shell, enable the APIs by entering the following in order:

	gcloud config set project qwiklabs-gcp-02-942dbf7e6f71
	gcloud services enable containerregistry.googleapis.com
	gcloud services enable container.googleapis.com
	
	Confirm they are enabled with:
	gcloud services list


Task 3: Start a Kubernetes Engine cluster

	Place the zone into an environment variable called MY_ZONE:
	export MY_ZONE=us-central1-a

	Start a Kubernetes cluster managed by Kubernetes Engine. Name the cluster webfrontend and configure it to run 2 nodes:
	gcloud container clusters create webfrontend --zone $MY_ZONE --num-nodes 2

	After the cluster is created, check your installed version of Kubernetes using the kubectl version command:
	kubectl version

	View your running nodes in CloudShell with:
	gcloud compute instances list


Task 4: Run and deploy a container
	Launch a single instance of the nginx container:
	kubectl create deploy nginx --image=nginx:1.17.10

	View the pod running the nginx container:
	kubectl get pods

	Expose the nginx container to the Internet:
	kubectl expose deployment nginx --port 80 --type LoadBalancer

	View the new service:
	kubectl get services

	Scale up the number of pods running on your service:
	kubectl scale deployment nginx --replicas 3

	Confirm that Kubernetes has updated the number of pods:
	kubectl get pods

	Confirm that your external IP address has not changed:
	kubectl get services

	Return to the web browser tab in which you viewed your cluster's external IP address. Refresh the page to confirm that the nginx web server is still responding.
  
```
```
Google Cloud Fundamentals: Getting Started with BigQuery

Objectives
In this lab, you learn how to perform the following tasks:

-Load data from Cloud Storage into BigQuery.

-Perform a query on the data in BigQuery.

Task 1: N/A

Task 2: Load data from Cloud Storage into BigQuery
	Create a new dataset within your project by selecting your project in the Resources section, then clicking on CREATE DATASET on the right.
	In the Create Dataset dialog, for Dataset ID, type logdata.
	For Data location, select the continent closest to the region your project was created in. 
	Click create dataset.

	Create a new table in the logdata to store the data from the CSV file.

	Click on Create Table. On the Create Table page, in the Source section:
	For Create table from, choose select Google Cloud Storage, and in the field, type gs://cloud-training/gcpfci/access_log.csv.
	Verify File format is set to CSV.

	In the Destination section:
	For Dataset name, leave logdata selected.
	For Table name, type accesslog.
	For Table type, Native table should be selected.
	Under Schema section, for Auto detect check the Schema and input Parameters.
	Accept the remaining default values and click Create Table.

	When the load job is complete, click logdata > accesslog.
	On the table details page, click Details to view the table properties, and then click Preview to view the table data.

Task 3: Perform a query on the data using the BigQuery web UI
	In the Query editor window, type the following query:
	select int64_field_6 as hour, count(*) as hitcount from logdata.accesslog
	group by hour
	order by hour
	Click Run 

Task 4: Perform a query on the data using the bq command
	At Cloud Shell prompt, enter:
	bq query "select string_field_10 as request, count(*) as requestcount from logdata.accesslog group by request order by requestcount desc"
```
