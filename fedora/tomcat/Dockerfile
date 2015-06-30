FROM docker.io/fedora
RUN ["dnf", "-y", "install", "tomcat"]
RUN ["dnf", "clean", "all"]
ADD tomcat.conf /etc/tomcat/
CMD ["/usr/libexec/tomcat/server", "start"]
EXPOSE 8080

