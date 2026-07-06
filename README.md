# 📄 Invoice Data Extractor & Organizer using n8n

Automatically monitor a Google Drive folder for newly uploaded invoice PDFs, extract invoice information using **OCR.space API**, organize the data in Google Sheets, and send a Telegram notification whenever a new invoice is processed.

Built as part of my **30-Day n8n Automation Portfolio**, this project demonstrates document automation, OCR integration, PDF processing, and workflow automation without relying on AI agents.

---

# 📌 Features

* 📁 Automatically detects new PDF invoices in Google Drive
* 📥 Downloads uploaded PDF files
* 🔍 Extracts invoice text using OCR.space API
* 🧾 Parses invoice details with a JavaScript Code node
* 📊 Stores extracted data in Google Sheets
* 📲 Sends Telegram notifications after successful processing
* ⚡ Fully automated workflow
* 🆓 Uses OCR.space Free API

---

# 🛠 Technologies Used

* n8n
* Google Drive Trigger
* Google Drive
* HTTP Request
* OCR.space API
* JavaScript (Code Node)
* Google Sheets API
* Telegram Bot API

---

# 📂 Workflow

```text
Google Drive Trigger
      │
      ▼
Download File
      │
      ▼
HTTP Request (OCR.space API)
      │
      ▼
Code (Extract Invoice Details)
      │
      ▼
Google Sheets
      │
      ▼
Telegram
```

---

# ⚙ Workflow Explanation

## 1. Google Drive Trigger

Monitors a specific Google Drive folder for newly uploaded invoice PDFs.

Configuration

* Event: File Created
* Folder: Invoice Uploads

---

## 2. Download File

Downloads the uploaded PDF from Google Drive as binary data.

Purpose

* Retrieve the invoice file
* Pass the binary file to OCR.space

---

## 3. HTTP Request (OCR.space API)

Uploads the PDF to OCR.space for text extraction.

Method

```
POST
```

Endpoint

```
https://api.ocr.space/parse/image
```

Headers

```
apikey: YOUR_API_KEY
```

Form Data

```
file
language = eng
isOverlayRequired = false
```

Expected Output

```json
{
  "ParsedResults": [
    {
      "ParsedText": "Invoice # INV-1001\nDate 2026-07-06\nSample Client\n710,000"
    }
  ]
}
```

---

## 4. Code Node

Extracts important invoice information from the OCR response.

Fields Extracted

* Invoice Number
* Invoice Date
* Customer
* Total Amount

Example Output

```json
{
  "invoiceNumber": "INV-1001",
  "date": "2026-07-06",
  "billTo": "Sample Client",
  "amount": "710,000"
}
```

---

## 5. Google Sheets

Automatically appends every processed invoice to a spreadsheet.

Columns

| Timestamp | Invoice Number | Invoice Date | Customer | Total Amount |
| --------- | -------------- | ------------ | -------- | ------------ |

---

## 6. Telegram

Sends a notification after an invoice has been successfully processed.

Example

```
🧾 Invoice Processed Successfully

📄 Invoice Number:
INV-1001

📅 Invoice Date:
2026-07-06

👤 Customer:
Sample Client

💰 Total Amount:
710,000

✅ Saved automatically to Google Sheets.
🤖 Processed by n8n + OCR.space
```

---

# 📊 Google Sheets Structure

| Timestamp | Invoice Number | Invoice Date | Customer | Total Amount |
| --------- | -------------- | ------------ | -------- | ------------ |

Example

| Timestamp           | Invoice Number | Invoice Date | Customer      | Total Amount |
| ------------------- | -------------- | ------------ | ------------- | ------------ |
| 2026-07-06 14:25:32 | INV-1001       | 2026-07-06   | Sample Client | 710,000      |

---

# 📁 Repository Structure

```text
Invoice-Data-Extractor-Organizer/
│
├── README.md
├── workflow.json
│
├── screenshots/
│   ├── workflow.png
│   ├── google-drive-trigger.png
│   ├── http-request-ocr.png
│   ├── code-node-output.png
│   ├── google-sheets.png
│   ├── telegram-notification.png
│   └── workflow-execution.png
│
└── assets/
    ├── sample-invoice.pdf
    └── sample-output.json
```

---

# 📷 Screenshots

Include the following screenshots:

* Complete Workflow
* Google Drive Trigger
* HTTP Request (OCR.space API)
* Code Node Output
* Google Sheets Results
* Telegram Notification
* Workflow Execution

---

# 📄 sample-output.json

```json
{
  "invoiceNumber": "INV-1001",
  "date": "2026-07-06",
  "billTo": "Sample Client",
  "amount": "710,000"
}
```

---

# 🎯 Learning Objectives

This project demonstrates:

* Google Drive Automation
* OCR API Integration
* PDF Processing
* HTTP Request Configuration
* JavaScript Data Extraction
* JSON Parsing
* Google Sheets Automation
* Telegram Automation
* End-to-End Document Processing

---

# 🚀 Possible Improvements

* Support multi-page invoices
* Extract vendor information
* Detect invoice currency
* Auto-categorize expenses
* Export processed invoices to Google Drive
* Duplicate invoice detection
* Email notifications
* Notion or Airtable integration
* Invoice analytics dashboard
* Support multiple OCR providers

---

# 📄 License

This project is licensed under the MIT License.

---

# 🙌 Acknowledgements

* n8n
* OCR.space API
* Google Drive API
* Google Sheets API
* Telegram Bot API
