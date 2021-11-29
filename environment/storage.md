# Demonstrating Storage (Openshift Data Foundation)

Openshift is a platform that enables you to manage both applications and the infraestrucutre behind it. Storage is a main part when we are using databases. In this demo, we demonstrate the simple process to deploy a ODF cluster and deploy an application using a block device storage class deployed by ODF.

### Installing a ODF Cluster (internal deploy)

Inside the WebUI: 
```
- [x] Click "Operator Hub"
- [x] Search for "ocs" 
- [x] Click "Openshift Container Storage"
- [x] Then, click "Install"
```
You can leave all options as default. When the installation is complete, it is now time to deploy the storage nodes:
```
- [x] Go to the installed operator
- [x] Click "Storage Cluster"
- [x] Then click "Create Storage Cluster"
```
Here, we will need to select the worker nodes that will host the ODF storage cluster.
```
- [x] Select the 3 worker nodes you want to host the cluster.
```
You can leave the rest of the configurations as default.

Once you click `Create` the cluster will start to go up and create the block, device and file storage classes. Now we wil demonstrate de deployment of an application using the storage class created by the storage cluster.

First, create a project named `new-app` then, create the application template: 

`oc create -f https://raw.githubusercontent.com/red-hat-storage/ocs-training/master/training/modules/ocs4/attachments/configurable-rails-app.yaml`

Once created:
```
- [x] In the Developer view, click "+Add"
- [x] Click "All services"
- [x] Search for "rails" and click the Configurable StorageClass template
- [x] Click "Instanciate Template"
- [X] Set the "Volume Capacity" to 5Gi
- [X] Set the "Volume Storage Class" to ocs-storagecluster-ceph-rbd
```
Now the application and the database will run on top of the block storage provided and managed by ODF.