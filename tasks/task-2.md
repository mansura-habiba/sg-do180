Description
---
Task 2 is to work with Standard Images.
- Use our developers.redhat.com credentials to log into the RedHat image registries,
- Use the appropriate command to inspect the Mariadb image without downloading it,
- then download the image without ruining it, and
- inspect the image to find out which command started as the default command,
- next, run the image as a container, and
-  after starting it, open and interactive shell on the container and find which operating system and kernel it uses.

# log into the RedHat image registries

## Find the valid registries

```
vim /etc/containers/registry.conf
```

## login

```
podman login -u <username> -p <password> registry.access.redhat.com
```

```
podman login -u <email> -p <password> registry.redhat.io
```
```
podman login -u <username> -p <password> quay.io
```

## search for Images

```
podman search <service name>
```
### Example

```
podman search mariadb
```

![image](https://user-images.githubusercontent.com/26741425/129452610-00d856a0-dc10-4c1e-a3df-2d49f516b58d.png)

# inspect the Mariadb image without downloading it

```
skopeo inspect docker://registry.access.redhat.com/<placer>/<image name>:<tag>
```
![image](https://user-images.githubusercontent.com/26741425/129452648-8e468034-9433-43ee-8b80-6b8d255ecee6.png)


![image](https://user-images.githubusercontent.com/26741425/129452660-31a9584e-a14c-44ff-b286-dfe73c1d3bab.png)


# download the image without ruining it

```
podman pull registry.access.redhat.com/<placer>/<image name>:<tag>
```
![image](https://user-images.githubusercontent.com/26741425/129452671-6458495e-7815-4d0c-b95a-d469215e0c5d.png)

## check if the image is downloaded

```
podman images
```
OR

```
podman image list
```

![image](https://user-images.githubusercontent.com/26741425/129452685-991d6f39-44be-4601-adc2-b370297f9ee2.png)


# inspect the image to find out which command started as the default command

```
podman inspect <image name>
```


```
podman inspect -l | grep <keyword>
```


```
podman inspect -l | grep IPConfig
```


![image](https://user-images.githubusercontent.com/26741425/129452712-6a3daee4-1f2d-4376-bf72-10b6436957cf.png)

## Find entry point 

![image](https://user-images.githubusercontent.com/26741425/129452738-58f8e76e-56f9-46a9-a0f3-6bae921ef174.png)



# run the image as a container

```
podman run -d --name <container name> -p <from port>:<to port> -e Key1=value1 -e key2=value-2 registry.access.redhat.com/<placer>/<image name>:<tag>
```

## check running containers


```
podman ps -a
```
![image](https://user-images.githubusercontent.com/26741425/129452754-79fd1507-12cd-4220-9923-b0afc6cdaf60.png)


![image](https://user-images.githubusercontent.com/26741425/129452771-16abadf7-a876-4d10-9fe7-7128c7c2dabe.png)


# open and interactive shell on the container and find which operating system and kernel it uses

```
podman exec -it <container name > sh
```
![image](https://user-images.githubusercontent.com/26741425/129452847-561dbc0c-7b58-43ce-91a8-b20122347f7b.png)


# Trouble shoot 

## check logs
```
podman logs --tail <container name> 
```


## get help for podman run command 

```
podman run --help
```
![image](https://user-images.githubusercontent.com/26741425/129452815-71275304-24ca-4f44-a460-1179ec42f48f.png)

