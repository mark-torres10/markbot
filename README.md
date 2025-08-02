# MarkBot

A collection of AI tools, agents, and projects for personal AI development and experimentation.

## 🎯 Overview

This repository contains various AI projects and tools, including the MarkBot personal AI agent - a system that uses RAG (Retrieval-Augmented Generation) to create responses that sound like Mark based on his SMS/iMessage history.

## 📁 Projects

### [MarkBot Personal AI Agent](./projects/markbot-personal-ai-agent/)

A personal AI agent that sounds like Mark using RAG on SMS/iMessage data with persona-based fallback and feedback system.

**Key Features:**
- RAG system using Qdrant vector database
- Persona-based fallback for when no similar messages exist
- Next.js frontend with chat interface
- FastAPI backend with async/await
- Supabase for data storage and authentication
- Evaluation platform for comparing different response approaches

**Tech Stack:**
- Frontend: Next.js + Shadcn/ui + Tailwind CSS v3
- Backend: FastAPI (Python 3.12) on Railway
- Vector DB: Qdrant (local Docker → Qdrant Cloud)
- Data & Auth: Supabase (OAuth + data storage)
- LLM: OpenAI (GPT-4 + embeddings)

**Status:** Planning and setup complete - ready for implementation

**Linear Project:** [Personal AI Agent with RAG and Persona Fallback](https://linear.app/metresearch/project/personal-ai-agent-with-rag-and-persona-fallback-93acf2283a28)

## 🛠️ AI Tools

### [AI Tools](./ai-tools/)

A collection of AI agent personas, task instructions, and learning resources for building AI systems.

**Contents:**
- Agent personas for different roles (engineering, rapid prototyping, etc.)
- Task instructions for project management and execution
- Learning resources for AI development
- Prompt engineering and improvement guides

## 🚀 Quick Start

### Prerequisites
- Python 3.12 with UV package manager
- Docker for local development
- OpenAI API access
- Supabase, Qdrant, Railway, and Vercel accounts

### Development Setup
1. Clone the repository
2. Navigate to specific project directories
3. Follow individual project README files for setup instructions

## 📚 Documentation

- [MarkBot Project Specification](./projects/markbot-personal-ai-agent/spec.md)
- [MarkBot Brain Dump](./projects/markbot-personal-ai-agent/braindump.md)
- [AI Tools Documentation](./ai-tools/README.md)

## 🔮 Future Projects

- Additional personal AI agents
- AI tool integrations
- Research and experimentation projects

## 📄 License

Personal project - not for distribution.

---

**Note:** This repository contains personal AI projects and tools for learning and experimentation purposes.
