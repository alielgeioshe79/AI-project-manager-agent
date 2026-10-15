# 🤖 AI Project Manager Agent Workflow

An automated, intelligent **Project Management Assistant** built using **n8n**. Powered by the **Google Gemini Chat Model**, this AI agent interacts through **Telegram** to manage online course catalogues, handle communications via Gmail, schedule events in Google Calendar, and perform web searches via SerpApi—all connected to an **Airtable** backend database.

---

## 🖼️ Workflow Architecture

<img width="1165" height="639" alt="Screenshot 2026-10-15 182445" src="https://github.com/user-attachments/assets/715291da-5c12-4a0b-9b4f-599a0d48f80e" />


---

## 🚀 Features & Capabilities

- 💬 **Telegram Interface**: Receives commands and queries from users via Telegram and responds dynamically.
- 🧠 **AI-Powered Reasoning**: Uses **Google Gemini Chat Model** combined with conversational **Simple Memory** to handle complex context-aware queries.
- 📊 **Airtable Operations**:
  - **Read**: Queries existing `Courses`, `Instructors`, and `Categories`.
  - **Write/Update**: Dynamically creates or updates records across course management tables (`upsert: record`).
- 📧 **Gmail Automation**: Reads incoming emails (`check emails`) and dispatches outbound messages (`send emails`).
- 📅 **Google Calendar Integration**: Fetches schedule details (`check calendar`) and sets up new calendar entries (`create calendar`).
- 🔍 **Web Search Tooling**: Utilizes **SerpApi** for real-time web search capabilities when internal database info is insufficient.
- ⚡ **JavaScript Data Processing**: Custom code nodes to transform and format AI responses before returning them to Telegram.

---

## 🗄️ Database Structure (Airtable)

The workflow relies on three primary data collections (CSV templates included in the repository):

1. **`courses_only.csv`**: Contains course IDs, course names, descriptions, categories, instructor associations, and pricing.
2. **`instructors.csv`**: Stores instructor bios, titles, profile metadata, and assigned courses.
3. **`categories.csv`**: Classifies subjects into primary and secondary learning domains.

---

## 🛠️ Built With

* [n8n](https://n8n.io/) - Workflow Automation Platform
* [Google Gemini API](https://ai.google.dev/) - LLM Engine for Reasoning
* [Telegram Bot API](https://core.telegram.org/bots/api) - Chat User Interface
* [Airtable API](https://airtable.com/) - Relational Database Storage
* [Google Workspace API](https://developers.google.com/workspace) - Gmail & Google Calendar Services
* [SerpApi](https://serpapi.com/) - Search Engine Results API

---

## 📋 Setup & Installation

### Prerequisites
- An active **n8n** instance (Cloud or Self-Hosted).
- API Keys & OAuth Credentials for:
  - Telegram Bot Token (`@BotFather`)
  - Google Gemini API Key
  - Airtable Personal Access Token
  - Google Workspace OAuth2 (Gmail & Google Calendar)
  - SerpApi Key

### Workflow Import
1. Download the workflow JSON file from this repository.
2. Open your n8n workspace dashboard.
3. Click **Workflows** > **Import from File** and upload the `.json` file.
4. Set up your credentials under the respective node settings:
   - Connect **Telegram Trigger** and **Send a text message** nodes to your Telegram credentials.
   - Connect **Google Gemini Chat Model** to your Gemini API key.
   - Connect **Airtable** nodes to your Airtable Base containing the `courses`, `instructors`, and `categories` tables.
   - Connect **Gmail** & **Google Calendar** nodes to your Google OAuth account.
5. Toggle the workflow status to **Published**.

---

## 📂 File Structure

```text
.
├── README.md                          # Repository documentation
├── Screenshot 2026-10-15 182445.png   # Workflow architecture diagram
├── categories.csv                     # Database schema template for Categories
├── instructors.csv                    # Database schema template for Instructors
└── courses_only.csv                   # Database schema template for Courses
```
