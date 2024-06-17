# Session 82 Homework Kafka III

![alt text](<data/gb/Screenshot 2024-06-17 192156.png>)

Name: Gustian

Kelompok: A

Group: 3

# Kafka Bitcoin Price Streaming

This project demonstrates the use of Apache Kafka to stream Bitcoin price data from a CSV file into a Kafka topic and consume it. The setup involves Docker for running Kafka, Zookeeper, Schema Registry, and Control Center, along with Python scripts for producing and consuming messages.

## Prerequisites

- Docker and Docker Compose
- Python 3.x
- Pip

## Setup

1. **Clone the repository**:

   ```bash
   https://github.com/gustianmajs/Session-82-Homework-Kafka-III.git
   ```

2. **Install Python dependencies**:

   ```bash
   pip install -r requirements.txt
   ```

3. **Start the Kafka services using Docker Compose**:

   ```bash
   docker-compose up -d
   ```

   This will start the following services:

   - Zookeeper
   - Kafka Broker
   - Schema Registry
   - Control Center

![alt text](<data/gb/Screenshot 2024-06-17 192128.png>)

## Usage

### Run the Producer

The producer reads data from `data/bitcoin_price_Training.csv` and sends it to the Kafka topic `bitcoin_prices`.

```bash
python producer.py
```

### Run the Consumer

The consumer reads data from the Kafka topic `bitcoin_prices`.

```bash
python consumer.py
```

The consumer will continuously poll the Kafka topic and print the received messages.

## Docker Compose Services

- **Zookeeper**: Manages and coordinates the Kafka brokers.
- **Kafka Broker**: The Kafka server that handles message production and consumption.
- **Schema Registry**: Manages Avro schemas for Kafka topics, ensuring data compatibility.
- **Control Center**: A web interface to monitor and manage the Kafka cluster. Accessible at [http://localhost:9021](http://localhost:9021).
