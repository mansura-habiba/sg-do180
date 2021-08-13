# Help
```
podman --help
```
# Login

```
podman login -u <username> -p <password>  <url>
```


# Search Image

```
podman search
```
## Example
```
podman search mysql
```

# Pull Imahge

```
podman pull <registy_url>/<folder>/<name>:<tag>
```

# List of images

```
podman images
```

```
podman image list
```

## help for podman images

```
podman images --h
```

# podman run | creates a container

- -d runs in the background
- --name sets the name
- -p expose ports to host machine
- -e sets env variables


# Run command inside container

```
podman exec -it <container name > sh
```

```
podman exec -it <container name > /bin/bash
```
# List of services

```
podman ps -a
```

# get log for conatiners

```
podman logs --tail=10 <container name>
```
# Inspect Running containers
```
podman inspect -l | grep <keyword>
```
## Example
```
podman inspect -l | grep IPAddress
```

**Note:** *Note: The -l is a convenience argument for latest container. You can also use the container’s ID or name instead of -l or the long argument --latest.*

# Viewing the container’s pids

```
podman top -l

```

# Viewing the container’s port

```
podman port -l
```

# Stop container

```
podman stop <container name>
```

# Remove containers
```
podman rm <container name>
```
# Remove images
```
podman rmi <image name>
```
# Save Image
```
sudo podman save  -o <filename>.tar <registry_url>/<folder>/<imagename>:<tag>
```


## Example
```
sudo podman save  -o mysql.tar registry.access.redhat.com/rhscl/mysql-57-rhel7:5.7
```
# Load image
```
sudo podman load [-i FILE_NAME]

```
## Example
```
sudo podman load -i mysql.tar
```

# Skopeo Inspect Image

```
skopeo inspect  docker://<registry_url>/<folder>/<name>:<tag>
```
