FROM molab/hadoop

RUN apt-get update && apt-get install -y curl && \
    curl -s http://ftp.unicamp.br/pub/apache/spark/spark-2.2.1/spark-2.2.1-bin-hadoop2.7.tgz | tar -xz -C /usr/local/ && \
    apt-get remove -y curl
RUN cd /usr/local && ln -s spark-2.2.1-bin-hadoop2.7 spark
ENV SPARK_HOME /usr/local/spark

ENV YARN_CONF_DIR $HADOOP_HOME/etc/hadoop
ENV PATH $PATH:$SPARK_HOME/bin:$HADOOP_HOME/bin

RUN echo spark.yarn.jar hdfs:///spark/spark-assembly-2.2.1-hadoop2.7.jar > $SPARK_HOME/conf/spark-defaults.conf

ADD bootstrap.sh /bootstrap.sh
RUN chmod +x /bootstrap.sh

ENTRYPOINT [ "/bootstrap.sh" ]
