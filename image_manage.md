
Find the listed registries on the machine
---
```
vim /etc/containers/registry.conf
```
- registry.access.redhat.com
- registry.redhat.io
- quay.io

Login to the registry_url
---
```
 podman login -u <username> -p <passwrod> registry.access.redhat.com
```
Search Image
---

```
 podman search mysql
```

Pull Image
----

```
 podman pull <image name>
```

Run Image
---


Change container content
---
```
podman exec -it <container name> sh
```

```
echo "Hello World" > /var/www/index/index.html
```
