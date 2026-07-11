# 📄 Invoice Data Extractor & Organizer — n8n Automation

An automated document processing workflow built using **n8n**, **OCR.space API**, **Google Drive**, **Google Sheets**, and **Telegram Bot API**.

This system automatically monitors invoice uploads, downloads PDF documents, extracts text using OCR technology, processes invoice information using JavaScript, stores structured data in Google Sheets, and sends real-time notifications after successful processing.

**Stack:**  
n8n · OCR.space API · Google Drive · Google Sheets · Telegram Bot · JavaScript · Document Automation


---

# 🎯 Project Overview


## Problem

Businesses process hundreds of invoices containing important information such as:

- Invoice numbers
- Customer details
- Dates
- Payment amounts


Manual invoice processing creates challenges:

- Time-consuming data entry
- Human errors during transcription
- Difficulty organizing documents
- Slow financial record updates


---

## Solution

This project automates invoice data extraction by:


1. Monitoring invoice uploads
2. Downloading PDF documents automatically
3. Extracting text using OCR
4. Parsing important invoice fields
5. Storing structured records
6. Sending processing notifications


The workflow creates a simple document automation pipeline without requiring AI agents.


---

# ✨ Features


## Document Processing

✅ Automatic invoice detection  
✅ PDF document handling  
✅ OCR-based text extraction  
✅ Automated data parsing  


## Data Management

✅ Structured invoice records  
✅ Google Sheets database  
✅ JSON data transformation  
✅ Automated organization  


## Notifications

✅ Telegram success alerts  
✅ Processing status updates  
✅ Real-time workflow monitoring  


---

# 🗺️ System Architecture


```mermaid
flowchart TD


A["📁 Invoice PDF Upload"]

--> B["☁️ Google Drive Trigger"]


B --> C["📥 Download Invoice"]


C --> D["🔍 OCR.space API"]


D --> E["⚙️ JavaScript Parser"]


E --> F["📊 Google Sheets"]


F --> G["📱 Telegram Notification"]

````

---

# 🏗️ Workflow Implementation

# Workflow 1: Invoice Processing Pipeline

## Node 1 — Google Drive Trigger

### Purpose

Monitor a Google Drive folder for new invoice documents.

Configuration:

```text
Event:
File Created


Folder:
Invoice Uploads
```

Captured Information:

| Field        | Description             |
| ------------ | ----------------------- |
| File Name    | Invoice filename        |
| File ID      | Google Drive identifier |
| Created Time | Upload timestamp        |

---

# Node 2 — Download File

### Purpose

Retrieve the uploaded invoice PDF for processing.

Process:

```text
Google Drive

      ↓

Invoice PDF Binary Data

      ↓

OCR Processing
```

---

# Node 3 — HTTP Request (OCR.space API)

### Purpose

Convert invoice PDF images into readable text.

Request:

```text
Method:

POST


Endpoint:

https://api.ocr.space/parse/image
```

Parameters:

| Parameter | Value             |
| --------- | ----------------- |
| API Key   | OCR.space API Key |
| File      | Invoice PDF       |
| Language  | English           |

Example Response:

```json
{
"ParsedResults":[
{
"ParsedText":
"Invoice # INV-1001
Date 2026-07-06
Sample Client
710000"
}
]
}
```

---

# Node 4 — Code Node

### Purpose

Extract important invoice information from OCR results.

Processing:

```text
OCR Text

    ↓

JavaScript Parsing

    ↓

Structured Invoice Data
```

Extracted Fields:

| Field          | Description         |
| -------------- | ------------------- |
| Invoice Number | Invoice identifier  |
| Invoice Date   | Transaction date    |
| Customer       | Billing customer    |
| Amount         | Total invoice value |

Example Output:

```json
{
"invoiceNumber":
"INV-1001",

"date":
"2026-07-06",

"billTo":
"Sample Client",

"amount":
"710000"
}
```

---

# Node 5 — Google Sheets

### Purpose

Store processed invoice records.

Database Structure:

| Field          | Description     |
| -------------- | --------------- |
| Timestamp      | Processing time |
| Invoice Number | Invoice ID      |
| Invoice Date   | Invoice date    |
| Customer       | Client name     |
| Total Amount   | Invoice value   |

Example:

| Invoice  | Customer      | Amount |
| -------- | ------------- | ------ |
| INV-1001 | Sample Client | 710000 |

---

# Node 6 — Telegram Notification

### Purpose

Notify users after successful invoice processing.

Example:

```text
🧾 Invoice Processed Successfully


