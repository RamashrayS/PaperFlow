# Setup Guide

## Overview

This workflow automatically processes PDF documents stored in Google Drive, extracts their contents, analyzes them using Google Gemini, converts the response into a structured format, and stores the results in Google Sheets.

Workflow Architecture
Google Drive
    ↓
Locate PDF
    ↓
Download PDF
    ↓
Extract Text
    ↓
Gemini Analysis
    ↓
Structured Data
    ↓
Google Sheets

## Prerequisites
Required Software
n8n
Google Account
Google Drive Access
Google Sheets Access
Required APIs
Google Gemini API Key
Google Drive OAuth Credentials
Google Sheets OAuth Credentials

## Installation

### 1. Import Workflow
- Open n8n.
- Click Import Workflow.
- Select workflow.json. (Download from here https://github.com/RamashrayS/PaperFlow/blob/main/worklflow.json)
- Save the workflow.

### 2. Configure Google Drive Credentials

Create or connect a Google Drive credential inside n8n.
Required permissions:
drive.readonly
or
drive
depending on your setup.

Attach this credential to:
- Search files and folders
- Search files and folders1
- Download file

### 3. Configure Google Gemini (SKip if you are using another model)

Create a Gemini credential.
Obtain an API key from Google AI Studio.
Create a Gemini credential in n8n.

Connect it to:
- AI Agent models (both main and structured outut)

### 4. Configure Google Sheets

Create a Google Sheets credential.

Connect it to:
Append row in sheet

### 5. Configure Drive Folder

Update the folder search node.
Replace:
"YOUR_FOLDER_NAME" with the folder containing the PDFs you want to process.

### 6. Configure Spreadsheet

Update the APPEND_ROW_IN_SHEET node.
Replace:
YOUR_SPREADSHEET_ID" with your target spreadsheet.


## Output Schema

The Gemini agent is expected to return structured data.

Example:

{
  "title": "",
  "author": "",
  "summary": "",
  "keywords": "",
  "category": ""
}

## Thanks for checking it out! 

Adjust the schema to match your use case.
Feel free to modify and adapt this workflow for personal or commercial projects.
