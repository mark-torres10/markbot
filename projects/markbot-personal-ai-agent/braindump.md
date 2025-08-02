# MarkBot Brain Dump

## Project Overview
**MarkBot** is a personal AI agent trained on personal text messages using RAG to generate responses that sound like the user. Lightweight, modular, and easy-to-extend app that can later evolve into more advanced agents.

## Core Requirements
- **Purpose**: Create a bot that sounds like Mark based on historical conversations
- **Architecture**: RAG-based system with vector search + persona-based fallback
- **MVP Focus**: Core RAG functionality with simple UI + feedback system
- **Success Criteria**: Response quality, style similarity, and user satisfaction
- **Personal Project**: Fun experiment for RAG strategies and embedding techniques

## Technical Stack
- **Frontend**: Next.js with TypeScript
- **UI Components**: Shadcn/ui
- **Styling**: Tailwind CSS v3
- **Backend API**: FastAPI (Python 3.12) on Railway
- **Package Management**: UV
- **Vector DB**: Qdrant (local Docker dev, Qdrant Cloud for production)
- **LLM**: OpenAI (GPT-4)
- **Embeddings**: OpenAI text-embedding-3-small
- **Data & Auth**: Supabase (data storage and authentication)
- **Deployment**: Vercel (frontend), Railway (backend API)

## Data Source
- SMS/iMessage history from `chat.db` (macOS export)
- Data currently in `raw/` directory as text file
- Moderate volume, manageable locally
- Format: `{ timestamp, speaker, text }`
- Requires data pipeline for processing and chunking

## Architecture Components

### Frontend (Next.js)
- Main tab `/markbot` for chat interface
- Secondary tab `/emails` for feedback and reviews (placeholder content)
- Simple chat UI: text input → display response
- "Leave Feedback and Review" button for each MarkBot response
- Connect to backend via `/api/ask-markbot`
- Connect to Supabase for feedback storage
- Deploy to Vercel

### Backend API (FastAPI on Railway)
- RAG logic handler
- Embedding generation
- Vector search orchestration
- OpenAI API integration
- Deploy to Railway

### Data & Auth (Supabase)
- User authentication via OAuth
- Data storage for feedback and user data
- Secure credential management

### Vector Store (Qdrant)
- Local Docker setup for development
- Collection: `messages` with 1536-dim cosine vectors
- Similarity search using cosine distance
- Migrate to Qdrant Cloud for production

## RAG Flow with Persona Fallback
1. Receive user query
2. Embed query using OpenAI embeddings
3. Search top-k similar past messages in Qdrant
4. If similar messages found:
   - Construct RAG prompt with retrieved context
   - Send to OpenAI GPT-4
   - Return Mark-style reply
5. If no similar messages found:
   - Use persona-based template (generated from message clusters)
   - Send to OpenAI GPT-4 with persona prompt
   - Return Mark-style reply

## Persona Generation Process
1. Process all message chunks through clustering
2. Perform topic modeling on each cluster
3. Analyze response patterns within each cluster
4. Generate style guide: "This is how Mark responds to [topic]"
5. Create default persona template for fallback responses

## Development Setup
- Qdrant local: `docker run -p 6333:6333 qdrant/qdrant`
- Backend: FastAPI + uvicorn locally
- Frontend connects to local backend
- Environment variables managed in Vercel/Railway

## Implementation Order
1. **Data Pipeline** (parallel with frontend)
   - Process raw text file
   - Clean and chunk data
   - Generate embeddings
   - Load into Qdrant
   - Generate persona clusters and style guide
2. **Frontend** (parallel with data pipeline)
   - Next.js app with chat interface
   - Shadcn/ui components
   - Tailwind CSS styling
   - Supabase authentication integration
3. **Backend API** (after data pipeline)
   - FastAPI server with async/await on Railway
   - Vector search logic
   - OpenAI integration
   - Persona fallback system
4. **Data & Auth** (parallel with backend)
   - Supabase setup for data storage
   - OAuth authentication implementation
   - Feedback system integration

## Future Considerations
- Fine-tuning on message-reply pairs
- Multi-persona or emotion-conditioning
- Dynamic memory updates
- Behavioral drift detection
- Agent evolution capabilities

## Data Pipeline Requirements
- Process raw text file from `raw/` directory
- Clean data: filter out multimedia content (images, files, hashes)
- Create text chunks of 10 messages each
- Experiment with various chunk sizes
- Generate embeddings for chunks
- Load into Qdrant vector database

## UI/UX Requirements
- Simple ChatGPT-style conversation thread
- Optional dropdown to show retrieved context (like AI agent "thinking" dropdown)
- "Leave Feedback and Review" button for each MarkBot response
- Simple loading animation for response generation
- Error state component: "Hey there's an error, the backend is down"
- Clean, minimal interface
- Two tabs: `/markbot` (main) and `/emails` (feedback placeholder)

## Success Metrics
- Response quality (subjective assessment)
- Style similarity to Mark's voice
- User satisfaction scores
- Feedback collection and analysis

## Technical Decisions Made
- **Fine-tuning**: Cloud-based approach, test both Quen and Mistral models
- **Authentication**: Simple OAuth with rate limiting and API protection
- **GitHub Workflow**: Follow GITHUB_OPERATIONS.md guidelines
- **Package Management**: UV for Python 3.12

## Questions to Address
- Testing strategy for RAG quality
- Feedback analysis and improvement loop

## Constraints
- MVP scope - core RAG functionality first
- No conda environment needed
- Local data processing
- Simple timeline expectations
- Focus on response quality over metrics

## Dependencies
- Qdrant account (already have)
- Railway account (already have)
- Vercel deployment (to be set up)
- OpenAI API access
- Docker for local Qdrant development 