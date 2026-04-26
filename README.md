<p align="center">
  <h1 align="center">⚡ AutoOps AI</h1>
  <p align="center"><strong>The Autonomous Enterprise Workflow Agent</strong></p>
  <p align="center">
    <em>"From RPA to Reasoning Process Automation (RPA 2.0)"</em>
  </p>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Python-3.11+-blue?style=for-the-badge&logo=python&logoColor=white" alt="Python">
  <img src="https://img.shields.io/badge/FastAPI-0.110+-green?style=for-the-badge&logo=fastapi&logoColor=white" alt="FastAPI">
  <img src="https://img.shields.io/badge/React-18+-61DAFB?style=for-the-badge&logo=react&logoColor=black" alt="React">
  <img src="https://img.shields.io/badge/LangChain-0.2+-orange?style=for-the-badge&logo=chainlink&logoColor=white" alt="LangChain">
  <img src="https://img.shields.io/badge/License-MIT-yellow?style=for-the-badge" alt="License">
</p>

---

## 🚀 What is AutoOps AI?

**AutoOps AI** is a fully autonomous enterprise workflow agent that connects to your company tools — email, Slack, CRM, ERP — and autonomously completes repetitive business workflows end-to-end.

**Not a chatbot. Not an assistant. A decision-making workflow executor.**

> *"We are not building another SaaS tool. We are building digital employees."*

### Key Capabilities

- 🔍 **Event Understanding** — Reads and comprehends incoming emails, tickets, and documents
- 🧠 **Autonomous Decision Making** — Uses LLM reasoning to determine the best next action
- ⚡ **Cross-System Execution** — Executes tasks across Gmail, Slack, CRM, and more
- 📚 **Continuous Learning** — Improves from human feedback and past interactions
- 🔄 **Self-Evaluation** — Validates its own outputs before executing actions

---

## 🎯 Problem We Solve

Enterprises waste **30–40% of employee time** on repetitive, fragmented workflows:

| Problem | Impact |
|---|---|
| Manual data movement between tools | Hours wasted daily |
| Delayed approval chains | Revenue bottlenecks |
| Human error in repetitive tasks | Compliance & quality risks |
| Context switching across 5+ tools | Productivity drain |

**Traditional solutions fail:**
- **RPA** → Rule-based, brittle, breaks on change
- **Chatbots** → Conversational only, can't execute workflows
- **Zapier/Integrations** → Trigger-action, no reasoning capability

**AutoOps AI** combines LLM reasoning, tool-use APIs, persistent memory, and self-evaluation into a true autonomous agent.

---

## 🏗 Architecture

```
                    ┌─────────────────────┐
                    │   React Dashboard   │
                    │  (Monitor & Control) │
                    └──────────┬──────────┘
                               │ REST + WebSocket
                    ┌──────────▼──────────┐
                    │   FastAPI Backend    │
                    │  (Orchestrator API)  │
                    └──────────┬──────────┘
                               │
              ┌────────────────┼────────────────┐
              │                │                │
    ┌─────────▼──────┐ ┌──────▼───────┐ ┌──────▼───────┐
    │  Agent Engine   │ │  Memory Store │ │  Tool Router  │
    │  (LLM + Chain)  │ │ (FAISS/       │ │  (API Layer)  │
    │                 │ │  Pinecone)    │ │               │
    └─────────┬──────┘ └──────────────┘ └──────┬───────┘
              │                                 │
        ┌─────▼───────┐              ┌──────────┤
        │Self-Evaluate │         ┌────▼──┐ ┌────▼──┐ ┌────▼──┐
        │   & Learn    │         │ Gmail │ │ Slack │ │  CRM  │
        └─────────────┘         └───────┘ └───────┘ └───────┘
```

### Core Components

| Component | Description |
|---|---|
| **Agent Engine** | LLM-powered reasoning core using LangChain/LangGraph |
| **Memory Store** | Vector database for persistent context and learning |
| **Tool Router** | Unified API layer for enterprise tool integrations |
| **Self-Evaluation Loop** | Agent validates outputs before execution |
| **Dashboard** | Real-time monitoring and human-in-the-loop controls |

---

## 🛠 Tech Stack

| Layer | Technology | Version |
|---|---|---|
| **Runtime** | Python | 3.11+ |
| **Backend Framework** | FastAPI | 0.110+ |
| **LLM Orchestration** | LangChain / LangGraph | 0.2+ |
| **LLM Provider** | OpenAI GPT-4 / Open-source | Latest |
| **Vector Database** | FAISS / Pinecone | Latest |
| **Frontend** | React + Vite | 18+ |
| **Database** | SQLite (dev) / PostgreSQL (prod) | — |
| **Integrations** | Gmail API, Slack SDK, Mock CRM | — |

