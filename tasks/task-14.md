Description
---
- Create a wordpress app with mysql 
- Create mysql 
- Create secret and 
- update mysql deployment with that secret
- Add volume to the mysql 
- Create a wordpress app
- Create a config map 
- update wordpress app with configmap

# Cfreate a new project

```
oc new-project task14
```

# Create a new app
```
oc new-app mysql registry.access.redhat.com/rhscl/mysql-57-rhel7:5.7
```

![image](https://user-images.githubusercontent.com/26741425/129489585-13813519-7988-4491-8af9-5ae2eab82f38.png)

# Check 

```
 oc get deployment
```

![image](https://user-images.githubusercontent.com/26741425/129489602-eb41afa6-8030-4e8c-8343-97349ecc2165.png)


# Create a secret 

```
oc create secret genric <secret name> --from-literal=key1=value1  --from-literal=key2=value2 
```

## Example 

```
oc create secret generic mysql --from-literal=password=pa55
```

# Update deployment with secret

```
 oc set env deployment <deployment name > --prefix <prefix> --from secret/<secret name>
```

## Example 

```
 oc set env deployment mysql --prefix MYSQL_ROOT_ --from secret/mysql
```
# Check 
```
oc get pods
```
# Set volume

```
oc set volume deployment/mysql --name mysql-pvc --add --type pvc --claim-size 1Gi --claim-type rwo --mount-path /var/lib/mysql
```


# Create Wordpress 

```
oc new-app --docker-image=bitnami/wordpress
```
![image](https://user-images.githubusercontent.com/26741425/129489751-d52f74df-a2c4-42bd-be8e-a938902a772d.png)

# Expose service 

```
oc expose service/<service name>
```

## Example 

```
oc expose service/wordpress
```

# Create Config map 

```
oc create configmap <configmap name > --from-literal=host=mysql --from-literal=name=wpordpress --from-literal=user=root --from-literal=password=pa55
```

## Example 
```
oc create configmap wordpress-cm --from-literal=host=mysql --from-literal=name=wpordpress --from-literal=user=root --from-literal=password=pa55
```

# update deployment 

```
oc set env deployment/wordpress --prefix WORDPRESS_DATABASE_ --from configmap/wordpress-cm
```

# Check 

```
oc get pods
```

```
oc exec -it wordpress-pod-name env
```
