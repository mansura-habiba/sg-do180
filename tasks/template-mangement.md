Description
----
Task 8 is about Decoupling Information.
- Run a Pod that offers mysql services, meeting the following requirements,
- use a mysql image, make sure that the /var/lib/mysql directory in the container is mounted on a Persistent Volume Claim,
- and provide variables that are required to start the application in an efficient way.

# Check template process
```
oc get template mariadb-persistent -n openshift
```
# Create database from template 

```
oc new-app --template=mariadb-persistent -p MYSQL_USER=bob -p MYSQL_PASSWORD=secret -p MYSQL_DATABSE_NAME=books-p MYSQL_ROOT_PASSWORD=secret
```

# Check

```
oc get all -selector app=mysql
```


# provide variables that are required to start the application in an efficient way

```
oc  create secret generic mysql --from-literal username=user1 --from-literal password=pa55 --from-literal root_password=rootpa55 --from-literal database=books
```

```
os set env deployment mysql --prefix MYSQL_ -from secret/mysql
```
