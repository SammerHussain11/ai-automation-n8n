# My First N8N Workflow

## Overview

This N8N workflow implements a simple AI-powered chatbot that can provide weather information for Karachi, Pakistan. The workflow uses Google's Gemini AI model for conversational responses and integrates with the OpenWeatherMap API to fetch real-time weather data.

## Workflow Components

### Nodes

1. **When chat message received** (`@n8n/n8n-nodes-langchain.chatTrigger`)

   - Triggers the workflow when a chat message is received
   - Acts as the entry point for user interactions

2. **AI Agent** (`@n8n/n8n-nodes-langchain.agent`)

   - Main AI agent that processes user messages
   - Configured with a system message to handle weather queries by calling the Weather Node
   - Ensures responses are well-formatted

3. **Google Gemini Chat Model** (`@n8n/n8n-nodes-langchain.lmChatGoogleGemini`)

   - Provides the AI language model for generating responses
   - Uses Google Gemini (PaLM) API for conversational AI

4. **Simple Memory** (`@n8n/n8n-nodes-langchain.memoryBufferWindow`)

   - Maintains conversation context using a buffer window memory
   - Allows the AI to remember recent messages for coherent conversations

5. **Weather Node** (`n8n-nodes-base.httpRequestTool`)
   - Makes HTTP requests to the OpenWeatherMap API
   - Fetches weather data for Karachi using the endpoint: `https://api.openweathermap.org/data/2.5/weather?q=karachi&appid={API_KEY}`

## Connections

- **When chat message received** → **AI Agent**
- **Google Gemini Chat Model** → **AI Agent** (as AI language model)
- **Simple Memory** → **AI Agent** (as AI memory)
- **Weather Node** → **AI Agent** (as AI tool)

## Prerequisites

1. **N8N Instance**: This workflow requires an active N8N installation
2. **Google Gemini API Key**: Required for the AI chat model
   - Sign up at [Google AI Studio](https://makersuite.google.com/app/apikey)
   - Create credentials in N8N with the name "Google Gemini(PaLM) Api account"
3. **OpenWeatherMap API Key**: Required for weather data
   - Sign up at [OpenWeatherMap](https://openweathermap.org/api)
   - Replace the `appid` parameter in the Weather Node with your API key

## Setup Instructions

1. Import this workflow JSON into your N8N instance
2. Configure the required credentials:
   - Add your Google Gemini API key to the "Google Gemini Chat Model" node
   - Update the OpenWeatherMap API key in the Weather Node URL
3. Activate the workflow in N8N
4. Set up a webhook or chat interface to trigger the "When chat message received" node

## Usage

1. Send a chat message to the workflow trigger
2. For weather queries, ask something like "What's the weather in Karachi?" or "How's the weather today?"
3. The AI agent will automatically call the Weather Node and provide a formatted response
4. For general conversation, the AI will respond using the Gemini model

## Notes

- The workflow is currently set to inactive (`"active": false`)
- Ensure all API keys are properly configured before activating
- The workflow uses execution order v1
- Memory is maintained using a simple buffer window for conversation context

## Example Interaction

**User:** "What's the weather like in Karachi today?"

**AI Response:** [Formatted weather information fetched from OpenWeatherMap API]

## Troubleshooting

- Verify API keys are correctly set in N8N credentials
- Check OpenWeatherMap API limits and billing
- Ensure the webhook URL is properly configured for chat integration
