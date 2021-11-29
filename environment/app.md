1. quay.io/openshiftroadshow/parksmap:latest
2. app=parksmap-app role=frontend component=parksmap
3. https://github.com/openshift-roadshow/nationalparks
4. app=parksmap-app role=backend component=nationalparks
5. oc create -f https://raw.githubusercontent.com/openshift-labs/starter-guides/ocp-4.6/mongodb-template.yaml 
6. mongodb-nationalparks mongodb

https://openshift-labs.github.io/starter-guides-html/parksmap-container-image.html