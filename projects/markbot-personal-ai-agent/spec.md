# 🧾 Spec: Personal AI Agent with RAG and Persona Fallback

## 1. Problem Statement

**Who is affected?** Mark wants to create a personal AI agent that sounds like him based on his SMS/iMessage history.

**What's the pain point?** No existing solution provides a lightweight, modular way to create a personal AI that reflects one's own voice and communication style using RAG techniques.

**Why now?** This is a fun personal project to experiment with RAG strategies and embedding techniques, while building a foundation for more advanced personal AI agents.

**Strategic link?** This serves as a learning platform for understanding RAG implementation, vector databases, and persona generation, with potential to evolve into more sophisticated personal AI systems.

## 2. Desired Outcomes & Metrics

**What should be true once this is done?**
- A functional chat interface where users can interact with MarkBot
- Responses that sound authentically like Mark based on his message history
- A feedback system to collect and analyze response quality
- A persona-based fallback system for when RAG doesn't find relevant context

**How do we measure it?**
- Response quality (subjective assessment)
- Style similarity to Mark's voice
- User satisfaction scores (1-5 scale)
- Feedback collection and analysis
- Successful fallback to persona when RAG context is insufficient

## 3. In Scope / Out of Scope

**In Scope:**
- Data pipeline to process SMS/iMessage text file
- RAG system using Qdrant vector database
- Persona generation from message clusters and topic modeling
- Next.js frontend with chat interface
- Data storage and authentication with Supabase
- FastAPI backend API with async/await
- Local development setup with Docker
- Deployment to Vercel (frontend) and Railway (backend API)

**Out of Scope:**
- Real-time message processing
- Multi-user support
- Email integration (placeholder only for now)
- Complex analytics or dashboards
- Mobile app development

**Optional/Future Scope:**
- Fine-tuning in-house models (Qwen/Mistral with LoRA/QLoRA adapters)
- Advanced model training and optimization
- Evaluation platform for comparing RAG, persona, and baseline responses

## 4. Stakeholders & Dependencies

**Who is impacted?**
- Mark (primary user and developer)
- Future users of the personal AI system

**What teams, systems, or sign-offs are involved?**
- OpenAI API (for embeddings and LLM)
- Qdrant Cloud (for production vector database)
- Supabase (for data storage and authentication)
- Vercel (for frontend deployment)
- Railway (for backend API deployment)

**Dependencies:**
- Raw SMS/iMessage data in text format
- Docker for local Qdrant development
- Python 3.12 and UV package manager
- Existing Vercel and Railway accounts

## 5. Risks / Unknowns

**Failure modes:**
- No similar messages found in vector database (mitigated by persona fallback)
- OpenAI API rate limits or costs (need monitoring)
- Data quality issues in raw text file (need robust preprocessing)
- Vector database performance with large datasets
- Security vulnerabilities in data handling or API endpoints

**Research spikes required:**
- Optimal chunking strategy for message embeddings
- Topic modeling and clustering algorithms
- Persona prompt engineering for fallback responses

**Decision uncertainties:**
- Best clustering approach for persona generation
- Optimal number of similar messages to retrieve
- Feedback system design and metrics

## 6. UX Notes & Accessibility

**User flows:**
- Main chat interface at `/markbot` with simple input/output
- Optional "thinking" dropdown to show retrieved context
- "Leave Feedback and Review" button for each response
- Secondary `/emails` tab for future feedback system

**Design system impact:**
- Uses Shadcn/ui components
- Tailwind CSS v3 for styling
- Simple, clean interface following ChatGPT patterns

**Accessibility considerations:**
- Basic keyboard navigation
- Screen reader compatibility
- Clear error states and loading indicators

## 7. Technical Notes

**Architecture hints:**
- FastAPI with async/await for embedding and LLM calls
- Qdrant vector database with 1536-dim cosine vectors
- Persona generation through clustering and topic modeling
- Supabase for data storage and authentication
- Railway for backend API hosting
- Vercel for frontend hosting

**Known constraints:**
- Python 3.12 requirement
- UV package manager
- Local Docker setup for development
- OpenAI API dependency
- Security requirements for personal data handling

**Implementation direction:**
- Start with data pipeline and persona generation
- Build frontend and backend in parallel
- Integrate RAG system after data is processed
- Add Supabase authentication and data storage
- Deploy to Railway (backend API) and Vercel (frontend)

## 8. Compliance, Cost, GTM

**Legal/privacy implications:**
- Personal data processing (SMS/iMessage history)
- OpenAI API data usage
- No external user data collection beyond feedback
- Data security and privacy protection requirements

**Infra costs:**
- OpenAI API usage (embeddings + LLM calls)
- Qdrant Cloud subscription
- Supabase usage (data storage and auth)
- Railway hosting (backend API)
- Vercel hosting (frontend)

**Launch implications:**
- Personal project, no formal launch required
- No marketing or support training needed
- Documentation for personal use and learning

## 9. Success Criteria

**Measurable definition of "done":**
- Functional chat interface that responds to user queries
- RAG system successfully retrieves relevant context from message history
- Persona fallback system works when no similar messages found
- Feedback system collects and stores user ratings
- Response quality meets subjective "sounds like Mark" criteria
- System deployed and accessible via Vercel/Railway
- Local development environment fully functional

**Acceptance criteria:**
- MVP delivers core RAG functionality with persona fallback
- UI is clean and intuitive
- Error handling works gracefully
- Feedback collection is functional
- Performance is acceptable for personal use
- Security measures prevent data leaks and unauthorized access
- Basic authentication protects sensitive endpoints

## 10. Security & Authentication

**Security requirements:**
- No sensitive information in logs (PII, API keys, personal messages)
- Secure handling of personal SMS/iMessage data
- Basic authentication for API endpoints
- Environment variable protection for API keys
- Input validation and sanitization
- Rate limiting to prevent abuse

**Authentication approach:**
- Supabase OAuth implementation
- Environment-based configuration
- Secure storage of credentials
- Audit trail for data access
- Rate limiting and basic API protection

## 11. Fine-tuning Extension (Optional)

**Future capability:**
- Fine-tune in-house models (Qwen/Mistral) using LoRA/QLoRA adapters
- Replace OpenAI with local fine-tuned models
- Maintain same RAG + persona architecture
- Performance optimization for local inference

**Technical approach:**
- Use Hugging Face transformers library
- Implement LoRA/QLoRA for efficient fine-tuning
- Cloud-based training (no local GPU requirements)
- Test both Qwen and Mistral models for comparison
- Create training pipeline for message-reply pairs
- Model serving integration with existing backend

## 12. Evaluation Platform (Optional)

**Future capability:**
- Blind comparison system for three response types:
  1. RAG implementation + persona
  2. Persona only
  3. Baseline ChatGPT (no prompting)
- Continuous evaluation platform for measuring effectiveness
- Statistical analysis of response quality and user preferences

**Technical approach:**
- Frontend interface for blind A/B/C testing
- Backend API for generating and storing comparison responses
- Database for storing evaluation results and user preferences
- Analytics dashboard for measuring response effectiveness
- Integration with existing MarkBot system for seamless testing 