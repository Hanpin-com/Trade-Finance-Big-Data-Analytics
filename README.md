# Trade Finance Big Data Analytics Platform

An end-to-end Big Data analytics project that simulates Trade Finance transactions and processes them through batch analytics, real-time streaming, machine learning, and business visualization.

The project demonstrates how Hadoop, Spark, Kafka, Hive, HBase, Python, machine learning, and Tableau can work together to support transaction monitoring, risk analysis, operational reporting, and data-driven decision making.

---

## Project Overview

Trade Finance involves large volumes of transaction, document, shipment, payment, and compliance data.

This project simulates a Trade Finance environment and builds a data pipeline that processes and analyzes information across different stages of the transaction lifecycle.

The platform includes:

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
| Business Intelligence | Tableau |
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
Tableau Dashboard
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

Synthetic data is used so the project can demonstrate realistic analytical workflows without using real customer information.

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

The event producer creates Trade Finance Kafka topics and publishes transaction lifecycle events.

Streaming data can then be processed for near real-time monitoring and analytics.

This demonstrates how transaction activity can be monitored continuously instead of relying only on historical batch reports.

---

## Hive Analytics

Hive provides SQL-based access to historical Trade Finance data.

It is used for analytical tasks such as:

- Transaction aggregation
- Exposure analysis
- Historical transaction analysis
- Risk-related reporting
- Operational analysis

Hive makes distributed datasets easier to analyze using SQL-style queries.

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

Used to identify transactions with unusual characteristics that may require additional review.

### Documentary Discrepancy Prediction

**Model:** Random Forest Classification

Used to estimate whether a Trade Finance transaction may contain documentary discrepancies.

### Processing Delay Prediction

**Models:** Random Forest Classification and Regression

Used to identify transactions that may experience processing delays and estimate processing time.

### Trade Volume Forecasting

**Model:** Holt-Winters / Exponential Smoothing

Used to estimate future monthly Trade Finance transaction volumes based on historical patterns.

Machine learning results are stored in HBase and can also be published through Kafka topics.

---

## Business Visualization

The business visualization layer was rebuilt in Tableau for the portfolio version of this project.

The Tableau dashboard transforms transaction, operational, and machine learning outputs into business-focused visualizations.

### Executive Dashboard

The dashboard includes:

- Total Transactions
- High-Risk Transactions
- Average Processing Days
- Discrepancy Rate
- Transactions by Product Type
- Transactions by Beneficiary Country
- Overall Risk Distribution
- Transaction Trend Over Time

### Business Questions

The dashboard helps answer questions such as:

- How many Trade Finance transactions are being processed?
- How many transactions are classified as high risk?
- What is the average processing time?
- What proportion of transactions contain discrepancies?
- Which Trade Finance products have the highest transaction volume?
- Which beneficiary countries receive the most transactions?
- How are transactions distributed across risk levels?
- How does transaction volume change over time?

### Dashboard Preview

![Trade Finance Executive Overview](docs/images/Dashboard%20-%20Executive%20Overview.png)

---

## Business Value

### Risk Monitoring

Identify unusual and high-risk transactions using analytical and machine learning techniques.

### Operational Monitoring

Track transaction activity, discrepancies, processing time, and workflow performance.

### Historical Analysis

Use Hadoop, Hive, and HBase to analyze distributed historical transaction data.

### Real-Time Monitoring

Use Kafka and Spark-based processing to analyze continuously generated transaction events.

### Decision Support

Use Tableau to convert technical analytical outputs into information that business users can interpret quickly.

---

## Project Structure

```text
Trade-Finance-Big-Data-Analytics/
│
├── config/
├── data/
├── docker/
├── docs/
│   └── images/
│       └── Trade_Finance_Executive_Overview.png
├── mapreduce/
├── member1/
├── powerbi/
├── scripts/
├── sql/
├── sqlserver/
├── structured_streaming/
├── tableau/
│   └── Trade_Finance_Analytics_Tableau.twbx
├── trade_finance/
│
├── docker-compose.yml
└── README.md
```

The original Power BI materials from the academic team project remain in the `powerbi/` directory for project history and reference.

The Tableau workbook in the `tableau/` directory represents the rebuilt portfolio visualization layer.

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

The original team project covered:

- Business case and architecture
- Hadoop, HDFS, and YARN
- Hive and HBase analytics
- Kafka and Spark streaming
- Machine learning
- Power BI visualization

The repository has since been reorganized as a portfolio project to better demonstrate the technical architecture, analytical workflow, machine learning use cases, and business visualization.

---

## My Contributions

My main contribution to the original academic project focused on historical and batch analytics, including:

- Working with Hive for historical analytical queries
- Working with HBase for distributed data storage
- Implementing Hadoop Streaming transaction aggregation
- Developing Hive-to-HBase analytical workflows
- Creating CAD-normalized exposure analysis
- Testing HBase PUT, GET, and SCAN operations
- Supporting project documentation and integration

For the portfolio version, I also:

- Reorganized the repository for portfolio presentation
- Rebuilt the business visualization layer in Tableau
- Designed an executive dashboard for transaction, risk, and operational monitoring
- Created KPI views for total transactions, high-risk transactions, average processing time, and discrepancy rate
- Created visualizations for product activity, beneficiary countries, risk distribution, and transaction trends

---

## Tableau Portfolio Dashboard

The Tableau portfolio version uses:

```text
data/trade-finance/member4-output/powerbi_trade_finance_ml.csv
```

as the primary dashboard dataset.

The packaged Tableau workbook is stored at:

```text
tableau/Trade_Finance_Analytics_Tableau.twbx
```

---

## Future Improvements

Potential future improvements include:

- Add a visual system architecture diagram
- Add Kafka streaming screenshots
- Add Hive query output examples
- Add HBase operation screenshots
- Add additional Tableau risk analysis views
- Integrate historical and forecast transaction trends
- Simplify the project setup process
- Improve automated data refresh between the analytics pipeline and visualization layer

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
- Tableau
- Data visualization
- Distributed data processing
```