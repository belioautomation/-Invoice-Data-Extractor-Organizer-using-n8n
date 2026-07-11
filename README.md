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
