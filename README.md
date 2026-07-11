# 📄 Invoice Data Extractor & Organizer using n8n

An automated document processing workflow built with **n8n**, **OCR.space API**, **Google Drive**, **Google Sheets**, and **Telegram**. This project automatically monitors a Google Drive folder for newly uploaded invoice PDFs, extracts invoice information using OCR, organizes the extracted data in Google Sheets, and sends Telegram notifications after successful processing.

Developed as part of my **30-Day n8n Automation Portfolio**, this workflow demonstrates document automation, OCR integration, PDF processing, and workflow automation without relying on AI agents.

---

# 📌 Features

* 📁 Monitors Google Drive for newly uploaded invoice PDFs
* 📥 Downloads PDF invoices automatically
* 🔍 Extracts invoice text using OCR.space API
* 🧾 Parses invoice details with a JavaScript Code Node
* 📊 Stores extracted data in Google Sheets
* 📲 Sends Telegram notifications after successful processing
* ⚡ Fully automated invoice processing workflow
* 🆓 Uses the OCR.space Free API

---

# 🛠 Technologies Used

* n8n
* Google Drive Trigger
* Google Drive
* HTTP Request
* OCR.space API
* Code Node (JavaScript)
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
Code Node (Extract Invoice Details)
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

Monitors a Google Drive folder for newly uploaded invoice PDFs.

**Configuration**

* Event: File Created
* Folder: Invoice Uploads

---

## 2. Download File

Downloads uploaded invoice PDFs from Google Drive for processing.

---

## 3. HTTP Request (OCR.space API)

Uploads the PDF invoice to OCR.space for text extraction.

**Method**

```text
POST
```

**Endpoint**

```text
https://api.ocr.space/parse/image
```

**Required Parameters**

* API Key
* Invoice PDF File
* Language: English

### Example OCR Response

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

**Extracted Fields**

* Invoice Number
* Invoice Date
* Customer
* Total Amount

### Example Output

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

Stores all processed invoice information.

### Logged Information

| Timestamp | Invoice Number | Invoice Date | Customer | Total Amount |
| --------- | -------------- | ------------ | -------- | ------------ |

---

## 6. Telegram

Sends an instant notification after an invoice has been successfully processed.

### Example Notification

```text
🧾 Invoice Processed Successfully

Invoice Number:
INV-1001

Invoice Date:
2026-07-06

Customer:
Sample Client

Total Amount:
710,000

✅ Saved automatically to Google Sheets.
🤖 Processed using n8n and OCR.space.
```

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

This project is licensed under the **MIT License**.

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

GitHub: https://github.com/belioautomation

This project is part of my **30-Day n8n Automation Portfolio**, showcasing practical workflow automation using n8n, OCR APIs, and document processing.
