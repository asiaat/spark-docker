# the base image is a trusted java build (https://registry.hub.docker.com/_/java/)
# FROM java:8

# MAINTAINER m.sioufy@anchormen.nl

FROM ubuntu:14.04


MAINTAINER m.sioufy@anchormen.nl


####installing [software-properties-common] so that we can use [apt-add-repository] to install Java8
RUN apt-get update -y \
&&  apt-get install software-properties-common -y \
&&  apt-add-repository ppa:webupd8team/java -y \
&&  apt-get update -y \

####automatically agreeing on oracle license agreement [for installing java]
&&  echo debconf shared/accepted-oracle-license-v1-1 select true | sudo debconf-set-selections \
&&  echo debconf shared/accepted-oracle-license-v1-1 seen true | sudo debconf-set-selections \

####installing java and supervisor
&&  apt-get install -y oracle-java8-installer \
    supervisor


####downloading & unpacking Spark 2.2.1 [prebuilt for Hadoop 2.6+ and scala 2.10]
RUN wget http://apache.mirror.triple-it.nl/spark/spark-2.2.1/spark-2.2.1-bin-hadoop2.7.tgz \
&&  tar -xzf spark-2.2.1-bin-hadoop2.7.tgz \
&&  mv spark-2.2.1-bin-hadoop2.7 /opt/spark


#####adding conf files [to be used by supervisord for running spark master/slave]
COPY master.conf /opt/conf/master.conf
COPY slave.conf /opt/conf/slave.conf


#######exposing port 8080 for spark master UI
EXPOSE 8080

#default command: running an interactive spark shell in the local mode
CMD ["/opt/spark/bin/spark-shell", "--master", "local[*]"]
