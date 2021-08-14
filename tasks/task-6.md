Description
---
Task 6 is about CRC.
- Install CodeReady Containers,
- start an nginx application that is based on the bitnami/nginx application,
- and use the command line client to verify that the application is running. 


# Check

```
oc whoami --show-console
```

# Login 

```
oc login -u <username> -p <password> <master api>
```

# create a new project 

```
oc new-project task6
```

# Create new app

```
oc new-app bitname/nginx
```

# Check

```
oc get pods
```

```
oc get all --selector app==nginx
```

