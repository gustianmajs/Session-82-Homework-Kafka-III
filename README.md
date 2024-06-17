# Session 82 Homework Kafka III

![alt text](<data/gb/Screenshot 2024-06-17 192156.png>)

Name: Gustian

Kelompok: A

Group: 3

### README.md

```markdown
# Kafka Bitcoin Price Streaming

This project demonstrates the use of Apache Kafka to stream Bitcoin price data from a CSV file into a Kafka topic and consume it. The setup involves Docker for running Kafka, Zookeeper, Schema Registry, and Control Center, along with Python scripts for producing and consuming messages.

## Table of Contents

- [Project Structure](#project-structure)
- [Prerequisites](#prerequisites)
- [Setup](#setup)
- [Avro Schemas](#avro-schemas)
  - [Bitcoin Price Key Schema](#bitcoin-price-key-schema)
  - [Bitcoin Price Value Schema](#bitcoin-price-value-schema)
- [Usage](#usage)
  - [Run the Producer](#run-the-producer)
  - [Run the Consumer](#run-the-consumer)
- [Docker Compose Services](#docker-compose-services)
- [Contributing](#contributing)
- [License](#license)

## Project Structure
```

|- data
| |- bitcoin_price_Training.csv
| |- rides.csv
|- docker-compose.yml
|- consumer.py
|- producer.py
|- requirements.txt
|- taxi_ride_key.avsc
|- taxi_ride_value.avsc
|- bitcoin_price_key.avsc
|- bitcoin_price_value.avsc

````

## Prerequisites

- Docker and Docker Compose
- Python 3.x
- Pip

## Setup

1. **Clone the repository**:

   ```bash
   git clone https://github.com/yourusername/kafka-bitcoin-price-streaming.git
   cd kafka-bitcoin-price-streaming
````

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

## Avro Schemas

To ensure data consistency and compatibility between producers and consumers, we use Avro schemas.

### Bitcoin Price Key Schema

`bitcoin_price_key.avsc`

```json
{
  "namespace": "com.bagas.bitcoin",
  "type": "record",
  "name": "BitcoinPriceKey",
  "fields": [
    {
      "name": "date",
      "type": "string"
    }
  ]
}
```

### Bitcoin Price Value Schema

`bitcoin_price_value.avsc`

```json
{
  "namespace": "com.bagas.bitcoin",
  "type": "record",
  "name": "BitcoinPrice",
  "fields": [
    {
      "name": "date",
      "type": "string"
    },
    {
      "name": "open",
      "type": "float"
    },
    {
      "name": "high",
      "type": "float"
    },
    {
      "name": "low",
      "type": "float"
    },
    {
      "name": "close",
      "type": "float"
    },
    {
      "name": "volume",
      "type": "string"
    },
    {
      "name": "marketCap",
      "type": "string"
    }
  ]
}
```

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
