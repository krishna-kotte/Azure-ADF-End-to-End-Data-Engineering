# Azure ADF End-to-End Data Engineering Pipeline

An end-to-end Azure Data Engineering project that ingests data from an on-premises SQL Server into Azure Data Lake Storage Gen2 using Azure Data Factory. The project implements the Medallion Architecture (Bronze, Silver, Gold) with incremental loading, data transformations using ADF Data Flows, and automated email notifications using Azure Logic Apps.

---

## Architecture

![Architecture](Screenshots/architecture.png)

---

## Project Overview

This project demonstrates a production-style Azure Data Engineering pipeline.

### Source
- On-Premises SQL Server

### Data Ingestion
- Azure Data Factory
- Self-Hosted Integration Runtime
- Incremental Loading (Watermark)

### Storage
- Azure Data Lake Storage Gen2
- Delta Format

### Data Processing
- Bronze Layer (Raw Data)
- Silver Layer (Cleaned & Enriched Data)
- Gold Layer (Business Summary Tables)

### Notifications
- Azure Logic Apps
- Email Alerts for Pipeline Success/Failure

---

## Technologies Used

- Azure Data Factory
- Azure Data Lake Storage Gen2
- Azure Logic Apps
- SQL Server
- Self-Hosted Integration Runtime
- Delta Lake

---

## Project Workflow

```
On-Prem SQL Server
        │
        ▼
Self-Hosted Integration Runtime
        │
        ▼
Azure Data Factory
        │
        ▼
Bronze Layer (Raw Delta)
        │
        ▼
Silver Layer (Cleaned & Enriched)
        │
        ▼
Gold Layer (Business Ready)
        │
        ▼
Logic Apps
        │
        ▼
Email Notifications
```

---

## Bronze Layer

- Extracts data from On-Prem SQL Server
- Incremental ingestion using Watermark
- Stores raw data in Parquet format

---

## Silver Layer

Performed using Azure Data Factory Mapping Data Flows.

Transformations include:

- Remove unnecessary columns
- Generate Current Date
- Booking Month
- Booking Quarter
- Day of Week
- Flight Category
- Ticket Category
- Clean Check-in Status
- Filter invalid records
- Upsert into Silver Layer

---

## Gold Layer

Business-ready aggregated tables created using Mapping Data Flows.

### Airline Summary

- Total Bookings
- Total Revenue
- Average Ticket Price
- Average Flight Duration
- Checked-in Passengers

### Monthly Summary

- Booking Year
- Booking Month
- Total Bookings
- Total Revenue
- Average Ticket Cost

### Airport Summary

- Flights
- Revenue
- Average Ticket Cost

---

## Pipeline Monitoring

The project uses Azure Logic Apps to send automated email notifications.

Alerts are triggered for:

- Bronze Layer Success
- Bronze Layer Failure
- Silver Layer Success
- Silver Layer Failure
- Gold Layer Success
- Gold Layer Failure

---

## Repository Structure

```
Azure-ADF-End-to-End-Data-Engineering/
│
├── pipeline/
├── dataflow/
├── dataset/
├── linkedService/
├── integrationRuntime/
├── factory/
├── Screenshots/
├── Architecture.png
└── README.md
```

---

## Screenshots

Project screenshots are available in the **Screenshots** folder.

Examples include:

- Pipeline
- Silver Data Flow
- Gold Data Flow
- Logic Apps
- Email Notifications
- Azure Data Lake Storage
- Azure Data Factory Pipelines

---

## Security

Sensitive information has been removed from this repository.

The following items have been masked:

- Server Names
- Usernames
- Credentials
- Linked Service Secrets
- Logic App URLs
- Storage Account Details

---

## Future Enhancements

- CI/CD using Azure DevOps
- Parameterized Pipelines
- Trigger-based Scheduling
- Data Quality Validation
- Monitoring Dashboard

---

## Author

**Krishna K**

GitHub: https://github.com/krishna-kotte
