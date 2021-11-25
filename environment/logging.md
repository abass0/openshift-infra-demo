# Setting up logging and monitoring (Grafana & Kibana)

- Install logging operators (Operator Hub): 
 
 ```
  Openshift Elasticsearch Operator
     
  Openshift Logging Operator
 ```

- Create a logging instance:

```
apiVersion: "logging.openshift.io/v1"
kind: "ClusterLogging"
metadata:
  name: "instance"
  namespace: "openshift-logging"
spec:
  managementState: "Managed"
  logStore:
    type: "elasticsearch"
    elasticsearch:
      nodeCount: 2
      resources:
        limits:
          memory: 2Gi
        requests:
          cpu: 200m
          memory: 2Gi
      storage:
        storageClassName: logging
      redundancyPolicy: "SingleRedundancy"
  visualization:
    type: "kibana"
    kibana:
      resources:
        limits:
          memory: 1Gi
        requests:
          cpu: 500m
          memory: 1Gi
      replicas: 1
  curation:
    type: "curator"
    curator:
      resources:
        limits:
          memory: 200Mi
        requests:
          cpu: 200m
          memory: 200Mi
      schedule: "*/5 * * * *"
  collection:
    logs:
      type: "fluentd"
      fluentd:
        resources:
          limits:
            memory: 1Gi
          requests:
            cpu: 200m
            memory: 1Gi
  ```

  - Create Kiabana index (logging dashboard):

-[ ] Click "Create index pattern"

-[ ] Name-it "infra" 

-[ ] Next step

-[ ] Click "Discover" and the infra loggs will be on display
