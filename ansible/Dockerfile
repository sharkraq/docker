FROM centos:latest
#ADD centos-8-container.tar.xz /

LABEL org.label-schema.schema-version="1.0" \
    org.label-schema.name="CentOS Base Image" \
    org.label-schema.vendor="CentOS" \
    org.label-schema.license="GPLv2" \
    org.label-schema.build-date="20190927"

RUN echo "proxy=http://160.62.237.218:2011" >>/etc/yum.conf
RUN yum install epel-release -y; yum install python3-argcomplete.noarch ansible-2.8.5-2.el8.noarch -y

CMD ["/bin/bash"]