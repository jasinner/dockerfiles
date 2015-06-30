FROM docker-registry.usersys.redhat.com:5000/jshepher/rhel71
RUN ["yum", "install", "-y", "java-1.7.0-openjdk"]
RUN ["yum", "install", "-y", "unzip"]
RUN ["mkdir", "/opt/eap/"]
RUN ["cd", "/opt/eap"]
RUN ["curl", "-o", "jboss-eap-6.4.1-full-build.zip", "http://download.bne.redhat.com/released/JBEAP-6/6.4.1/jboss-eap-6.4.1-full-build.zip"]
RUN ["unzip", "-d", "/opt/eap/", "jboss-eap-6.4.1-full-build.zip"]
CMD ["/opt/eap/jboss-eap-6.4/bin/standalone.sh", "-b", "0.0.0.0"]
EXPOSE 8080