---

## 📁 Project Structure

```
AutoOps-AI/
├── backend/
│   ├── app/
│   │   ├── main.py              # FastAPI application entry point
│   │   ├── config.py            # Configuration & environment variables
│   │   ├── models/              # Pydantic models & database schemas
│   │   │   ├── workflow.py
│   │   │   ├── agent.py
│   │   │   └── events.py
│   │   ├── agents/              # AI Agent logic
│   │   │   ├── base_agent.py    # Base agent class
│   │   │   ├── support_agent.py # Customer support agent
│   │   │   ├── sales_agent.py   # Sales qualification agent
│   │   │   └── orchestrator.py  # Multi-agent orchestrator
│   │   ├── tools/               # Enterprise tool integrations
│   │   │   ├── gmail_tool.py    # Gmail API integration
│   │   │   ├── slack_tool.py    # Slack API integration
│   │   │   ├── crm_tool.py      # CRM integration (mock/real)
│   │   │   └── tool_registry.py # Tool registration & routing
│   │   ├── memory/              # Agent memory & context
│   │   │   ├── vector_store.py  # FAISS/Pinecone integration
│   │   │   └── context.py       # Context management
│   │   ├── evaluation/          # Self-evaluation engine
│   │   │   ├── evaluator.py     # Output validation
│   │   │   └── feedback.py      # Human feedback loop
│   │   ├── routes/              # API endpoints
│   │   │   ├── workflows.py     # Workflow management
│   │   │   ├── agents.py        # Agent control
│   │   │   └── events.py        # Event ingestion
│   │   └── services/            # Business logic layer
│   │       ├── workflow_engine.py
│   │       └── event_processor.py
│   ├── tests/                   # Unit & integration tests
│   ├── requirements.txt         # Python dependencies
│   └── Dockerfile               # Backend container
├── frontend/
│   ├── src/
│   │   ├── components/          # React components
│   │   │   ├── Dashboard.jsx    # Main dashboard
│   │   │   ├── AgentMonitor.jsx # Agent activity monitor
│   │   │   ├── WorkflowView.jsx # Workflow visualization
│   │   │   ├── EventFeed.jsx    # Real-time event feed
│   │   │   └── MetricsPanel.jsx # Performance metrics
│   │   ├── hooks/               # Custom React hooks
│   │   ├── services/            # API service layer
│   │   ├── App.jsx              # Main application
│   │   └── main.jsx             # Entry point
│   ├── public/
│   ├── package.json
│   ├── vite.config.js
│   └── Dockerfile               # Frontend container
├── docker-compose.yml           # Full stack orchestration
├── .env.example                 # Environment variables template
├── PROJECT_CANVAS.md            # Project canvas & strategy
└── README.md                    # This file
```

---

## ⚡ Quick Start

### Prerequisites

- Python 3.11+
- Node.js 18+
- OpenAI API key (or compatible LLM provider)
- Gmail API credentials (for email integration)
- Slack Bot Token (for Slack integration)

### 1. Clone the Repository

```bash
git clone https://github.com/your-team/autoops-ai.git
cd autoops-ai
```

### 2. Backend Setup

```bash
cd backend

# Create virtual environment
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate

# Install dependencies
pip install -r requirements.txt

# Configure environment
cp .env.example .env
# Edit .env with your API keys

# Run the backend
uvicorn app.main:app --reload --port 8000
```

### 3. Frontend Setup

```bash
cd frontend

# Install dependencies
npm install

# Run the development server
npm run dev
```

### 4. Access the Application

- **Dashboard**: http://localhost:5173
- **API Docs**: http://localhost:8000/docs
- **API Redoc**: http://localhost:8000/redoc

---

## 🎬 Demo Scenario

### Customer Support Resolution Agent

Watch AutoOps AI handle a complete support workflow autonomously:

```
1. 📧 New support email arrives from a frustrated customer
2. 🔍 AI reads and understands the email sentiment & content
3. 🏷️ Categorizes the issue → "Billing Dispute - Priority: High"
4. ✍️ Drafts a contextual, empathetic reply using knowledge base
5. 📊 Updates CRM with interaction record & customer sentiment
6. 🎫 Creates a support ticket with full context
7. 💬 Notifies the support team on Slack with a summary
```

**Total time: < 30 seconds** (vs. 15–20 minutes manually)

---

## 🔌 Supported Integrations

