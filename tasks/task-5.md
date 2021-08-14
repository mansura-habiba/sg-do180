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


``
