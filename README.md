# 🚀 InterviewBit — AI-Powered Resume Builder

**InterviewBit** is a full-stack, GenAI-driven resume platform that transforms unstructured profile information into professional, job-tailored resumes.

It analyzes a target job description, rewrites resume content using Generative AI, calculates an NLP-based resume match score, and generates a clean, single-page, ATS-friendly PDF.

🔗 **Live Application:** https://interviewbit-frontend.vercel.app/login

---

## ✨ Key Features

### 🤖 Smart Resume Tailoring

Uses **Groq's `llama-3.3-70b-versatile` model** to customize resume content according to a target job description.

The AI can:

* Rewrite professional summaries
* Improve project descriptions
* Highlight relevant technical skills
* Generate stronger achievement-oriented bullet points
* Align resume content with job requirements

---

### 📄 Automated Resume Parsing

Users can provide raw or unstructured resume information, which is automatically converted into structured data.

The parser extracts information such as:

* Education
* Work Experience
* Technical Skills
* Projects
* Professional Summary

The extracted information is converted into structured **JSON** using specialized LLM prompts.

---

### 📊 Resume–Job Match Score

InterviewBit calculates how closely a generated resume matches the target job description using **Cosine Similarity**.

The custom similarity pipeline performs:

```text
Text Input
   ↓
Tokenization
   ↓
Word Frequency Vectorization
   ↓
Vector Dot Product
   ↓
Magnitude Calculation
   ↓
Cosine Similarity Score
```

This gives users a measurable indication of how relevant their resume is to the selected job.

---

### 📑 ATS-Friendly PDF Generation

The application generates compact, professional resumes using **PDFKit**.

Generated resumes are designed to be:

* Single-page
* ATS-friendly
* Clean and readable
* Professionally structured
* Inspired by LaTeX-style resume layouts

---

### 🧠 GenAI-Based Content Enhancement

Instead of simply formatting user data, InterviewBit intelligently improves resume content based on the job description.

For example:

```text
Original:
Built a React website for roommate matching.

AI-Tailored:
Developed a React-based roommate matching platform using
habit-based compatibility analysis and responsive UI components.
```

---

### 🛡️ In-Memory Database Fallback

The backend includes an in-memory fallback mechanism using JavaScript:

```javascript
Map()
```

and array-based storage.

If MongoDB becomes temporarily unavailable, profile and CV-generation workflows can continue using the in-memory data store.

This improves development reliability and application resilience.

---

## 🛠️ Tech Stack

| Layer                   | Technology               | Purpose                                      |
| ----------------------- | ------------------------ | -------------------------------------------- |
| **Frontend**            | React 18, Vite, ESLint   | Responsive Single Page Application           |
| **Backend**             | Node.js, Express.js      | REST API and business logic                  |
| **Database**            | MongoDB, Mongoose        | Persistent users, profiles and generated CVs |
| **AI**                  | Groq SDK — Llama 3.3 70B | Resume parsing and intelligent rewriting     |
| **NLP**                 | Custom Cosine Similarity | Resume-to-job relevance scoring              |
| **PDF Engine**          | PDFKit                   | Programmatic resume PDF generation           |
| **Frontend Deployment** | Vercel                   | Production hosting                           |

---

## 🏗️ System Workflow

```text
               ┌─────────────────┐
               │      User       │
               └────────┬────────┘
                        │
                        ▼
               ┌─────────────────┐
               │ React Frontend  │
               └────────┬────────┘
                        │
                        ▼
               ┌─────────────────┐
               │ Express Backend │
               └────────┬────────┘
                        │
           ┌────────────┼────────────┐
           │            │            │
           ▼            ▼            ▼
      MongoDB       Groq LLM     PDF Generator
           │            │            │
           │            ▼            │
           │     Resume Tailoring    │
           │            │            │
           │            ▼            │
           │    Cosine Similarity    │
           │            │            │
           └────────────┼────────────┘
                        │
                        ▼
                ATS Resume PDF
```

---

## 🗂️ Project Structure

