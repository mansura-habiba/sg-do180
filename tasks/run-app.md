DESCRIPTION
---
Task 7 is about Running Applications in OpenShift.
- Create a YAML manifest file that allows you to run an application with the name newnginx and meets the following requirements,
- use the bitnami/nginx image,
- provide access to the application using a route, and ensure that the YAML file is created, but no API resources are actually added to the cluster.

# Login 


# Create project 

```
oc new-project task7
```

# Create A deploy 

```
oc create deploy myapp --image=bitnami/nginx --dry-run=client -o yaml > myapp.yaml
```

# Check 

```
oc create -f myapp.yaml
```

# Expose

```
oc expose deploy myapp --dry-run=client --port=8080 -o yaml >> myapp.yaml
```

# Check 

```
oc get all --selector app=myapp
```

# Expose service 

```
oc expose svc myapp --dry-run=client -o yaml >> myapp.yaml
```

# Deleet all service 

```
oc delete all --all
```
Add separator between the blocks 
```
...

---
```
# Create 

```
oc create -f myapp.yaml
```

