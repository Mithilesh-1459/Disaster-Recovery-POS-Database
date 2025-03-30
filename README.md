# Disaster-Recovery-POS-Database

This project showcases the implementation of a robust ETL (Extract, Transform, Load) pipeline on a cloud-based infrastructure using AWS EC2. Designed to handle POS (Point-of-Sale) data, the pipeline facilitates smooth data processing, transformation, and migration from a structured MariaDB system to a NoSQL MongoDB environment for high-performance analytics.

---

## Key Features

- **ETL Workflow**: Efficiently extracts transactional data, applies transformations, and loads it into a target NoSQL store.
- **AWS EC2 Deployment**: Entire pipeline and database systems are hosted on EC2 for reliable cloud operations.
- **MariaDB Integration**: Acts as the core relational storage system; supports schema design and advanced querying.
- **MongoDB Support**: Final data is loaded into MongoDB as structured JSON documents for scalable querying.
- **Advanced JSON Aggregation**: Generates nested documents representing:
  - Detailed customer purchase history.
  - Product sales data with customer associations.

### Pipeline Flow
- Data is extracted from the POS transactional system.
- Cleaned and transformed to fit analytical models.
- Loaded into MongoDB for reporting and business intelligence.

### Business Insights
- Enables revenue analysis, trend tracking, and customer behavior evaluation.

### MariaDB Cluster Design
- Distributed setup with peer-to-peer replication.
- Implements sharding and synchronization mechanisms for high availability.

---

## Entity Relationship Diagram

![ERD](./assets/erd-diagram.png)

---

## Database Schema Overview

### Product Table
- `id`: Unique identifier for the product
- `name`: Descriptive product name
- `currentPrice`: Active sale price
- `availableQuantity`: Inventory count

### City Table
- `zip`: Postal code
- `city`: Municipality
- `state`: Province/State name

### Customer Table
- `id`: Unique customer identifier
- `firstName`: Given name
- `lastName`: Surname
- `email`: Contact email
- `address1`: Main residential address
- `address2`: Optional secondary address
- `phone`: Contact number
- `birthdate`: Date of birth
- `zip`: City link via ZIP code

### Order Table
- `id`: Unique order reference
- `datePlaced`: Order date
- `dateShipped`: Dispatch date
- `customer_id`: References customer record

### Orderline Table
- `order_id`: Associated order ID
- `product_id`: Linked product identifier
- `quantity`: Number of items ordered

---

## Project Development Timeline

### Week 1 – Infrastructure Setup
- Launched AWS EC2 instance and configured secure access.
- Installed MariaDB and OpenSSH.
- Created user roles, firewall rules, and initial schema.

### Week 2 – Data Loading & Cleaning
- Loaded CSV datasets using `INFILE`.
- Applied transformations to fix formatting errors and incomplete data.

### Week 3 – Views and Indexing
- Created virtual views for restricted and simplified access.
- Defined indexes to enhance query performance.

### Week 4 – Transactions & Prepared Queries
- Developed atomic transactions and learned rollback strategies.
- Implemented prepared statements to enhance security.

### Week 5 – Stored Procedures
- Designed reusable procedures for repetitive database operations.
- Generated computed columns and modified schema structures.

### Week 6 – Triggers for Automation
- Wrote triggers for real-time updates on data events.
- Ensured consistency across data sources during user operations.

### Week 7 – Clustering for Scalability
- Configured primary and replica MariaDB nodes.
- Validated replication and backup recovery mechanisms.

### Week 8 – Peer-to-Peer Clustering
- Set up Galera Cluster for active-active node replication.
- Ensured consistent multi-node write support.

### Week 9 – JSON Export
- Extracted data from MariaDB into JSON format using SQL functions.
- Prepared datasets for import into MongoDB.

### Week 10 – MongoDB Integration
- Installed MongoDB and used `mongoimport` for loading documents.
- Queried nested data to generate analytics and support business needs.

---

## Tech Stack

- **AWS EC2** – Hosting environment
- **MariaDB** – Relational DB for core data processing
- **MongoDB** – Document database for analytics
- **SQL** – Used for scripting, transformation, and data shaping
- **Linux (Ubuntu)** – OS for configuration and deployment tasks

---

## File Organization
```
scripts/
├── create_schema.sql        # Table definitions
├── etl_script.sql           # ETL process logic
├── generate_aggregates.sql  # Queries for JSON outputs

json/
├── cust.json                # Customer-based aggregates
├── prod.json                # Product-focused aggregates
├── custom.json              # Additional reports

README.md                    # Documentation
```


