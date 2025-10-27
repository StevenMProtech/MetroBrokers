# MetroBrokers Next Chapter Campaign Dashboard

## Features

- **Dashboard**: Real-time submission tracking with MetroBrokers branding
- **Test Page**: Live email preview with working form (`/test`)
- **Submissions View**: Full table of all submissions
- **CSV Export**: Download submissions for CRM import
- **API**: JSON endpoint for integrations

## Deployment Options

### Option 1: Render.com (Recommended - Free)

1. Push this folder to a GitHub repository
2. Go to [render.com](https://render.com)
3. Click "New +" → "Web Service"
4. Connect your GitHub repo
5. Render will auto-detect the `render.yaml` config
6. Click "Create Web Service"
7. Your app will be live at: `https://metrobrokers-dashboard.onrender.com`

### Option 2: Railway.app (Free)

1. Push to GitHub
2. Go to [railway.app](https://railway.app)
3. Click "New Project" → "Deploy from GitHub repo"
4. Select your repo
5. Railway will auto-detect Python and deploy
6. Get your live URL from the dashboard

### Option 3: Vercel (Free)

1. Install Vercel CLI: `npm i -g vercel`
2. Run: `vercel`
3. Follow prompts
4. Your app will be live

### Option 4: PythonAnywhere (Free)

1. Go to [pythonanywhere.com](https://www.pythonanywhere.com)
2. Create free account
3. Upload files via "Files" tab
4. Set up web app pointing to `app.py`
5. Install requirements: `pip install -r requirements.txt`

## Local Development

```bash
pip install -r requirements.txt
python app.py
```

Visit: http://localhost:5002

## Routes

- `/` - Dashboard
- `/test` - Email preview & test form
- `/submissions` - All submissions table
- `/api/submissions` - JSON API
- `/export` - CSV download
- `/api/submit` - Form submission endpoint (POST)

## Environment Variables

- `PORT` - Server port (default: 5001)

## Data Storage

Uses simple JSON file storage (`submissions.json`). For production with high volume, consider upgrading to PostgreSQL or MongoDB.

## MetroBrokers Branding

- Primary Green: `#5a9f3e`
- Accent Orange: `#f7931e`
- Gradients and modern design throughout

