# base image
FROM java:openjdk-8-jdk
# define spark and hadoop versions
ENV HADOOP_VERSION 2.7.7
ENV SPARK_VERSION 2.4.0

# download and install hadoop
RUN mkdir -p /opt && \
    cd /opt && \
    curl https://mirror.tuna.tsinghua.edu.cn/apache/hadoop/common/hadoop-${HADOOP_VERSION}/hadoop-${HADOOP_VERSION}.tar.gz | tar -zx && \
    ln -s hadoop-${HADOOP_VERSION} hadoop && \
    echo Hadoop ${HADOOP_VERSION} native libraries installed in /opt/hadoop/lib/native

# download and install spark
RUN mkdir -p /opt && \
    cd /opt && \
    curl  https://mirror.tuna.tsinghua.edu.cn/apache/spark/spark-${SPARK_VERSION}/spark-${SPARK_VERSION}-bin-hadoop2.7.tgz | tar -zx && \
    ln -s spark-${SPARK_VERSION}-bin-hadoop2.7 spark && \
    echo Spark ${SPARK_VERSION} installed in /opt

# add scripts and update spark default config
ADD common.sh spark-master spark-worker /
ADD spark-defaults.conf /opt/spark/conf/spark-defaults.conf
ENV PATH $PATH:/opt/spark/bin
