FROM centos:7

LABEL org.label-schema.schema-version="1.0" \
    org.label-schema.name="CentOS Base Image" \
    org.label-schema.vendor="CentOS" \
    org.label-schema.license="GPLv2" \
    org.label-schema.build-date="20190305"
  RUN yum install -y gcc gcc++ tar make.x86_64 gnutls-c++.x86_64 

  COPY /SOURCES/* /
  RUN pwd; ls
  RUN tar zxvf /nginx-1.16.0.tar.gz
  RUN tar zxvf /pcre-8.43.tar.gz
  RUN tar zxvf /zlib-1.2.11.tar.gz
  RUN tar zxvf /openssl-1.1.1.tar.gz

  RUN cd /nginx-1.16.0; ./configure \
    --with-http_ssl_module \
    --with-openssl=/openssl-1.1.1 \
    --with-pcre=/pcre-8.43 \
    --with-zlib=/zlib-1.2.11 && make && make install
    


CMD ["/bin/bash"]
