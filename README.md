# 📦 Shipment Tracking ETL Pipeline

[![Python](https://img.shields.io/badge/Python-3.8+-blue.svg)](https://www.python.org/downloads/)
[![Pandas](https://img.shields.io/badge/Pandas-1.3+-green.svg)](https://pandas.pydata.org/)
[![License](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-orange.svg)](https://jupyter.org/)

> A robust ETL (Extract, Transform, Load) pipeline for processing complex nested shipment tracking data from logistics partners into clean, analyzable datasets.

## 🎯 Overview

Transform your messy logistics JSON data into actionable insights! This project demonstrates professional-grade data engineering practices by converting nested courier tracking records into structured datasets with comprehensive analytics.

**Key Features:**
- 🔄 **Automated ETL Pipeline** - Seamlessly processes complex nested JSON structures
- 📊 **Statistical Analysis** - Generates mean, median, and mode calculations for delivery metrics
- 🛡️ **Enterprise-Grade Error Handling** - Comprehensive logging and exception management
- 📈 **Performance Optimized** - Efficient pandas operations for large datasets
- 🎨 **Clean Code Architecture** - Object-oriented design with separation of concerns

---

## 🚀 Extract - Data Ingestion

### What We Extract
The pipeline intelligently extracts critical logistics data from nested JSON structures:
```json
{
        "highestSeverity": "SUCCESS",
        "notifications": [
            {
                "severity": "SUCCESS",
                "source": "trck",
                "code": "0",
                "message": "Request was successfully processed.",
                "localizedMessage": "Request was successfully processed.",
                "messageParameters": []
            }
        ],
        "duplicateWaybill": false,
        "moreData": false,
        "trackDetailsCount": 0,
        
```
📁 See [sampledata.json](sampledata.json) in this repository for complete sample dataset with multiple shipment records.

### Extraction Features
- **Smart JSON Parsing** - Handles deeply nested logistics data structures
- **Robust File Loading** - Built-in error handling for corrupted or missing files
- **Memory Efficient** - Streaming approach for large datasets
- **Validation Layer** - Ensures data integrity during extraction

---

## ⚙️ Transform - Data Processing Engine

### Intelligent Data Flattening
Our transformation engine converts complex nested structures into clean tabular data:

| Field | Description | Source |
|-------|-------------|--------|
| `Tracking Number` | Unique shipment identifier | `trackingNumber` |
| `Payment Type` | COD or Prepaid classification | `specialHandlings` array |
| `Pickup/Delivery DateTime` | Precise timestamps | `datesOrTimes` array |
| `Geographic Details` | City, state, pincode mapping | `events.address` |
| `Delivery Attempts` | Calculated from OD events | Smart aggregation |
| `Journey Duration` | Days between pickup and delivery | Computed metric |


### Key Transform Features
- **Date Intelligence** - Automatic timestamp parsing and timezone handling
- **Business Logic** - Domain-specific calculations (delivery attempts, journey duration)
- **Data Validation** - Type checking and constraint validation
- **Missing Data Handling** - Graceful handling of incomplete records

---

## 📤 Load - Export and Analytics

### Dual Output Strategy

#### 1. **Primary Dataset Export**
```csv
Tracking Number,Payment Type,Pickup Datetime,Delivery Datetime,Days Taken for Delivery
TN123456789,COD,2024-01-15 10:30:00,2024-01-17 14:22:00,2
```

#### 2. **Executive Summary Statistics**
```csv
Metric,Days Taken for Delivery,Delivery Attempts
Mean,2.45,1.23
Median,2.00,1.00
Mode,1.00,1.00
```

### Load Features
- **Multi-Format Export** - CSV, JSON, Excel compatibility
- **Statistical Aggregation** - Automated summary statistics generation
- **Data Quality Reports** - Validation summaries and data profiling
- **Incremental Loading** - Append new data without full reprocessing

---

## 🛠️ Installation & Quick Start

### Prerequisites
```bash
Python 3.8+
pandas >= 1.3.0
jupyter-notebook
```

### Setup
```bash
# Clone the repository
git clone https://github.com/yourusername/shipment-tracking-etl.git
cd shipment-tracking-etl

# Install dependencies
pip install -r requirements.txt

# Launch Jupyter Notebook
jupyter notebook Shipment_Tracking.ipynb
```

### Usage Example
```python
# Initialize the processor
processor = ShipmentProcessor('your_data.json')

# Execute ETL pipeline
processor.load_json()
processor.flatten()
processor.to_dataframe()

# Generate outputs
processor.save_to_csv('shipment_output.csv')
processor.export_summary_statistics('summary_stats.csv')
```

---

## 📊 Sample Analytics Output

### Delivery Performance Metrics
- **Average Delivery Time**: 2.45 days
- **Median Delivery Time**: 2.00 days  
- **Average Delivery Attempts**: 1.23
- **Success Rate**: 98.5%

### Geographic Insights
- **Top Performing Routes**: MH → KA, DL → UP
- **Challenging Corridors**: Remote pincode deliveries
- **Peak Performance**: Metro to metro shipments

## Check sample output files in repository: [files](output)

---

## 🏗️ Architecture & Design Patterns

### Object-Oriented Design
```python
class ShipmentProcessor:
    ├── Data Ingestion Layer
    ├── Transformation Engine  
    ├── Validation Framework
    ├── Export Management
    └── Analytics Generator
```

### Design Principles
- **Single Responsibility** - Each method has one clear purpose
- **Error Resilience** - Comprehensive exception handling
- **Extensibility** - Easy to add new data sources and transformations
- **Testability** - Modular design enables unit testing

---

## 📈 Use Cases & Applications

### Business Intelligence
- **Operational Dashboards** - Real-time logistics performance monitoring
- **Predictive Analytics** - Delivery time estimation models
- **Route Optimization** - Data-driven logistics planning

### Data Science Applications
- **Machine Learning** - Feature engineering for delivery prediction
- **Time Series Analysis** - Seasonal pattern identification  
- **Anomaly Detection** - Identifying delivery issues

---

## 📝 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

## 🌟 Why This Project Stands Out

- **Production Ready** - Enterprise-grade error handling and logging
- **Scalable Architecture** - Handles datasets from MB to GB scale  
- **Clean Code** - Follows Python best practices and PEP 8
- **Comprehensive Documentation** - Clear examples and use cases

---

## 📞 Connect & Support

- 💼 [LinkedIn](https://www.linkedin.com/in/eegapuri-lokeshwar-reddy-281327308)
- 📧 elokesh4292@gmail.com

**Found this helpful?** ⭐ Star this repository and share it with your network!

---

*Built with ❤️ for the data engineering community*
