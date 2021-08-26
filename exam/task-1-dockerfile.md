Description
---
A Docker file is given
1. **/opt/jboss** directory is not created
2. User **jboss** is already created under 0 group
3. User **jboss** need to give access to the working directory
4. java is also installed
5. WORKING DIR is already set


ToDo
---
1. 2 Environment variable needs to be created *JBOSS_HOME* *JBOSS_VERSION*
2. Expose 3 different ports 8080, 9990 and 9999
3. there is a .zip file in the */home/desktop* directory that need to be copied in the image and extracted
4. run a .sh file in the JBOSS_HOME/bin
5. the commands in the .sh file has some argument those need to be passed as input.
6. build the Dockerfile with name acme_jboss

Solution
---
1. Prepare the Dockerfile
2. Build image
3. Check output

Prepare Dockerfile
---
```
# Use latest jboss/base-jdk:11 image as the base
FROM jboss/base-jdk:11

# Set the WILDFLY_VERSION env variable
ENV JBOSS_VERSION 24.0.7.Final

ENV JBOSS_HOME /opt/jboss/

USER root

# Add the WildFly distribution to /opt, and make wildfly the owner of the extracted tar content

ADD jboss.24.0.7.Final.zip ${JBOSS_HOME}
RUN unzip ${JBOSS_HOME}/jboss.24.0.7.Final.zip

# Make sure the distribution is available from a well-known place
RUN cd $HOME \
    && chown -R jboss:0 ${JBOSS_HOME} \
    && chmod -R g+rw ${JBOSS_HOME}


# Ensure signals are forwarded to the JVM process correctly for graceful shutdown
ENV LAUNCH_JBOSS_IN_BACKGROUND true

USER jboss

# Expose the ports in which we're interested
EXPOSE 8080
EXPOSE 9990
EXPOSE 9999

RUN /opt/jboss/wildfly/bin/add-user.sh admin Admin#70365 --silent

# Set the default command to run on boot
# This will boot WildFly in standalone mode and bind to all interfaces
CMD ["/opt/jboss/bin/standalone.sh", "-b", "0.0.0.0", "-bmanagement", "0.0.0.0"]
```

Build Docker File
---
```
podman build -t acme_jboss .
```

Check the result
---

```
podman images
```

Note
---
1. Copy the zip file to current directory and then use **ADD** command in the Dockerfile
2. Do not run the new image as that is the next task

Reference
---
1. https://github.com/jboss-dockerfiles/wildfly/blob/master/Dockerfile
2. https://github.com/Max-Jaeger/redhat-PE180-exam-tips
