FROM dataiku

USER root

WORKDIR /
RUN git clone https://github.com/wolfcw/libfaketime.git
WORKDIR /libfaketime/src
RUN apt-get -y update && \
    apt-get -y install build-essential && \
    make install

ENV LD_PRELOAD=/usr/local/lib/faketime/libfaketime.so.1
ENV FAKETIME="@2018-06-07 20:30:00"
RUN chmod -R 777 /usr/local/lib/faketime/libfaketime.so.1 && \
    chown -R dataiku:dataiku /usr/local/lib/faketime/libfaketime.so.1


USER dataiku
COPY license.json /var/lib/dataiku/config


