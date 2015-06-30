FROM docker-registry.usersys.redhat.com:5000/jshepher/rhel71
RUN ["yum", "install", "-y", "java-1.8.0-openjdk"]
RUN ["yum", "install", "-y", "unzip"]
RUN ["yum", "clean", "all"]
RUN mkdir /opt/jws
WORKDIR /opt/jws
RUN ["curl", "http://download.bne.redhat.com/released/JBossEWS/3.0.0/jws-application-servers-3.0.0-RHEL7-x86_64.zip", "-o", "jws-application-servers-3.0.0-RHEL7-x86_64.zip"]
RUN ["unzip", "jws-application-servers-3.0.0-RHEL7-x86_64.zip"]
EXPOSE 8080

