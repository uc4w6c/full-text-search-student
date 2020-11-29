From openjdk:14.0.1

ARG SOLR_VER=8.7.0
ENV PATH $PATH:/usr/local/src/solr-${SOLR_VER}/bin

WORKDIR /usr/local/src
RUN curl -OL http://ftp.meisei-u.ac.jp/mirror/apache/dist/lucene/solr/${SOLR_VER}/solr-${SOLR_VER}.tgz
RUN tar zxvf solr-${SOLR_VER}.tgz

RUN yum install -y procps

WORKDIR /usr/local/src/solr-${SOLR_VER}
# ENTRYPOINT ["solr", "start", "-f", "-force"]

