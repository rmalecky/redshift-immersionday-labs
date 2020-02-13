# LAB 1 - Creating Redshift Clusters
In this lab you will launch a new Redshift Cluster and setup connectivity 

## Contents
* [Configure Security](#configure-security)
* [Launch Redshift Cluster ](#launch-redshift-cluster)
* [Run Sample Query](#run-sample-query)


## Configure Security

### S3 Access
Create an **IAM Role** with the type "Redshift" and the use-case of "Redshift - Customizable" and attach the AmazonS3ReadOnlyAccess and AWSGlueConsoleFullAccess policies to the role.
```
https://console.aws.amazon.com/iam/home?#/roles$new?step=type
```
![](../images/Role.png)

## Launch Redshift Cluster
Navigate to the **Amazon Redshift Dashboard** and click on the "Create Cluster" button.  
```
https://console.aws.amazon.com/redshiftv2/home?#clusters
```
* Cluster Configuration - Choose the node type and set the number of nodes.  For these labs a dc2.large node type with 4 nodes will be suitable. 
<table><tr><td><img src=../images/CreateCluster1.png></td></tr></table> 

* Cluster Details - Enter values as appropriate for your organization.  Note the Master user password as you will not be able to retrieve this value later.
<table><tr><td><img src=../images/CreateCluster2.png></td></tr></table> 

* Cluster Permissions - Select the Role which you identified or created earlier to associate to the cluster, and click **Add IAM role**
<table><tr><td><img src=../images/CreateCluster3.png></td></tr></table> 

* Additional Configuration - leave **Use defaults**  enabled

LClick **Create Cluster** to launch the Redshift cluster.

## Connect with the in console editor
Select the Editor tab on the Redshift console.  Enter your connection details.  The default name for the database is`dev` the default name for the database user is `awsuser`.  Hit the `Connect to database` button when you are done.

Once connected select the `public` schema from the schema dropdown.

## Run Sample Query
* Run the following query to list the users within the redshift cluster.  
```
select * from pg_user
```
* If you receive the following results, you have established connectivity and this lab is complete.  
![](../images/Users.png)


