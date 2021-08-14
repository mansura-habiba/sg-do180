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
# inspect the Mariadb image without downloading it

```
skopeo inspect docker://registry.access.redhat.com/<placer>/<image name>:<tag>
```
# download the image without ruining it

```
podman pull registry.access.redhat.com/<placer>/<image name>:<tag>
```

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

## check downloaded Images

```
podman images
```

# run the image as a container

```
podman run -d --name <container name> -p <from port>:<to port> -e Key1=value1 -e key2=value-2 registry.access.redhat.com/<placer>/<image name>:<tag>
```

## check running containers


```
podman ps -a
```

# open and interactive shell on the container and find which operating system and kernel it uses

```
podman exec -it <container name > sh
```