| Integration | Status | Description |
|---|---|---|
| **Gmail** | ✅ Ready | Read, categorize, and respond to emails |
| **Slack** | ✅ Ready | Send notifications and team updates |
| **Mock CRM** | ✅ Ready | Create/update customer records |
| **Salesforce** | 🔄 Roadmap | Full CRM integration |
| **HubSpot** | 🔄 Roadmap | Marketing & sales automation |
| **Jira** | 🔄 Roadmap | Issue tracking integration |
| **Microsoft 365** | 🔄 Roadmap | Email, Calendar, Teams |

---

## 📊 Agent Use Cases

| Agent | Domain | What It Does |
|---|---|---|
| **Support Agent** | Customer Service | Resolves tickets, drafts replies, escalates issues |
| **Sales Agent** | Sales | Qualifies leads, enriches data, routes to reps |
| **Compliance Agent** | Legal/Finance | Monitors documents for policy violations |
| **Invoice Agent** | Accounting | Reads invoices, validates data, triggers payments |
| **HR Agent** | Human Resources | Automates onboarding across IT, HR, admin |

---

## 🔧 Configuration

### Environment Variables

```env
# LLM Configuration
OPENAI_API_KEY=sk-your-api-key
LLM_MODEL=gpt-4
LLM_TEMPERATURE=0.3

# Gmail Integration
GMAIL_CREDENTIALS_PATH=./credentials/gmail.json
GMAIL_TOKEN_PATH=./credentials/gmail_token.json

# Slack Integration
SLACK_BOT_TOKEN=xoxb-your-bot-token
SLACK_CHANNEL_ID=C0123456789

# Vector Database
VECTOR_DB_TYPE=faiss  # or 'pinecone'
PINECONE_API_KEY=your-pinecone-key
PINECONE_ENVIRONMENT=us-east-1

# Database
DATABASE_URL=sqlite:///./autoops.db

# Application
APP_ENV=development
LOG_LEVEL=INFO
```

---

## 🧪 Testing

```bash
# Run backend tests
cd backend
pytest tests/ -v

# Run with coverage
pytest tests/ --cov=app --cov-report=html

# Run frontend tests
cd frontend
npm test
```

---

## 📈 Performance Metrics

| Metric | Target | Description |
|---|---|---|
| **Workflow Completion Rate** | > 95% | Percentage of workflows completed without human intervention |
| **Average Resolution Time** | < 2 min | Time from event to workflow completion |
| **Agent Accuracy** | > 90% | Correctness of agent decisions |
| **Human Escalation Rate** | < 15% | Percentage of tasks requiring human review |
| **Cost Efficiency** | 10x | Cost reduction vs. manual processing |

---

## 🗺 Roadmap

### ✅ Phase 1: Hackathon MVP (Current)
- Core agent engine with LLM reasoning
- Gmail, Slack, and Mock CRM integrations
- React monitoring dashboard
- Self-evaluation loop
- Live demo scenario

### 🔄 Phase 2: Beta (Month 1–3)
- Real CRM integrations (Salesforce, HubSpot)
- Multi-agent orchestration
- Human-in-the-loop approval workflows
- Audit trail & compliance logging

### 📋 Phase 3: Growth (Month 3–6)
- Industry-specific agent templates
- Self-learning agent memory
- Enterprise SSO & security
- API marketplace for custom integrations

### 🚀 Phase 4: Scale (Month 6–12)
- Multi-agent collaboration framework
- Agent performance analytics
- White-label enterprise deployment
- Agent marketplace ecosystem

---

## 🏆 Why AutoOps AI Wins

| vs. Traditional RPA | vs. Chatbots | vs. Workflow Tools |
|---|---|---|
| ✅ Reasoning, not rules | ✅ Executes, not just chats | ✅ Autonomous, not triggered |
| ✅ Adapts to change | ✅ Cross-system actions | ✅ Learns from feedback |
| ✅ No brittle scripts | ✅ Full workflow capability | ✅ Decision-making AI |

---

## 🤝 Contributing

We welcome contributions! Please see our [Contributing Guide](CONTRIBUTING.md) for details.

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

---

## 📄 License

This project is licensed under the MIT License — see the [LICENSE](LICENSE) file for details.

---

## 👥 Team

| Name | Role |
|---|---|
| **Guru Prasath** | AI/ML Engineer & Strategy Lead |
| **Jeevanandam** | Full-Stack Developer & Systems Architect |
| **Jayasuriya** | Backend & Tester |

---

<p align="center">
  <strong>Built with 🔥 for Hackathon 2026</strong><br>
  <em>AI Agents for Enterprise — Theme 1</em><br><br>
  <strong>"We are not building another SaaS tool. We are building digital employees."</strong>
</p>
