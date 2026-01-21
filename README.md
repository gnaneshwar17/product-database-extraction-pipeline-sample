# 🚀 Product Database Extraction Pipeline

A scalable, production-ready Python ETL pipeline for extracting, validating, transforming, and exporting product data from databases and APIs.

![Python](https://img.shields.io/badge/Python-3.8+-blue.svg)
![License](https://img.shields.io/badge/License-MIT-green.svg)
![Status](https://img.shields.io/badge/Status-Active-brightgreen.svg)

## 📋 Overview

This project demonstrates enterprise-grade data extraction capabilities with a modular architecture that supports multiple data sources, robust error handling, and comprehensive data quality validation.

### Key Features

- **Multi-Source Extraction**: SQL databases, REST APIs, and web scraping
- **Robust Error Handling**: Retry logic with exponential backoff
- **Data Quality Validation**: Automated quality scoring and validation rules
- **High Performance**: Async batch processing, chunked reads, parallel execution
- **Multi-Format Export**: CSV, JSON, Parquet, Excel, and SQL
- **Comprehensive Logging**: Detailed metrics and pipeline reports

## 🏗️ Architecture

```
┌─────────────────────────────────────────────────────────────────┐
│                    Pipeline Orchestrator                         │
├─────────────────────────────────────────────────────────────────┤
│                                                                  │
│  ┌──────────┐    ┌──────────┐    ┌──────────┐    ┌──────────┐  │
│  │  Extract │ -> │ Validate │ -> │Transform │ -> │  Export  │  │
│  └──────────┘    └──────────┘    └──────────┘    └──────────┘  │
│       │                                                │         │
│       v                                                v         │
│  ┌──────────┐                                   ┌──────────┐    │
│  │SQL/API/  │                                   │CSV/JSON/ │    │
│  │Web Source│                                   │Parquet   │    │
│  └──────────┘                                   └──────────┘    │
│                                                                  │
└─────────────────────────────────────────────────────────────────┘
```

## 🛠️ Tech Stack

- **Core**: Python 3.8+, Pandas, NumPy
- **Database**: SQLAlchemy, SQLite
- **Async Processing**: asyncio, aiohttp
- **Data Formats**: PyArrow (Parquet), openpyxl (Excel)
- **Web Scraping**: BeautifulSoup, requests
- **Testing Data**: Faker

## 📦 Installation

```bash
# Clone the repository
git clone https://github.com/gnaneshwar17/product-database-extraction-pipeline-sample.git
cd product-database-extraction-pipeline-sample

# Install dependencies
pip install pandas numpy requests sqlalchemy faker pyarrow openpyxl beautifulsoup4 aiohttp tqdm python-dateutil
```

## 🚀 Quick Start

### Option 1: Run the Jupyter Notebook
```bash
jupyter notebook Product_Database_Extraction_Pipeline.ipynb
```

### Option 2: Import as Module
```python
from pipeline import ProductExtractionOrchestrator, ExtractionConfig, SQLDatabaseExtractor

# Initialize configuration
config = ExtractionConfig(
    batch_size=1000,
    max_workers=5,
    output_dir="./extracted_data"
)

# Create extractor
sql_extractor = SQLDatabaseExtractor(config, "sqlite:///products.db")
sql_extractor.connect()

# Run pipeline
orchestrator = ProductExtractionOrchestrator(config)
results = orchestrator.run_pipeline([sql_extractor])

print(f"Extracted {results['total_products']} products")
print(f"Quality Score: {results['quality_score']:.1f}%")
```

## 📊 Pipeline Components

### 1. Data Extractors
- `BaseExtractor`: Abstract base class for all extractors
- `SQLDatabaseExtractor`: Extract from SQL databases with chunked reads
- `APIExtractor`: REST API integration with rate limiting
- `WebScraperExtractor`: Web scraping with BeautifulSoup

### 2. Data Validation
- Field completeness checks
- Data type validation
- Business rule enforcement
- Automated quality scoring

### 3. Data Transformation
- Text cleaning and normalization
- Price standardization
- Category mapping
- Deduplication

### 4. Export Formats
| Format | Use Case |
|--------|----------|
| CSV | Universal compatibility |
| JSON | API responses, web apps |
| Parquet | Big data, analytics |
| Excel | Business reporting |
| SQL | Database ingestion |

## 📈 Sample Output

```
============================================================
🚀 RUNNING COMPLETE EXTRACTION PIPELINE
============================================================
2026-01-21 02:37:58 | INFO | Extracting data from sources...
2026-01-21 02:37:59 | INFO | Validating data quality...
2026-01-21 02:38:00 | INFO | Transforming data...
2026-01-21 02:38:01 | INFO | Exporting data...

============================================================
📋 PIPELINE EXECUTION SUMMARY
============================================================
   Run ID: 20260121_023758
   Status: completed
   Total Products: 5,000
   Quality Score: 98.5%
   Execution Time: 3.2s

   Export Files:
      - CSV: ./extracted_data/products.csv
      - JSON: ./extracted_data/products.json
      - PARQUET: ./extracted_data/products.parquet
```

## 📁 Project Structure

```
product-database-extraction-pipeline-sample/
│
├── Product_Database_Extraction_Pipeline.ipynb  # Main notebook
├── README.md                                    # Documentation
├── requirements.txt                             # Dependencies
├── .gitignore                                   # Git ignore rules
│
└── extracted_data/                              # Output directory
    ├── products.csv
    ├── products.json
    ├── products.parquet
    └── pipeline_report.json
```

## 🔧 Configuration

```python
@dataclass
class ExtractionConfig:
    batch_size: int = 1000      # Records per batch
    max_retries: int = 3        # Retry attempts
    retry_delay: float = 1.0    # Base delay (seconds)
    timeout: int = 30           # Request timeout
    max_workers: int = 5        # Parallel workers
    validate_data: bool = True  # Enable validation
    output_dir: str = "./extracted_data"
```

## 🎯 Use Cases

This pipeline architecture is applicable to:
- **E-commerce**: Product catalog management and synchronization
- **Data Platforms**: Data ingestion and transformation pipelines
- **Analytics**: Product performance data extraction
- **Marketing**: Campaign data collection and processing

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 👤 Author

**Gnaneshwar**
- GitHub: [@gnaneshwar17](https://github.com/gnaneshwar17)
- LinkedIn: [Connect with me](https://www.linkedin.com/in/gnaneshwar17/)

## 🤝 Contributing

Contributions, issues, and feature requests are welcome! Feel free to check the [issues page](https://github.com/gnaneshwar17/product-database-extraction-pipeline-sample/issues).

---

⭐ Star this repository if you found it helpful!
