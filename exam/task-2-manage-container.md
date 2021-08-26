Description
---
1. There are 3 .sh file already created. Each file needs to be updated with corresponding task

ToDo
---
1. write command to run container from newly build image
2. write command to view last 10 lines of the log of the running conatiner
3. stop the running container


Solution
---
Update each .sh file with corresponding commands.

## Create container from the image

```
podman run -d --name acme_jsboss localhost/acme_jboss:latest
```

### Check
```
podman ps
```

## view last 10 lines of the log of the running container

```
podman logs --tail=10 acme_jboss
```

## Stop Conatiner

```
podman stop acme_jboss
```
Here *acme_jboss* is the container name specified in the task.
