Description
---
Task 5 is about Dockerfile. Create a Dockerfile that will start a network scan on the local network using the Linux command nmap -sn 172.17.0.0, you may replace it with any network that works for you, ensure that this container image is built on a minimal RHEL-based container image, and also make sure that the container image provides the ip, ps, and ping utilities for troubleshooting.

```
FROM ubi8

MANINTAINER <name> <email>

DESCRIPTION 'will start a network scan on the local network using the Linux command nmap -sn 172.17.0.0'


RUN yum install -y nmap && yum install -y bash && yum install -y iputils && yum install -y iproute && yum install -y procps-ng && yum clean all

CMD ["nmap", "-sn" , "172.17.0.0/24"]

```


# Build 
```
podman build -h
```

![image](https://user-images.githubusercontent.com/26741425/129453439-0f0e0960-3387-46a5-b005-2108c14222c8.png)

```
podman build -t <imagename> .
```

## Check 

```
podman images
```

# Run 

```
podman run -d --name <container name> localhost://<image name>
```