Invoice Number:
INV-1001


Customer:
Sample Client


Amount:
710,000


✅ Saved automatically to Google Sheets.

⚙ Processed using n8n + OCR automation.
```

---

# 🔐 Credentials Required

| Service           | Purpose                 |
| ----------------- | ----------------------- |
| Google OAuth2     | Drive and Sheets access |
| OCR.space API Key | Text extraction         |
| Telegram API      | Notifications           |
| n8n Instance      | Workflow execution      |

---

# ⚙️ Setup Guide

## 1. Create Google Drive Folder

Create:

```text
Invoice Uploads
```

Upload invoice PDFs into this folder.

---

## 2. Configure OCR.space API

Create OCR.space API credentials.

Required:

```text
API Key
Language Configuration
```

Test OCR extraction.

---

## 3. Create Google Sheets Database

Create:

```text
Invoice Records
```

Columns:

```text
Timestamp

Invoice Number

Invoice Date

Customer

Total Amount
```

---

## 4. Configure Telegram Bot

Steps:

1. Create bot using BotFather
2. Copy bot token
3. Add Telegram credential in n8n
4. Configure notification chat ID

---

## 5. Import Workflow

Import:

```text
workflow.json
```

Configure:

* Google Drive Trigger
* OCR API
* Google Sheets
* Telegram

Activate workflow.

---

# 🧪 Testing Checklist

| Test Case              | Expected Result        |
| ---------------------- | ---------------------- |
| Upload invoice PDF     | Workflow starts        |
| OCR processes document | Text extracted         |
| Code Node runs         | Invoice fields created |
| Google Sheets updates  | Record saved           |
| Telegram sends message | Notification received  |

---

# 📁 Repository Structure

```text
Invoice-Data-Extractor-Organizer/

│
├── README.md
│
├── workflow.json
│
├── screenshots/
│   │
│   ├── workflow.png
│   ├── google-drive-trigger.png
│   ├── download-file.png
│   ├── ocr-request.png
│   ├── code-node-output.png
│   ├── google-sheets.png
│   ├── telegram-notification.png
│   └── execution-result.png
│
├── assets/
│   │
│   ├── sample-invoice.pdf
│   └── sample-output.json
│
└── LICENSE
```

---

# 📸 Screenshots

Recommended screenshots:

* Complete workflow
* Google Drive Trigger
* Download File
* OCR.space API Request
* OCR Response
* JavaScript Extraction
* Google Sheets Database
* Telegram Notification
* Workflow Execution

---

# 🚀 Future Improvements

| Feature                    | Implementation               |
| -------------------------- | ---------------------------- |
| Multi-page Invoice Support | Advanced PDF processing      |
| Vendor Detection           | Extract supplier information |
| Currency Detection         | Financial normalization      |
| Expense Categorization     | Automated accounting tags    |
| Duplicate Detection        | Invoice matching             |
| Email Processing           | Process invoice attachments  |
| Cloud Storage Export       | Archive documents            |
| Dashboard Analytics        | Invoice reporting            |
| Multiple OCR Providers     | Azure OCR / Google Vision    |

---

# 🎓 Skills Applied

## Automation

* n8n Workflow Automation
* Document processing pipelines
* Event-driven automation

## APIs

* OCR.space API
* Google Drive API
* Google Sheets API
* Telegram Bot API

## Programming

* JavaScript
* JSON parsing
* Data extraction
* Data transformation

## Business Automation

* Invoice processing
* Digital document management
* Automated reporting

---

# 📚 Learning Objectives

This project demonstrates:

* Building document automation systems
* Integrating external APIs with n8n
* Processing PDF documents
* Extracting structured information
* Automating business workflows

---

# 🙌 Acknowledgements

* n8n
* OCR.space API
* Google Drive API
* Google Sheets API
* Telegram Bot API

---

# 👨‍💻 Author

**Belio C. Sinangote**

BS Information Technology Student
Cebu Technological University (CTU)

GitHub:

[https://github.com/belioautomation](https://github.com/belioautomation)

This project is part of my **30-Day n8n Automation Portfolio**, showcasing practical workflow automation using n8n, OCR APIs, document processing, and business automation solutions.

---

# 📄 License

MIT License

```

This project is now positioned as a **real business automation workflow** similar to what companies build for:
- Accounting automation
- Finance operations
- Document management
- Back-office process automation

It also complements your AI projects because it shows you can build both **AI workflows and traditional API automation pipelines**.
```
