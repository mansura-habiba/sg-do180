Description
---
Use the image created in first task.
1. tag the new image
2. publish the image to a private registry
3. save the image in the .tar file
4. create contaienr from image


Solution
---
1. tag the new image
```
podman tag localhost/jboss_acme acme:8080/jboss_acme:7.2
```


2. publish the image to a private registry

```
podman push localhost/jboss_acme acme:8080/jboss_acme:7.2
```

3. save the image in the .tar file

```
podman save acme:8080/jboss_acme:7.2 > jboss_acme_7.2.gz
```

4. Load image

```
podman load -i jboss_acme_7.2.gz
```

Reference
---
                                                                                                                                use podman --help
