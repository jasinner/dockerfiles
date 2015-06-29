FROM docker-registry.usersys.redhat.com:5000/jshepher/rhel6
RUN ["/usr/bin/yum", "install", "-y", "tomcat6"]
COPY tomcat6 /usr/sbin/
ENV CATALINA_BASE "/usr/share/tomcat6"
ENV CATALINA_HOME "/usr/share/tomcat6"
ENV JASPER_HOME "/usr/share/tomcat6"
ENV CATALINA_TMPDIR "/var/cache/tomcat6/temp"
ENV JAVA_OPTS "-Djavax.sql.DataSource.Factory=org.apache.commons.dbcp.BasicDataSourceFactory"
ENV TOMCAT_USER "tomcat"
ENV SECURITY_MANAGER "false"
ENV SHUTDOWN_WAIT "0"
ENV SHUTDOWN_VERBOSE false
ENV CATALINA_PID "/var/run/tomcat6.pid"
RUN ["/bin/chmod", "+x", "/usr/sbin/tomcat6"]
CMD ["/usr/sbin/tomcat6", "start"] 
EXPOSE 8080

