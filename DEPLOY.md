# MetroBrokers Dashboard - Permanent Deployment Guide

## Quick Deploy to Render.com (Recommended - 5 minutes)

### Step 1: Create GitHub Repository

1. Go to https://github.com/new
2. Repository name: `metrobrokers-dashboard`
3. Set to **Public** (required for free Render deployment)
4. Click "Create repository"

### Step 2: Upload Files

**Option A: Using GitHub Web Interface**
1. On your new repo page, click "uploading an existing file"
2. Drag and drop ALL files from the `metrobrokers_deploy` folder:
   - `app.py`
   - `email_template.html`
   - `requirements.txt`
   - `render.yaml`
   - `README.md`
3. Click "Commit changes"

**Option B: Using Git Command Line**
```bash
cd metrobrokers_deploy
git remote add origin https://github.com/YOUR_USERNAME/metrobrokers-dashboard.git
git branch -M main
git push -u origin main
```

### Step 3: Deploy to Render

1. Go to https://render.com
2. Sign up/login (can use GitHub account)
3. Click **"New +"** → **"Web Service"**
4. Click **"Connect GitHub"** and authorize Render
5. Find and select your `metrobrokers-dashboard` repository
6. Render will auto-detect the `render.yaml` config
7. Click **"Create Web Service"**

### Step 4: Get Your Permanent URL

- Render will build and deploy (takes ~2-3 minutes)
- Your permanent URL will be: `https://metrobrokers-dashboard.onrender.com`
- You can customize this in Render settings

### Step 5: Update Email Form (Important!)

Once deployed, update the form action URL in your email template:

1. Open `email_template.html`
2. Find line ~49: `<form action="https://5002-icblfgg80tscggjvf4889-0604546c.manusvm.computer/api/submit"`
3. Replace with: `<form action="https://YOUR-APP-NAME.onrender.com/api/submit"`
4. Re-upload to GitHub
5. Render will auto-deploy the update

---

## Alternative: Deploy to Railway.app (Also Free)

### Step 1: Create GitHub Repository (same as above)

### Step 2: Deploy to Railway

1. Go to https://railway.app
2. Sign up with GitHub
3. Click **"New Project"** → **"Deploy from GitHub repo"**
4. Select `metrobrokers-dashboard`
5. Railway auto-detects Python and deploys
6. Click on your deployment → **"Settings"** → **"Domains"**
7. Click **"Generate Domain"**
8. Your URL: `https://metrobrokers-dashboard.up.railway.app`

---

## Alternative: Deploy to PythonAnywhere (Free)

### Step 1: Sign Up

1. Go to https://www.pythonanywhere.com
2. Create free account

### Step 2: Upload Files

1. Go to **"Files"** tab
2. Upload all files from `metrobrokers_deploy` folder

### Step 3: Install Dependencies

1. Go to **"Consoles"** tab → **"Bash"**
2. Run:
```bash
pip3 install --user flask flask-cors gunicorn
```

### Step 4: Configure Web App

1. Go to **"Web"** tab → **"Add a new web app"**
2. Choose **"Manual configuration"** → **"Python 3.10"**
3. In **"Code"** section:
   - Source code: `/home/YOUR_USERNAME/`
   - Working directory: `/home/YOUR_USERNAME/`
4. In **"WSGI configuration file"**, replace contents with:
```python
import sys
path = '/home/YOUR_USERNAME'
if path not in sys.path:
    sys.path.append(path)

from app import app as application
```
5. Click **"Reload"**
6. Your URL: `https://YOUR_USERNAME.pythonanywhere.com`

---

## What You Get

### Live URLs:
- `/` - Dashboard with email preview & stats
- `/submissions` - All submissions table
- `/export` - CSV download
- `/api/submissions` - JSON API
- `/test` - Standalone email preview

### Features:
- ✅ Real-time submission tracking
- ✅ Color-coded priority badges
- ✅ AI-suggested follow-up categories
- ✅ CSV export for CRM
- ✅ MetroBrokers branding throughout
- ✅ Mobile responsive
- ✅ Zero downtime (on paid plans)

---

## Free Tier Limits

### Render.com
- ✅ Free forever
- ⚠️ Sleeps after 15 min inactivity (wakes in ~30 seconds)
- ✅ 750 hours/month (enough for 24/7 if only one app)
- ✅ Custom domain support

### Railway.app
- ✅ $5 free credit/month
- ✅ No sleep
- ✅ ~500 hours/month
- ✅ Custom domain support

### PythonAnywhere
- ✅ Free forever
- ✅ Always on (no sleep)
- ⚠️ Limited to pythonanywhere.com subdomain
- ⚠️ Manual updates (no auto-deploy)

---

## Recommended: Render.com

**Why?**
- Auto-deploys from GitHub (push = deploy)
- Free SSL certificate
- Easy custom domain setup
- Professional URLs
- Simple dashboard

**Only downside:** Sleeps after 15 min (but wakes fast)

---

## Need Help?

All files are ready to deploy. Just:
1. Upload to GitHub
2. Connect to Render
3. Click deploy
4. Update form URL

That's it!

---

## Custom Domain (Optional)

Once deployed, you can add a custom domain like `dashboard.metrobrokers.com`:

**On Render:**
1. Go to your service → **"Settings"** → **"Custom Domain"**
2. Add `dashboard.metrobrokers.com`
3. Add the CNAME record to your DNS:
   - Name: `dashboard`
   - Value: `your-app.onrender.com`

**On Railway:**
1. Go to **"Settings"** → **"Domains"**
2. Click **"Custom Domain"**
3. Follow DNS instructions

---

Your dashboard is ready to go live! 🚀

