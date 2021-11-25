# Demonstrating monitoring (Grafana)

### Default monitoring dashboard

    Grafana is up by default in the Openshift cluster inside the openshift-monitoring namespace. It is possible to customize and set it up to be specific for used defined workload. 

### Accessing Grafana dashboard

```
- [x] Click "Networking"
- [x] Then "Routes" 
- [x] Select "openshift-monitoring" project (namespace)
- [x] You will find the Grafana instance already running and routed.
```

### Displaying monitoring dashboards
```
In the Grafana dashboard:

- [x] Click "Dashboards"
- [x] Then "Manage" 
- [x] Select the Default directory
- [x] Here you will find some premade dashboards for monitoring compute resources, etcd, networking.  
```

