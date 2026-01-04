# 🚀 RAG Platform - Full-Stack Application

**Production-ready RAG (Retrieval-Augmented Generation) application with user authentication, document management, and AI-powered question answering.**

## ✨ Features

✅ **User Authentication**
- Register/Login with JWT tokens
- Secure password hashing with Werkzeug
- Session management
- Profile management

✅ **Document Management**
- Upload multiple file types (PDF, TXT, CSV, HTML, XML, JSON)
- Automatic chunking and processing
- Document metadata tracking

✅ **RAG AI Engine**
- LangChain integration
- OpenAI GPT-3.5-turbo powered Q&A
- Context-aware responses
- Multi-document support

✅ **Modern Tech Stack**
- React.js frontend with responsive design
- Flask backend with SQLAlchemy ORM
- PostgreSQL/SQLite database
- JWT authentication
- Docker containerization

## 📁 Project Structure

```
RAG-Platform/
├── backend/
│   ├── app.py                 # Flask application entry point
│   ├── config.py              # Configuration settings
│   ├── requirements.txt        # Python dependencies
│   ├── .env.example            # Environment variables template
│   ├── models/                 # Database models
│   │   ├── user.py             # User model
│   │   └── document.py         # Document model
│   ├── routes/                 # API routes
│   │   ├── auth.py             # Authentication endpoints
│   │   └── rag.py              # RAG endpoints
│   └── utils/                  # Utility functions
│       └── rag_handler.py      # RAG processing logic
├── frontend/                   # React application (TBD)
├── DEPLOYMENT.md               # Deployment instructions
├── README.md                   # This file
└── .gitignore                  # Git ignore rules
```

## 🚀 Quick Start

### Backend Setup

```bash
# Navigate to backend
cd backend

# Create virtual environment
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate

# Install dependencies
pip install -r requirements.txt

# Configure environment
cp .env.example .env
# Edit .env with your settings

# Run Flask application
python app.py
```

Backend will be available at: `http://localhost:5000`

## 📚 API Documentation

### Authentication Endpoints

**Register User**
```bash
POST /api/auth/register
Content-Type: application/json

{
  "username": "john_doe",
  "email": "john@example.com",
  "password": "secure_password",
  "first_name": "John",
  "last_name": "Doe",
  "company": "Acme Corp"
}
```

**Login User**
```bash
POST /api/auth/login
Content-Type: application/json

{
  "username": "john_doe",
  "password": "secure_password"
}
```

Response:
```json
{
  "access_token": "eyJ0eXAiOiJKV1QiLCJhbGc...",
  "user": {
    "id": 1,
    "username": "john_doe",
    "email": "john@example.com"
  }
}
```

**Get Profile**
```bash
GET /api/auth/profile
Authorization: Bearer {access_token}
```

### RAG Endpoints

**Upload Document**
```bash
POST /api/rag/upload
Authorization: Bearer {access_token}
Content-Type: multipart/form-data

File: document.pdf
```

**Get User Documents**
```bash
GET /api/rag/documents
Authorization: Bearer {access_token}
```

**Query RAG System**
```bash
POST /api/rag/query
Authorization: Bearer {access_token}
Content-Type: application/json

{
  "query": "What is the main topic of the document?",
  "document_id": 1
}
```

## 🔧 Environment Variables

Create a `.env` file in the `backend` directory:

```bash
# Flask
FLASK_ENV=development
FLASK_DEBUG=True

# Database
DATABASE_URL=sqlite:///rag_app.db
# Or for PostgreSQL:
# DATABASE_URL=postgresql://user:password@localhost:5432/rag_db

# JWT
JWT_SECRET_KEY=your-super-secret-key-here

# OpenAI
OPENAI_API_KEY=sk-your-api-key-here

# LLM Configuration
LLM_MODEL=gpt-3.5-turbo
TEMPERATURE=0.7

# CORS
CORS_ORIGINS=http://localhost:3000,http://localhost:5000
```

## 📦 Dependencies

### Backend
- Flask 3.0.0
- Flask-CORS 4.0.0
- Flask-SQLAlchemy 3.1.1
- Flask-JWT-Extended 4.5.3
- LangChain 0.1.1
- OpenAI 1.3.8
- SQLAlchemy 2.0.23
- gunicorn 21.2.0

## 🌐 Deployment

See [DEPLOYMENT.md](./DEPLOYMENT.md) for detailed deployment instructions for:
- Render (Backend)
- Vercel (Frontend)
- Railway (Database)
- Docker

## 🔒 Security

- Passwords hashed with Werkzeug
- JWT token-based authentication
- SQL injection prevention with SQLAlchemy ORM
- CORS configuration for secure cross-origin requests
- Environment variables for sensitive data

## 📝 License

MIT License - Feel free to use this project for personal and commercial purposes.

## 🤝 Contributing

Contributions are welcome! Please feel free to submit pull requests.

## 📧 Support

For issues or questions, please open a GitHub issue.

---

**Made with ❤️ by Akash**

Star ⭐ this repo if you find it useful!
