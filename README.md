# AWS Textract Table Extraction

### Recognize Tables in PDF Files and Convert Them into Pandas DataFrames Using AWS Textract

This repository demonstrates how to use **AWS Textract** to recognize and extract tables from PDF files and convert them into **Pandas DataFrames** for easy data manipulation. The project also integrates with **AWS S3** for storing PDF files and extracted data.

---

## Table of Contents
- [Overview](#overview)
- [Features](#features)
- [Requirements](#requirements)
- [Installation](#installation)
- [Usage](#usage)
- [Configuration](#configuration)
- [Examples](#examples)
- [Contributing](#contributing)
- [License](#license)

---

## Overview

This project uses AWS Textract, a service that automatically extracts text and data from scanned documents, to recognize tables from PDF files. The extracted tables are then converted into Pandas DataFrames for further analysis and processing. Files are stored and retrieved from AWS S3 buckets.

---

## Features

- **AWS Textract Integration**: Automatically extracts tables from PDF files using AWS Textract.
- **AWS S3 Integration**: PDF files and extracted data are stored and accessed from AWS S3.
- **Pandas DataFrames**: Extracted tables are converted into Pandas DataFrames for easy analysis and manipulation.
- **CSV Export**: Convert DataFrames to CSV for downstream processing or storage.
  
---

## Requirements

1. **AWS Account** with access to Textract and S3.
2. **IAM Role** with appropriate permissions for Textract and S3.
3. **AWS CLI** configured with access credentials.
4. **Python 3.7+** and the following libraries:
    - `boto3`: AWS SDK for Python
    - `pandas`: For working with DataFrames
    - `awscli`: For AWS CLI commands (optional)
    - `textract-trp`: Textract response parser (optional)

---

## Installation

1. Clone the repository:
    ```bash
    git clone https://github.com/yourusername/aws-textract-table-extraction.git
    ```

2. Navigate to the project directory:
    ```bash
    cd aws-textract-table-extraction
    ```

3. Install the required dependencies:
    ```bash
    pip install -r requirements.txt
    ```

4. Configure AWS CLI with your credentials:
    ```bash
    aws configure
    ```

---

## Usage

1. **Upload a PDF to S3**:
    Upload your PDF file to your S3 bucket. Make sure to note the bucket name and file key for processing.
    ```bash
    aws s3 cp path_to_your_file.pdf s3://your-s3-bucket/path/to/file.pdf
    ```

2. **Run the table extraction**:
    Execute the script to extract tables from the PDF stored in S3:
    ```bash
    python extract_tables.py --bucket your-s3-bucket --file_key path/to/file.pdf
    ```

3. **Convert to Pandas DataFrame**:
    Once the extraction is complete, the tables will be processed and converted into Pandas DataFrames.

4. **Save DataFrame to CSV** (optional):
    You can export the extracted tables to CSV for further use:
    ```python
    df.to_csv('extracted_table.csv', index=False)
    ```

---

## Configuration

Before running the script, ensure that your AWS environment is correctly configured with the following:

- **S3 Bucket**: A bucket to store and retrieve your PDF files.
- **AWS Textract Role**: Ensure that your AWS IAM role has `Textract` and `S3` access.

---

## Examples

Here's a sample usage of the script to extract tables from a PDF:

```bash
python extract_tables.py --bucket my-bucket --file_key documents/sample.pdf
