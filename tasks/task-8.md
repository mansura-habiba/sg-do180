Description
----
Task 8 is about Decoupling Information.
- Run a Pod that offers mysql services, meeting the following requirements,
- use a mysql image, make sure that the /var/lib/mysql directory in the container is mounted on a Persistent Volume Claim,
- and provide variables that are required to start the application in an efficient way.


# provide variables that are required to start the application in an efficient way

```
oc  create secret generic mysql --from-literal username=user1 --from-literal password=pa55 --from-literal root_password=rootpa55 --from-literal database=books
```

```
os set env deployment mysql --prefix MYSQL_ -from secret/mysql
```
