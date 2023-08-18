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
podman search nginx
```

## start

```
podman run -d --name mynginx <registry url>/<location>/<image name>:<tag>
```
### Example 

```
podman run -d --name mynginx  bitnami/nginx
```


![image](https://user-images.githubusercontent.com/26741425/129452905-6aa0ca1f-c3f5-4347-801b-082178a87c65.png)


# Add the file /tmp/hello, and ensure the changes to the image are saved

## check container is running

```
podman ps -a
```

## open interactive terminal

```
podman exec -it mynginx sh
```

```
echo "Hello" > /tmp/hello
```
![image](https://user-images.githubusercontent.com/26741425/129452921-c1636cad-d86f-477b-87bf-13c541313c90.png)

# Commit the changes in the image

```
podman commit <old image name>:<old image tag> <new image name>:<new image tag> 
```
## Example
```
podman commit -a <name> mynginx localhost://mynginx:v1.0
```

![image](https://user-images.githubusercontent.com/26741425/129452948-cc63b73f-74ef-4672-9e8c-0b379d57780a.png)




# save the modified image to a tar archive

```
podman save -o <tar file> localhost://mynginx:v1.0
```

```
podman save > <tar file> localhost://mynginx:v1.0
```

![image](https://user-images.githubusercontent.com/26741425/129452985-4fdb9235-9f7e-464e-9810-8d23548c2b44.png)


## help
![image](https://user-images.githubusercontent.com/26741425/129452974-d8737cc1-e32e-4125-9ecd-dbc21e80ac34.png)



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
pdoman load -i <tar file>
```
![image](https://user-images.githubusercontent.com/26741425/129453027-2a2e3cf3-afa1-47c3-9b85-3f8e1322f9d5.png)

## load help
![image](https://user-images.githubusercontent.com/26741425/129453013-ba3e5988-a490-4109-b425-6072c97a73d1.png)


# Create container from new image
## get the new image name 

```
podman images
```
Copy image name for next command 
```
podman run -d --name mynginx-2 <local new image name>
```
![image](https://user-images.githubusercontent.com/26741425/129453044-8ea1ba03-4c3c-4489-982d-e845d5e0c5c4.png)
