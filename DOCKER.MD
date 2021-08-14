Example Docker
----
```
FROM <image name>
MAINTAINER <email>
ENV PORT 8080
RUN yum install -y httpd && yum clean all
EXPOSE ${PORT}
COPY ./src/ /var/www/index/index.html
CMD ["httpd" , "-D", "FOREGROUND"]
```
