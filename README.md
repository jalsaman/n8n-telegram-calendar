# Telegram AI Calendar Assistant 🤖📅

An intelligent n8n automation that converts natural language messages from Telegram into Google Calendar events using AI.

## ✨ Features

- **Natural Language Processing**: Understands event details from casual messages
- **Smart Date/Time Extraction**: Automatically calculates dates relative to current time
- **Google Calendar Integration**: Creates events with proper formatting
- **Telegram Two-Way Communication**: Receives messages and sends confirmations
- **AI-Powered**: Uses OpenAI's GPT model for intelligent parsing

## 🏗️ Workflow Architecture
Telegram Message → AI Agent (OpenAI) → Google Calendar Event → Telegram Confirmation



## 📦 Nodes Used

| Node | Purpose | Configuration Needed |
|------|---------|----------------------|
| **Telegram Trigger** | Receives messages from Telegram bot | Bot Token, Webhook URL |
| **AI Agent** | Processes natural language, extracts event details | Connected to OpenAI |
| **OpenAI Chat Model** | Provides AI capabilities | OpenAI API Key |
| **Google Calendar Tool** | Creates calendar events | Google OAuth, Calendar ID |
| **Telegram Send** | Sends confirmation messages | Bot Token, Chat ID |

## 🚀 Quick Start

### Prerequisites
- [n8n](https://n8n.io/) instance (self-hosted or cloud)
- Telegram Bot Token ([@BotFather](https://t.me/botfather))
- OpenAI API Key
- Google Cloud OAuth Client ID

### Installation Steps

1. **Import the Workflow**
In n8n: Settings → Workflows → Import


2. **Configure Credentials**
- **Telegram**: Add your bot token
- **OpenAI**: Add your API key
- **Google Calendar**: Connect OAuth2 with calendar scope

3. **Update Configuration**
- In "Send a text message" node: Update `chatId` to your Telegram chat ID
- In Google Calendar node: Update calendar email address

4. **Set Up Webhooks**
- Ensure n8n has HTTPS (ngrok/cloud deployment)
- Activate Telegram Trigger with webhook URL

5. **Test the Workflow**
- Send a message to your Telegram bot
- Check Google Calendar for the created event

## 💬 Example Messages

The AI understands various formats:
"Team meeting tomorrow at 2pm for 1 hour"
"Lunch with John Friday at 12:30pm"
"Dentist appointment next Monday at 10am for 30 minutes"
"Conference call with sales team in 2 days at 3pm"

## 🔧 Configuration Details

### AI Agent Prompt
The system prompt includes:
- Current date/time context
- Year 2025 focus (configurable)
- Relative date calculation instructions
- JSON extraction requirements

### Calendar Settings
- Timezone: Configurable in n8n settings
- Event format: RFC3339 compliant
- Attendees: Optional email invitation support
- Reminders: Default Google Calendar settings

## 🌐 Deployment Options

### Option 1: Local with ngrok
```bash
docker-compose up -d
ngrok http 5678  # For HTTPS webhooks

Note: This automation requires active n8n instance, API keys, and proper OAuth setup. Test thoroughly before production use.





