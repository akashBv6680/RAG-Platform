# 🚀 RAG Platform - Complete Deployment Guide

## Quick Start - Deploy in 5 Minutes

### Prerequisites
- GitHub Account (✓ You have this)
- Render Account (Free deployment) OR Railway/Vercel
- OpenAI API Key

### STEP 1: Deploy Backend (Flask) on Render

1. Go to https://render.com
2. Click "New +" → "Web Service"
3. Connect your GitHub repo: `akashBv6680/RAG-Platform`
4. Fill in:
   - **Name**: `rag-platform-api`
   - **Root Directory**: `backend`
   - **Runtime**: `Python 3.11`
   - **Build Command**: `pip install -r requirements.txt`
   - **Start Command**: `gunicorn app:app`
5. Add Environment Variables:
   ```
   DATABASE_URL=postgresql://[your-postgres-url]
   JWT_SECRET_KEY=your-super-secret-key-here
   OPENAI_API_KEY=sk-xxx
   FLASK_ENV=production
   ```
6. Click "Create Web Service"
7. Wait 5 minutes for deployment ✓

**Backend URL**: `https://rag-platform-api.onrender.com`

### STEP 2: Deploy Frontend (React) on Vercel

1. Go to https://vercel.com
2. Click "Add New" → "Project"
3. Import your GitHub repo
4. Configure:
   - **Framework**: React
   - **Root Directory**: `frontend`
   - **Build Command**: `npm run build`
5. Add Environment Variable:
   ```
   REACT_APP_API_URL=https://rag-platform-api.onrender.com
   ```
6. Click "Deploy"

**Frontend URL**: `https://rag-platform-xxx.vercel.app`

### STEP 3: Configure Database

**Option A: Free PostgreSQL (Recommended)**
1. Go to https://railway.app
2. Create New Project → Add PostgreSQL
3. Copy connection string
4. Update `DATABASE_URL` in Render dashboard

**Option B: SQLite (Local)**
- Leave as is (default)

## Project Structure

```
RAG-Platform/
├── backend/
│   ├── app.py
│   ├── config.py
│   ├── requirements.txt
│   ├── models/
│   ├── routes/
│   └── utils/
├── frontend/
│   ├── public/
│   ├── src/
│   └── package.json
├── docker-compose.yml
├── README.md
└── DEPLOYMENT.md
```

## Features

✅ User Authentication (Login/Register)
✅ Document Upload (PDF, TXT, CSV, HTML, XML, JSON)
✅ RAG-Powered Q&A (Using your Streamlit RAG)
✅ User Profile Management
✅ Session Management with JWT
✅ Responsive React Frontend
✅ Production-Ready Flask Backend
✅ Docker Support

## Local Development

### Backend
```bash
cd backend
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
pip install -r requirements.txt
python app.py
```

### Frontend
```bash
cd frontend
npm install
npm start
```

## API Endpoints

### Authentication
- `POST /api/auth/register` - Register user
- `POST /api/auth/login` - Login user
- `GET /api/auth/profile` - Get user profile
- `PUT /api/auth/profile` - Update profile
- `POST /api/auth/change-password` - Change password

### RAG
- `POST /api/rag/upload` - Upload document
- `GET /api/rag/documents` - Get user documents
- `POST /api/rag/query` - Query RAG system
- `DELETE /api/rag/documents/<id>` - Delete document

## Environment Variables

### Backend `.env`
```
FLASK_ENV=production
DATABASE_URL=postgresql://user:pass@localhost/db
JWT_SECRET_KEY=your-secret-key
OPENAI_API_KEY=sk-xxx
LLM_MODEL=gpt-3.5-turbo
TEMPERATURE=0.7
CORS_ORIGINS=http://localhost:3000,https://yourdomain.com
```

### Frontend `.env`
```
REACT_APP_API_URL=https://rag-platform-api.onrender.com
```

## Troubleshooting

**Backend Not Connecting?**
- Check API URL in frontend
- Verify CORS settings
- Check API logs on Render

**Login Not Working?**
- Verify DATABASE_URL is correct
- Check JWT_SECRET_KEY is set
- Clear browser localStorage

**Document Upload Failed?**
- Check file size (max 200MB)
- Verify file type is allowed
- Check backend logs

## Production Checklist

- [ ] Set `FLASK_DEBUG=False`
- [ ] Use strong JWT_SECRET_KEY
- [ ] Configure real PostgreSQL database
- [ ] Set CORS_ORIGINS to your domain only
- [ ] Enable HTTPS
- [ ] Set up monitoring/logging
- [ ] Configure backups
- [ ] Test all API endpoints
- [ ] Update API URL in frontend
- [ ] Set secure cookie settings

## Support & Resources

- GitHub: https://github.com/akashBv6680/RAG-Platform
- Flask Docs: https://flask.palletsprojects.com
- React Docs: https://react.dev
- Render Docs: https://render.com/docs
- Vercel Docs: https://vercel.com/docs

---

**Deployed Successfully? Star the repo! ⭐**
