Description
---
Task 3 is about Managing Images.
- Start the bitnami and nginx image using the name mynginx,
- add the file /tmp/hello, and ensure the changes to the image are saved,
- save the modified image to a tar archive, and
- remove the image from the local image list, next,
- restore the backup that you previously created.

# Start the bitnami and nginx image using the name mynginx

## login

```
podman login -u <username> -p <password> registry.access.redhat.com
```

## search

```
podman search bitnami
```


```
podman search nginx
```

## start

```
podman run -d --name mynginx <registry url>/<location>/<image name>:<tag>
```


# add the file /tmp/hello, and ensure the changes to the image are saved

## check container is running

```
podman ps -a
```

## open interactive terminal

```
podman exec -it mynginx sh
```

```
touch /tmp/hello
```

```
podman commit -a <name> mynginx localhost://mynginx:v1.0
```
# save the modified image to a tar archive
```
podman save -o <tar file> localhost://mynginx:v1.0
```
# remove the image from the local image list
## stop container

```
podman stop mynginx
```

## remove container

```
podman rm mynginx
```

## remove old image

```
podman rmi <registry url>/<location>/<image name>:<tag>
```
# restore the backup that you previously created

```
podman run -d --name mynginx localhost://<location>/mynginx:v1.0
```
