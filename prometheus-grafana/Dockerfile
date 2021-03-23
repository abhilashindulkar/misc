FROM tomcat

RUN mkdir -p /home/data

COPY jmx_prometheus_javaagent-0.15.0.jar /home/data/jmx_prometheus_javaagent-0.15.0.jar

ADD prometheus-jmx-config.yaml /home/data/prometheus-jmx-config.yaml

EXPOSE 8080
ENV TOMCAT_HOME=/usr/local/tomcat
CMD java -javaagent:/home/data/jmx_prometheus_javaagent-0.15.0.jar=8081:/home/data/prometheus-jmx-config.yaml -jar $TOMCAT_HOME/start.jar