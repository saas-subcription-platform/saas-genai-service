# SaaS GenAI Service
Python-based GenAI chatbot microservice for the SaaS Subscription Platform.

Tech Stack
Python
FastAPI
Google Gemini
Uvicorn

Features
Application-specific SaaS chatbot
Subscription and module information
Session-based conversation memory
End-chat session reset
CORS support for React frontend

Project Structure
saas-genai-service/
├── app.py
├── knowledge.txt
├── requirements.txt
├── run.bat
├── .env
├── .gitignore
└── venv/

Setup
1. Clone the repository
cd saas-genai-service
2. Create virtual environment
python -m venv venv
3. Install dependencies
pip install -r requirements.txt
4. Configure Gemini API

Create a .env file in the project root:

GEMINI_API_KEY=your_api_key_here

Do not commit .env to Git.

5. Start the service

Windows: double-click run.bat

Or run:

.\run.bat

Service URL:

http://127.0.0.1:8000

Swagger documentation:

http://127.0.0.1:8000/docs

API Endpoints
GET /

Checks whether the GenAI service is running.

POST /chat

Send a message to the chatbot.

Request:

{
  "session_id": "test123",
  "message": "What subscription plans are available?"
}

The same session_id maintains conversation context.

POST /chat/end

Ends the current chat and clears its conversation memory.

Request:

{
  "session_id": "test123"
}

After ending the chat, the session starts fresh.

Frontend Integration

The React frontend runs on:

http://localhost:5173

It can call:

POST http://127.0.0.1:8000/chat
POST http://127.0.0.1:8000/chat/end

The frontend should generate a unique session_id when a new chat starts and use the same ID for messages during that chat.

Important
Keep the Gemini API key private.
Do not commit .env.
Do not commit venv/.
knowledge.txt contains the application's chatbot knowledge.