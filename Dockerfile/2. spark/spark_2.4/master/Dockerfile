FROM openjdk11

MAINTAINER alexleethinker <alexleethinker@gmail.com> 

ENV MASTER "local[*]" 
ENV SPARK_HOME='/spark-2.4.3-bin-hadoop2.7' 

ADD spark-2.4.3-bin-hadoop2.7.tgz /

EXPOSE 8080 7077 6066

CMD /spark-2.4.3-bin-hadoop2.7/sbin/start-master.sh && bash
