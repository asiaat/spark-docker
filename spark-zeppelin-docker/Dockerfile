FROM apache/zeppelin:0.7.3

RUN wget https://www-eu.apache.org/dist/spark/spark-2.4.0/spark-2.4.0-bin-hadoop2.7.tgz \
&&  tar -xzf spark-2.4.0-bin-hadoop2.7.tgz \
&&  mv spark-2.4.0-bin-hadoop2.7 /opt/spark

ENV SPARK_HOME=/opt/spark

