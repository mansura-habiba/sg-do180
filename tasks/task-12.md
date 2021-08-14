Description
---
- Create a new project 
- Create a maridb app from template but without parameter
- Create a generic secret for maridb parameter
- set parameter value 

# Create project
```
 oc new-project task12
```
# Create mariadb app without parameter

```
oc new-app --template=mariadb-persistent --as-deployment-confi
```

# Check 

```
oc get all
```

![image](https://user-images.githubusercontent.com/26741425/129456246-7de57544-ab53-48fb-a5a5-4adff71c6bff.png)


# Create secret

```
oc create secret generic mariadb2 --from-literal user=user1 --from-literal password=pa55 --from-literal root_password=pa55 --from-literal database=items
```

# Check Environement variable 
![image](https://user-images.githubusercontent.com/26741425/129456281-e5458459-1856-4b9b-a817-b0828aa04e3b.png)

```
oc set env dc/mariadb --list
```

![image](https://user-images.githubusercontent.com/26741425/129456289-bbccfdfd-eb7a-4a4a-a8e1-6a28818f4760.png)


![image](https://user-images.githubusercontent.com/26741425/129456310-a78f44c8-7e89-4f04-8a02-44084d477039.png)


# apply new secret

```
oc set env dc/mariadb --prefix MYSQL_ --from secret/mariadb2
```

![image](https://user-images.githubusercontent.com/26741425/129456335-43ab6ec8-860e-4f50-b4b1-d0055546b35c.png)


# check log 

```
oc logs <container name>
```
![image](https://user-images.githubusercontent.com/26741425/129456390-4c5bf896-3159-491d-bfd4-8f6a705107f2.png)
