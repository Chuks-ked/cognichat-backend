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





Clone the repository:

