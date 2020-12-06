# Use the httpd-parent image as base
FROM quay.io/redhattraining/httpd-parent

LABEL io.k8s.description="A basic Apache HTTP Server child image, uses ONBUILD" \
      io.k8s.display-name="Apache HTTP Server" \
      io.openshift.expose-services="8080:http" \
      io.openshift.tags="apache, httpd"

RUN subscription-manager repos --enable rhel-7-server-optional-rpms --enable rhel-server-rhscl-7-rpms && \
    yum -y install @development && \
    yum -y install rh-python36 && \
    yum clean all

RUN sed -i "s/Listen 80/Listen 8080/g" /etc/httpd/conf/httpd.conf && \
    chgrp -R 0 /var/log/httpd /var/run/httpd && \
    chmod -R g=u /var/log/httpd /var/run/httpd

USER 1001

EXPOSE 8080



