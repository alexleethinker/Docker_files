FROM sparkling-water:2.4

MAINTAINER alexleethinker <alexleethinker@gmail.com> 

ENV MASTER "local[*]" 
ENV SPARK_HOME='/spark-2.4.3-bin-hadoop2.7' 

RUN apt-get -y update && \
    apt-get -y install curl acl git nginx zip python2.7 libpython2.7 libgfortran3 libgomp1 locales make liblapack-dev build-essential mongodb-clients && \
    locale-gen en_US.UTF-8 && \
    groupadd -r dataiku && \
    useradd -r -m -s /bin/bash -g dataiku dataiku

COPY dataiku-dss-5.1.4.tar.gz /tmp/dataiku-dss.tar.gz

RUN su - dataiku -c '/bin/tar xzf /tmp/dataiku-dss.tar.gz -C /home/dataiku --strip-components=1' \
 && rm /tmp/dataiku-dss.tar.gz \
 && mkdir -p /var/lib/dataiku \
 && mkdir -p /etc/dataiku \
 && mkdir -p /var/cache/dataiku \
 && chown -R dataiku:dataiku /var/lib/dataiku \
 && chown -R dataiku:dataiku /spark-2.4.3-bin-hadoop2.7 \
 && chown -R dataiku:dataiku /sparkling-water \
 && apt-get -y autoremove \
 && apt-get clean \
 && rm -rf /var/lib/apt/lists/* \
 && rm -f /var/lib/dpkg/info/* \
 && rm -f /var/cache/debconf/* \
 && rm -rf /tmp/* 

USER dataiku
RUN /home/dataiku/installer.sh -d /var/lib/dataiku -p 11000 
RUN /var/lib/dataiku/bin/dssadmin install-spark-integration -sparkHome /spark-2.4.3-bin-hadoop2.7 && \
    /var/lib/dataiku/bin/dssadmin install-h2o-integration -sparklingWaterDir /sparkling-water 


# ENTRYPOINT ["/var/lib/dataiku/bin/dss", "start", "&&","bash"]
CMD /var/lib/dataiku/bin/dss start && bash