```text
InterviewBit/
│
├── Backend/
│   │
│   ├── src/
│   │   ├── models/
│   │   ├── routes/
│   │   ├── services/
│   │   └── utils/
│   │
│   ├── package.json
│   ├── package-lock.json
│   └── server.js
│
├── Frontend/
   │
   ├── public/
   │
   ├── src/
   │   ├── components/
   │   ├── pages/
   │   └── ...
   │
   ├── eslint.config.js
   ├── index.html
   ├── package.json
   ├── package-lock.json
   └── vite.config.js



---

# 🚀 Getting Started

## 1️⃣ Clone the Repository

```bash
git clone https://github.com/pragati6306/Interviewbit.git
```

Move into the project directory:

```bash
cd Interviewbit
```

---

## 2️⃣ Backend Setup

Navigate to the backend:

```bash
cd Backend
```

Install dependencies:

```bash
npm install
```

Create a `.env` file inside the `Backend` directory:

```env
PORT=5000

GROQ_API_KEY=your_groq_api_key_here

MONGO_URI=your_mongodb_connection_string
```

> ⚠️ Never commit your `.env` file or API keys to GitHub.

Start the backend:

```bash
node server.js
```

Or, if a development script with Nodemon is configured:

```bash
npm run dev
```

The backend should run at:

```text
http://localhost:5000
```

---

## 3️⃣ Frontend Setup

Open another terminal and navigate to:

```bash
cd Frontend
```

Install dependencies:

```bash
npm install
```

Create a `.env` file if your frontend uses an environment variable for the backend URL:

```env
VITE_API_BASE_URL=http://localhost:5000
```

Start the Vite development server:

```bash
npm run dev
```

Open:

```text
http://localhost:5173
```

in your browser.

---

# 🔌 API Overview

| Method | Endpoint                | Description                                         |
| ------ | ----------------------- | --------------------------------------------------- |
| `POST` | `/api/auth/register`    | Register a new user                                 |
| `POST` | `/api/auth/login`       | Authenticate an existing user                       |
| `POST` | `/api/auth/profile`     | Create or update resume profile information         |
| `POST` | `/api/auth/generate-cv` | Generate an AI-tailored CV and similarity score     |
| `POST` | `/api/auth/download-cv` | Generate and stream the resume PDF                  |
| `POST` | `/api/profile/parse`    | Parse unstructured resume text into structured JSON |

---

# 🧩 Core Technologies

### Frontend

```text
React 18
Vite
JavaScript
CSS
ESLint
```

### Backend

```text
Node.js
Express.js
REST APIs
```

### Database

```text
MongoDB
Mongoose
```

### Generative AI

```text
Groq SDK
llama-3.3-70b-versatile
```

### Document Generation

```text
PDFKit
```

### NLP

```text
Tokenization
Vectorization
Dot Product
Vector Magnitude
Cosine Similarity
```

---

# 🎯 Main Workflow

```text
Create Account
      ↓
Add Resume Information
      ↓
Parse Profile Information
      ↓
Enter Target Job Description
      ↓
Generate AI-Tailored Resume
      ↓
Calculate Job Match Score
      ↓
Generate ATS-Friendly PDF
      ↓
Download Resume
```

---

# 🌟 Why InterviewBit?

Traditional resume builders mainly focus on formatting.

**InterviewBit focuses on relevance.**

It combines:

* Generative AI
* Natural Language Processing
* Resume parsing
* Job-description analysis
* Automated PDF generation
* Full-stack web development

to create resumes specifically tailored to individual job opportunities.

---

# 🔮 Future Improvements

Potential enhancements include:

* Multiple resume templates
* ATS keyword analysis
* Resume version history
* Job recommendation engine
* LinkedIn profile import
* Skill-gap analysis
* Resume analytics dashboard
* Cover-letter generation
* Multiple resume exports
* User dashboard with previous applications

---

# 👩‍💻 Author

**Pragati Pandey**

GitHub: [@pragati6306](https://github.com/pragati6306)

---

## 🔗 Project Links

🌐 **Live Application**
https://interviewbit-frontend.vercel.app/login

💻 **GitHub Repository**
https://github.com/pragati6306/Interviewbit

---

## ⭐ Support

If you find this project useful or interesting, consider giving the repository a **⭐ star on GitHub**.
