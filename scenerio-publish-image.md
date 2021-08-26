# Scenrio-3:Publish image after chages

## run image
sudo podman run --name <image_name> -d -p port1:port2 -e VAR1=value1 <registryname>/<imagename>:<tag>
```
sudo podman run --name httpd-real -d -p 8080:80 redhattraining/httpd-parent
```

## view images
```
sudo podman images
```

## exec images
sudo podman exec -it <imagename> /bin/bash

```
sudo podman exec -it httpd-real /bin/bash
```

# change the image content

```
echo "Hello HTTPD!" > /var/www/html/index.html

```

# exit the conatiner
```
exit
```

##check if the chnages

```
curl 127.0.01:8080
```

# view differences in the new version
```
sudo podman diff httpd-real
```

# stop the images
```
sudo podman stop httpd-real
```

## commit locally the changes

sudo podman --author <authorName> <original_image_name> <new_image_name>

```
sudo podman commit --author Jhon Doe httpd-real httpd-custom
```

## tag image
sudo podman tag <new_image_name>  <registryurl>/<username>/<new_image_name>:<tag>

```
sudo podman tag httpd-custom  quay.io/johndoe/httpd-custom:v1.0
```

# publish the image 

sudo podman  push <registry>/<username>/<image>:<tag>

```sudo podman push quay.io/johndoe/httpd-custom:v1.0
```
