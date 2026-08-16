# Deep-Agents

Learning project exploring the [`deepagents`](https://github.com/langchain-ai/deepagents) framework for building autonomous, tool-using AI agents with LangChain and Groq.

## What's Inside

| Notebook | What it covers |
|---|---|
| `1-basicdeepagent.ipynb` | Creating a simple Deep Agent from scratch |
| `2-contextengineering.ipynb` | Context engineering techniques for agents |
| `3-backends.ipynb` | Comparing agent storage backends: `StateBackend`, `FilesystemBackend`, and `StoreBackend` |
| `4-subagents.ipynb` | Delegating work to specialized subagents, including structured output |

## Tech Stack

- **[deepagents](https://pypi.org/project/deepagents/)** — agent framework (planning, tool use, virtual filesystem)
- **LangChain / LangGraph** — orchestration and state management
- **Groq** — LLM inference (`openai/gpt-oss-120b`)
- **Tavily** — web search tool for research subagents
- **python-dotenv** — environment variable management

## Setup

1. Clone the repo:
   ```bash
   git clone https://github.com/Nasreen1717/Deep-Agents.git
   cd Deep-Agents/deepagentstdemo
   ```

2. Create and activate a virtual environment:
   ```bash
   python -m venv .venv
   .venv\Scripts\activate      # Windows
   source .venv/bin/activate   # macOS/Linux
   ```

3. Install dependencies:
   ```bash
   pip install -r requiremtents.txt
   ```

4. Create a `.env` file in the project root with your API keys:
   ```
   GROQ_API_KEY=your_groq_key_here
   TAVILY_API_KEY=your_tavily_key_here
   OPENAI_API_KEY=your_openai_key_here
   ```

5. Open any notebook in VS Code / Jupyter and run the cells top to bottom.

## Notes

- The default model used across notebooks is `groq:openai/gpt-oss-120b` (served via Groq, not OpenAI directly).
- Groq's `on_demand` tier does **not** allow combining `response_format` (structured output) with tool/function calling in a single request — see `4-subagents.ipynb` for the workaround (run the tool-using agent first, then a separate structured-output call).
- `FilesystemBackend` writes real files to disk — point `root_dir` at a scratch folder, not anything important.

## Author

Built by [Nasreen1717](https://github.com/Nasreen1717) while learning agent engineering through the Panaversity / PIAIC program.