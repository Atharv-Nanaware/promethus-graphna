# Data Capture and Real-time Processing Pipeline

## Project Overview
This project implements an end-to-end data pipeline that extracts user data from a random API, processes it in real-time, and stores it in a distributed database. The pipeline uses Apache Airflow for orchestration, Apache Kafka for streaming, Apache Spark for distributed processing, and Apache Cassandra for storage.

## Architecture

```
Random User API → Airflow DAG → Kafka → Spark Streaming → Cassandra
                                 ↑          ↑             ↑
                                 ↓          ↓             ↓
                         Prometheus/Grafana Monitoring
```

## Components

### Data Extraction
- Airflow DAG extracts user data from the RandomUser API
- Data is formatted and transformed
- Transformed data is sent to Kafka topic

### Data Streaming
- Kafka topic "user_profile_stream" handles the real-time data flow
- Kafka UI provides a visual interface for monitoring topics and messages

### Data Processing
- Spark Streaming processes the data from Kafka in real-time
- Distributed processing enables scalable handling of high-volume data

### Data Storage
- Processed data is stored in Cassandra database
- Data is organized in the "spark_streaming.created_users" table

### Monitoring
- Prometheus collects metrics from all services
- Grafana provides visualizations of system and application metrics
- Custom dashboards for each component of the pipeline

## Agile Implementation

### Sprint Planning

#### Sprint 1: Infrastructure Setup
- [x] Set up Docker environment
- [x] Configure Airflow
- [x] Set up Kafka and Zookeeper
- [x] Set up Spark master and worker
- [x] Set up Cassandra database

#### Sprint 2: Data Pipeline Development
- [x] Implement data extraction from RandomUser API
- [x] Configure Kafka topics and producers
- [x] Implement Spark Streaming processing
- [x] Set up Cassandra schema and writes

#### Sprint 3: Monitoring Implementation
- [x] Set up Prometheus and exporters
- [x] Configure Grafana
- [x] Create dashboards for system monitoring
- [x] Create dashboards for Kafka monitoring
- [x] Create dashboards for Spark monitoring
- [x] Create dashboards for data pipeline monitoring

### Backlog (Future Enhancements)
- [ ] Implement data validation and error handling
- [ ] Add data quality monitoring
- [ ] Implement alerting for critical metrics
- [ ] Add unit and integration tests
- [ ] Implement CI/CD pipeline

## Getting Started

### Prerequisites
- Docker and Docker Compose
- Git

### Setup and Run

1. Clone the repository

2. Start the services
   ```bash
   docker-compose up -d
   ```

3. Access the interfaces:
   - Airflow: http://localhost:8080 (username: airflow, password: airflow)
   - Kafka UI: http://localhost:8085
   - Spark Master UI: http://localhost:9090
   - Prometheus: http://localhost:9091
   - Grafana: http://localhost:3000 (username: admin, password: admin)

## Monitoring

### Prometheus
Prometheus is used to collect metrics from all services in the pipeline. It scrapes metrics from:
- Node Exporter (system metrics)
- Kafka Exporter (Kafka metrics)
- Airflow metrics endpoints
- Spark metrics
- Cassandra metrics

### Grafana Dashboards

The following dashboards are available in Grafana:

1. **System Overview**: CPU, memory, disk usage, and network metrics
2. **Kafka Monitoring**: Message rates, topic offsets, consumer lag
3. **Spark Monitoring**: Application metrics, executor stats, job progress
4. **Data Pipeline**: End-to-end metrics, throughput, and latency

## Project Structure

```
./
├── dags/                   # Airflow DAG definitions
├── monitoring/             # Monitoring configuration
│   ├── grafana/            # Grafana configuration and dashboards
│   └── prometheus/         # Prometheus configuration
├── pipelines/              # Data pipeline code
├── plugins/                # Airflow plugins
├── script/                 # Utility scripts
├── docker-compose.yaml     # Docker Compose configuration
├── requirements.txt        # Python dependencies
├── spark_processing.py     # Spark Streaming code
└── README.md               # Project documentation
```

## Troubleshooting

### Common Issues
- **Services not starting**: Check Docker logs using `docker-compose logs [service_name]`
- **Kafka not receiving messages**: Verify producer configuration and network settings
- **Spark job failures**: Check Spark UI for detailed error messages

## Contributing
Contributions are welcome! Please follow the Agile methodology and create feature branches for new functionality.

1. Create a user story in the backlog
2. Plan your implementation in a sprint
3. Develop in small, testable increments
4. Submit a pull request with comprehensive testing
