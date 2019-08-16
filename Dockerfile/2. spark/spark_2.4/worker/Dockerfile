FROM spark-master:2.4

ENV SPARK_MASTER=spark://spark-master:7077
EXPOSE 8081

CMD /spark-2.4.3-bin-hadoop2.7/sbin/start-slave.sh $SPARK_MASTER && bash
