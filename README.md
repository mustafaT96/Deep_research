# 🔬 Deep Research — Multi-Agent AI Research System

An autonomous multi-agent system that takes a research query, plans and executes web searches in parallel, synthesizes a detailed report, and emails it to you — all with a single click via a Gradio UI.

---

## 🧠 How It Works

The system is built using the [OpenAI Agents SDK](https://github.com/openai/openai-agents-python) and orchestrates four specialized agents in a pipeline:
User Query  
│  
▼  
Planner Agent  ──►  generates 5 search queries  
│  
▼  
Search Agents  ──►  run in parallel, each summarizes web results  
│  
▼  
Writer Agent   ──►  synthesizes a detailed markdown report (1000+ words)  
│  
▼  
Email Agent    ──►  formats and sends the report via SendGrid  

---

## 🤖 Agents

| Agent | Model | Role |
|-------|-------|------|
| **Planner Agent** | gpt-4o-mini | Takes the user query and generates 5 targeted web search terms |
| **Search Agent** | gpt-4o-mini | Searches the web for a given term and returns a concise 2-3 paragraph summary |
| **Writer Agent** | gpt-4o-mini | Synthesizes all search results into a structured, detailed markdown report |
| **Email Agent** | gpt-4o-mini | Converts the report to HTML and sends it via SendGrid |

---

## 🗂️ Project Structure
deep_research/
├── deep_research.py       # Gradio UI entry point  
├── research_manager.py    # Orchestrates the full pipeline  
├── planner_agent.py       # Plans search queries  
├── search_agent.py        # Executes web searches  
├── writer_agent.py        # Writes the final report  
├── email_agent.py         # Sends the report via email  
├── pyproject.toml         # Project dependencies  
├── requirements.txt       # Pinned dependencies  
├── uv.lock                # uv lockfile  
└── .env                   # API keys (not committed)  

---

## ⚙️ Setup

### Prerequisites
- Python 3.12+
- [uv](https://github.com/astral-sh/uv) (recommended) or pip
- OpenAI API key
- SendGrid API key

### Installation

```bash
# Clone the repo
git clone https://github.com/mustafaT96/Deep_research.git
cd Deep_research

# Install dependencies using uv
uv sync

# Or using pip
pip install -r requirements.txt
```

### Environment Variables

Create a `.env` file in the root directory:

```env
OPENAI_API_KEY=your_openai_api_key
SENDGRID_API_KEY=your_sendgrid_api_key
```

---

## 🚀 Usage

```bash
python deep_research.py
```

This launches a Gradio UI in your browser. Enter any research topic and click **Run**. The system will:

1. Plan 5 targeted searches for your query
2. Execute all searches in parallel
3. Write a detailed markdown report
4. Email the report to you
5. Display the full report in the UI

---

## 📦 Key Dependencies

- [`openai-agents`](https://github.com/openai/openai-agents-python) — Agent orchestration framework
- [`gradio`](https://gradio.app/) — Web UI
- [`sendgrid`](https://sendgrid.com/) — Email delivery
- [`pydantic`](https://docs.pydantic.dev/) — Structured agent outputs
- `python-dotenv` — Environment variable management

---

## 📝 Output Example

The writer agent produces a structured report with:
- A short 2-3 sentence summary
- A full markdown report (5-10 pages, 1000+ words)
- Suggested follow-up research questions

---

## ⚠️ Notes

- `.env` is gitignored — never commit your API keys
- The search agent runs all searches concurrently using `asyncio` for speed
- Traces are available on [OpenAI Platform](https://platform.openai.com/traces) for debugging

---

## 👤 Author

**Mustafa Tariq**  
AI Engineer | [GitHub](https://github.com/mustafaT96)
