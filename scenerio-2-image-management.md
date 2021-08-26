# Image managerment

## search for image 

```
sudo podman search rhel
```

## pull desired image 

podman pull registry/username/image:tag

```
sudo podman pull rhel
```

## view  local images
```
sudo podman images 
```

## view history of images
podman history <image:tag>
```
sudo podman history rhel:latest
```


## create an image from redhat image registry