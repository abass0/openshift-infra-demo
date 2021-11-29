# Demonstrating cluster scalling

### Taking advantage of the WebUI

    You can use the documentation to create a new MachineSet to demonstrate cluster scalling. However, in a demo envrionment it is simpler to use the already available resources. In this dynamic you can choose do "descale" a MachineSet and demostrate the scaling of it live. 

    Before demostrating, an explanation of what a MachineSet is will facilitate the understanding of what is beeing "demoed". 

[MachineSet creating documentation (for AWS)](https://docs.openshift.com/container-platform/4.9/machine_management/creating_machinesets/creating-machineset-aws.html#machineset-yaml-aws_creating-machineset-aws)

### Scalling a MachineSet 

```
- [x] Click "Compute"
- [x] Then "MachineSets" 
- [x] Select the "descaled" MachineSet that sould have "0 of 0 machines"
- [x] Click the "Actions" dropdown and then "Edit Machine count"
```

### Stress testing the Machine Autoscaler

    Using the same thought process as before, you can use the already available MachineSets to create a Machine Autoscaler through the WebUI.

```
- [x] Click "Compute"
- [x] Then "MachineSets" 
- [x] Select the "3 dots" of the MachineSet you wish to create the Autosaler for. 
- [x] Click "Create MachineAutoscaler"
- [x] Set the min. replicas of 1 and the max at 10
```
Next we will use a "stress test job" to demonstrate the scaling of the machines inside de MachineSet we just created the autoscaler for. 

```
- [x] Create a new project called "stress-test" (optional)
- [x] Use this example to lauch a stress job to force the cluster to scale:
```

stress-job.yaml:
```
apiVersion: batch/v1
kind: Job
metadata:
  generateName: work-queue-
spec:
  template:
    spec:
      containers:
      - name: work
        image: busybox
        command: ["sleep",  "300"]
        resources:
          requests:
            memory: 500Mi
            cpu: 500m
      restartPolicy: Never
  backoffLimit: 4
  completions: 50
  parallelism: 50
```
```
- [x] In the WebUI, select the stress-test project
- [x] Go to Workloads and click Pods
```
Here you will be able to show the newly created pods as they start to go up. Next, we want to show how the cluster responded to the stress test:
```
- [x] Go to Compute and then Machines
```
You should see the new nodes start to build. Observe that, because we set the max machines ate 10, the cluster will only create 10 new nodes to support the new workload. You can also use the `Node` visualization to demonstrate the newly created resources. 

`Important: If you have a cluster with enough resources (big worker nodes) the cluster wont scale.`