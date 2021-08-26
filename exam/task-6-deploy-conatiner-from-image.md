Description
---
An image is available in public registry for mariadb. A container needs to be created for that
Host directory is also created.


Solution
---

1. searcg the image

```
podman search mariadb
```

2. pull the image

```
podman pull docker:8080/mariadb
```

3. check if the image is downloaded correctrly

```
podman images
```

4. open the corresponding .sh file and write the command in it


```
podman run -d wordpress -e WORDPRESS_DATABASE=blogs --pod wordpresspod
```

Reference
---
