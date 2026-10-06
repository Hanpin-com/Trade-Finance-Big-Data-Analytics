# Trade Finance Big Data Analytics Platform

An end-to-end Big Data analytics project that simulates Trade Finance transactions and processes them through batch analytics, real-time streaming, machine learning, and business visualization.

The project demonstrates how Hadoop, Spark, Kafka, Hive, HBase, Python, and Power BI can work together to support transaction monitoring, risk analysis, operational reporting, and data-driven decision making.

---

## Project Overview

Trade Finance involves large volumes of transaction, document, shipment, payment, and compliance data.

This project simulates a Trade Finance environment and builds a data pipeline that can process and analyze information from different stages of the transaction lifecycle.

The platform supports:

- Batch data processing
- Real-time event streaming
- Distributed data storage
- SQL-based analytics
- Machine learning
- Business visualization and reporting

---

## Technology Stack

| Area | Technologies |
|---|---|
| Programming | Python |
| Big Data | Hadoop, HDFS, Spark |
| Streaming | Apache Kafka |
| Data Warehouse | Apache Hive |
| NoSQL Database | Apache HBase |
| Machine Learning | scikit-learn, statsmodels |
| Business Intelligence | Power BI |
| Environment | Docker |

---

## System Architecture

```text
Synthetic Trade Finance Data
            |
            v
       Data Generator
            |
            v
          Kafka
     Real-Time Events
            |
      +-----+------+
      |            |
      v            v
 Spark Streaming   HBase
      |            |
      v            |
 Hadoop / HDFS     |
      |            |
      v            |
     Hive <--------+
      |
      v
Machine Learning
      |
      v
Analytics Results
      |
      v
Power BI Dashboard
```

The architecture combines historical analytics, real-time processing, machine learning, and business intelligence within the same Trade Finance environment.

---

## Simulated Trade Finance Data

The project generates synthetic Trade Finance lifecycle events including:

- Letters of Credit
- Guarantees
- Documentary Collections
- Documents and discrepancies
- Shipments
- Payments
- Compliance screening
- Sanctions screening
- Credit and limit checks
- Foreign exchange reference rates

Synthetic data is used so the project can demonstrate realistic financial workflows without using real customer information.

---

## Batch Analytics

Historical Trade Finance data is processed using Hadoop, HDFS, Hive, and HBase.

The batch workflow includes:

- Hadoop Streaming transaction aggregation
- Historical analysis using Hive
- Hive-to-HBase analytical views
- CAD-normalized exposure reporting
- HBase PUT, GET, and SCAN operations

Example scripts:

```bash
bash scripts/trade-finance/run-mapreduce.sh
bash scripts/trade-finance/run-hive-analytics.sh
bash scripts/trade-finance/hbase-operations.sh
```

---

## Real-Time Streaming

Apache Kafka is used to simulate real-time Trade Finance events.

The event producer automatically creates the required Trade Finance Kafka topics and publishes transaction lifecycle events.

Streaming data can then be processed for near real-time monitoring and analytics.

This demonstrates how financial institutions could monitor changing transaction conditions instead of relying only on historical batch reports.

---

## Hive Analytics

Hive provides SQL-based access to historical Trade Finance data.

It is used for analytical tasks such as:

- Transaction aggregation
- Exposure analysis
- Historical transaction analysis
- Risk-related reporting
- Operational analysis

Hive allows large distributed datasets to be analyzed using SQL-style queries.

---

## HBase

HBase is used as the distributed NoSQL storage layer for Trade Finance analytical data and machine learning outputs.

The project demonstrates:

- HBase table creation
- Row-key design
- PUT operations
- GET operations
- SCAN operations
- Storage of analytical results

Machine learning outputs are written to the `trade_ml_results` table.

---

## Machine Learning

The project includes several machine learning use cases.

### Transaction Anomaly Detection

**Model:** Isolation Forest

Used to identify transactions with unusual characteristics that may require further review.

### Documentary Discrepancy Prediction

**Model:** Random Forest Classification

Used to estimate whether a Trade Finance transaction may contain documentary discrepancies.

### Processing Delay Prediction

**Models:** Random Forest Classification and Regression

Used to identify transactions that may experience processing delays and estimate delay-related outcomes.

