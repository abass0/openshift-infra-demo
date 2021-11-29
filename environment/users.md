# Demonstrating User Permission (RBAC)

One of Openshift's strenghts is the Developer vs Administrator view that makes it possible to divide the relevent tools for each role.


    It is possible to integrate other auth agents with Openshift, but for demonstratrion purposes, we can take advantage of HTPassword.

For this demo, we will show de differences we acheive by using cluster roles on different users for different purposes. 

### Create the users

` htpasswd -c -B -b users.htpasswd admin redhat`

` htpasswd -B -b users.htpasswd dev redhat `

### Create the secret with the newly created htpass file

` oc create secret generic htpass-secret --from-file=htpasswd=users.htpasswd -n openshift-config `

### Create and apply the cluster resource 

```
apiVersion: config.openshift.io/v1
kind: OAuth
metadata:
  name: cluster
spec:
  identityProviders:
  - name: htpasswd_provider
    mappingMethod: claim
    type: HTPasswd
    htpasswd:
      fileData:
        name: htpass-secret
```

` oc apply htpass-cr.yaml `

Now that we have the users created, we need to define cluster roles for them. For this demo, we will make the `admin` user `cluster-admin` and leave the `dev` as a normal user. 

### Applying the cluster role 

` oc adm policy add-cluster-role-to-user cluster-admin admin `

` oc adm policy add-cluster-role-to-user basic-user dev `

Then, demonstrate the differences of what each user can do inside the cluster dashboard.  