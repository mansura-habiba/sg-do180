Description
---
- Create a project 

- Create a database from docker image but no deployment config
- Create a database from docker image with deployment config

# Create a Project 
```
oc new-project task13
```
![image](https://user-images.githubusercontent.com/26741425/129456635-d3a7a59d-5efa-4b09-bb03-32a99e007751.png)

# search for mysql image 

Checkout help 
```
oc new-app -h
```
![image](https://user-images.githubusercontent.com/26741425/129456669-1be6495e-f85b-4668-aff3-74d43fff336a.png)


# Create app

```
oc new-app --name mysql-1 --docker-image=registry.access.redhat.com/rhscl/mysql-57-rhel7:latest -e MYSQL_USER=user1 -e MYSQL_PASSWORD=pa55 -e MYSQL_ROOT_PASSWORD=rootpa55 -e MYSQL_DATABASE=testdb
```

![image](https://user-images.githubusercontent.com/26741425/129456737-8b65e44b-7807-4f35-85e2-995fc45ffd24.png)


## Check status 

```
oc status
```
![image](https://user-images.githubusercontent.com/26741425/129456787-e66ab726-33cd-4aec-95e0-588aa5a313e2.png)

```
oc get all
```
![image](https://user-images.githubusercontent.com/26741425/129456750-e903ff51-a674-42e0-8c29-296e10e4716f.png)

Also check log

```
oc logs <podname>
```

![image](https://user-images.githubusercontent.com/26741425/129456764-a6eab1d1-c792-4825-92cb-9a1b204f9ca2.png)

## Check newly created deployment 

```
oc get deployment 
```

```
oc describe deployment <deployment name>
```

![image](https://user-images.githubusercontent.com/26741425/129456877-89b8a01f-186e-447c-85e3-9b714b9b41dc.png)


## Check newly created Service 

```
oc get service
```

```
oc describe service <service name>
```

![image](https://user-images.githubusercontent.com/26741425/129456832-74c7e257-9a90-4561-ba9b-81ac7549b2e8.png)

At this moment, this service is not exposed. 

```
oc expose service <service name >
```

![image](https://user-images.githubusercontent.com/26741425/129457089-bd4970ca-2899-4c42-95f2-5e44174b2e2b.png)


## Delete app

```
oc delete all --all
```
![image](https://user-images.githubusercontent.com/26741425/129456949-9b01a0aa-01b2-4c45-a427-fa1714f7ee9b.png)


# Create app with deployment config

```
oc new-app --name mysql-1 --docker-image=registry.access.redhat.com/rhscl/mysql-57-rhel7:latest -e MYSQL_USER=user1 -e MYSQL_PASSWORD=pa55 -e MYSQL_ROOT_PASSWORD=rootpa55 -e MYSQL_DATABASE=testdb --as-deployment-config 
```

![image](https://user-images.githubusercontent.com/26741425/129456975-83fe927e-f387-4f84-82cd-59e02eae3264.png)
 There will be no deployment but deploymet config 
 
 ```
 oc describe dc <deployment config name>
 ```
 
 ```
 oc describe dc mysql-1
 ```
 
 ![image](https://user-images.githubusercontent.com/26741425/129456996-d17c1760-014f-4c49-bedc-2fc5ed8ecc7e.png)
