# Openshift Infrastructure Demo 

This repo is an example for a initial "default" demo of Openshift exploring the basics of the platform from an infrastructure and management point of view. 

## Baseline Narrative

In this demo, we will discuss:

    - General Management Dashboard
    - Logging Dashboard (Kibana)
    - Monitoring Dashboard (Grafana)
    - Users and Cluster Roles
    - Overview, Scaling and Management of nodes 
    - Storage Overview and App Deployment

## Recommended order of demo

You can follow this content anyway you want, below is my recommendation of the topic order:

- [General Overview of the Openshift Web UI and cluster]() 
- [Users and Cluster Roles](https://github.com/abass0/openshift-infra-demo/blob/main/environment/users.md) 
- [Monitoring Dashboard](https://github.com/abass0/openshift-infra-demo/blob/main/environment/monitoring.md) 
- [Logging Dashboard](https://github.com/abass0/openshift-infra-demo/blob/main/environment/logging.md)
- [Scaling and Management of nodes](https://github.com/abass0/openshift-infra-demo/blob/main/environment/scaling.md) 
- [Storage Overview and App Deployment](https://github.com/abass0/openshift-infra-demo/blob/main/environment/storage.md) 

## Some notes

- Create the users and add the roles prior to the demo so you can focus on simply show the differences between the permissions. 
- Create the .yaml file of the Stress Job beforehand
- Deploy Kibana prior to your demonstration
- Create the application template and the project in advance so you can simply select it on the WebUI


