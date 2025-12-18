 # Scrap-LangGraph

 Developer Tools Research Agent that combines LangGraph, Gemini, and Firecrawl to discover, scrape, and summarize developer tooling for a given query. It runs as an interactive CLI that extracts likely tools from web articles, fetches official pages, analyzes developer-focused details (pricing, APIs, language support, integrations), and then produces concise recommendations.

 ## How it works
 1. **Extract tools from articles** – Firecrawl searches comparison articles and the LLM pulls out tool names.
 2. **Research each tool** – Official sites are scraped and summarized into structured fields (pricing, open-source status, tech stack, language support, integrations, API availability).
 3. **Generate recommendations** – The LLM provides a short recommendation tailored to the original query.

 Core flow is implemented in `src/workflow.py` using a LangGraph state machine with the `FirecrawlService`, `DeveloperToolsPrompts`, and Pydantic models in `src/models.py`.

 ## Setup
 - Python 3.13+
 - Environment variables:
   - `FIRECRAWL_API_KEY` – required for Firecrawl search/scrape
   - `GOOGLE_API_KEY` – required for `ChatGoogleGenerativeAI`
 - Install dependencies (e.g., `pip install .` or `uv pip install .`).

 ## Usage
 1. Create a `.env` file with the required keys.
 2. Run the CLI:
    ```bash
    python main.py
    ```
 3. Enter a developer tooling query (e.g., “feature flag platforms”); the agent will print summarized companies/tools and brief recommendations.
