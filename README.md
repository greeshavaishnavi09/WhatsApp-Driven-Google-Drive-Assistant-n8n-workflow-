# 📦 WhatsApp-Driven Google Drive Assistant (n8n Workflow)

> Think Act Rise Foundation – Python Development Internship (Task 2)  
> Submitted by: **Greesha Vaishnavi Rampally**

---

## 📚 Overview

This project demonstrates a **WhatsApp-integrated assistant** that performs actions on a user’s **Google Drive** using an **n8n workflow**. The assistant can respond to commands sent via WhatsApp (through Twilio Sandbox), and supports listing files, deleting, moving, and summarising documents using OpenAI GPT-4o.

It is designed to be lightweight, extensible, and secure — running entirely within the user's authenticated Google account and responding via WhatsApp with contextual feedback.

---

## 🚀 Features Implemented

| Feature                     | Status |
|----------------------------|--------|
| ✅ LIST files              | ✔️     |
| ✅ DELETE file             | ✔️     |
| ✅ MOVE file               | ✔️     |
| ✅ SUMMARY of documents    | ✔️     |
| ✅ Twilio WhatsApp Input   | ✔️     |
| ✅ Google Drive Integration| ✔️     |
| ✅ OpenAI GPT-4o Summaries | ✔️     |
| ✅ Logging to Google Sheet | ✔️     |
| ✅ Error Feedback via WhatsApp | ✔️     |

---

## 📷 Demo Video

📺 **[Click to Watch Demo Video]*(https://www.loom.com/share/623f63965906403a93cefc7fa3293fe4?sid=2de73e4e-b318-4263-aff4-1c8a755c3873)*  
*(Demo shows end-to-end flow of LIST, DELETE, MOVE, and SUMMARY commands in WhatsApp)*

---

## 📂 Folder Structure

whatsapp-drive-assistant/
├── README.md
├── env-sample
├── n8n-workflows/
│ └── workflow.json
└── demo-video-link.txt
   

---

## 🧪 WhatsApp Commands Supported

| Command | Format | Description |
|--------|--------|-------------|
| `LIST` | `LIST /MyFolder` | Lists all files in folder |
| `DELETE` | `DELETE /MyFolder/file.pdf` | Deletes specific file |
| `MOVE` | `MOVE /MyFolder/file.pdf /Archive` | Moves file to destination folder |
| `SUMMARY` | `SUMMARY /MyFolder` | Returns AI summary of each document in folder (PDF, DOCX, TXT) |

📝 Folder and file names are case-sensitive and based on Google Drive.

---

## 🧰 Tech Stack & Tools

- 🔄 **n8n** (workflow automation)
- 💬 **Twilio Sandbox for WhatsApp**
- ☁️ **Google Drive API** (OAuth2)
- 📄 **Google Sheets API** (for audit log)
- 🧠 **OpenAI GPT-4o** (text summarisation)
- 🌐 **ngrok** (for local webhook exposure)

---

## 🔧 Setup Instructions

### 1. Clone the Repository
```bash
git clone  https://github.com/greeshavaishnavi09/WhatsApp-Driven-Google-Drive-Assistant-n8n-workflow-.git
cd whatsapp-drive-assistant

2. Set Up .env File

  Create a .env file with your actual credentials based on the structure in env-sample:

TWILIO_ACCOUNT_SID=your_twilio_sid
TWILIO_AUTH_TOKEN=your_twilio_auth_token
TWILIO_WHATSAPP_NUMBER=whatsapp:+14155238886

OPENAI_API_KEY=your_openai_key

GDRIVE_CLIENT_ID=your_client_id
GDRIVE_CLIENT_SECRET=your_client_secret
GDRIVE_REFRESH_TOKEN=your_refresh_token

AUDIT_SPREADSHEET_ID=your_google_sheet_id

3. Import the Workflow in n8n

   Start your n8n instance (local or Docker).

   Import the workflow from n8n-workflows/workflow.json:

   Go to top-right corner in n8n > Import Workflow

----

n8n import:workflow --input n8n-workflows/workflow.json

4. Setup Twilio Sandbox for WhatsApp

  Go to Twilio Console

  Activate the WhatsApp Sandbox

  Join the sandbox by sending the provided code to Twilio number

  Set the inbound message webhook to your n8n Webhook URL (from ngrok):
  https://<your-ngrok-id>.ngrok.io/webhook/whatsapp

---

📒 How It Works

1. User sends a command like LIST /ProjectX via WhatsApp

2. Twilio sends it to the n8n webhook

3. Workflow parses the command and performs:

   LIST → Fetches file list from folder

   DELETE → Deletes specified file (with confirmation)

   MOVE → Moves file to another folder

   SUMMARY → Reads each file and uses OpenAI GPT-4o to return bullet summaries

4. A Google Sheet is updated with the action log

5. User receives a confirmation or response message via WhatsApp

---

📌 CAPTCHA / Security / Audit Strategy

✅ No CAPTCHA bypass required (Drive API)

✅ API tokens are stored in env vars / n8n credentials

✅ All commands and actions are logged in a private Google Sheet

✅ Delete action requires exact file path and confirmation — no bulk deletions

---

🧠 AI Summary Logic

Uses OpenAI GPT-4o for high-quality summaries

Works with PDF, DOCX, and TXT

Summary includes key points in bullet format

Skips files it can’t read (e.g., images, protected PDFs)

---

⚠️ Known Limitations

Requires exact folder/file names

SUMMARY ignores image-based documents

No advanced natural-language parsing

---


📜 License
Licensed under the MIT License – use and modify freely.

---


🙋‍♀️ Author Notes

This project is submitted as part of the Think Act Rise Foundation Python Internship.
It builds on my earlier Task 1 (Court Data Fetcher) and showcases my ability to work with:

  APIs (Google Drive, Twilio, OpenAI)

  Automation workflows using n8n

  Prompt engineering + summarisation

  Backend integration and error handling

  ---


🔗 GitHub Repository
https://github.com/greeshavaishnavi09/WhatsApp-Driven-Google-Drive-Assistant-n8n-workflow-.git