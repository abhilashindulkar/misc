 helm install prometheus prometheus-community/kube-prometheus-stack

 kubectl patch service prometheus-grafana -p '{"spec": {"type": "LoadBalancer", "externalIPs":["IP"]}}'

  kubectl patch service prometheus-kube-prometheus-prometheus -p '{"spec": {"type": "LoadBalancer", "externalIPs":["IP"]}}'

  kubectl patch service prometheus-prometheus-node-exporter -p '{"spec": {"type": "LoadBalancer", "externalIPs":["IP"]}}'

  --------------------------------------------------------------------------------------------------------------------------

   helm install prometheus prometheus-community/kube-prometheus-stack -f prometheus.yml

----------------------------------------------------------------------------------------------------------------------------

wget https://repo1.maven.org/maven2/io/prometheus/jmx/jmx_prometheus_javaagent/0.15.0/jmx_prometheus_javaagent-0.15.0.jar  //jmx java-agent-jar

----------------------------------------------------------------------------------------------------------------------------
