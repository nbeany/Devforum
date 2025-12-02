# DevForum - Q&A Platform

<div align="center">

![DevForum](frontend/public/fav.png)

A modern, full-stack Question and Answer platform built with React, Node.js, and PostgreSQL.

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Node.js](https://img.shields.io/badge/Node.js-v16+-green.svg)](https://nodejs.org/)
[![React](https://img.shields.io/badge/React-18.x-blue.svg)](https://reactjs.org/)
[![PostgreSQL](https://img.shields.io/badge/PostgreSQL-13+-blue.svg)](https://www.postgresql.org/)

[Features](#features) • [Tech Stack](#tech-stack) • [Installation](#installation) • [Usage](#usage) • [API Documentation](#api-documentation) • [Contributing](#contributing)

</div>

---

## 📋 Table of Contents

- [Overview](#overview)
- [Features](#features)
- [Tech Stack](#tech-stack)
- [Prerequisites](#prerequisites)
- [Installation](#installation)
- [Configuration](#configuration)
- [Running the Application](#running-the-application)
- [Project Structure](#project-structure)
- [API Documentation](#api-documentation)
- [Database Schema](#database-schema)
- [Deployment](#deployment)
- [Contributing](#contributing)
- [License](#license)

---

## 🎯 Overview

DevForum is a community-driven Q&A platform designed to facilitate knowledge sharing among developers and tech enthusiasts. Users can ask questions, provide answers, search for topics, and engage with the community through an intuitive and modern interface.

### Live Demo
- **Frontend**: [Your Vercel URL]
- **Backend**: [Your Render/Railway URL]

---

## ✨ Features

### User Management
- 🔐 **Secure Authentication** - JWT-based authentication system
- 👤 **User Registration & Login** - Complete account management
- 🔒 **Protected Routes** - Secure access to authenticated features

### Question Management
- ❓ **Ask Questions** - Post questions with titles, descriptions, and tags
- 📝 **Edit & Delete** - Manage your own questions
- 🏷️ **Tag System** - Organize questions by topics
- 🔍 **Advanced Search** - Find questions by keywords
- 🎯 **Filter by Tags** - Browse questions by specific topics

### Answer Management
- 💬 **Post Answers** - Contribute knowledge to the community
- ✏️ **Edit Answers** - Update your responses
- 🗑️ **Delete Answers** - Remove your contributions
- 👥 **User Attribution** - See who answered each question

### User Experience
- 🎨 **Modern UI** - Beautiful, responsive design with Tailwind CSS
- 📱 **Mobile Responsive** - Works seamlessly on all devices
- 🌓 **Dark Mode Support** - Easy on the eyes (if implemented)
- 🔔 **Toast Notifications** - Real-time feedback for user actions
- ⚡ **Fast & Optimized** - Built with performance in mind

---

## 🛠️ Tech Stack

### Frontend
- **Framework**: React 18.3
- **Language**: TypeScript
- **Routing**: React Router DOM v6
- **State Management**: React Context API
- **HTTP Client**: Axios
- **UI Components**: Radix UI
- **Styling**: Tailwind CSS
- **Form Handling**: React Hook Form + Zod
- **Build Tool**: Vite
- **Icons**: Lucide React

### Backend
- **Runtime**: Node.js
- **Framework**: Express.js 5
- **Language**: JavaScript (ES6+)
- **Authentication**: JWT (jsonwebtoken)
- **Password Hashing**: bcryptjs
- **ORM**: Sequelize
- **Database**: PostgreSQL
- **Environment**: dotenv
- **CORS**: cors middleware

### Development Tools
- **Backend Dev Server**: Nodemon
- **Code Quality**: ESLint
- **Version Control**: Git

---

## 📋 Prerequisites

Before you begin, ensure you have the following installed:

- **Node.js** (v16.x or higher) - [Download](https://nodejs.org/)
- **npm** (v8.x or higher) - Comes with Node.js
- **PostgreSQL** (v13.x or higher) - [Download](https://www.postgresql.org/download/)
- **Git** - [Download](https://git-scm.com/)

### Verify Installation

```bash
node --version
npm --version
psql --version
git --version
```

---

## 🚀 Installation

### 1. Clone the Repository

```bash
git clone https://github.com/yourusername/devforum.git
cd devforum
```

### 2. Install Backend Dependencies

```bash
cd backend
npm install
```

### 3. Install Frontend Dependencies

```bash
cd ../frontend
npm install
```

---

## ⚙️ Configuration

### Backend Configuration

1. **Create a `.env` file in the `backend` directory:**

```bash
cd backend
touch .env  # Linux/Mac
# or
echo. > .env  # Windows
```

2. **Add the following environment variables:**

```env
# Database Configuration
DB_HOST=localhost
DB_PORT=5432
DB_DIALECT=postgres
DB_USER=postgres
DB_PASS=your_postgresql_password
DB_NAME=devforum

# Server Configuration
PORT=5000
NODE_ENV=development

# JWT Configuration
JWT_SECRET=your_super_secure_jwt_secret_key_change_this_in_production
```

### PostgreSQL Database Setup

1. **Create a new PostgreSQL database:**

```bash
# Login to PostgreSQL
psql -U postgres

# Create database
CREATE DATABASE devforum;

# Exit PostgreSQL
\q
```

2. **Update credentials**: Make sure the `DB_USER` and `DB_PASS` in your `.env` file match your PostgreSQL credentials.

### Frontend Configuration (Optional)

If you need to change the backend API URL:

1. Open `frontend/src/services/api.ts`
2. Update the `API_URL` constant:

```typescript
const API_URL = 'http://localhost:5000'; // Change if needed
```

---

## 🏃 Running the Application

### Development Mode

#### Option 1: Run Both Servers Separately

**Terminal 1 - Backend:**
```bash
cd backend
npm run dev
# Server runs on http://localhost:5000
```

**Terminal 2 - Frontend:**
```bash
cd frontend
npm run dev
# Application runs on http://localhost:5173
```

#### Option 2: Use the Start Script (if available)

```bash
# From the root directory
chmod +x start.sh  # Linux/Mac only
./start.sh
```

### Production Mode

**Build Frontend:**
```bash
cd frontend
npm run build
```

**Start Backend:**
```bash
cd backend
npm start
```

---

## 📁 Project Structure

```
devforum/
├── backend/
│   ├── config/
│   │   └── db.js                 # Database configuration
│   ├── controllers/
│   │   ├── authController.js      # Authentication logic
│   │   ├── questionController.js  # Question CRUD operations
│   │   └── answerController.js    # Answer CRUD operations
│   ├── middleware/
│   │   └── authMiddleware.js      # JWT verification
│   ├── models/
│   │   ├── index.js               # Model exports
│   │   ├── User.js                # User model
│   │   ├── Question.js            # Question model
│   │   └── Answer.js              # Answer model
│   ├── routes/
│   │   ├── auth.js                # Auth routes
│   │   ├── questions.js           # Question routes
│   │   └── answers.js             # Answer routes
│   ├── .env                       # Environment variables (create this)
│   ├── package.json
│   └── server.js                  # Entry point
│
├── frontend/
│   ├── public/                    # Static assets
│   ├── src/
│   │   ├── components/
│   │   │   ├── ui/                # Reusable UI components
│   │   │   ├── AnswerCard.tsx
│   │   │   ├── Navbar.tsx
│   │   │   ├── ProtectedRoute.tsx
│   │   │   ├── QuestionCard.tsx
│   │   │   ├── SearchBar.tsx
│   │   │   └── TagFilter.tsx
│   │   ├── context/
│   │   │   └── AuthContext.tsx    # Authentication context
│   │   ├── hooks/
│   │   │   └── use-toast.ts       # Custom hooks
│   │   ├── lib/
│   │   │   └── utils.ts           # Utility functions
│   │   ├── pages/
│   │   │   ├── Home.tsx           # Homepage
│   │   │   ├── Login.tsx          # Login page
│   │   │   ├── Register.tsx       # Registration page
│   │   │   ├── AskQuestion.tsx    # Create question
│   │   │   ├── QuestionDetail.tsx # Question detail & answers
│   │   │   ├── MyQuestions.tsx    # User's questions
│   │   │   └── NotFound.tsx       # 404 page
│   │   ├── services/
│   │   │   └── api.ts             # API service layer
│   │   ├── App.tsx                # Main app component
│   │   ├── main.tsx               # Entry point
│   │   └── index.css              # Global styles
│   ├── package.json
│   ├── tsconfig.json
│   ├── vite.config.ts
│   └── tailwind.config.ts
│
├── LICENSE
├── README.md
└── start.sh                       # Startup script (optional)
```

---

## 📡 API Documentation

### Base URL
```
http://localhost:5000
```

### Authentication Endpoints

#### Register User
```http
POST /auth/register
Content-Type: application/json

{
  "username": "johndoe",
  "firstname": "John",
  "lastname": "Doe",
  "email": "john@example.com",
  "password": "securePassword123"
}
```

**Response:**
```json
{
  "userid": 1,
  "username": "johndoe",
  "firstname": "John",
  "lastname": "Doe",
  "email": "john@example.com"
}
```

#### Login User
```http
POST /auth/login
Content-Type: application/json

{
  "email": "john@example.com",
  "password": "securePassword123"
}
```

**Response:**
```json
{
  "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...",
  "user": {
    "userid": 1,
    "username": "johndoe",
    "email": "john@example.com",
    "firstname": "John",
    "lastname": "Doe"
  }
}
```

### Question Endpoints

#### Get All Questions
```http
GET /questions
GET /questions?tag=javascript
GET /questions?q=react
```

#### Get Question by ID
```http
GET /questions/:questionid
```

#### Create Question (Protected)
```http
POST /questions
Authorization: Bearer <token>
Content-Type: application/json

{
  "title": "How to use React Hooks?",
  "description": "I'm new to React and want to learn about hooks...",
  "tag": "React"
}
```

#### Update Question (Protected)
```http
PUT /questions/:questionid
Authorization: Bearer <token>
Content-Type: application/json

{
  "title": "Updated title",
  "description": "Updated description",
  "tag": "UpdatedTag"
}
```

#### Delete Question (Protected)
```http
DELETE /questions/:questionid
Authorization: Bearer <token>
```

### Answer Endpoints

#### Get Answers for Question
```http
GET /answers/:questionid
```

#### Create Answer (Protected)
```http
POST /answers
Authorization: Bearer <token>
Content-Type: application/json

{
  "questionid": "uuid-here",
  "answer": "You can use useState and useEffect hooks..."
}
```

#### Update Answer (Protected)
```http
PUT /answers/:answerid
Authorization: Bearer <token>
Content-Type: application/json

{
  "answer": "Updated answer content"
}
```

#### Delete Answer (Protected)
```http
DELETE /answers/:answerid
Authorization: Bearer <token>
```

---

## 🗃️ Database Schema

### Users Table
```sql
userid      INTEGER PRIMARY KEY AUTO INCREMENT
username    VARCHAR UNIQUE NOT NULL
firstname   VARCHAR
lastname    VARCHAR
email       VARCHAR UNIQUE NOT NULL
password    VARCHAR NOT NULL
createdAt   TIMESTAMP
updatedAt   TIMESTAMP
```

### Questions Table
```sql
questionid  UUID PRIMARY KEY
userid      INTEGER FOREIGN KEY → Users(userid)
title       VARCHAR NOT NULL
description TEXT
tag         VARCHAR
createdAt   TIMESTAMP
updatedAt   TIMESTAMP
```

### Answers Table
```sql
answerid    UUID PRIMARY KEY
userid      INTEGER FOREIGN KEY → Users(userid)
questionid  UUID FOREIGN KEY → Questions(questionid)
answer      TEXT NOT NULL
createdAt   TIMESTAMP
updatedAt   TIMESTAMP
```

---

## 🚢 Deployment

### Backend Deployment (Render/Railway)

1. **Prepare your repository:**
   - Ensure `.env` is in `.gitignore`
   - Commit all changes

2. **Deploy to Render:**
   - Create a new Web Service
   - Connect your GitHub repository
   - Set environment variables
   - Deploy

3. **Environment Variables to Set:**
   ```
   DATABASE_URL=postgresql://user:pass@host:5432/dbname
   JWT_SECRET=your_production_jwt_secret
   NODE_ENV=production
   ```

### Frontend Deployment (Vercel)

1. **Build the project:**
   ```bash
   cd frontend
   npm run build
   ```

2. **Deploy to Vercel:**
   ```bash
   npm install -g vercel
   vercel
   ```

3. **Update API URL:**
   - Change the API_URL in `frontend/src/services/api.ts` to your backend URL

---

## 🤝 Contributing

Contributions are welcome! Please follow these steps:

1. **Fork the repository**
2. **Create a feature branch**
   ```bash
   git checkout -b feature/AmazingFeature
   ```
3. **Commit your changes**
   ```bash
   git commit -m 'Add some AmazingFeature'
   ```
4. **Push to the branch**
   ```bash
   git push origin feature/AmazingFeature
   ```
5. **Open a Pull Request**

### Code Style Guidelines

- Use meaningful variable and function names
- Comment complex logic
- Follow existing code formatting
- Write clean, readable code
- Test your changes before submitting

---

## 🐛 Troubleshooting

### Common Issues

**Issue: Database connection failed**
```
Solution: 
1. Ensure PostgreSQL is running
2. Check database credentials in .env
3. Verify database exists: psql -U postgres -l
```

**Issue: Frontend can't connect to backend**
```
Solution:
1. Verify backend is running on port 5000
2. Check API_URL in frontend/src/services/api.ts
3. Ensure CORS is configured correctly
```

**Issue: JWT token errors**
```
Solution:
1. Clear browser localStorage
2. Check JWT_SECRET in .env
3. Ensure token is being sent in Authorization header
```

---

## 📝 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

## 👥 Authors

- **Your Name** - *Initial work* - [YourGitHub](https://github.com/yourusername)

---

## 🙏 Acknowledgments

- React community for amazing tools and libraries
- Radix UI for accessible component primitives
- Tailwind CSS for utility-first styling
- Sequelize for powerful ORM capabilities

---

## 📞 Contact & Support

- **Email**: your.email@example.com
- **GitHub Issues**: [Create an issue](https://github.com/yourusername/devforum/issues)
- **Discussions**: [Join the discussion](https://github.com/yourusername/devforum/discussions)

---

<div align="center">

**⭐ If you find this project helpful, please give it a star! ⭐**

Made with ❤️ by developers, for developers

</div>
