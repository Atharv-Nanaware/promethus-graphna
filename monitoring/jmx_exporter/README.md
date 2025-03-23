# JMX Exporter Setup for Cassandra

To complete the JMX exporter setup, please follow these steps:

1. Download the JMX Prometheus Java Agent JAR file:
   - Go to: https://repo1.maven.org/maven2/io/prometheus/jmx/jmx_prometheus_javaagent/0.19.0/
   - Download: `jmx_prometheus_javaagent-0.19.0.jar`
   - Save it in this directory as `jmx_prometheus_javaagent.jar`

2. Make sure the file permissions are correct:
   ```bash
   chmod 644 jmx_prometheus_javaagent.jar
   ```

3. The Cassandra configuration `cassandra.yml` has already been created in this directory.

Once these steps are completed, restart your containers with `docker-compose down` and `docker-compose up -d`.
