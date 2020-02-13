# LAB 1 - Creating Redshift Clusters
In this lab you will launch a new Redshift Cluster and setup connectivity 

## Contents
* [Before You Begin](#before-you-begin)
* [Configure Security](#configure-security)
* [Launch Redshift Cluster ](#launch-redshift-cluster)
* [Run Sample Query](#run-sample-query)
* [Before You Leave](#before-you-leave)

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

* Additional Configuration - Disable **Use defaults** and choose the VPC, Subnet Group, and VPC Security group you identified or created earlier.
<table><tr><td><img src=../images/CreateCluster4.png></td></tr></table> 

Leave the remaining settings with their default values.  Click **Create Cluster** to launch the Redshift cluster.

## Configure Client Tool
* See [Prerequisites](#prerequisites) for more details on downloading and installing [SQL Workbench/J](http://www.sql-workbench.net) and the [Redshift JDBC Driver](https://docs.aws.amazon.com/redshift/latest/mgmt/connecting-to-cluster.html). 
* Launch SQL Workbench/J and navigate to [File | Manage Drivers].
* Select "Amazon Redshift" and set the driver Library location to where you downloaded the Redshift JDBC Driver. Click Ok.
![](../images/Library.png)
* Navigate to [File | Connect Window] to create a new connection profile and modify the following settings and once complete click on the "Test Connection" button.
  * Name - "LabConnection"
  * Driver - Amazon Redshift (com.amazon.redshift.jdbc.Driver)
  * URL - Find this by navigating to the [Cluster List](https://console.aws.amazon.com/redshiftv2/home?#clusters), selecting your cluster, clicking on **Properties** and copying the **Endpoint** located in the **Connection details**.  
  ![](../images/JDBCUrl.png)
  * Username - [Master user name]
  * Password - [Master user password]
  * Autocommit - Enabled
  
![](../images/Connection.png)

## Run Sample Query
* Run the following query to list the users within the redshift cluster.  
```
select * from pg_user
```
* If you receive the following results, you have established connectivity and this lab is complete.  
![](../images/Users.png)

## Before You Leave
If you are done using your cluster, please think about decommissioning it to avoid having to pay for unused resources.
