FROM xemuliam/zeppelin-base:0.8.0


ENV ZEPPELIN_HOME=/opt/zeppelin

COPY ./shiro.ini ${ZEPPELIN_HOME}/conf/shiro.ini

EXPOSE 8080 8443 

VOLUME     ${ZEPPELIN_HOME}/logs \
           ${ZEPPELIN_HOME}/notebook
WORKDIR    ${ZEPPELIN_HOME}

CMD        ./bin/zeppelin.sh run
