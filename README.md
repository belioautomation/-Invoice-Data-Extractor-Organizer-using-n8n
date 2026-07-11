# 📄 Invoice Data Extractor & Organizer — n8n Automation

![n8n](https://img.shields.io/badge/n8n-Automation-orange)
![OCR](https://img.shields.io/badge/API-OCR.space-blue)
![Google Drive](https://img.shields.io/badge/Storage-Google%20Drive-green)
![Google Sheets](https://img.shields.io/badge/Database-Google%20Sheets-yellow)
![JavaScript](https://img.shields.io/badge/Code-JavaScript-yellow)
![License](https://img.shields.io/badge/license-MIT-green)

An automated document processing workflow built using **n8n**, **OCR.space API**, **Google Drive**, **Google Sheets**, and **Telegram Bot API**.

This system automatically monitors invoice uploads, downloads PDF documents, extracts text using OCR technology, processes invoice information using JavaScript, stores structured invoice records in Google Sheets, and sends real-time notifications after successful processing.

**Stack:**  
n8n · OCR.space API · Google Drive · Google Sheets · Telegram Bot API · JavaScript · Document Automation


---

# 🎯 Project Overview


## Problem

Businesses process hundreds or thousands of invoices containing important financial information such as:


- Invoice numbers
- Customer information
- Billing dates
- Payment amounts
- Product details


Manual invoice processing creates several challenges:


- Time-consuming data entry
- Human transcription errors
- Difficulty organizing records
- Slow financial tracking
- Poor document management


---

## Solution

This project creates an automated invoice processing pipeline that:


1. Detects newly uploaded invoice files
2. Downloads PDF documents automatically
3. Extracts invoice text using OCR
4. Processes extracted information using JavaScript
5. Converts raw OCR data into structured fields
6. Stores invoice records in Google Sheets
7. Sends processing notifications through Telegram


The workflow provides a lightweight document automation system without requiring complex AI agents.


---

# ✨ Features


## Document Processing

✅ Automatic Google Drive monitoring  
✅ PDF invoice detection  
✅ OCR-based text extraction  
✅ Automated document processing  
✅ Invoice field extraction  


## Data Management

✅ JavaScript-based parsing  
✅ JSON data transformation  
✅ Structured invoice database  
✅ Google Sheets record management  
✅ Automated document organization  


## Notifications

✅ Telegram processing alerts  
✅ Workflow completion updates  
✅ Real-time automation monitoring  


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

Monitor invoice folders for newly uploaded documents.

Configuration:

```
Trigger:

Google Drive Trigger


Event:

File Created


Folder:

Invoice Uploads
```

Captured Information:

| Field       | Description             |
| ----------- | ----------------------- |
| File Name   | Invoice filename        |
| File ID     | Google Drive identifier |
| File Type   | PDF document            |
| Upload Date | Processing timestamp    |

---

# Node 2 — Download File

### Purpose

Retrieve invoice documents from Google Drive for processing.

Input:

```
Google Drive File ID
```

Output:

```
Binary PDF File
```

---

# Node 3 — OCR.space API

### Purpose

Extract readable text from invoice documents.

Processing:

```
Invoice PDF

      ↓

OCR.space API

      ↓

Extracted Text
```

Example OCR Output:

```
Invoice Number:

INV-2026-001


Date:

2026-07-11


Customer:

ABC Corporation


Amount:

$500.00
```

---

# Node 4 — Code Node (Invoice Parser)

### Purpose

Convert OCR-generated text into structured invoice information.

Processing:

```
OCR Text

    ↓

JavaScript Parsing

    ↓

Structured Invoice Data
```

Example Output:

```json
{
"invoiceNumber":
"INV-2026-001",

"date":
"2026-07-11",

"customer":
"ABC Corporation",

"amount":
"500.00"
}
```

---

# Node 5 — Google Sheets

### Purpose

Store processed invoice information.

Database Structure:

| Field          | Description       |
| -------------- | ----------------- |
| Timestamp      | Processing date   |
| Invoice Number | Unique invoice ID |
| Customer       | Customer name     |
| Date           | Invoice date      |
| Amount         | Payment amount    |
| Status         | Processing result |

Example:

| Invoice      | Customer        | Amount  |
| ------------ | --------------- | ------- |
| INV-2026-001 | ABC Corporation | $500.00 |

---

# Node 6 — Telegram Notification

### Purpose

Notify users after successful invoice processing.

Example:

```
✅ Invoice Processed Successfully


📄 Invoice:

INV-2026-001


👤 Customer:

ABC Corporation


💰 Amount:

$500.00


📊 Status:

Saved to Google Sheets
```

---

# 📊 Invoice Database Example

| Invoice Number | Customer        | Date       | Amount | Status    |
| -------------- | --------------- | ---------- | ------ | --------- |
| INV-2026-001   | ABC Corporation | 2026-07-11 | $500   | Completed |
| INV-2026-002   | XYZ Company     | 2026-07-12 | $850   | Completed |

---

# 🔐 Credentials Required

| Service       | Purpose                  |
| ------------- | ------------------------ |
| Google OAuth2 | Drive and Sheets access  |
| OCR.space API | Document text extraction |
| Telegram API  | Notifications            |
| n8n Instance  | Workflow execution       |

---

# ⚙️ Setup Guide

## 1. Create Google Drive Folder

Create folder:

```
Invoice Uploads
```

Upload PDF invoices into this folder.

---

## 2. Configure Google Drive

Enable:

```
Google Drive API
```

Connect Google OAuth credentials inside n8n.

---

## 3. Configure OCR.space API

Create OCR API credentials:

```
OCR_SPACE_API_KEY
```

Test PDF text extraction.

---

## 4. Create Google Sheets Database

Create spreadsheet:

```
Invoice Records
```

Columns:

```
Timestamp

Invoice Number

Customer

Date

Amount

Status
```

---

## 5. Configure Telegram Bot

Steps:

1. Create bot using BotFather
2. Copy API token
3. Add Telegram credentials in n8n
4. Configure notification chat ID

---

## 6. Import Workflow

Import:

```
workflow.json
```

Configure:

* Google Drive Trigger
* OCR API
* Google Sheets
* Telegram Bot

Activate workflow.

---

# 🧪 Testing Checklist

| Test Case                  | Expected Result        |
| -------------------------- | ---------------------- |
| Upload invoice PDF         | Workflow starts        |
| File downloaded            | PDF processed          |
| OCR executes               | Text extracted         |
| Parser runs                | Invoice data created   |
| Google Sheets updated      | Record saved           |
| Telegram notification sent | Success alert received |

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
│   ├── ocr-output.png
│   ├── code-parser.png
│   ├── google-sheets-record.png
│   ├── telegram-notification.png
│   └── execution-result.png
│
└── LICENSE
```

---

# 📸 Screenshots

Recommended screenshots:

* Complete n8n workflow
* Google Drive Trigger
* Invoice PDF download
* OCR.space response
* JavaScript parsing output
* Google Sheets invoice records
* Telegram notification
* Workflow execution result

---

# 🚀 Future Improvements

| Feature                  | Implementation          |
| ------------------------ | ----------------------- |
| AI Invoice Understanding | Gemini invoice analysis |
| Multi-document Support   | Receipts and contracts  |
| Duplicate Detection      | Invoice comparison      |
| Automatic Categorization | Expense classification  |
| Email Invoice Processing | Gmail integration       |
| Cloud Storage Support    | Dropbox/OneDrive        |
| Accounting Integration   | QuickBooks/Xero         |
| Dashboard Analytics      | Financial reporting     |

---

# 🎓 Skills Applied

## Automation

* n8n Workflow Automation
* Document processing pipelines
* Event-driven workflows

## APIs

* OCR.space API
* Google Drive API
* Google Sheets API
* Telegram Bot API

## Programming

* JavaScript
* JSON processing
* Data extraction
* Text parsing

## Business Automation

* Invoice management
* Document digitization
* Financial workflow automation

---

# 📚 Learning Objectives

This project demonstrates:

* Building document automation systems
* Extracting structured data from PDFs
* Integrating external APIs with n8n
* Creating automated financial workflows
* Processing real-world business documents

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

This project is part of my **30-Day n8n Automation Portfolio**, showcasing practical workflow automation using **n8n, APIs, JavaScript, and business document processing systems**.

---

# 📄 License

MIT License

```
```
