FROM centos:latest
#ADD centos-8-container.tar.xz /

LABEL org.label-schema.schema-version="1.0" \
    org.label-schema.name="CentOS Base Image" \
    org.label-schema.vendor="CentOS" \
    org.label-schema.license="GPLv2" \
    org.label-schema.build-date="20190927"

RUN echo "proxy=http://160.62.237.218:2011" >>/etc/yum.conf
RUN echo "export HTTP_PROXY=http://160.62.237.218:2011">>/etc/environment
RUN yum install epel-release -y; yum install python3-argcomplete.noarch ansible.noarch python3-pip unzip groff-base.x86_64 python3-boto3.noarch python3-botocore.noarch -y
RUN pip3 --proxy http://160.62.237.218:2011 install boto 
RUN curl -x http://160.62.237.218:2011 "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"; unzip awscliv2.zip; ./aws/install
RUN curl -o kubectl https://amazon-eks.s3-us-west-2.amazonaws.com/1.14.6/2019-08-22/bin/linux/amd64/kubectl; chmod 755 kubectl; mv kubectl /usr/local/bin
RUN curl -x http://160.62.237.218:2011 --location "https://get.helm.sh/helm-v3.0.3-linux-amd64.tar.gz" | tar xz -C /tmp; mv /tmp/linux-amd64/helm /usr/local/bin
RUN curl -x http://160.62.237.218:2011 --location "https://github.com/weaveworks/eksctl/releases/download/latest_release/eksctl_$(uname -s)_amd64.tar.gz" | tar xz -C /usr/local/bin
RUN curl -x http://160.62.237.218:2011 -o aws-iam-authenticator https://amazon-eks.s3-us-west-2.amazonaws.com/1.14.6/2019-08-22/bin/linux/amd64/aws-iam-authenticator; \
chmod +x aws-iam-authenticator; mv aws-iam-authenticator /usr/local/bin

CMD ["/bin/bash"]
