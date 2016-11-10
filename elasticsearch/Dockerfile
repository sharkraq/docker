FROM oraclelinux:latest

RUN  yum install net-tools tar java-1.8.0-openjdk.x86_64 -y \
&& yum clean all

RUN curl https://download.elastic.co/elasticsearch/release/org/elasticsearch/distribution/tar/elasticsearch/2.4.1/elasticsearch-2.4.1.tar.gz|tar zx; mv elasticsearch* /etc/elasticsearch

RUN /etc/elasticsearch/bin/plugin install mobz/elasticsearch-head; /etc/elasticsearch/bin/plugin install royrusso/elasticsearch-HQ

RUN useradd elasticsearch; chown -R elasticsearch:elasticsearch /etc/elasticsearch

ENV PATH=$PATH:/etc/elasticsearch/bin

ENV JAVA_HOME  /usr/lib/jvm/jre-1.8.0

ENV ES_HOME	/etc/elasticsearch

ENV ES_USER	elasticsearch

###Sets memory allocated to els
ENV ES_HEAP_SIZE 1g

###Expose port
EXPOSE 9200 9300

CMD ["elasticsearch", "--network.host=0.0.0.0"]
