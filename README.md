# Real-Time Cybersecurity Log & Threat Analytics Pipeline

A real-time cybersecurity log analytics pipeline built using **Java, Apache Kafka, PostgreSQL, and Apache Superset**.

## Project Overview

This project processes cybersecurity logs as real-time events. Apache Kafka is used to stream security logs, Java handles the Producer and Consumer logic, PostgreSQL stores the processed logs, and Apache Superset provides real-time visualization and analysis.

## Technologies Used

* Java
* Apache Kafka
* PostgreSQL
* Apache Superset
* SQL
* JSON

## Architecture

```text
Security Logs (CSV)
        ↓
   Kafka Producer
        ↓
   Apache Kafka
        ↓
   Kafka Consumer
        ↓
     PostgreSQL
        ↓
 Apache Superset
        ↓
Real-Time Dashboard
```

## Features

* Real-time security log streaming using Apache Kafka
* Java-based Kafka Producer and Consumer
* PostgreSQL database for storing security logs
* Real-time security event visualization
* Analysis of attack types and severity levels
* Identification of frequently occurring source IP addresses

## Kafka Configuration

Kafka topic:

```text
security_log_events
```

Partitions:

```text
3
```

The Kafka Producer reads security log records from a CSV file, converts them into JSON, and publishes them to the Kafka topic.

The Kafka Consumer subscribes to the topic, processes the incoming events, and inserts them into PostgreSQL.

## PostgreSQL

The consumed security logs are stored in a PostgreSQL database in a structured `security_logs` table.

The stored fields include:

* Log ID
* Event Time
* Source IP
* Destination IP
* Protocol
* Event Type
* Severity
* Attack Flag

## Dashboard

Apache Superset is used to visualize the processed cybersecurity data.

The dashboard provides:

* Security event distribution by severity
* Attack type frequency
* Top source IP addresses
* Real-time security log analysis

## How to Run

### 1. Start Apache Kafka

Make sure Kafka is running locally.

### 2. Create the Kafka Topic

Create the topic:

```text
security_log_events
```

with 3 partitions.

### 3. Configure PostgreSQL

Create the required database and `security_logs` table.

Update the PostgreSQL connection details in `SecurityLogConsumer.java`.

### 4. Run the Kafka Producer

Run:

```text
SecurityLogProducer.java
```

The Producer reads the CSV file and sends security log events to Kafka.

### 5. Run the Kafka Consumer

Run:

```text
SecurityLogConsumer.java
```

The Consumer reads events from Kafka and stores them in PostgreSQL.

### 6. Open Apache Superset

Connect Superset to the PostgreSQL database and create visualizations for the security logs.

## Project Outcome

The project demonstrates an end-to-end real-time data pipeline for cybersecurity log processing, from log ingestion and Kafka streaming to PostgreSQL storage and dashboard visualization.
