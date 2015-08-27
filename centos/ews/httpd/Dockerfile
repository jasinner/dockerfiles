#################################################################
# Creates a base CentOS 6 image with JBoss Fuse
#
#                    ##        .
#              ## ## ##       ==
#           ## ## ## ##      ===
#       /""""""""""""""""\___/ ===
#  ~~~ {~~ ~~~~ ~~~ ~~~~ ~~ ~ /  ===- ~~~
#       \______ o          __/
#         \    \        __/
#          \____\______/
#
# Author:    Paolo Antinori <paolo.antinori@gmail.com>
# License:   MIT
#################################################################

FROM centos:centos6

MAINTAINER Jason Shepherd <jason@jasonshepherd.net>

# Installing prerequisites from https://access.redhat.com/documentation/en-US/Red_Hat_JBoss_Web_Server/2.1/html/Installation_Guide/ZIP_Installation_Prerequisites1.html
RUN yum install -y mailcap httpd22 httpd-devel mod_auth_kerb-eap6 apr-util-ldap krb5-workstation elinks && \
    yum install -y wget unzip hostname && \
    yum clean all -y

# download & Install EWS 2.1 ZIP Binary
WORKDIR /opt
RUN wget http://download.devel.redhat.com/released/JBossEWS/2.1.0/jboss-ews-httpd-2.1.0-RHEL6-x86_64.zip && \
    unzip jboss-ews-httpd-2.1.0-RHEL6-x86_64.zip

# add a user for the HTTPD
WORKDIR jboss-ews-2.1
RUN chown -R apache:apache httpd

# disable HTTPS & AUTH_KERB 
WORKDIR httpd/conf.d
RUN mv ssl.conf ssl.conf.disabled ; mv auth_kerb.conf auth_kerb.disabled

# run postinstall script
WORKDIR /opt/jboss-ews-2.1/httpd
RUN ./.postinstall

# Create a homepage
RUN echo "<html><body>helloWorld</body></html>" > www/html/index.html

# TODO: makes this an abstract EWS image 
# onbuild instructions are invoked only while building another image that inherits from this one.
#ONBUILD ADD . /root/
#ONBUILD RUN unzip -q -d /opt/rh /root/*.zip && \
#            rm /root/*.zip && \
#            sed -i "s/#admin/admin/" /opt/rh/*/etc/users.properties && \
#            chown -R fuse:fuse /opt/rh
#CMD echo "This is just an abstract image that provides java and ssh. You need to build your own JBoss Fuse image. See here: https://github.com/paoloantinori/dockerfiles/edit/master/centos/fuse/README.md"i

CMD su -m -c "./sbin/apachectl -D FOREGROUND"

# declaring exposed ports. helpful for non Linux hosts. add "-P" flag to your "docker run" command to automatically expose them and "docker ps" to discover them.
EXPOSE 80 
