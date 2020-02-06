FROM centos:latest
#ADD centos-8-container.tar.xz /

LABEL org.label-schema.schema-version="1.0" \
    org.label-schema.name="CentOS Base Image" \
    org.label-schema.vendor="CentOS" \
    org.label-schema.license="GPLv2" \
    org.label-schema.build-date="20190927"

RUN echo "proxy=http://160.62.237.218:2011" >>/etc/yum.conf
RUN yum install epel-release -y; yum install python3-argcomplete.noarch ansible.noarch python3-pip -y
RUN pip3 --proxy http://160.62.237.218:2011 install awscli
RUN curl -x http://160.62.237.218:2011 -LO https://storage.googleapis.com/kubernetes-release/release/v1.17.0/bin/linux/amd64/kubectl
RUN chmod 755 kubectl; mv kubectl /usr/local/bin
RUN cd /tmp 
RUN curl -LO -x http://160.62.237.218:2011 https://get.helm.sh/helm-v3.0.3-linux-amd64.tar.gz; tar zxvf helm*
RUN mv linux-amd64/helm /usr/local/bin

CMD ["/bin/bash"]
