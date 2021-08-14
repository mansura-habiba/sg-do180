Description
---
Task 4 is about Managing Containers.
- Use podman to start from mysql container,
- ensure that this container will store files that are written to /var/lib/mysql persistently to the host directory /srv/mysql, and
- expose the default container port on port 30306 on the localhost.


# Create host directory

```
mkdir -pv /srv/mysql
```

# Set SELinux to the host directory

```
sudo semanage fcontext -a -t container_file_t "/srv/mysql(/.*)?"
```

```
sudo restorecon -R "/srv/mysql(/.*)?"
```
# Give mysqld permisssion to execute

```
sudo chown 27:27 -R /srv/mysql
```
# start from mysql container

```
podman run -d --name mysql-1 -p 130306:30306 -v /srv/mysql:/var/lib/mysql \
       -e MYSQL_USERNAME=user1 -e MYSQL_PASSWORS=user1 -e MYSQL_ROOT_PASSWORD=admin -e MYSQL_DATBASE=books
        image url:tag  
```
