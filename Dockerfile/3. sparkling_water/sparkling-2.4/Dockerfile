FROM spark-master:2.4

MAINTAINER alexleethinker <alexleethinker@gmail.com> 

ENV MASTER "local[*]" 
ENV SPARK_HOME='/spark-2.4.3-bin-hadoop2.7' 

ADD sparkling-water-2.4.13 /sparkling-water 

CMD /sparkling-water/bin/run-sparkling.sh
