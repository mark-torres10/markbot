# MarkBot - Personal AI Agent

A personal AI agent that sounds like Mark using RAG on SMS/iMessage data with persona-based fallback and feedback system.

## 🎯 Project Overview

MarkBot is a lightweight, modular personal AI agent that uses retrieval-augmented generation (RAG) to generate responses that sound like Mark, based on his historical SMS/iMessage conversations. The system includes a persona-based fallback for when no similar messages are found.

## 🏗️ Architecture

- **Frontend**: Next.js with TypeScript, Shadcn/ui, Tailwind CSS v3
- **Backend API**: FastAPI (Python 3.12) on Railway
- **Vector DB**: Qdrant (local Docker dev, Qdrant Cloud for production)
- **Data & Auth**: Supabase (data storage and authentication)
- **LLM**: OpenAI (GPT-4) with embeddings (text-embedding-3-small)
- **Deployment**: Vercel (frontend), Railway (backend API)

## 📋 Project Status

**Linear Project**: [Personal AI Agent with RAG and Persona Fallback](https://linear.app/metresearch/project/personal-ai-agent-with-rag-and-persona-fallback-93acf2283a28)

### Tickets

**Phase 1 (Parallel Execution):**
- [MAR-1](https://linear.app/metresearch/issue/MAR-1/build-data-pipeline-and-persona-generation-system): Build data pipeline and persona generation system
- [MAR-2](https://linear.app/metresearch/issue/MAR-2/create-frontend-mvp-with-chat-interface-and-auth): Create frontend MVP with chat interface and auth

**Phase 2 (After Data Pipeline):**
- [MAR-3](https://linear.app/metresearch/issue/MAR-3/implement-backend-api-with-rag-system-and-persona-fallback): Implement backend API with RAG system and persona fallback

**Phase 3 (Integration):**
- [MAR-4](https://linear.app/metresearch/issue/MAR-4/integrate-frontend-and-backend-with-final-polish): Integrate frontend and backend with final polish

**Phase 4 (Optional - Fine-tuning):**
- [MAR-5](https://linear.app/metresearch/issue/MAR-5/implement-fine-tuning-with-qwen-and-mistral-models): Implement fine-tuning with Qwen and Mistral models

**Phase 5 (Optional - Evaluation Platform):**
- [MAR-6](https://linear.app/metresearch/issue/MAR-6/build-evaluation-platform-backend-for-response-comparison): Build evaluation platform backend for response comparison
- [MAR-7](https://linear.app/metresearch/issue/MAR-7/create-evaluation-platform-frontend-for-blind-testing): Create evaluation platform frontend for blind testing

## 🚀 Quick Start

### Prerequisites
- Python 3.12 with UV package manager
- Docker for local Qdrant development
- OpenAI API access
- Supabase project
- Vercel and Railway accounts

### Development Setup
1. **Data Pipeline**: Process raw SMS data and create embeddings
2. **Frontend**: Set up Next.js app with authentication
3. **Backend**: Deploy FastAPI with RAG system
4. **Integration**: Connect all components and polish

## 📁 Project Structure

```
projects/markbot-personal-ai-agent/
├── spec.md              # Complete project specification
├── braindump.md         # Initial brainstorming and context
├── tickets/             # Individual ticket documentation
└── README.md           # This file
```

## 🎯 Success Criteria

- Functional chat interface that responds to user queries
- RAG system successfully retrieves relevant context from message history
- Persona fallback system works when no similar messages found
- Feedback system collects and stores user ratings
- Response quality meets subjective "sounds like Mark" criteria
- System deployed and accessible via Vercel/Railway

## 🔮 Future Enhancements

- Fine-tune in-house models (Qwen/Mistral) using LoRA/QLoRA adapters
- Multi-persona or emotion-conditioning layer
- Dynamic memory updates for new messages
- Behavioral drift detection and agent evolution
- Evaluation platform for comparing RAG, persona, and baseline responses

## 📚 Documentation

- [Specification](spec.md) - Complete project specification
- [Brain Dump](braindump.md) - Initial planning and context
- [Linear Project](https://linear.app/metresearch/project/personal-ai-agent-with-rag-and-persona-fallback-93acf2283a28) - Project tracking and tickets 