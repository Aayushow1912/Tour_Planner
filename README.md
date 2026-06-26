# Multi Agent Tour Planner

A Streamlit web app that uses a LangGraph agent workflow to plan trips with
flight lookup, hotel search, itinerary generation, and a final travel summary.

## Run locally

```powershell
python -m venv langgraph_env2
.\langgraph_env2\Scripts\Activate.ps1
pip install -r requirements.txt
Copy-Item .env.example .env
streamlit run frontend.py
```

Fill `.env` with real values before starting the app:

- `DATABASE_URL`: PostgreSQL connection string used by LangGraph checkpointing
- `GROQ_API_KEY`: Groq API key for `llama-3.3-70b-versatile`
- `TAVILY_API_KEY`: Tavily API key for hotel/search results
- `AVIATIONSTACK_API_KEY`: AviationStack API key for flight results

## Deploy

This app is ready for services that run Streamlit apps from a Git repository,
such as Render, Railway, Heroku, or Streamlit Community Cloud.

### Render or Railway

1. Push this repository to GitHub.
2. Create a new web service from the repo.
3. Use Python 3.12.
4. Build command:

```bash
pip install -r requirements.txt
```

5. Start command:

```bash
streamlit run frontend.py --server.port $PORT --server.address 0.0.0.0
```

6. Add the environment variables from `.env.example`.
7. Attach or provide a PostgreSQL database and set `DATABASE_URL`.

### Streamlit Community Cloud

1. Push this repository to GitHub.
2. Create a new app and set the main file to `frontend.py`.
3. Add the values from `.env.example` in app secrets/environment settings.
4. Use an external hosted PostgreSQL database for `DATABASE_URL`.
