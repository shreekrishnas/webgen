# WebinarIQ — White-Label Webinar Analytics Platform

WebinarIQ is an AI-powered webinar analytics platform that tracks speaker performance, audience engagement, and outcomes. This is a white-label version that any company can deploy under their own brand.

## Quick Start

### 1. Environment Variables

Set these environment variables before deploying:

| Variable | Description | Default |
|---|---|---|
| `COMPANY_NAME` | Your company/organisation name | `Your Company` |
| `COMPANY_DOMAIN` | Your email domain (used for speaker defaults) | `yourcompany.com` |
| `COMPANY_DESC` | One-line description of your business | `a company running professional webinars` |
| `DATABASE_URL` | PostgreSQL connection string (Supabase recommended) | *(required)* |
| `OPENROUTER_API_KEY` | API key from [OpenRouter](https://openrouter.ai/) for AI features (insights, Q&A, email drafts) | *(optional — AI features disabled without it)* |
| `APP_URL` | Public URL of your deployed app | `https://webinar-analytics-six.vercel.app` |

### 2. Database (Supabase)

1. Create a project at [supabase.com](https://supabase.com/).
2. Copy the **Connection string (URI)** from Settings > Database.
3. Set it as `DATABASE_URL`.
4. Tables are auto-created on first startup. To seed sample data, run:
   ```bash
   python seed_data.py
   ```

### 3. Deploy on Vercel

1. Push this repo to GitHub.
2. Import the repo in [Vercel](https://vercel.com/).
3. Add the environment variables above in Vercel's project settings.
4. Deploy — the `vercel.json` and `api/index.py` handle routing automatically.

### 4. Local Development

```bash
pip install -r requirements.txt
export DATABASE_URL="postgresql://..."
export COMPANY_NAME="Acme Corp"
export COMPANY_DOMAIN="acmecorp.com"
python main.py
```

The app runs at `http://localhost:8000`.

## Project Structure

- `main.py` — FastAPI application with all API routes and AI features
- `models.py` — SQLAlchemy ORM models
- `database.py` — Database connection setup
- `crud.py` — CRUD operations
- `schemas.py` — Pydantic request/response schemas
- `seed_data.py` — Sample data seeder
- `static/` — Frontend (single-page app)
- `api/index.py` — Vercel serverless entry point

## Customisation

- **Branding**: Set `COMPANY_NAME`, `COMPANY_DOMAIN`, and `COMPANY_DESC` env vars.
- **Seed data**: Edit `seed_data.py` to populate speakers and webinars relevant to your business.
- **CSS**: The `static/styles.css` file uses CSS custom properties (`--rh-*`) that you can override for your brand colours.