### Trade Volume Forecasting

**Model:** Holt-Winters / Exponential Smoothing

Used to estimate future monthly Trade Finance transaction volumes based on historical patterns.

Machine learning results are stored in HBase and can also be published through Kafka topics.

---

## Business Visualization

Power BI is used to transform analytical outputs into business-focused dashboards.

The visualization layer is designed to make Big Data and machine learning results easier for business users to understand.

The dashboards can visualize:

- Transaction volume
- Trade value and exposure
- High-risk transactions
- Transaction anomalies
- Documentary discrepancies
- Processing delays
- Trade activity by country or region
- Product-level transaction activity
- Monthly transaction trends
- Forecasted trade volume

### Example Business Questions

The visualization layer can help answer questions such as:

- How is Trade Finance transaction volume changing over time?
- Which transactions may require additional risk review?
- Which regions or products have the highest exposure?
- Where are processing delays occurring?
- Are documentary discrepancies increasing?
- What transaction patterns appear unusual?
- What is the expected future trade volume?

### Dashboard Preview

Power BI dashboard screenshots will be added as the portfolio version of the project is updated.

---

## Business Value

### Risk Monitoring

Identify unusual or potentially high-risk transactions using analytical and machine learning techniques.

### Operational Monitoring

Track transaction activity, processing delays, and workflow performance.

### Historical Analysis

Use Hadoop, Hive, and HBase to analyze large volumes of transaction data.

### Real-Time Monitoring

Use Kafka and Spark-based processing to analyze continuously generated transaction events.

### Decision Support

Use Power BI dashboards to turn technical analytical outputs into information that business users can interpret quickly.

---

## Project Structure

```text
Trade-Finance-Big-Data-Analytics/
│
├── config/
├── data/
├── docker/
├── docs/
├── mapreduce/
├── member1/
├── powerbi/
├── scripts/
├── sql/
├── sqlserver/
├── structured_streaming/
├── trade_finance/
│
├── docker-compose.yml
└── README.md
```

---

## Running the Project

The project uses Docker to run the Big Data environment.

### 1. Validate Docker configuration

```bash
docker compose config
```

### 2. Build Trade Finance services

```bash
docker compose build tf-data-generator tf-event-producer tf-hbase-consumer tf-ml-worker
```

### 3. Start the core Big Data platform

```bash
docker compose up -d namenode datanode resourcemanager nodemanager zookeeper kafka hive-metastore-postgresql hive-metastore hive-server hbase
```

### 4. Start Trade Finance services

```bash
docker compose up -d tf-data-generator
docker compose up -d tf-event-producer tf-hbase-consumer tf-ml-worker
```

### 5. Validate the environment

```bash
bash scripts/trade-finance/validate-trade-finance.sh
```

---

## Project Background

This project was originally developed as a four-person academic Big Data project.

The project covered several areas including:

- Business case and architecture
- Hadoop, HDFS, and YARN
- Hive and HBase analytics
- Kafka and Spark streaming
- Machine learning
- Power BI visualization

The repository is now being reorganized as a portfolio project to better demonstrate the technical architecture, analytical workflow, and business use cases.

---

## My Contributions

My main contribution focused on the historical and batch analytics portion of the project, including:

- Working with Hive for historical analytical queries
- Working with HBase for distributed data storage
- Implementing Hadoop Streaming transaction aggregation
- Developing Hive-to-HBase analytical workflows
- Creating CAD-normalized exposure analysis
- Testing HBase PUT, GET, and SCAN operations
- Supporting documentation and integration

This project also helped me better understand how different Big Data technologies work together within an end-to-end analytics platform.

---

## Future Improvements

- Add a visual system architecture diagram
- Add Power BI dashboard screenshots
- Add Kafka streaming screenshots
- Add Hive and HBase output examples
- Improve project documentation
- Simplify the project setup process
- Add clearer explanations of machine learning results
- Add more business-focused visualizations

---

## Skills Demonstrated

- Big Data architecture
- Hadoop and HDFS
- Apache Hive
- Apache HBase
- Apache Kafka
- Apache Spark
- Python
- Machine learning
- Data analytics
- Business intelligence
- Power BI
- Data visualization
- Distributed data processing
```
