Description
---
 - Create a new project 
 - Create a new app from templates

#
 ```
 oc new-project 
 ```
# Check available templates
![image](https://user-images.githubusercontent.com/26741425/129455107-f6ac9259-2b3f-4312-a16b-439179945382.png)

OR 
```
oc new-app --search --template=mariadb
```
![image](https://user-images.githubusercontent.com/26741425/129455152-fe1894a3-dabf-491e-b16a-748fc2c8f8e3.png)

# Find the required the parameters

```
oc process --parameters mariadb-persistent -n openshift
```
![image](https://user-images.githubusercontent.com/26741425/129455201-0bd7ed27-7889-43fb-98d5-505fef849793.png)

# Create an app from template 
```
oc new-app --template=mariadb-persistent --as-deployment-config -p MYSQL_USER=user1 -p MYSQL_PASSWORD=pa55 -p MYSQL_ROOT_PASSWORD=rootpa55
```
![image](https://user-images.githubusercontent.com/26741425/129455357-975f5220-8b14-4c3a-bd3b-b1b8f6a78788.png)

# Check deployment 

```
oc describe deploymentconfigs.apps.openshift.io/mariadb
```
![image](https://user-images.githubusercontent.com/26741425/129455395-20c4520a-09ae-4de9-b3cf-104f95ae4b92.png)

# Check Pods
```
oc get pods
```
![image](https://user-images.githubusercontent.com/26741425/129455377-97f40c61-63a2-42fc-8761-d474f4e89aaf.png)
