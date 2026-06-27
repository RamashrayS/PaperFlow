# Setup Guide

## Overview

This workflow automatically processes PDF documents stored in Google Drive, extracts their contents, analyzes them using Google Gemini, converts the response into a structured format, and stores the results in Google Sheets.

## Prerequisites

Required Software
- [n8n](https://github.com/n8n-io/n8n)
- Google Gemini API Key [Get from Google AI Atudio](https://aistudio.google.com/app/api-keys)
- Google Drive OAuth Credentials [Get from Google Cloud](https://console.cloud.google.com/welcome)
- Google Sheets OAuth Credentials [Get from Google Cloud](https://console.cloud.google.com/welcome)

*Here I have used Gemini as an example use API key of any AI model of your choice*

## Installation

### 1. Import Workflow
- Open n8n.
- Click Import Workflow.
- Select workflow.json. [Download from here if you didn't alraedy](https://github.com/RamashrayS/PaperFlow/blob/main/worklflow.json)
- Save the workflow.

### 2. Configure Google Drive Credentials

Create or connect a Google Drive credential inside n8n.
Required permissions:
drive.readonly
or
drive
depending on your setup.

Attach this credential to:
- Search file nodes
- Download file node

### 3. Configure Google Gemini (Follow according to your AI model)

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

So you can edit this output in the AI prompt to get the fields you require.

For Eg if you are studying a material you can add fields like 
{
"morphology": "",
"hardness": "",
"crstal_structure": ""
}

In the AI prompt give it some contexts about what you want it to do then the utput schemma of what info you want to obtain from the paper.


## Thanks for checking it out! 

Reach out for any troubles.
Feel free to modify and adapt this workflow for personal or commercial projects.
