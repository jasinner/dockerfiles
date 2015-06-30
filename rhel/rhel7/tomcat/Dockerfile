FROM docker-registry.usersys.redhat.com:5000/jshepher/rhel71
RUN ["yum", "-y", "install", "tomcat"]
RUN ["yum", "clean", "all"]
ADD tomcat.conf /etc/tomcat/
CMD ["/usr/libexec/tomcat/server", "start"]
EXPOSE 8080

