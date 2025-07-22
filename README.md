Chat AI Backend
Overview
This project is a Django-based backend for a chat AI application, integrating with OpenAI's GPT and Google's Gemini models. It supports creating, managing, and retrieving chat sessions and messages, with endpoints for interacting with AI models and fetching chat history.
Features

User Authentication: Custom user model with email-based authentication.
Chat Management: Create and manage chat sessions with unique IDs.
AI Integration: Supports OpenAI GPT and Google Gemini for generating responses.
Chat History: Retrieve chats from today, yesterday, or the past seven days.
RESTful API: Built with Django REST Framework for easy integration with frontends.
CORS Support: Configured for local development with specific origins.

Project Structure

models.py: Defines the database models:
CustomUser: Extends Django's AbstractUser with a unique email field.
Chat: Stores chat sessions with a UUID, title, and creation timestamp.
ChatMessage: Stores messages with roles (user or assistant), content, and timestamps.


serializers.py: Serializes Chat and ChatMessage models for API responses.
urls.py: Defines API endpoints for prompting AI models and retrieving chat data.
views.py: Contains logic for handling API requests, including AI interactions and chat history retrieval.
settings.py: Configures CORS, custom user model, and API keys for OpenAI and Gemini.

Installation
Prerequisites

Python 3.8+
Django hunting for Django
PostgreSQL/MySQL (or any supported database)
API keys for OpenAI and Google Gemini

Steps

Clone the repository:git clone <repository-url>
cd chat-ai-backend


Create a virtual environment and activate it:python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate


Install dependencies:pip install -r requirements.txt


Set up environment variables:
Create a .env file in the project root.
Add the following:OPENAI_API_KEY=your_openai_api_key
GEMINI_API_KEY=your_gemini_api_key




Configure your database in settings.py and run migrations:python manage.py makemigrations
python manage.py migrate


Run the development server:python manage.py runserver



API Endpoints

POST /prompt_gpt/: Send a prompt to OpenAI's GPT model and save the conversation.
Request: { "chat_id": "<uuid>", "content": "<user_message>" }
Response: { "reply": "<gpt_response>" }


POST /prompt_gemini/: Send a prompt to Google's Gemini model and save the conversation.
Request: { "chat_id": "<uuid>", "content": "<user_message>" }
Response: { "reply": "<gemini_response>" }


GET /get_chat_messages//: Retrieve all messages for a specific chat session.
Response: List of messages with id, role, content, and created_at.


GET /todays_chat/: Get up to 10 chat sessions created today.
Response: List of chats with all fields.


GET /yesterdays_chat/: Get up to 10 chat sessions from yesterday.
Response: List of chats with all fields.


GET /seven_days_chat/: Get up to 10 chat sessions from the past seven days (excluding today and yesterday).
Response: List of chats with all fields.



Configuration

CORS: Allowed origins are set to http://localhost:5173, http://localhost:5174, and http://localhost:5175 for local development.
API Keys: Store OpenAI and Gemini API keys in environment variables (OPENAI_API_KEY, GEMINI_API_KEY).
Gemini Model: Configured to use gemini-1.5-flash by default.

Usage

Start a new chat session by sending a POST request to /prompt_gpt/ or /prompt_gemini/ with a unique chat_id (UUID) and user message.
The system generates a title for the chat based on the user message (up to 5 words).
Messages are stored in the database and can be retrieved using /get_chat_messages/<pk>/.
Use /todays_chat/, /yesterdays_chat/, or /seven_days_chat/ to fetch recent chat sessions.

Dependencies

Django
Django REST Framework
django-cors-headers
openai
google-generativeai
python-dotenv

Notes

Ensure API keys are securely stored in environment variables and not hardcoded.
The system limits chat history to the last 10 messages for context in AI prompts.
Error handling is implemented for API failures, returning appropriate HTTP status codes.
The backend is designed to work with a frontend running on the specified CORS origins.

Contributing

Fork the repository.
Create a feature branch (git checkout -b feature/new-feature).
Commit changes (git commit -m 'Add new feature').
Push to the branch (git push origin feature/new-feature).
Create a Pull Request.

License
This project is licensed under the MIT License.