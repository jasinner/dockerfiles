FROM docker-registry.usersys.redhat.com:5000/cloud_enablement/jboss-eap:6.4
ADD standalone.conf /opt/eap/bin/
ADD cve.war /opt/eap/standalone/deployments/
CMD ["/opt/eap/bin/standalone.sh", "-b", "0.0.0.0"]
EXPOSE 8080

